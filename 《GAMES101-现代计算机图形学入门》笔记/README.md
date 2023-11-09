# GAMES101-现代图形学入门
![intro](assets/1-1.png)
[TOC]
## Lecture 1:Overview of Computer Graphics
### 1.什么是好的画面？
* 直观的标准就是看画面是否足够亮，体现的是渲染中的关键技术：全局光照，画面做的好，整个画面就会亮，看起来很舒服
### 2.VR/AR的区别
* 虚拟现实是看不到现实的，头戴式设备内看到的东西都是电脑生成的；增强现实，可以看到现实的环境，并会看到新的电脑生成的东西显示在画面里面
### 3.图形学≠计算机视觉
* 计算机视觉，一切需要进行猜测的内容，比如语义分割（分割出来哪些是人哪些是道路），目标检测（推理找出某个目标对象）希望计算机能以视觉的方式进行分析理解、推断推理。在本课程中不会涉及，不属于图形学的范畴
* 二者的结合越来越紧密，界限也越来越模糊
![intro](assets/1-3.png)
### 4.随记
#### The Quick Brown Fox Jumps Over The Lazy Dog
* 这句话里面包含了26个字母，所以常用于Typography的测试，会出现一遍大写一遍小写，可以测试一个字体的美感和完整性
#### Learn Graphics ，Not Graphics API
![intro](assets/1-2.png)
#### Geek
* Geek = Genius✔ + Freak❌
#### Tradeoff思想
* No Free Lunch，没有免费的午餐
* 在两个或多个竞争性或矛盾的选择之间进行权衡或取舍的行为，例如：时间复杂度vs空间复杂度
## Lecture 2:Review of Linear Algebra
### 0.阅读材料
* Tiger Book : 第2章Miscellaneous Math、第5章Linear Algebra
### 1.Vectors
#### 1.1基本概念
* 数学上叫向量、物理上叫矢量，含有两个重要的属性：方向和长度
* 向量平移到不同位置，依然是一个向量，因为向量间两点AB的相对位置并没有改变，并不关心向量的绝对开始位置
* 向量的长度：若长度为1，则称为单位向量。任一向量想要变为单位向量，用向量本身去除以其长度，就可以得到一个和原始向量同方向，且长度为1的一个单位向量
![intro](assets/2-1.png)
#### 1.2 Vector Addition
* 平行四边形法则：在几何上的表述方式，向量间尾部相接
* 三角形法则：在几何上的表述方式，向量间首尾相接
* 笛卡尔坐标：在代数上的表述方式
#### 1.3 Vector Multiplication
* Dot(scalar) product：点乘最后得到的是一个数  
	a、应用：1、可以通过点乘快速的得到两个向量间的夹角（计算光线入射的夹角、物体表面的法线、摄像机目视角度等）2、将一个向量投影到另一个向量上 3、通过点乘判断多个向量的方向相近或相离
  ![intro](assets/2-2.png)
* Cross(vector) product：叉乘得到的是一个向量
	a、向量的叉积并不满足交换律，若要交换顺序需要加个负号  
	b、右手螺旋定则（right-handed）：bxa，则除大拇指外从b芳香手指并列卷向a，则此时大拇指指向的方向为叉积后的方向  
	c、向量的叉乘可以表示成矩阵形式  
  ![intro](assets/2-3.png)
	d、应用：1、判断左和右（叉乘得到的结果为正，则在左侧，若为负则在右侧） 2、判断内与外（叉乘的结果都在封闭图形各边的左边，则在该封闭图形的内部，否则在外部）
* Orthonormal bases and coordinate frames.
### 2.Matrices
#### 2.1基本概念
* 矩阵就是一组m行n列的数
* 矩阵相乘要遵循“第一个矩阵的列数等于第二个矩阵的行数”这个原则
#### 2.2 Matrix-Matrix Multiplication
* 矩阵的相乘依然不满足交换律
#### 2.3 Matrix-Vector Multiplication
* 将向量看作一个m * 1的矩阵
* 求一个向量关于y轴对称的镜像
![intro](assets/2-4.png)
#### 2.4 Transpose of a Matrix
* 两个矩阵乘积的转置 = 各自转置矩阵的乘积（次序颠倒AB->BA）
#### 2.5 Identity Matrix and Inverses
* 单位矩阵：对角线上为1，其他均为0的矩阵
* 逆矩阵：一个矩阵A如果和另一个矩阵B相乘得到单位矩阵，则矩阵B称为矩阵A的逆矩阵
* 两个矩阵的乘积的逆矩阵 = 各自逆矩阵的乘积（次序颠倒AB->BA）
#### 2.6 Vector multiplication in Matrix form
* 用矩阵的形式表示向量乘积
![intro](assets/2-5.png)
## Lecture 3:Transformation
### 0.名词解释
* Transformation：变换
* Modeling：模型变换
* Viewing：视图/观测变换
* Shear：切变
* Homogeneous coordinates：齐次坐标
### 1. 2D transformations
#### 1.1 Scale Transform（Uniform/Non-Uniform）
* s<sub>x</sub>，s<sub>y</sub>分别为x轴和y轴上的缩放的倍率，则其中由s<sub>x</sub>，s<sub>y</sub>和0组成的矩阵称之为缩放矩阵Scale Matrix
![intro](assets/3-1.png)
#### 1.2 Reflection Transform
* Reflection Matrix
![intro](assets/3-2.png)
#### 1.3 Shear Transform
* Shear Matrix
![intro](assets/3-3.png)
#### 1.4 Rotate Transform
* 讨论基准：不特殊说明默认绕零点（0，0）旋转，默认按逆时针方向旋转
* Rotate Matrix，如果是负角度，则旋转矩阵为该旋转矩阵的转置
* 从定义中可知，旋转θ角度和旋转-θ角度的旋转矩阵相乘为单位矩阵，则我们又可以发现，所以在旋转矩阵中，旋转矩阵的转置就等于旋转矩阵的逆矩阵
* 在数学上，如果某个矩阵的转置等于该矩阵的逆矩阵，则我们又称它为正交矩阵。所以旋转矩阵就是一种正交矩阵
![intro](assets/3-5.png)
* 推导过程
![intro](assets/3-4.png)
#### 1.5 Linear Transforms = Matrices
* 可见，线性变换都可以用矩阵的形式进行表达
* 前提：相同维度
### 2. Homogeneous coordinates
#### 2.1 Why Homogeneous coordinates
![intro](assets/3-6.png)
* 可以发现平移变换之后，无法直接的写为一个向量和矩阵相乘的形式了，可以在上面的2D变换的基础上通过和另一个向量的相加减实现描述。这也反映出来平移变换不是一个线性变换
* 但人类总是懒惰的，并不想把平移变换当作一个特殊的变换，是否有某种统一方式能将所有的变换包括进来？这就是齐次坐标
#### 2.2 Solution:Homogeneous coordinates
![intro](assets/3-7.png)
* 给二维向量或点增加第三维，使得平移操作能用一个矩阵乘以一个向量的方式进行表达
* 二维点增加第三维为1，二维坐标增加第三维为0（保护向量具有平移不变性）
* tradeoff的代价就是增加了维度进行存储额外的0 0 1
* 变换的执行顺序是先进行线性变换再进行平移
#### 2.3 Affine Transformations
* 放射变换 = 线性变换 + 平移，可以用齐次坐标表示如下，可见在二维变换的情况下最后一行永远为0, 0 ,1，最后一列永远为平移变换的距离t<sub>x</sub>，t<sub>y</sub> , 1
![intro](assets/3-8.png)
![intro](assets/3-9.png)
#### 2.4 Inverse Transform
* 逆变换：之前所作变换的逆矩阵
#### 2.5 Composite Transform
* 矩阵间乘操作的顺序不一样，出来的效果也会不一样，也反映出矩阵是不满足交换律的
* 矩阵的执行顺序：从右到左
* 但别忘了矩阵是有结合律的，可以先对矩阵进行计算，合成得到一个矩阵，再和点进行相乘
#### 2.6 Decomposing Complex Transform
* 一个复杂的变换可以分解为若干个简单的变换来实现，例如：先平移回原点再进行其他操作，完成后再从原点平移回出发点即可
### 3. 3D Transformations
* 同理，在三维坐标中也可以用齐次坐标的形式对点和向量进行升维，用4 * 4的矩阵进行仿射变换的表示，4 * 4矩阵的最后一行永远为0 ，0 ，0 ，1，最后一列永远为平移变换的距离t<sub>x</sub>，t<sub>y</sub> , t<sub>z</sub> ，1，左上角的3 * 3为三维空间中的线性变换过程
* 3 * 3的执行顺序是先进行线性变换，再进行平移，所以如果是点左乘一个线性变换矩阵，再左乘一个平移矩阵，是可以写在一起的
![intro](assets/3-10.png) 
#### 3.1 Rotate Transform
* 三维空间的旋转先从简单的绕坐标轴进行旋转看起，例如在绕x轴进行旋转的时候，三维点的x值是不变的，y和z的值会进行改变，则只对y和z进行旋转，变成了一个二维空间上的旋转问题，所以第一行第一列为1，该行该列其余位置均为0.
* 同理，绕y轴旋转时，第二行第二列为1，该行该列其余位置均为0；绕z轴旋转时，第三行第三列为1，该行该列其余位置均为0
* 可见在绕y轴进行旋转时，区别于绕x轴和绕z轴旋转，sinα的正负号反了过来，是因为基于xyz的顺序，前两个向量叉乘能得到下一个，则向量y是由z向量叉乘x向量得到的，所以它的负号是反过来的
![intro](assets/3-11.png) 
#### 3.2 3D Rotations
* 对于一般性旋转则可以转换为简单旋转的组合
* Euler angles：欧拉角，roll（翻滚角）、pitch（俯仰角）、yaw（旋转角）
![intro](assets/3-13.png) 
* Rodrigues’ Rotation Formula：罗德里格斯旋转公式，n为旋转轴，α为旋转角度，沿着某一个轴旋转，默认过原点，将原点作为起点
![intro](assets/3-12.png) 
* 对于复杂任意轴同样是进行分解
* quaternions四元数：计算旋转矩阵与旋转矩阵之间的差值，该课程不进行讲解及运用
## Lecture 4:Transformation Cont
### 0.名词解释
* Projection：投影
* Orthographic：正交
* Perspective：透视
### 1.Viewing Transformation
* MVP变换：model transformation -> view transformation -> projection transformation，模型->视图->投影
#### 1.1 View/Camera transformation
* 放置相机的三个要素：1、位置e 2、向上的朝向t 3、上下所看的角度g，这三个元素就构成了观测矩阵，向上的朝向可以理解为欧拉角中的roll翻滚角，（人拿着相机侧身弯腰，拍到的水平画面会倾斜）
![intro](assets/4-1.png) 
* 当相机和所有的物体移动的速度、方向都相同时，即不产生相对运动的情况下，相机所拍出的照片是相同的
* 为了简化操作，人们就将相机固定放在原点（0，0，0）上，在y轴上永远向上看，在z轴上永远向-z的方向看，这个称为相机的标准位置
* 则将相机放置在标准位置上的过程在数学上可以表示为：（1）将位置e平移到原点上（2）将所看的角度g旋转到-Z（3）将向上的朝向t旋转到Y（4）将g叉乘t旋转到X
![intro](assets/4-2.png) 
* 将上述操作用矩阵的方式表达，这里由于要先到原点，所以先做平移。但是正操作过程不太好写，如果是从原点出发做逆操作就好写了,也就是X->(g x t)，Y->t,Z->-g。又因为旋转矩阵是正交矩阵，所以直接对内部的3 * 3变换部分进行转置即可
![intro](assets/4-3.png) 
#### 1.2 Projection transformation
* 正交投影更多用于工程制图，不会带来近大远小的现象；人眼的成像会更接近透视投影，看到的平行线不平行会相交到某个地方去，一叶障目，经典图片“鸽子那么大”
![intro](assets/4-4.png) 
* 透视投影，认为摄像机放在某一个位置上作为一个点，点与画面连出空间上的一个四棱锥，四棱锥中某一个深度到另一个深度之间的区域称之为frustum（视锥体），把这块区域中的所有东西显示在近处平面上
* 正交投影，则认为将相机拿到足够远的位置，则此时发现近处和远处的平面一样的大小，无论物体有多远，投影到平面上的东西都是一样的
##### 1.2.1 Orthographic projection
* 具体的做法：（1）将相机放到标准位置（2）然后把Z轴丢掉，此时所有的东西都在xoy平面上了（3）最后不管xy的范围多大，都缩到[-1,1]之间（约定俗成，方便后续的计算），就得到了正交投影的结果，一个[-1,1]^3的canonical cube，此时物体在里面会被拉伸，后续还要做一个视口变换，后续会提及
* 更正式的说法：不管空间上多少长宽高的长方体，都可以正则成一个标准的立方体，做法：先平移到原点，再缩放
![intro](assets/4-5.png) 
* 注意在z轴上，实际上是越远的值比越近的值越小
* Transformation Matrix：其中平移部分（r+l）/2为x轴上左和右的中心，负号是因为要把一个点往原点方向移动，无论是正负数都是负号，其他的类似；缩放部分中2/（r-l）做的是缩放操作，2是因为-1到1的距离为2，其他的类似
![intro](assets/4-6.png) 
* 网上看到的结果和这里不一样是正常的，可能是使用的坐标系不同，比如OpenGL使用的左手系
##### 1.2.2 Perspective projection
* 透视投影，使用最广泛，近大远小。
* 实现透视投影的过程可以理解为，（1）将远端平面上的四个点往近平面上面挤，将frustum视棱锥挤成一个长方体（2）再做一次正交投影
* 上文已经知道了第二步正交投影怎么做了，那么第一步“挤”的过程怎么做，首先先规定几个规则，（1）近平面的位置永远不变，该平面下任何一个点都不会变（2）远处的平面，在经过挤压后，z值（即深度）依然不变（3）远平面最中心的点，在经过挤压后，其位置仍然在最中心（0，0，f）三个轴的值都不变
![intro](assets/4-7.png) 
* 从透视->正交的矩阵M[persp->ortho]求解过程如下所示，
	a、下图为侧视图，左边的zoy是相机拜放的位置，向-z的方向看，只看z方向的话可以得到一个相似三角形，根据相似三角形原理，可以通过(x,y,z)和底边n、z等距离信息,n和z的比值，可以求出挤压后的y'
	![intro](assets/4-8.png) 
	b、同理，通过从相机从前往后看的视角，x'也可以通过相似三角形定理求出来。此时在齐次坐标系下，我们可以得到如下的一个变换过程，由于z是怎么变的还不知道所以先写为unknown，一个点同时缩放z倍后仍然是同一个点  
  ![intro](assets/4-9.png) 
	c、此时，从透视到变换的结果已经知道了，我们可以填出变换矩阵的部分信息，比如第一行第一列第二行第二列，涉及x，y变换的部分一定是n，第四行第三列一定是1
	![intro](assets/4-10.png) 
    d、结合我们前面的三条规则，近平面上任何点不变和远平面上的z不变。根据第一条规则近平面上任何点不变，代入近平面上的点（x,y,n）,缩放n倍，依然是原本那个向量，此时知道了unknown,此时已经得出来变换矩阵的第三行部分信息，前两位必为0，因为n^2和x,y没有任何关系，但无法确认第三列第四列的A和B是n 0 还是0 n^2  
	![intro](assets/4-11.png)
	e、根据第三条规则，远平面上的中心点，无论怎么挤压仍然在中心点（0，0，f）,代入结合上一步中的An+B=n^2，可以解出A=n+f,B=-nf，此时已经得到了完整的透视到变换矩阵
	![intro](assets/4-12.png)
* 最后再做一个正交投影即可
* 思考：对于近平面和远平面中间的某一个点，经过挤压的点，它的z是会变小还是变大？
* 如何定义一个视锥？定义一个可视角度，定义一个宽高比
* Vertical Field of View：可视角度，定义看到的视界。广角相机就是可视角度比较大，视棱锥扩张的更大。垂直可视角度就是从相机出发到顶边和底边连线的夹角，
* 此时我们可以通过垂直可视角度的一半，结合平面和相机的距离n的绝对值，正切计算出顶部高度top值，结合宽高比可以算出宽度
![intro](assets/4-13.png)
## Lecture 5:Rasterization 1 (Triangles)
### 0.名词解释
* Rasterization：光栅化，三维空间的几何形体显示在平面上就叫做光栅化，实时图形学中会广泛的应用到
* 实时图形学：当一秒钟能生成30张画面，也就是fps达到30，否则称为offline离线图形学
* Sampling：采样
* Jaggies：锯齿
* Aliasing：信号走样
### 1.Canonical Cube to Screen
* 在我们通过MVP的透视变换得到一个canonical cube后我们要把它画在屏幕上
##### 1.1 What is screen
* 屏幕是一个二维的数组，数组中的每一个元素是一个像素Pixel，屏幕的大小称之为分辨率，代表像素的多少
* 屏幕是典型的光栅成像设备，Raster光栅是德语中的一个词，就是屏幕的意思，光栅化则是把东西画在屏幕上的意思
#### 1.2 Canonical Cube -> Screen
* 三维的怎么映射到二维？先不管z，x和y映射到width和height中，变换矩阵如下，该变换也被称为视口变换Viewport，把[-1,1]^2映射到屏幕空间。左上角的3 * 3 对角阵将宽度变为width，高度变为height,z方向不变;第四列的平移部分把原本在canonical cube原点的中心移动到屏幕中心（width/2,height/2）
![intro](assets/5-1.png)
### 2.Raster Displays
#### 2.1 LCD(Liquid Crystal Display) Pixel
* 液晶显示器，液晶通过不同的排布扭曲影响光的极化（光的偏振方向），调整光的振动方向，液晶显示器两侧有两个光栅，通过了一个光栅后，光的振动方向和光栅的振动方向一致
![intro](assets/5-2.png)
### 3.Drawing to Raster Displays
#### 3.1 Why trangles
* 三角形是最基础的多边形，没有比三角形边更少的多边形了，任何其他的多边形都可以拆成若干个三角形
* 三角形给定三个点，连成一个三角形一定是在一个平面的，而四边形对角线一折，就不在一个平面了
* 三角形内外部定义清楚，不存在凸凹多边形的说法，且可以通过向量的叉积定义一个点是否在三角形内
* 三角形内部的任意点和其三个顶点可以得到一个逐渐的变化得到插值，中心坐标的插值方法
#### 3.2 Sampling
* 光栅化的核心问题：一个像素里面只可能有一个值，如何判断一个像素的中心点和所要绘制的三角形的位置关系
* 采样：给定一个连续函数，在不同的地方问这个函数的值是多少的过程，采样就是把一个函数离散化的过程
* 采样判断屏幕内的每个像素中心是否在三角形内，可以定义一个函数如下，其中x,y不一定是整数，是实数即可
![intro](assets/5-3.png)
* inside函数如何实现？结合之前提到的向量间的叉积判断点在多边形内/外，如下图所示。默认向量方向为逆时针，P1P2与P1PQ叉乘，根据右手定则，得到一个向屏幕外的向量，z是正的，则Q在P1P2左侧；同理叉乘P0P1、P0PQ得到Q在P0P1左侧；最后叉乘P2P0和P2Q，发现Q在P2P0右侧；叉乘的结果不都在同侧，则在该三角形外部
![intro](assets/5-4.png)
* 若刚好有一点在两个三角形的相接边界上，则可以自己定义要么不做处理，要么做特殊处理，本课程不作处理。比如OpenGL认为点落在多边形的上边和左边上都认为在多边形内，落在右边和下边则不算在多边形内
* 对于inside函数的运用，为了提高速度，不必要将这个宽高屏幕遍历一遍，将要填充覆盖的最小包围区域AABB（Axis-Aligned Bounding Box，轴对齐边界框）遍历就好。更快的办法是只找绘制三角形每行只涉及的像素坐标
* 那么填充后一个三角形会变成如下的一个图，存在大量的锯齿Jaggies，光栅化中致力于解决的问题，产生的原因是采样的频率对于该信号来说还不够高，产生信号走样的问题Aliasing，解决方案就是抗锯齿/反走样
![intro](assets/5-6.png)
#### 4.随记
* Real LCD Screen Pixels（Close up）:可以看到右侧的图，这种RGB的排列方式称为Bayer Pattern，将传感器上的像素排列成一种特定的格点模式，绿色的点密度比蓝色和红色的更高，是因为人眼对于绿色更为敏感。很多相机也是这样设置的
![intro](assets/5-5.png)
## Lecture 6:Rasterization 2（Antialiasing and Z-Buffering）
### 0.名词解释
* Artifacts：瑕疵，Errors/Mistakes/Inaccuracies一切看上去不太对的东西称之为Artifacts
* Staircase Pattern：阶梯图案或阶梯状模式，锯齿的表现形式
* Moire Pattern：摩尔纹，将原图的奇数行奇数列都去掉，还显示原本一样大，例如拿手机拍摄显示器屏幕时，出现的条纹
* Wagon wheel illusion：一种视觉错觉，人眼的采样速度跟不上物体的运动速度，导致错觉使得物体在与实际方向不用的方向徐娜转，甚至有时候会逆时针旋转
* Frequency Domain：频域
* Spatial Domain：时域
### 1.Antialiasing
#### 1.1 Sampling theory
* Sampling Artifacts：Jaggies、Moire、Wagon wheel effect
#### 1.2 Antialiasing Idea
* Blurring(Pre-Filtering) Before Sampling：采样之前先对原始的函数/信号做模糊处理。拿到一个三角形先变成一个模糊的三角形，模糊的边界会变成其他的颜色（比如边界值和背景的中间值），从而实现反走样
![intro](assets/6-1.png)
* Burring的顺序不能调换的，不能先采样再滤波（称之为Blurred Aliasing）
![intro](assets/6-2.png)
#### 1.3 Frequency Domain
* Sines and Cosines
* Frequencies：频率是周期的倒数，f=1/T
* Fourier Transform：傅里叶变换，首先要先知道傅里叶级数展开（任何一个周期函数都可以写为若干个正弦或余弦函数的组合，加上一个常数项），可见通过傅里叶级数展开，任一函数可以分解为不同的频率，傅里叶变换的作用就是把时域变成频域
![intro](assets/6-3.png)
* 还可以通过逆变换变回原本的函数
![intro](assets/6-4.png)
* 高频率的函数需要更快速的采样
* 如下图中，同样的采样方法下采样这两个频率截然不同的信号函数得到的结果（采样点）都是相同的，无法区分两个信号，也就是我们所提到的“走样”
![intro](assets/6-5.png)
#### 1.4 Filtering
* 滤波：从频域的角度上来说，将某个特定频率上的信号删掉的一种手段
* 傅里叶变换的作用就是把时域变成频域，中间是频率最低的地方，周边是频率最高的地方，可见一个图像的大多数信息都集中在中间的低频部分，高频信息较少，大多数图片都有这个特性。
* 图片转换为频域可以看作同样一张函数周期性的重复，大多数的图片其实左边界的信息和右边界的信息并不太相似，中间的十字线则是右边界和下一张图片左边界部分相接时产生的信息剧变
##### 1.4.1 High-pass filter
* 高通滤波，将图像中的低频部分进行过滤，只保留高频信息让其通过，常用于保存边界信息。可见图像中的内容边界信息被保存了下来
* 什么是边界？图像的某部分信息突然发生了剧变的现象
![intro](assets/6-6.png)
##### 1.4.2 Low-pass filter
* 低通滤波，和高通滤波相反，常用于模糊图像，去掉边界
![intro](assets/6-7.png)
##### 1.5 Filtering = Convolution (=Averaging)
* 从另一个角度说，滤波等于平均等于卷积
* 卷积定理：时域上如果想对两个信号进行卷积，对应到两个信号上各自频域上，是两个信号频域的乘积；在时域上如果是乘积，则在频域上是卷积
* 对一幅图可以直接用卷积进行卷积操作，也可以对图像先进行傅里叶变换，把滤波器变到频域上，进行相乘，得到频域的结果，再逆傅里叶变换转化回时域上。这两个操作是等效的
![intro](assets/6-8.png)
* Wider Filter Kernel = Lower Frequencies，更大的卷积核意味着更低频，得到更模糊的信息
##### 1.6 Sampling = Repeating Frequency Contents
* 采样实际上就是重复频率的内容，下图左右两列中看，ace为时域，b,d,f为频域，ac时域上做乘积得到e，bd频域上做卷积得到f。在时域上采样后表现为离散的采样点，频域上表示为将频谱进行重复的复制粘贴
![intro](assets/6-9.png)
##### 1.7 Aliasing = Mixed Frequency Contents
* 采样不够快，频率过低，导致原始信号和复制粘贴的信号频域上产生重叠，这种情况下就称为走样，所以走样在频域上的描述就是在复制粘贴的过程中产生了混别
![intro](assets/6-10.png)
##### 1.8 How Can We Reduce Aliasing Error
* 1、增大采样频率：更高分辨率的显示器，但也以为着更高的成本
* 2、反走样：先模糊再采样，在频域上先模糊就相当于下图的上半部分，将矩形框的外部部分都认为是高频部分去掉，只保留框内的部分，结果如下图的下半部分所示
![intro](assets/6-11.png)
##### 1.9 Antialiasing = Limiting , then repeating
* A 1 pixel-width box filter(low pass , blurring) ：使用一个像素大小的滤波器作为低通滤波进行模糊，计算覆盖的面积占比，决定滤波后显示的值是多少
* 如何计算覆盖的面积占比呢？Antialiasing By Supersampling(MSAA)，通过更多的样本信息，近似第一步反走样的模糊过程，在像素的内部再加采样点，再判断覆盖率。下图内某个像素内三个点覆盖了，则认为该像素在像素块内，覆盖率为75%；同理，左下角的点只有25%
![intro](assets/6-12.png)
![intro](assets/6-13.png)
* MSAA不是靠提升分辨率解决的走样问题，是计算覆盖率。tradeoff则是引入更多的点增大了计算量，在实际应用中，并不是将一个像素规则的划分成4个像素，而是会考虑一些邻近像素的方法，同不规则的分布增加像素点，复用以减少计算量
#####  1.10 Antialiasing Milestones
* 除了MSAA外比较重要的两种抗锯齿方法，得到工业界的广泛应用
* 1、FXAA(Fast Approximate AA)：先得到一个有锯齿的图，用图像匹配的方法找到锯齿边界，将这些边界换成没有锯齿的边界，速度十分快
* 2、TAA(Temporal AA)：Temporal可见与时间相关，如不是在运动场景，相邻两帧显示的信息是一样的，相邻两帧可以用一个像素内不同的点感知这个像素点是否在三角形内，复用上一帧的结果，相当于将MSAA对应的样本分布在了时间上，且没有引入其他数据，速度也很快
* Super resolution / super sampling：比如深度学习中的DLSS
### 2.Visibility/occlusion
#### Z-buffering
## Lecture 7:Shading 1(Illumination,Shading and Graphics Pipeline)
### 0.名词解释
* Shading：着色
### 1.
## Lecture 8:Shading 2
## Lecture 9:Shading 3
## Lecture 10:Geometry 1 (Introduction)
## Lecture 11:Geometry 2
## Lecture 12:Geometry 3
## Lecture 13:Ray Tracing 1
### 0.名词解释
* Ray Tracing：光线追踪
## Lecture 14:Ray Tracing 2
## Lecture 15:Ray Tracing 3
## Lecture 16:Ray Tracing 4
## Lecture 17:Materials and Appearances
## Lecture 18:Advanced Topics in Rendering
## Lecture 19:Cameras,Lenses and Light Fields
