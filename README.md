## README


    
    cli_data_sales_num.py       cli   假数据测试
    curl_post.sh                curl  假数据测试
    date_sales_num.py           预测核心py函数
    flask_data_sales_num.py     flask调用预测核心py函数
    install_packages.sh         docker里跑这个安装conda所有依赖
    request_data_sales_num.py   requests包 假数据测试
    requirements.txt            py依赖包
    dcoker-compose.yml          docker-compose一体化启动文件
    Dockerfile                  Docker编译脚本

    
## Docker 的镜像提交

## Docker copy 会引发build

## Docker 如何执行文件
docker tag a3b256b601c9 gc/python:devel
docker images gc/python

## Docker 删除无用的None镜像
docker run -it gc/python:devel /bin/bash
docker run -p 80:80 gc/python:devel

## 如何提交到私有仓库
docker tag 
docker push