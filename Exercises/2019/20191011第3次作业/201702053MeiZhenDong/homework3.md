# 第三次作业
&emsp;这次课老师讲解了vs code的使用方法，并在vs code中安装了markdown插件，演示了markdown的操作方法，并指导我们在github上完成了注册，clone了老师的文件到本地电脑上，了解了上传文件的方法，随后又学习了图像处理方面的有关知识，从滤波，漫水填充，膨胀腐蚀，开闭梯度，图像金字塔与缩放，阈值化等方面进行了深入讲解，具体代码的调试与运行结果如下：
>1.滤波综合 ![](011.png)

>2.膨胀腐蚀 ![](012.png)

>3.漫水填充 ![](013.png)

>4.图像金字塔与缩放 ![](014.png)

>5.开闭梯度 ![](015.png)

代码总结：
1. 空域滤波是一种邻域处理方法，通过直接在图像空间中对邻域内像素进行处理，达到平滑或锐化图像的作用。此外，在图像识别中，通过滤波还可以抽出图像的特征作为图像识别的特征模式。

空域滤波是图像处理领域中广泛使用的主要工具。空域滤波主要可以分为线性滤波和非线性滤波，其中，线性滤波和频域滤波存在一一对应的关系。但是，空域滤波可以用于非线性滤波，但是频域滤波不能用于非线性滤波。

从根源上讲，滤波这一词语来自于频域，信号处理中频域滤波指的是允许或者限制一定的频率成分通过。但空域滤波直接在图像空间中增强图像的某些特征或者减弱图像的某些特征。

空域滤波的作用域是像素及其邻域，通常使用空域模板对邻域内的像素进行处理从而产生该像素的输出值。

线性空域滤波指的是像素的输出值是计算该像素邻域内像素值的线性组合，系数矩阵在这里我们称之为模板。由信号处理的原理可以得出，线性滤波可以用卷积来实现。因此，在数字图像处理中，线性滤波通常是利用滤波模板与图像的空域进行卷积来实现的，在线性滤波中滤波模板也称为卷积模板。

根据空域卷积的定义可以知道，卷积首先需要将模板进行反褶，也就是将模板绕模板中心旋转180°，但是在数字图像处理中，卷积模板通常是关于原点对称的，因此通常不需要考虑反褶过程。模板卷积的主要步骤包括如下几个步骤，

>将模板在图像中进行遍历，将模板中心和各个像素位置重合；

>将模板的各个系数与模板对应像素值进行相乘；

>将所有的乘积相加，并将求和结果赋值于模板中心对应的像素;

2. 图像的膨胀与腐蚀其实也是一种类似的卷积操作。其卷积操作非常简单，对于图像的每个像素，取其一定的邻域，计算最大值/最小值作为新图像对应像素位置的像素值。其中，取最大值就是膨胀，取最小值就是腐蚀。

3. 漫水填充的基本思想是自动选中了和种子点相连的区域，接着将该区域替换成指定的颜色，经常用来标记或者分离图像的一部分进行处理或分析。漫水填充也可以用来从输入图像获取掩码区域，掩码会加速处理过程，或者只处理掩码指定的像素点。其中掩膜Mask用于进一步控制那些区域将被填充颜色。

4. resize( )为OpenCV中专职调整图像大小的函数，此函数将源图像精确地转换为指定尺寸的目标图像。如果源图像中设置了ROI（Region Of Interest ，感兴趣区域），那么resize( )函数会对源图像的ROI区域进行调整图像尺寸的操作，来输出到目标图像中。若目标图像中已经设置ROI区域，不难理解resize( )将会对源图像进行尺寸调整并填充到目标图像的ROI中。

5. 调用void morphologyEx(InputArray src, OutputArray dst, int op, InputArray kernel, ...)，其中：

第一个参数 输入

第二个参数 输出

第三个参数 操作类型

MORTH_OPEN                函数做开运算

MORTH_CLOSE              函数做闭运算

MORTH_GRADIENT       函数做形态学梯度运算

MORTH_TOPHAT            函数做顶帽运算

MORTH_BLACKHAT       函数做黑帽运算

MORTH_DILATE              函数做膨胀运算

MORTH_ERODE             函数做腐蚀运算

心得体会：本节课进一步学习了opncv的相关知识，学习了利用opencv进行图像处理的方法，通过几个图像处理的相关例子，加深了对opencv的理解，几次课的学习可能效率不是很高，对于opencv的进一步理解我还是处于探索阶段，需要接下来的课程进行深度学习。