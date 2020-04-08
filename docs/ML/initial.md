# Initial

神经网络参数初始化

## xavier初始化

```torch.nn.init.xavier_uniform(tensor, gain=1)```

对于输入的tensor或者变量，通过论文Understanding the difficulty of training deep feedforward neural networks” - Glorot, X. & Bengio, Y. (2010)的方法初始化数据。初始化服从均匀分布U(−a,a)，该初始化方法也称Glorot initialisation。

参数：

	tensor：n维的 torch.Tensor 或者 autograd.Variable类型的数据
	a：可选择的缩放参数

例：

	w = torch.Tensor(3, 5)
	nn.init.xavier_uniform(w, gain=nn.init.calculate_gain('relu'))

```torch.nn.init.xavier_normal(tensor, gain=1)```

也是上面论文中的方法，初始化服从高斯分布N(0,std)，该初始化方法也称Glorot initialisation。

参数：

	tensor：n维的 torch.Tensor 或者 autograd.Variable类型的数据
	a：可选择的缩放参数

例如：

	w = torch.Tensor(3, 5)
	nn.init.xavier_normal(w)


## kaiming初始化

```torch.nn.init.kaiming_uniform(tensor, a=0, mode='fan_in')```

对于输入的tensor或者变量，通过论文“Delving deep into rectifiers: Surpassing human-level performance on ImageNet classification” - He, K. et al. (2015)的方法初始化数据。初始化服从均匀分布U(−bound,bound)，其中，该初始化方法也称He initialisation。

参数：

	tensor：n维的 torch.Tensor 或者 autograd.Variable类型的数据
	a：该层后面一层的激活函数中负的斜率(默认为ReLU，此时a=0)
	mode：'fan_in' (default) 或者 'fan_out'。 
		  使用fan_in保持weights的方差在前向传播中不变；
		  使用fan_out保持weights的方差在反向传播中不变。

例如：

	w = torch.Tensor(3, 5)
	nn.init.kaiming_uniform(w, mode='fan_in')

```torch.nn.init.kaiming_normal(tensor, a=0, mode='fan_in')```

基于上文方法初始化数据。初始化服从高斯分布N(0,std)，其中std=√[2/((1+a^2)×fan_in)]，该初始化方法也称He initialisation。

参数：

	tensor：n维的 torch.Tensor 或者 autograd.Variable类型的数据
	a：该层后面一层的激活函数中负的斜率(默认为ReLU，此时a=0)
	mode：'fan_in' (default) 或者 'fan_out'。 
		  使用fan_in保持weights的方差在前向传播中不变；
		  使用fan_out保持weights的方差在反向传播中不变。

例如：

	w = torch.Tensor(3, 5)
	nn.init.kaiming_normal(w, mode='fan_out')



