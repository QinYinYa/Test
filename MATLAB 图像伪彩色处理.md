# MATLAB 图像伪彩色处理



伪彩色处理是根据特定的准则对灰度值附以彩色的处理，是将黑白图像转化为彩色图像，或者将单色图像变换成给定彩色分布的图像。由于人眼对彩色的分辨率远高于灰度差的分辨率，所以这种技术可用来识别灰度差较小的像素。以下是使用MATLAB来实现。

我使用的是灰度级变换方法：先将灰度图像经不同变换特性的红、绿、蓝三个通道，不同的灰度级三种颜色实施的变换不同，再讲三个不同的输出合成某种颜色，这样不同大小的灰度级就可以合成不同的颜色。

灰度值和三个通道的映射关系如图（这种关系可以根据需要更改）：

![img](http://blog.csdn.net/qq_28215385/article/details/72845435)

![img](http://img.blog.csdn.net/20170602172303749)

![img](http://img.blog.csdn.net/20170602172359301)

![img](http://img.blog.csdn.net/20170602172315765)

![img](http://blog.csdn.net/qq_28215385/article/details/72845435)

由图中的对应关系，可以得出r、g、b、在四个灰度级的对应的函数关系式，用MATLAB实现如下:

```matlab
im=imread('cell.jpg');
gray=rgb2gray(im);
I=double(gray);
[m,n]=size(I);
L=256;
for i=1:m
    for j=1:n
if I(i,j)<=L/4
    R(i,j)=0;
    G(i,j)=4*I(i,j);
    B(i,j)=L;
else if I(i,j)<=L/2
        R(i,j)=0;
        G(i,j)=L;
        B(i,j)=-4*I(i,j)+2*L;
    else if I(i,j)<=3*L/4
            R(i,j)=4*I(i,j)-2*L;
            G(i,j)=L;
            B(i,j)=0;
        else
            R(i,j)=L;
            G(i,j)=-4*I(i,j)+4*L;
            B(i,j)=0;
        end
    end
end
    end
end
for i=1:m
    for j=1:n
        rgbim(i,j,1)=R(i,j);
        rgbim(i,j,2)=G(i,j);
        rgbim(i,j,3)=B(i,j);
    end
end
rgbim=rgbim/256;
figure;
subplot(1,2,1);
imshow(gray);
subplot(1,2,2);
imshow(rgbim);
```

图像处理结果：

![img](http://blog.csdn.net/qq_28215385/article/details/72845435)![img](http://img.blog.csdn.net/20170602180548749)