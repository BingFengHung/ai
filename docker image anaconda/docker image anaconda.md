# Pull anaconda images
首先，先去 docker hub 找尋是否有 anaconda 的 images 可以下載，發現是有可以下載的

![](images/01.png)

先將 image pull 下來
> docker pull continuumio/anaconda3

下載下來之後，根據官網下面的開啟 container 的方式會跳錯
> docker run -i -t -p 8888:8888 continuumio/anaconda3 /bin/bash -c "/opt/conda/bin/conda install jupyter -y --quiet && mkdir /opt/notebooks && /opt/conda/bin/jupyter notebook --notebook-dir=/opt/notebooks --ip='*' --port=8888 --no-browser"


![](images/02.png)

後面有說要使用 --allow-root

在後面加上一個
> docker run -i -t -p 8888:8888 continuumio/anaconda3 /bin/bash -c "/opt/conda/bin/conda install jupyter -y --quiet && mkdir /opt/notebooks && /opt/conda/bin/jupyter notebook --notebook-dir=/opt/notebooks --ip='*' --port=8888 --no-browser --allow-root"

在後面加入 --allow-root 指令之後，即可順利運行

![](images/04.png)

並等入 http://localhost:8888，進入 jupyer notebook

![](images/03.png)

會跳出此頁面要求輸入 token

此時，我們另外開一個 termial ，登入此 container 的 shell termial，
> docker exec -it <container name> /bin/bash 

進入之後輸入 jupyter notebook list  
取得 token
![](images/05.png)

開啟 jupyter notebook termial 安裝 tensorflow

> conda install -c anaconda tensorflow-gpu
![](images/06.png)
![](images/07.png)