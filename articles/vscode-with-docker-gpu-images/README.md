# Using Tensorflow with GPU Support in VS Code using Docker

This repo is a simple example of how to use tensorflow with GPU support while writing code in VS Code in jupyter notebooks. No need to install python or tensorflow on your machine - we use the docker images to create a tensorflow environment that we can recreate as many as we like.

## Steps

### 1. Start Docker Container

Use the below commands to clone this repo and run the docker image on your machine. The first line below clones the repo (if you haven't cloned it yet) - if you already have cloned the repo - then simple open terminal and ```cd``` into the code repo directory (hope you know how to ```cd``` :stuck_out_tongue_winking_eye: ) 

```bash
git clone https://github.com/the-geeks-diary/machine-learning-guides.git #If you haven't cloned the repo
cd ./machine-learning-guides/articles/vscode-with-docker-gpu-images
docker-compose up
```
You should see output similar to what is whown below:

```bash
[I 06:22:39.209 LabApp] Writing notebook server cookie secret to /root/.local/share/jupyter/runtime/notebook_cookie_secret
[I 06:22:40.550 LabApp] jupyter_tensorboard extension loaded.
[I 06:22:40.557 LabApp] JupyterLab extension loaded from /usr/local/lib/python3.8/dist-packages/jupyterlab
[I 06:22:40.557 LabApp] JupyterLab application directory is /usr/local/share/jupyter/lab
[I 06:22:40.560 LabApp] [Jupytext Server Extension] NotebookApp.contents_manager_class is (a subclass of) jupytext.TextFileContentsManager already - OK
[I 06:22:40.561 LabApp] Serving notebooks from local directory: /environment
[I 06:22:40.561 LabApp] Jupyter Notebook 6.4.10 is running at:
[I 06:22:40.561 LabApp] http://hostname:8888/?token=...
[I 06:22:40.561 LabApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
```

The port 8888 on container is mapped against the local port 8888 - this means that you can access the Jupyter notebook server using the URL ```http://localhost:8888```. In the next step we will connect to the server from VS Code jupyter extension.

### 2. Create a new Notebook or Open the example notebook

You can create a new notebook or open the one that is provided as an [example](./remote-kernel-example.ipynb) in this repo. Open the notebook and follow the steps mentioned on the [article](https://thegeeksdiary.com/2023/05/11/super-fast-tensorflow-2-setup-with-gpu-support-in-vs-code/) on my [blog](https://thegeeksdiary.com).
