## 项目目的

用 C++ 部署 pytorch 训练的 mnist，yolov5s, retinaface(mobile0.25) 模型

## 目录介绍

### mnist_cpp
```
9:30                mnist    mnist python 训练代码
15:08      CMakeLists.txt    cmake文件
21:39        CRnnDeploy.h
17:07            main.cpp    main函数
16:47              run.sh    构建sh
```

### yolov5_cpp
```
weights/last.torchscript.pt
```

### face_detector_cpp(ncnn) 缺点： python和c++版差别有点大，尤其是在测试sample.jpg图片时，人脸检测的数量差别明显，有待优化
```
./run.sh
```
<img src="./face_detector_cpp/test.png" alt="在这里插入图片描述" style="zoom:60%;" />

## 环境相关
```
1.Manjaro系统
2.gcc7
3.python3.6.10
```

## 环境搭建步骤

```
1.下载pytorch c++版：libtorch
2.安装opencv 可下载源文件自己构建也可直接pacman安装，请注意依赖问题，vtk包等
```

## 安装过程遇到的问题
```text
1.在安装opencv时，无论是 sudo pacman -S opencv ，还是 下载二进制包编译安装，都是可以成功的, 测试也是没问题的
2.加入libtorch后开始报错
/usr/bin/ld: CMakeFiles/demo.dir/main.cpp.o: in function `main':
main.cpp:(.text+0x95): undefined reference to `cv::imread(std::string const&, int)'

原因肯定是哪里的版本不对，又重新下载了libtorch，不过这个会下的慢，解压后替换原来的，完美运行！
Download here (cxx11 ABI):
https://download.pytorch.org/libtorch/cu101/libtorch-cxx11-abi-shared-with-deps-1.6.0%2Bcu101.zip
```
