# [Github Actions 编译 realcugan-ncnn-vulkan MacOS版](https://github.com/Tohrusky/realcugan-ncnn-vulkan/actions)

新版本```Vulkan SDK```开启```openmp```效果不明显，建议使用老版本编译，见```build.yml```


#### 以下为 MacOS M1 GPU 环境下测试，测试图片分辨率为```1920x1080```
```
import os
import time

if __name__ == "__main__":
    print("ncnn_official")  # vulkan 1.2.162.0
    t_1 = time.time()
    for _ in range(10):
        is_run = os.system("../realcugan-ncnn-vulkan -i input.jpg -o output.jpg -s 2 -n 3")
    t_2 = time.time()
    print("time: ", (t_2 - t_1) / 10)  # time:  6.009728312492371

    print("ncnn_MyBuild_omp11_old_vulkan_sdk")  # vulkan 1.2.162.1
    t_1 = time.time()
    for _ in range(10):
        is_run = os.system("../realcugan-ncnn-vulkan_old_sdk -i input.jpg -o output.jpg -s 2 -n 3")
    t_2 = time.time()
    print("time: ", (t_2 - t_1) / 10)  # time:  6.072064208984375

    print("ncnn_MyBuild_omp11")  # vulkan 1.3.239.0
    t_1 = time.time()
    for _ in range(10):
        is_run = os.system("../realcugan-ncnn-vulkan_omp11 -i input.jpg -o output.jpg -s 2 -n 3")
    t_2 = time.time()
    print("time: ", (t_2 - t_1) / 10)  # time:  6.963544702529907

    print("ncnn_MyBuild_no_openmp")  # vulkan 1.3.239.0
    t_1 = time.time()
    for _ in range(10):
        is_run = os.system("../realcugan-ncnn-vulkan_no_openmp -i input.jpg -o output.jpg -s 2 -n 3")
    t_2 = time.time()
    print("time: ", (t_2 - t_1) / 10)  # time:  6.972248911857605
 ```
 
 Vulkan SDK 备份至Release，方便拉取
