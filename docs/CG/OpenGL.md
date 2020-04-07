# OpenGL Note

管线、实现经验、注意点

## 关于贴图

### glActiveTexture与glBindTexture
&emsp;&emsp;在openGL中，存在一系列的texture unit，通过 glActiveTexture激活当前的texture unit，默认的unit是0。而当前的texture unit中存在多个texture target，例如GL_TEXTURE_2D, GL_TEXTURE_CUBEMAP。

&emsp;&emsp;通过glBindTexture将一个texture object绑定到当前激活的texture unit的texture target上。然后通过glTexImage2D, glTexParameteri等函数改变texture object的状态。

### 创建texture object的时候需要指定texture unit吗？
&emsp;&emsp;并不需要，无论当前是哪个texture unit，不影响创建texture object。创建好的texture object可以绑定到其他texture unit的texture target上使用。

&emsp;&emsp;创建texture object后(glCreateTexture)，第一次调用glBindTexture，决定了texture object的类型，比如调用的是glBindTexture(GL_TEXTURE_2D)，那么这个texture object就是一个2d texture，其内部状态被初始化为2d texture的状态，它不能再被bind到其他类型的texture target上，否则会产生运行时错误。

### 什么时候需要关心texture unit?
&emsp;&emsp;当使用多重纹理的时候，也就是说在shader里面要同时使用多于一个sampler的时候。通过glUniform1i将texture unit传给sampler，让sampler知道应该去哪个texture unit中获取texture object，那么应该获取哪个texture target指向的texture object呢？这就要看sampler的类型了。比如sampler2D，就会获取sampler被指向的texture unit中的GL_TEXTURE_2D texture targert。

### Is there a limit to the number of textures that can be created in OpenGL - that is, with glGenTextures?
&emsp;&emsp;The only limit of glGenTextures is given by the bit width of the texture name (GLint), which is 32 bit; indeed the number of texture names can be so great that you will probably never have problems when generating texture names.
&emsp;&emsp;The limit for textures is that of the graphics system's memory. The OpenGL implementation knows the texture size and format only when the application submits texture data using glTexImage2D (and other glTexImage* functions if available), which specifies the width, height and the internal texture format: having those parameters it's possible to determine the memory needed to store the texture data.
&emsp;&emsp;To check errors, you should query OpenGL error using glGetError, which returns GL_OUT_OF_MEMORY if the operation fails to allocate the required memory. This error can also be returned by glGenTextures and glTexImage2D etc.
&emsp;&emsp;This error is most likely to be returned by glTexImage2D etc., since the memory required for texture allocation is much larger than the memory required for marking a texture name as used.

### 总结

&emsp;&emsp;openGL中纹理的状态分为texture unit和texture object包含的状态。texture unit的状态包括当前激活的unit，每个unit下面的各个target分别指向哪些texture object。texture object的状态包含type, texParam, format等等。什么时候需要调用glActiveTexture以及glBindTexture就要看状态是否会改变。对于shader来说，他可以访问所有的texture unit中指定的texture object。只要你告诉他每个sampler使用哪个unit就行。如果每个unit的内容指定后不需要改变，则即便shader使用了多个sampler也不需要来回切换unit的状态。当然更常见的是渲染完一个pass后，需要改变当前texture unit中某target中的texture object，也就是需要换贴图了。那么标准的操作就是先glActiveTexture，然后glBindTexture。当然如果你只使用unit0，则不需要调用glActiveTexture。

## API详解
### void glActiveTexture(GLenum texUnit); 
&emsp;&emsp;该函数选择一个纹理单元，线面的纹理函数将作用于该纹理单元上，参数为符号常量GL_TEXTUREi ，i的取值范围为0~K-1，K是OpenGL实现支持的最大纹理单元数，可以使用GL_MAX_TEXTURE_UNITS来调用函数glGetIntegerv()获取该值。

&emsp;&emsp;可以这样简单的理解为：显卡中有N个纹理单元（具体数目依赖你的显卡能力），每个纹理单元（GL_TEXTURE0、GL_TEXTURE1等）都有GL_TEXTURE_1D、GL_TEXTURE_2D等，如下：

	struct TextureUnit { 
		GLuint targetTexture1D; 
		GLuint targetTexture2D; 
		GLuint targetTexture3D; 
		GLuint targetTextureCube;
		... 
	}; 

	TextureUnit textureUnits[GL_MAX_TEXTURE_IMAGE_UNITS] 
	GLuint currentTextureUnit = 0;

&emsp;&emsp;默认情况下当前活跃的纹理单元为0.

	void glActiveTexture(GLenum textureUnit) { 
		currentTextureUnit = textureUnit - GL_TEXTURE0 ; 
	}

&emsp;&emsp;Active应理解为选择(Select)某纹理单元(Texture Unit), 即表示后续的glEnable(GL_TEXTURE_2D)和glBindTexture(GL_TEXTURE_2D, texture)作用于此所选的纹理单元，所以glActiveTextue 并不是激活纹理单元，而是选择当前活跃的纹理单元。

	void glBindTexture(GLenum textureTarget, GLuint textureObject) { 
		TextureUnit *texUnit = &textureUnits[currentTextureUnit]; 
		switch(textureTarget) { 
			case GL_TEXTURE_1D: texUnit->targetTexture1D = textureObject; break; 
			case GL_TEXTURE_2D: texUnit->targetTexture2D = textureObject; break; 
			case GL_TEXTURE_3D: texUnit->targetTexture3D = textureObject; break; 
			case GL_TEXTURE_CUBEMAP: texUnit->targetTextureCube = textureObject; break; 
		} 
	}

从示例代码中可以看到：当绑定纹理目标时，所作用的是当前活跃的纹理单元。

#### glBindTexture的使用方法实际上体现在两个地方：

- 首先是载入纹理时，将载入的纹理与纹理分配号绑定在一起。也就是给当前的纹理分配相应的纹理号。
- 其次载入多个纹理之后，需要在多个纹理之间进行切换，此时也需要使用glBindTexture函数进行切换。