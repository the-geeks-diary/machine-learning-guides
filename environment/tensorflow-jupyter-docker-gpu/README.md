# Tensorflow GPU With Jupyter Notebooks

We are providing a docker image with most of the libraries pre-installed for running a full fledged machine learning environment using [tensorflow](https://www.tensorflow.org/) inside docker with GPU support. The docker image uses the base image provided by [nvidia](https://www.nvidia.com/en-in/).

The image is available on [Docker Hub](https://hub.docker.com/r/thegeeksdiary/tensorflow-jupyter-gpu).

## Running a new container

To spin up a new container using this image - please run the following commands in your terminal.

```bash
docker run --gpus all -ti -p 8888:8888 thegeeksdiary/tensorflow-jupyter-gpu:latest
```

Wait for the image to be downloaded and the container to start up. This will take a while depending on your machine and network as the image is approximately 9 GB in size, you might need to increase the allocated storage for the docker desktop on your machine - I am using the [WSL backend](https://docs.docker.com/desktop/windows/wsl/) for docker which means that that I am not affected by the image size but if you are still using Hyper-V as the virtualization backend then [this article](https://www.nakivo.com/blog/increase-disk-size-hyper-v-complete-guide/) might help you. Once the container is running you should see something like this in your terminal.

```
/usr/local/lib/python3.8/dist-packages/traitlets/traitlets.py:2544: FutureWarning: Supporting extra quotes around strings is deprecated in traitlets 5.0. You can use '' instead of "''" if you require traitlets >=5.                                                                                                                                                                      warn(                                                                                                                                                                                                           
[I 16:50:53.312 NotebookApp] Writing notebook server cookie secret to /root/.local/share/jupyter/runtime/notebook_cookie_secret
[I 16:50:53.313 NotebookApp] Authentication of /metrics is OFF, since other authentication is disabled.
[W 16:50:53.718 NotebookApp] All authentication is disabled.  Anyone who can connect to this server will be able to run code.
[I 16:50:54.492 NotebookApp] jupyter_tensorboard extension loaded.
[I 16:50:54.537 NotebookApp] JupyterLab extension loaded from /usr/local/lib/python3.8/dist-packages/jupyterlab
[I 16:50:54.537 NotebookApp] JupyterLab application directory is /usr/local/share/jupyter/lab
[I 16:50:54.539 NotebookApp] [Jupytext Server Extension] NotebookApp.contents_manager_class is (a subclass of) jupytext.TextFileContentsManager already - OK
[I 16:50:54.540 NotebookApp] Serving notebooks from local directory: /environment
[I 16:50:54.540 NotebookApp] Jupyter Notebook 6.4.10 is running at:
[I 16:50:54.540 NotebookApp] http://hostname:8888/
[I 16:50:54.540 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
```

Navigate to http://localhost:8888 to access the Jupyter notebooks and open the ```test-env.ipynb``` notebook. Running the first cell will give you an output as listed below.

```
Tensor Flow Version: 2.11.0
Keras Version: 2.11.0
GPU is available
```

If you see ```GPU is available``` - this means that your OS is correctly exposing the GPU to the docker container.

## Using docker-compose

Here is a docker-compose file example that you can use to spin up the new environment.

```yml
version: '3.0'
services:
  tensorflow:
    container_name: tensorflow-gpu
    image: thegeeksdiary/tensorflow-jupyter-gpu:latest
    restart: unless-stopped
    # uncomment the below to map the notebooks from your machine inside the docker container - please make sure to change the path applicable to you.
    # volumes:
    #   - ./notebooks:/environment/notebooks
    #   - ./data:/environment/data
    deploy:
      resources:
        reservations:
          devices:
          - driver: nvidia
            device_ids: ['0']
            capabilities: [gpu]
    ports:
      - '8888:8888'
    networks:
      - jupyter
networks:
  jupyter:
    driver: bridge
```
Create a new file ```docker-compose.yml``` and add the above code to it. next run the below commands to create your environment (from the same directory where you created the ```docker-compose.yml``` file).

```bash
docker-compose up
```
