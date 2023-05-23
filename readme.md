# 安装

1. 进入dockerfile文件目录，运行dockerfile文件创建镜像

    ```
    cd /path_to_dockerfile

    docker build -t multinerf_df .
    ```
 
2. 在portainer.io中用镜像创建容器，配置如下
   
   ![20230523141634](https://raw.githubusercontent.com/skykone1/images/main/20230523141634.png)

   ![20230523141643](https://raw.githubusercontent.com/skykone1/images/main/20230523141643.png)

   ![20230523141650](https://raw.githubusercontent.com/skykone1/images/main/20230523141650.png)

3. 用root启动容器
   
    ```
    docker exec -ti -u root multinerf_df_con bash
    ```

4. 安装colmap
   
   ```
   sudo apt-get install \
    git \
    cmake \
    ninja-build \
    build-essential \
    libboost-program-options-dev \
    libboost-filesystem-dev \
    libboost-graph-dev \
    libboost-system-dev \
    libboost-test-dev \
    libeigen3-dev \
    libflann-dev \
    libfreeimage-dev \
    libmetis-dev \
    libgoogle-glog-dev \
    libgflags-dev \
    libsqlite3-dev \
    libglew-dev \
    qtbase5-dev \
    libqt5opengl5-dev \
    libcgal-dev \
    libceres-dev
    git clone https://github.com/colmap/colmap.git
    cd colmap
    git checkout dev
    mkdir build
    cd build
    cmake .. -GNinja -DCMAKE_CUDA_ARCHITECTURES="75"
    ninja
    sudo ninja install
    sudo apt-get install -y \
        nvidia-cuda-toolkit \
        nvidia-cuda-toolkit-gcc  
   ```
  


# 训练

1. 运行训练命令
   
    ```
    source scripts/train_colmap.sh
    ```
2. 开始训练
   
    ![![20230523143641](httpsraw.githubusercontent.comskykone1imagesmain20230523143641.png)](https://raw.githubusercontent.com/skykone1/images/main/!%5B20230523143641%5D(httpsraw.githubusercontent.comskykone1imagesmain20230523143641.png).png)


# 测试

1. 运行测试命令
   
   ```
   scripts/eval_colmap.sh
   ```


