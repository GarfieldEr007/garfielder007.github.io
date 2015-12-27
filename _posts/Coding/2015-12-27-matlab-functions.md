---
layout: post
title: MATLAB函数大全
date: 2015-12-25
categories: Coding
tags: [C++]
description: Python
---

Matlab有没有求矩阵行数/列数/维数的函数？
ndims(A)返回A的维数
size(A)返回A各个维的最大元素个数
length(A)返回max(size(A))
[m,n]=size(A)如果A是二维数组，返回行数和列数
nnz(A)返回A中非0元素的个数

MATLAB的取整函数:fix(x), floor(x) :,ceil(x) , round(x)
(1)fix(x) : 截尾取整.

>> fix( [3.12 -3.12])

ans =

     3    -3
(2)floor(x):不超过x 的最大整数.(高斯取整)

>> floor( [3.12 -3.12])

ans =

     3    -4

(3)ceil(x) : 大于x 的最小整数

>> ceil( [3.12 -3.12])

ans =

     4    -3

(4)四舍五入取整

>> round(3.12 -3.12)

ans =

     0

>> round([3.12 -3.12])

ans =

     3    -3

>> 




如何用matlab生成随机数函数
rand(1)
rand(n):生成0到1之间的n阶随机数方阵 rand(m,n):生成0到1之间的m×n的随机数矩阵 (现成的函数) 
另外: 
Matlab随机数生成函数 
betarnd 贝塔分布的随机数生成器 
binornd 二项分布的随机数生成器 
chi2rnd 卡方分布的随机数生成器 
exprnd 指数分布的随机数生成器 
frnd f分布的随机数生成器 
gamrnd 伽玛分布的随机数生成器 
geornd 几何分布的随机数生成器 
hygernd 超几何分布的随机数生成器 
lognrnd 对数正态分布的随机数生成器 
nbinrnd 负二项分布的随机数生成器 
ncfrnd 非中心f分布的随机数生成器 
nctrnd 非中心t分布的随机数生成器 
ncx2rnd 非中心卡方分布的随机数生成器 
normrnd 正态（高斯）分布的随机数生成器 
poissrnd 泊松分布的随机数生成器 
raylrnd 瑞利分布的随机数生成器 
trnd 学生氏t分布的随机数生成器 
unidrnd 离散均匀分布的随机数生成器 
unifrnd 连续均匀分布的随机数生成器 
weibrnd 威布尔分布的随机数生成器

一、MATLAB常用的基本数学函数
　　abs(x)：纯量的绝对值或向量的长度 
　　angle(z)：复数z的相角(Phase angle) 
　　sqrt(x)：开平方 
　　real(z)：复数z的实部 
　　imag(z)：复数z的虚部 
　　conj(z)：复数z的共轭复数 
　　round(x)：四舍五入至最近整数 
　　fix(x)：无论正负，舍去小数至最近整数 
　　floor(x)：地板函数，即舍去正小数至最近整数 
　　ceil(x)：天花板函数，即加入正小数至最近整数 
　　rat(x)：将实数x化为分数表示 
　　rats(x)：将实数x化为多项分数展开 
　　sign(x)：符号函数 (Signum function)。 
　　当x<0时，sign(x)=-1； 
　　当x=0时，sign(x)=0; 
　　当x>0时，sign(x)=1。 
　　 
　　rem(x,y)：求x除以y的馀数 
　　gcd(x,y)：整数x和y的最大公因数 
　　lcm(x,y)：整数x和y的最小公倍数 
　　exp(x)：自然指数 
　　pow2(x)：2的指数 
　　log(x)：以e为底的对数，即自然对数或 
　　log2(x)：以2为底的对数 
　　log10(x)：以10为底的对数 
　　二、MATLAB常用的三角函数 
　　sin(x)：正弦函数 
　　cos(x)：馀弦函数 
　　tan(x)：正切函数 
　　asin(x)：反正弦函数 
　　acos(x)：反馀弦函数 
　　atan(x)：反正切函数 
　　atan2(x,y)：四象限的反正切函数 
　　sinh(x)：超越正弦函数 
　　cosh(x)：超越馀弦函数 
　　tanh(x)：超越正切函数 
　　asinh(x)：反超越正弦函数 
　　acosh(x)：反超越馀弦函数 
　　atanh(x)：反超越正切函数 
　　三、适用於向量的常用函数有：
　　min(x): 向量x的元素的最小值 
　　max(x): 向量x的元素的最大值 
　　mean(x): 向量x的元素的平均值 
　　median(x): 向量x的元素的中位数 
　　std(x): 向量x的元素的标准差 
　　diff(x): 向量x的相邻元素的差 
　　sort(x): 对向量x的元素进行排序（Sorting） 
　　length(x): 向量x的元素个数 
　　norm(x): 向量x的欧氏（Euclidean）长度 
　　sum(x): 向量x的元素总和 
　　prod(x): 向量x的元素总乘积 
　　cumsum(x): 向量x的累计元素总和 
　　cumprod(x): 向量x的累计元素总乘积 
　　dot(x, y): 向量x和y的内积 
　　cross(x, y): 向量x和y的外积 
　　四、MATLAB的永久常数
　　i或j：基本虚数单位（即） 
　　eps：系统的浮点（Floating-point）精确度 
　　inf：无限大， 例如1/0 
　　nan或NaN：非数值（Not a number），例如0/0 
　　pi：圆周率 p（= 3.1415926...） 
　　realmax：系统所能表示的最大数值 
　　realmin：系统所能表示的最小数值 
　　nargin: 函数的输入引数个数 
　　nargin: 函数的输出引数个数 
　　五、MATLAB基本绘图函数
　　plot: x轴和y轴均为线性刻度（Linear scale） 
　　loglog: x轴和y轴均为对数刻度（Logarithmic scale） 
　　semilogx: x轴为对数刻度，y轴为线性刻度 
　　semilogy: x轴为线性刻度，y轴为对数刻度 
　　六、plot绘图函数的叁数 
　　字元 颜色 字元 图线型态 
　　 y 黄色 . 点 
　　 k 黑色 o 圆 
　　 w 白色 x x 
　　 b 蓝色 + + 
　　 g 绿色 * * 
　　 r 红色 - 实线 
　　 c 亮青色 : 点线 
　　 m 锰紫色 -. 点虚线 
　　 -- 虚线 
　　七、注解
　　xlabel('Input Value'); % x轴注解 
　　ylabel('Function Value'); % y轴注解 
　　title('Two Trigonometric Functions'); % 图形标题 
　　legend('y = sin(x)','y = cos(x)'); % 图形注解 
　　grid on; % 显示格线 
　　八、二维绘图函数
　　bar 长条图 
　　 errorbar 图形加上误差范围 
　　 fplot 较精确的函数图形 
　　 polar 极座标图 
　　 hist 累计图 
　　 rose 极座标累计图 
　　 stairs 阶梯图 
　　 stem 针状图 
　　 fill 实心图 
　　 feather 羽毛图 
　　 compass 罗盘图 
　　 quiver 向量场图 

－－－－－－－－－－－－－－－－－－－－－－－－－－－－
附录1 常用命令

附录1.1 管理用命令函数名 功能描述 函数名 功能描述

addpath 增加一条搜索路径 rmpath 删除一条搜索路径

demo 运行Matlab演示程序 type 列出.M文件

doc 装入超文本文档 version 显示Matlab的版本号

help 启动联机帮助 what 列出当前目录下的有关文件

lasterr 显示最后一条信息 whatsnew 显示Matlab的新特性

lookfor 搜索关键词的帮助 which 造出函数与文件所在的目录

path 设置或查询Matlab路径





附录1.2管理变量与工作空间用命令 函数名 功能描述 函数名功能描述

clear 删除内存中的变量与函数 pack 整理工作空间内存

disp 显示矩阵与文本 save 将工作空间中的变量存盘

length 查询向量的维数 size 查询矩阵的维数

load 从文件中装入数据 who,whos 列出工作空间中的变量名





附录1.3文件与操作系统处理命令 函数名 功能描述 函数名 功能描述

cd 改变当前工作目录 edit 编辑.M文件

delete 删除文件 matlabroot 获得Matlab的安装根目录

diary 将Matlab运行命令存盘 tempdir 获得系统的缓存目录

dir 列出当前目录的内容 tempname 获得一个缓存(temp)文件

! 执行操作系统命令





附录1.4窗口控制命令 函数名 功能描述 函数名 功能描述

echo 显示文件中的Matlab中的命令 more 控制命令窗口的输出页面

format 设置输出格式





附录1.5启动与退出命令 函数名 功能描述 函数名 功能描述

matlabrc 启动主程序 quit 退出Matlab环境

startup

Matlab自启动程序





附录2 运算符号与特殊字符附录

2.1运算符号与特殊字符函数名 功能描述 函数名 功能描述

+ 加 ... 续行标志

- 减 , 分行符(该行结果不显示)

* 矩阵乘 ; 分行符(该行结果显示)

.* 向量乘 % 注释标志

^ 矩阵乘方 ! 操作系统命令提示符

.^ 向量乘方 ' 矩阵转置

kron 矩阵kron积 . 向量转置

\ 矩阵左除 = 赋值运算

/ 矩阵右除 == 关系运算之相等

.\ 向量左除 ~= 关系运算之不等

./ 向量右除 < 关系运算之小于

: 向量生成或子阵提取 <= 关系运算之小于等于

() 下标运算或参数定义 > 关系运算之大于

[] 矩阵生成 >= 关系运算之大于等于

{} & 逻辑运算之与

. 结构字段获取符 | 逻辑运算之或

. 点乘运算,常与其他运算符联合使用(如.\) ~ 逻辑运算之非

xor 逻辑运算之异成





附录2.2逻辑函数 函数名 功能描述 函数名 功能描述

all 测试向量中所用元素是否为真 is*(一类函数)

检测向量状态.其中*表示一个确定的函数(isinf)

any 测试向量中是否有真元素 *isa 检测对象是否为某一个类的对象

exist 检验变量或文件是否定义 logical 将数字量转化为逻辑量

find 查找非零元素的下标





附录3 语言结构与调试

附录3.1编程语言 函数名 功能描述 函数名 功能描述

builtin 执行Matlab内建的函数 global 定义全局变量

eval 执行Matlab语句构成的字符串 nargchk 函数输入输出参数个数检验

feval 执行字符串指定的文件 script Matlab语句及文件信息

function Matlab函数定义关键词





附录3.2控制流程 函数名 功能描述 函数名 功能描述

break 中断循环执行的语句 if 条件转移语句

case 与switch结合实现多路转移 otherwise 多路转移中的缺省执行部分

else 与if一起使用的转移语句 return 返回调用函数

elseif 与if一起使用的转移语句 switch 与case结合实现多路转移

end 结束控制语句块 warning 显示警告信息

error 显示错误信息 while 循环语句

for 循环语句





附录3.3交互输入 函数名 功能描述 函数名 功能描述

input 请求输入 menu 菜单生成

keyboard 启动键盘管理 pause 暂停执行





附录3.4面向对象编程 函数名 功能描述 函数名 功能描述

class 生成对象 isa 判断对象是否属于某一类

double 转换成双精度型 superiorto 建立类的层次关系

inferiorto 建立类的层次关系 unit8 转换成8字节的无符号整数

inline 建立一个内嵌对象





附录3.5调试 函数名 功能描述 函数名 功能描述

dbclear 清除调试断点 dbstatus 列出所有断点情况

dbcont 调试继续执行 dbstep 单步执行

dbdown 改变局部工作空间内存 dbstop 设置调试断点

dbmex 启动对Mex文件的调试 sbtype 列出带命令行标号的.M文件

dbquit 退出调试模式 dbup 改变局部工作空间内容

dbstack 列出函数调用关系





附录4 基本矩阵与矩阵处理

附录4.1基本矩阵 函数名 功能描述 函数名 功能描述

eye 产生单位阵 rand 产生随机分布矩阵

linspace 构造线性分布的向量 randn 产生正态分布矩阵

logspace 构造等对数分布的向量 zeros 产生零矩阵

ones 产生元素全部为1的矩阵 : 产生向量





附录4.2特殊向量与常量 函数名 功能描述 函数名 功能描述

ans 缺省的计算结果变量 non 非数值常量常由0/0或Inf/Inf获得

computer 运行Matlab的机器类型 nargin 函数中参数输入个数

eps 精度容许误差(无穷小) nargout 函数中输出变量个数

flops 浮点运算计数 pi 圆周率

i 复数单元 realmax 最大浮点数值

inf 无穷大 realmin 最小浮点数值

inputname 输入参数名 varargin 函数中输入的可选参数

j 复数单元 varargout 函数中输出的可选参数





附录4.3时间与日期 函数名 功能描述 函数名 功能描述

calender 日历 eomday 计算月末

clock 时钟 etime 所用时间函数

cputime 所用的CPU时间 now 当前日期与时间

date 日期 tic 启动秒表计时器

datenum 日期(数字串格式) toc 读取秒表计时器

datestr 日期(字符串格式) weekday 星期函数

datevoc 日期(年月日分立格式)





附录4.4矩阵处理 函数名 功能描述 函数名 功能描述

cat 向量连接 reshape 改变矩阵行列个数

diag 建立对角矩阵或获取对角向量 rot90 将矩阵旋转90度

fliplr 按左右方向翻转矩阵元素 tril 取矩阵的下三角部分

flipud 按上下方向翻转矩阵元素 triu 取矩阵的上三角部分

repmat 复制并排列矩阵函数





附录5 特殊矩阵 函数名 功能描述 函数名 功能描述

compan 生成伴随矩阵 invhilb 生成逆hilbert矩阵

gallery 生成一些小的测试矩阵 magic 生成magic矩阵

hadamard 生成hadamard矩阵 pascal 生成pascal矩阵

hankel 生成hankel矩阵 toeplitz 生成toeplitz矩阵

hilb 生成hilbert矩阵 wilkinson 生成wilkinson特征值测试矩阵





附录6 数学函数

附录6.1三角函数 函数名 功能描述 函数名 功能描述

sin/asin 正弦/反正弦函数 sec/asec 正割/反正割函数

sinh/asinh 双曲正弦/反双曲正弦函数 sech/asech 双曲正割/反双曲正割函数

cos/acos 余弦/反余弦函数 csc/acsc 余割/反余割函数

cosh/acosh 双曲余弦/反双曲余弦函数 csch/acsch 双曲余割/反双曲余割函数

tan/atan 正切/反正切函数 cot/acot 余切/反余切函数

tanh/atanh 双曲正切/反双曲正切函数 coth/acoth 双曲余切/反双曲余切函数

atan2 四个象限内反正切函数





附录6.2指数函数 函数名 功能描述 函数名 功能描述

exp 指数函数 log10 常用对数函数

log 自然对数函数 sqrt 平方根函数





附录6.3复数函数 函数名 功能描述 函数名 功能描述

abs 绝对值函数 imag 求虚部函数

angle 角相位函数 real 求实部函数

conj 共轭复数函数





附录6.4数值处理 函数名 功能描述 函数名 功能描述

fix 沿零方向取整 round 舍入取整

floor 沿-∞方向取整 rem 求除法的余数

ceil 沿+∞方向取整 sign 符号函数





附录6.5其他特殊数学函数 函数名 功能描述 函数名 功能描述

airy airy函数 erfcx 比例互补误差函数

besselh bessel函数(hankel函数) erfinv 逆误差函数

bessili 改进的第一类bessel函数 expint 指数积分函数

besselk 改进的第二类bessel函数 gamma gamma函数

besselj 第一类bessel函数 gammainc 非完全gamma函数

bessely 第二类bessel函数 gammaln gamma对数函数

beta beta函数 gcd 最大公约数

betainc 非完全的beta函数 lcm 最小公倍数

betaln beta对数函数 log2 分割浮点数

elipj Jacobi椭圆函数 legendre legendre伴随函数

ellipke 完全椭圆积分 pow2 基2标量浮点数

erf 误差函数 rat 有理逼近

erfc 互补误差函数 rats 有理输出
－－－－－－－－－－－－－－－－－－－－－－－－－－－－－
A a
abs 绝对值、模、字符的ASCII码值
acos 反余弦
acosh 反双曲余弦
acot 反余切
acoth 反双曲余切
acsc 反余割
acsch 反双曲余割
align 启动图形对象几何位置排列工具
all 所有元素非零为真
angle 相角
ans 表达式计算结果的缺省变量名
any 所有元素非全零为真
area 面域图
argnames 函数M文件宗量名
asec 反正割
asech 反双曲正割
asin 反正弦
asinh 反双曲正弦
assignin 向变量赋值
atan 反正切
atan2 四象限反正切
atanh 反双曲正切
autumn 红黄调秋色图阵
axes 创建轴对象的低层指令
axis 控制轴刻度和风格的高层指令
B b

bar 二维直方图
bar3 三维直方图
bar3h 三维水平直方图
barh 二维水平直方图
base2dec X进制转换为十进制
bin2dec 二进制转换为十进制
blanks 创建空格串
bone 蓝色调黑白色图阵
box 框状坐标轴
break while 或for 环中断指令
brighten 亮度控制


C c

capture （3版以前）捕获当前图形
cart2pol 直角坐标变为极或柱坐标
cart2sph 直角坐标变为球坐标
cat 串接成高维数组
caxis 色标尺刻度
cd 指定当前目录
cdedit 启动用户菜单、控件回调函数设计工具
cdf2rdf 复数特征值对角阵转为实数块对角阵
ceil 向正无穷取整
cell 创建元胞数组
cell2struct 元胞数组转换为构架数组
celldisp 显示元胞数组内容
cellplot 元胞数组内部结构图示
char 把数值、符号、内联类转换为字符对象
chi2cdf 分布累计概率函数
chi2inv 分布逆累计概率函数
chi2pdf 分布概率密度函数
chi2rnd 分布随机数发生器
chol Cholesky分解
clabel 等位线标识
cla 清除当前轴
class 获知对象类别或创建对象
clc 清除指令窗
clear 清除内存变量和函数
clf 清除图对象
clock 时钟
colorcube 三浓淡多彩交叉色图矩阵
colordef 设置色彩缺省值
colormap 色图
colspace 列空间的基
close 关闭指定窗口
colperm 列排序置换向量
comet 彗星状轨迹图
comet3 三维彗星轨迹图
compass 射线图
compose 求复合函数
cond （逆）条件数
condeig 计算特征值、特征向量同时给出条件数
condest 范 -1条件数估计
conj 复数共轭
contour 等位线
contourf 填色等位线
contour3 三维等位线
contourslice 四维切片等位线图
conv 多项式乘、卷积
cool 青紫调冷色图
copper 古铜调色图
cos 余弦
cosh 双曲余弦
cot 余切
coth 双曲余切
cplxpair 复数共轭成对排列
csc 余割
csch 双曲余割
cumsum 元素累计和
cumtrapz 累计梯形积分
cylinder 创建圆柱


D d

dblquad 二重数值积分
deal 分配宗量
deblank 删去串尾部的空格符
dec2base 十进制转换为X进制
dec2bin 十进制转换为二进制
dec2hex 十进制转换为十六进制
deconv 多项式除、解卷
delaunay Delaunay 三角剖分
del2 离散Laplacian差分
demo Matlab演示
det 行列式
diag 矩阵对角元素提取、创建对角阵
diary Matlab指令窗文本内容记录
diff 数值差分、符号微分
digits 符号计算中设置符号数值的精度
dir 目录列表
disp 显示数组
display 显示对象内容的重载函数
dlinmod 离散系统的线性化模型
dmperm 矩阵Dulmage-Mendelsohn 分解
dos 执行DOS 指令并返回结果
double 把其他类型对象转换为双精度数值
drawnow 更新事件队列强迫Matlab刷新屏幕
dsolve 符号计算解微分方程


E e

echo M文件被执行指令的显示
edit 启动M文件编辑器
eig 求特征值和特征向量
eigs 求指定的几个特征值
end 控制流FOR等结构体的结尾元素下标
eps 浮点相对精度
error 显示出错信息并中断执行
errortrap 错误发生后程序是否继续执行的控制
erf 误差函数
erfc 误差补函数
erfcx 刻度误差补函数
erfinv 逆误差函数
errorbar 带误差限的曲线图
etreeplot 画消去树
eval 串演算指令
evalin 跨空间串演算指令
exist 检查变量或函数是否已定义
exit 退出Matlab环境
exp 指数函数
expand 符号计算中的展开操作
expint 指数积分函数
expm 常用矩阵指数函数
expm1 Pade法求矩阵指数
expm2 Taylor法求矩阵指数
expm3 特征值分解法求矩阵指数
eye 单位阵
ezcontour 画等位线的简捷指令
ezcontourf 画填色等位线的简捷指令
ezgraph3 画表面图的通用简捷指令
ezmesh 画网线图的简捷指令
ezmeshc 画带等位线的网线图的简捷指令
ezplot 画二维曲线的简捷指令
ezplot3 画三维曲线的简捷指令
ezpolar 画极坐标图的简捷指令
ezsurf 画表面图的简捷指令
ezsurfc 画带等位线的表面图的简捷指令



F f

factor 符号计算的因式分解
feather 羽毛图
feedback 反馈连接
feval 执行由串指定的函数
fft 离散Fourier变换
fft2 二维离散Fourier变换
fftn 高维离散Fourier变换
fftshift 直流分量对中的谱
fieldnames 构架域名
figure 创建图形窗
fill3 三维多边形填色图
find 寻找非零元素下标
findobj 寻找具有指定属性的对象图柄
findstr 寻找短串的起始字符下标
findsym 机器确定内存中的符号变量
finverse 符号计算中求反函数
fix 向零取整
flag 红白蓝黑交错色图阵
fliplr 矩阵的左右翻转
flipud 矩阵的上下翻转
flipdim 矩阵沿指定维翻转
floor 向负无穷取整
flops 浮点运算次数
flow Matlab提供的演示数据
fmin 求单变量非线性函数极小值点（旧版）
fminbnd 求单变量非线性函数极小值点
fmins 单纯形法求多变量函数极小值点（旧版）
fminunc 拟牛顿法求多变量函数极小值点
fminsearch 单纯形法求多变量函数极小值点
fnder 对样条函数求导
fnint 利用样条函数求积分
fnval 计算样条函数区间内任意一点的值
fnplt 绘制样条函数图形
fopen 打开外部文件
for 构成for环用
format 设置输出格式
fourier Fourier 变换
fplot 返函绘图指令
fprintf 设置显示格式
fread 从文件读二进制数据
fsolve 求多元函数的零点
full 把稀疏矩阵转换为非稀疏阵
funm 计算一般矩阵函数
funtool 函数计算器图形用户界面
fzero 求单变量非线性函数的零点


G g

gamma 函数
gammainc 不完全 函数
gammaln 函数的对数
gca 获得当前轴句柄
gcbo 获得正执行"回调"的对象句柄
gcf 获得当前图对象句柄
gco 获得当前对象句柄
geomean 几何平均值
get 获知对象属性
getfield 获知构架数组的域
getframe 获取影片的帧画面
ginput 从图形窗获取数据
global 定义全局变量
gplot 依图论法则画图
gradient 近似梯度
gray 黑白灰度
grid 画分格线
griddata 规则化数据和曲面拟合
gtext 由鼠标放置注释文字
guide 启动图形用户界面交互设计工具


H h

harmmean 调和平均值
help 在线帮助
helpwin 交互式在线帮助
helpdesk 打开超文本形式用户指南
hex2dec 十六进制转换为十进制
hex2num 十六进制转换为浮点数
hidden 透视和消隐开关
hilb Hilbert矩阵
hist 频数计算或频数直方图
histc 端点定位频数直方图
histfit 带正态拟合的频数直方图
hold 当前图上重画的切换开关
horner 分解成嵌套形式
hot 黑红黄白色图
hsv 饱和色图


I i

if-else-elseif 条件分支结构
ifft 离散Fourier反变换
ifft2 二维离散Fourier反变换
ifftn 高维离散Fourier反变换
ifftshift 直流分量对中的谱的反操作
ifourier Fourier反变换
i, j 缺省的"虚单元"变量
ilaplace Laplace反变换
imag 复数虚部
image 显示图象
imagesc 显示亮度图象
imfinfo 获取图形文件信息
imread 从文件读取图象
imwrite 把
imwrite 把图象写成文件
ind2sub 单下标转变为多下标
inf 无穷大
info MathWorks公司网点地址
inline 构造内联函数对象
inmem 列出内存中的函数名
input 提示用户输入
inputname 输入宗量名
int 符号积分
int2str 把整数数组转换为串数组
interp1 一维插值
interp2 二维插值
interp3 三维插值
interpn N维插值
interpft 利用FFT插值
intro Matlab自带的入门引导
inv 求矩阵逆
invhilb Hilbert矩阵的准确逆
ipermute 广义反转置
isa 检测是否给定类的对象
ischar 若是字符串则为真
isequal 若两数组相同则为真
isempty 若是空阵则为真
isfinite 若全部元素都有限则为真
isfield 若是构架域则为真
isglobal 若是全局变量则为真
ishandle 若是图形句柄则为真
ishold 若当前图形处于保留状态则为真
isieee 若计算机执行IEEE规则则为真
isinf 若是无穷数据则为真
isletter 若是英文字母则为真
islogical 若是逻辑数组则为真
ismember 检查是否属于指定集
isnan 若是非数则为真
isnumeric 若是数值数组则为真
isobject 若是对象则为真
isprime 若是质数则为真
isreal 若是实数则为真
isspace 若是空格则为真
issparse 若是稀疏矩阵则为真
isstruct 若是构架则为真
isstudent 若是Matlab学生版则为真
iztrans 符号计算Z反变换


J j , K k

jacobian 符号计算中求Jacobian 矩阵
jet 蓝头红尾饱和色
jordan 符号计算中获得 Jordan标准型
keyboard 键盘获得控制权
kron Kronecker乘法规则产生的数组


L l

laplace Laplace变换
lasterr 显示最新出错信息
lastwarn 显示最新警告信息
leastsq 解非线性最小二乘问题（旧版）
legend 图形图例
lighting 照明模式
line 创建线对象
lines 采用plot 画线色
linmod 获连续系统的线性化模型
linmod2 获连续系统的线性化精良模型
linspace 线性等分向量
ln 矩阵自然对数
load 从MAT文件读取变量
log 自然对数
log10 常用对数
log2 底为2的对数
loglog 双对数刻度图形
logm 矩阵对数
logspace 对数分度向量
lookfor 按关键字搜索M文件
lower 转换为小写字母
lsqnonlin 解非线性最小二乘问题
lu LU分解


M m

mad 平均绝对值偏差
magic 魔方阵
maple &nb, sp; 运作 Maple格式指令
mat2str 把数值数组转换成输入形态串数组
material 材料反射模式
max 找向量中最大元素
mbuild 产生EXE文件编译环境的预设置指令
mcc 创建MEX或EXE文件的编译指令
mean 求向量元素的平均值
median 求中位数
menuedit 启动设计用户菜单的交互式编辑工具
mesh 网线图
meshz 垂帘网线图
meshgrid 产生"格点"矩阵
methods 获知对指定类定义的所有方法函数
mex 产生MEX文件编译环境的预设置指令
mfunlis 能被mfun计算的MAPLE经典函数列表
mhelp 引出 Maple的在线帮助
min 找向量中最小元素
mkdir 创建目录
mkpp 逐段多项式数据的明晰化
mod 模运算
more 指令窗中内容的分页显示
movie 放映影片动画
moviein 影片帧画面的内存预置
mtaylor 符号计算多变量Taylor级数展开


N n

ndims 求数组维数
NaN 非数（预定义）变量
nargchk 输入宗量数验证
nargin 函数输入宗量数
nargout 函数输出宗量数
ndgrid 产生高维格点矩阵
newplot 准备新的缺省图、轴
nextpow2 取最接近的较大2次幂
nnz 矩阵的非零元素总数
nonzeros 矩阵的非零元素
norm 矩阵或向量范数
normcdf 正态分布累计概率密度函数
normest 估计矩阵2范数
norminv 正态分布逆累计概率密度函数
normpdf 正态分布概率密度函数
normrnd 正态随机数发生器
notebook 启动Matlab和Word的集成环境
null 零空间
num2str 把非整数数组转换为串
numden 获取最小公分母和相应的分子表达式
nzmax 指定存放非零元素所需内存


O o

ode1 非Stiff 微分方程变步长解算器
ode15s Stiff 微分方程变步长解算器
ode23t 适度Stiff 微分方程解算器
ode23tb Stiff 微分方程解算器
ode45 非Stiff 微分方程变步长解算器
odefile ODE 文件模板
odeget 获知ODE 选项设置参数
odephas2 ODE 输出函数的二维相平面图
odephas3 ODE 输出函数的三维相空间图
odeplot ODE 输出函数的时间轨迹图
odeprint 在Matlab指令窗显示结果
odeset 创建或改写 ODE选项构架参数值
ones 全1数组
optimset 创建或改写优化泛函指令的选项参数值
orient 设定图形的排放方式
orth 值空间正交化


P p

pack 收集Matlab内存碎块扩大内存
pagedlg 调出图形排版对话框
patch 创建块对象
path 设置Matlab搜索路径的指令
pathtool 搜索路径管理器
pause 暂停
pcode 创建预解译P码文件
pcolor 伪彩图
peaks Matlab提供的典型三维曲面
permute 广义转置
pi （预定义变量）圆周率
pie 二维饼图
pie3 三维饼图
pink 粉红色图矩阵
pinv 伪逆
plot 平面线图
plot3 三维线图
plotmatrix 矩阵的散点图
plotyy 双纵坐标图
poissinv 泊松分布逆累计概率分布函数
poissrnd 泊松分布随机数发生器
pol2cart 极或柱坐标变为直角坐标
polar 极坐标图
poly 矩阵的特征多项式、根集对应的多项式
poly2str 以习惯方式显示多项式
poly2sym 双精度多项式系数转变为向量符号多项式
polyder 多项式导数
polyfit 数据的多项式拟合
polyval 计算多项式的值
polyvalm 计算矩阵多项式
pow2 2的幂
ppval 计算分段多项式
pretty 以习惯方式显示符号表达式
print 打印图形或SIMULINK模型
printsys 以习惯方式显示有理分式
prism 光谱色图矩阵
procread 向MAPLE输送计算程序
profile 函数文件性能评估器
propedit 图形对象属性编辑器
pwd 显示当前工作目录


Q q

quad 低阶法计算数值积分
quad8 高阶法计算数值积分(QUADL)
quit 推出Matlab 环境
quiver 二维方向箭头图
quiver3 三维方向箭头图


R r

rand 产生均匀分布随机数
randn 产生正态分布随机数
randperm 随机置换向量
range 样本极差
rank 矩阵的秩
rats 有理输出
rcond 矩阵倒条件数估计
real 复数的实部
reallog 在实数域内计算自然对数
realpow 在实数域内计算乘方
realsqrt 在实数域内计算平方根
realmax 最大正浮点数
realmin 最小正浮点数
rectangle 画"长方框"
rem 求余数
repmat 铺放模块数组
reshape 改变数组维数、大小
residue 部分分式展开
return 返回
ribbon 把二维曲线画成三维彩带图
rmfield 删去构架的域
roots 求多项式的根
rose 数扇形图
rot90 矩阵旋转90度
rotate 指定的原点和方向旋转
rotate3d 启动三维图形视角的交互设置功能
round 向最近整数圆整
rref 简化矩阵为梯形形式
rsf2csf 实数块对角阵转为复数特征值对角阵
rsums Riemann和

S s

save 把内存变量保存为文件
scatter 散点图
scatter3 三维散点图
sec 正割
sech 双曲正割
semilogx X轴对数刻度坐标图
semilogy Y轴对数刻度坐标图
series 串联连接
set 设置图形对象属性
setfield 设置构架数组的域
setstr 将ASCII码转换为字符的旧版指令
sign 根据符号取值函数
signum 符号计算中的符号取值函数
sim 运行SIMULINK模型
simget 获取SIMULINK模型设置的仿真参数
simple 寻找最短形式的符号解
simplify 符号计算中进行简化操作
simset 对SIMULINK模型的仿真参数进行设置
simulink 启动SIMULINK模块库浏览器
sin 正弦
sinh 双曲正弦
size 矩阵的大小
slice 立体切片图
solve 求代数方程的符号解
spalloc 为非零元素配置内存
sparse 创建稀疏矩阵
spconvert 把外部数据转换为稀疏矩阵
spdiags 稀疏对角阵
spfun 求非零元素的函数值
sph2cart 球坐标变为直角坐标
sphere 产生球面
spinmap 色图彩色的周期变化
spline 样条插值
spones 用1置换非零元素
sprandsym 稀疏随机对称阵
sprank 结构秩
spring 紫黄调春色图
sprintf 把格式数据写成串
spy 画稀疏结构图
sqrt 平方根
sqrtm 方根矩阵
squeeze 删去大小为1的"孤维"
sscanf 按指定格式读串
stairs 阶梯图
std 标准差
stem 二维杆图
step 阶跃响应指令
str2double 串转换为双精度值
str2mat 创建多行串数组
str2num 串转换为数
strcat 接成长串
strcmp 串比较
strjust 串对齐
strmatch 搜索指定串
strncmp 串中前若干字符比较
strrep 串替换
strtok 寻找第一间隔符前的内容
struct 创建构架数组
struct2cell 把构架转换为元胞数组
strvcat 创建多行串数组
sub2ind 多下标转换为单下标
subexpr 通过子表达式重写符号对象
subplot 创建子图
subs 符号计算中的符号变量置换
subspace 两子空间夹角
sum 元素和
summer 绿黄调夏色图
superiorto 设定优先级
surf 三维着色表面图
surface 创建面对象
surfc 带等位线的表面图
surfl 带光照的三维表面图
surfnorm 空间表面的法线
svd 奇异值分解
svds 求指定的若干奇异值
switch-case-otherwise 多分支结构
sym2poly 符号多项式转变为双精度多项式系数向量
symmmd 对称最小度排序
symrcm 反向Cuthill-McKee排序
syms 创建多个符号对象
 
T t

tan 正切
tanh 双曲正切
taylortool 进行Taylor逼近分析的交互界面
text 文字注释
tf 创建传递函数对象
tic 启动计时器
title 图名
toc 关闭计时器
trapz 梯形法数值积分
treelayout 展开树、林
treeplot 画树图
tril 下三角阵
trim 求系统平衡点
trimesh 不规则格点网线图
trisurf 不规则格点表面图 triu 上三角阵 try-catch 控制流中的Try-catch结构 type 显示M文件
U u
uicontextmenu 创建现场菜单
uicontrol 创建用户控件
uimenu 创建用户菜单
unmkpp 逐段多项式数据的反明晰化
unwrap 自然态相角
upper 转换为大写字母


V v

var 方差
varargin 变长度输入宗量
varargout 变长度输出宗量
vectorize 使串表达式或内联函数适于数组运算
ver 版本信息的获取
view 三维图形的视角控制
voronoi Voronoi多边形
vpa 任意精度（符号类）数值


W w

warning 显示警告信息
what 列出当前目录上的文件
whatsnew 显示Matlab中 Readme文件的内容
which 确定函数、文件的位置
while 控制流中的While环结构
white 全白色图矩阵
whitebg 指定轴的背景色
who 列出内存中的变量名
whos 列出内存中变量的详细信息
winter 蓝绿调冬色图
workspace 启动内存浏览器


X x , Y y , Z z

xlabel X轴名
xor 或非逻辑
yesinput 智能输入指令
ylabel Y轴名
zeros 全零数组
zlabel Z轴名
zoom 图形的变焦放大和缩小
ztrans 符号计算Z变换 

from [豆瓣](http://www.douban.com/note/181460051/)