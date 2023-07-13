## enumerate() 函数

enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。

语法:

'''
enumerate(sequence, [start=0])
'''

参数:

sequence -- 一个序列、迭代器或其他支持迭代对象。

start -- 下标起始位置的值。

<img width="522" alt="image" src="https://github.com/corianderK/corianderleetcodediary/assets/65326195/435d21d8-e51a-4350-990b-239025de4ee7">

## Object Oriented Program 

<img width="560" alt="image" src="https://github.com/corianderK/corianderleetcodediary/assets/65326195/f63b638b-6f69-42bc-8c30-3609594fea0b">

[查找类的详细说明和用法案例](https://www.runoob.com/python/python-object.html)

****
# numpy
## np.random.choice()
语法：

'''
numpy.random.choice(a, size=None, replace=True, p=None)
'''

参数：

a : 如果是一维数组，就表示从这个一维数组中随机采样；如果是int型，就表示从0到a-1这个序列中随机采样。

size : 采样结果的数量，默认为1.可以是整数，表示要采样的数量；也可以为tuple，如(m, n, k)，则要采样的数量为m * n * k，size为(m, n, k)。

replace : boolean型，采样的样本是否要更换？这个地方我不太理解，测了一下发现replace指定为True时，采样的元素会有重复；当replace指定为False时，采样不会重复。

p : 一个一维数组，制定了a中每个元素采样的概率，若为默认的None，则a中每个元素被采样的概率相同。

<img width="643" alt="image" src="https://github.com/corianderK/corianderleetcodediary/assets/65326195/2d8f0e3b-403f-4414-80eb-44d472555c44">
