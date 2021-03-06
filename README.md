# Ex1: Build your own docker container and push it to the cloud.

Good you found this git repo!

**_IMPORTANT:_** Make sure to always replace YOUR_NAME with a lowercase name and use this name consistently. 
If there are people with the same name in this group, please use your nicknames to avoid confusion.

**_MOST IMPORTANT:_** please ask questions whenever you want.
 
## Choose your language

In this project you can find some basic examples for different programming languages. Have a quick look on all the different dockerfiles and source code in these folders.
Needless to say that this list of languages can be expanded. 

## google cloud
To build this docker images, I created a bunch of fake google account to log in to the google cloud console.
Please follow these steps:

1) Go to the google cloud console: https://console.cloud.google.com/ .

   **_NOTE:_**  If you use the chrome browser you should use an incognito window.

2) Login with the provided credentials.
3) Use the navigation menu to navigate to the Kubenetes engine
4) Connect to the cluster in a new terminal by pushing `connect` button
5) Create a folder with your own name:

 ```
 mkdir YOUR_NAME
 ```
6) Change directory to that folder.
 ```
 cd YOUR_NAME
 ```

From this terminal we can execute all pre-installed commands for the next exercises.

## Instructions
### Checkout Git repo
To use our code on the virtual machine, we need to clone this git repo.

1) Clone the git repo
 ```
 git clone https://github.com/WilmsJochen/ex1.git
 ```
2) Change your directory to the repo
 ```
 cd ex1
 ```
3) Have a look in all the folders and files.
 Verify all the directories and files corresponds to this git repo.
  ```
 ls
  ```

### Build your first docker image
In this step we are going to build a docker image and push it to a docker repo. We will start with the server code as we will deploy this to kubernetes in the next exercises. If you have time left at the end of the session you can come back to this exercise and build the job code as well.

1) Choose the programming language you are the most familiar with.
 ```
 cd go/server
 ```

2) Modify the message that the server will return to a funny message.
 ```
 nano main.py
 nano main.go 
 nano index.js
 ```
**_NOTE:_**  To exit nano, press crtl+x -> press y (yes) -> press enter to save it in the same file.

2) Build your docker image and name the image to your own name.
 ```
 docker build . --tag YOUR_NAME
 ```

3) Check your docker images.
 ```
 docker images
 ```

4) Tag your image to give it a proper version number
 ```
 docker tag YOUR_NAME YOUR_NAME:V1.0
 ```

5) Check your tagged image.
 ```
 docker images
 ```
6) Tag your image again with the docker registry as prefix. 
This is needed to push your locally created docker image to our docker registry on google cloud where everyone that has access to the project can access it.
 ```
 docker tag YOUR_NAME:V1.0 eu.gcr.io/kubernetestalk-295018/YOUR_NAME:V1.0
 ```

7) Push this tagged image to the docker registry.
 ```
 docker push eu.gcr.io/kubernetestalk-295018/YOUR_NAME:V1.0
 ```

Congratulations! You've managed to create your first docker image and make it accessible in a docker registry. 

**Note** There are many docker registries that you can use. We are using the private Google Cloud registries for this exercise, but if you want to make your container open to the world something like [docker hub](https://hub.docker.com/) might be more suitable.

 
## Tips

This link can be used if you can't access our kubernetes cluster on google cloud. But be aware that you will miss some functionality on this platform. 
https://www.katacoda.com/courses/kubernetes/playground
