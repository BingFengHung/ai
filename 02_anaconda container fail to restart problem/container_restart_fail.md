# Anaconda container fail to restart problem solve
發現重新開機之後，我想要再重新 start 容器，發現要再次啟動時，都會無法順利啟動
![](./images/01.PNG)
![](./images/02.PNG)

上網搜尋了一下原因，發現了以下的辦法
![](./images/03.PNG)

> docker run -i -t -p 8888:8888 continuumio/anaconda3 /bin/bash -c  "/opt/conda/bin/conda install jupyter -y --quiet && mkdir -p /opt/notebooks && /opt/conda/bin/jupyter notebook --notebook-dir=/opt/notebooks --ip='*' --port=8888 --no-browser --allow-root"

使用之後，即可順利重新啟動 container

reference: [https://forums.docker.com/t/how-to-re-run-the-continumio-anaconda3-docker-container/65713]