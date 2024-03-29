# Git

## basic
git clone a // bring down repository from github

$git status

$git add .

$git commit -m "some text"

$git push // send your changes to github

$git pull // get updates from github

$git checkout -b // create branch and switch to it

$git checkout b // switch to branch b

$git branch // list branches

$ gith branch -D b // delete branch b

$ git log // shows commits

# github branches

// If github has a branch test and you want to bring it down localy

$git fetch origin // update local repo

$git switch -c test origin/test // get the github branch (look in github for the branch name)

// Now you can push/pull normally

// Delete the branch in github and then locally

$git push --set-upstream origin b // push local branch b to github

// Only need to do this once, then your can use normal $git push and $git pull

# Merge

$git checkout a // checkout branch a. This is where you want to merge you code into

$git merge b // this will merge branch b into branch a

$git merge --abort // abort merge

// fix merge conflicts

$ git status // files that have merge conflics

$ git add b.cpp

$ git commit -m "fixed merge conflict"

// rebase is an alternative

# rolling back code

// revert rolls code back by adding a commit (keeps history) safer

// rest re-writes history so it disapears

$ git reset --hard sha

// where sha is found via $git log and is the commit you want to go back to

ex.

123 commit 1

|

456 commit 2

|

789 commit 3

then git rest --hard 456 will take you to the state you were in for "456 commit 2"

# Docker

// For windows containers you need to run the folowing in PS
$ Enable-WindowsOptionalFeature -Online -FeatureName $("Microsoft-Hyper-V", "Containers") -All

$docker -v // run at command prompt

$ docker run hello-world // hello world container

.dockerignore // like .gitignore

// FROM // specify base image

// WORKDIR /app // specify directy you start at when you enter the container (e.x. ~)

// COPY . . // Copy from to (local to container)

// ENV foo=1 // Enviornment variable foo = 1

// EXPOSE 3000 // Expose port 3000 for webapp

// RUN npn i // Run a command at docker build time

// CMD npm start // Run a command in docker (after it's built)

Dockerfile // specify command to create the image

// This will build the image you defined by the Dockerfile

$docker build -t some_name . // cd to where the Dockerfile is OR $docker image build -t some_name

$ docker image pull foo:bar // build the image e.g. like the FROM part in the Dockerfile

// shows you images you have built e.g. some_name

$docker image ls

$docker image rm -f image_name

## docker run
// run the image that you just built

$docker run -it same_name

// run the image that you just built and go to the shell

$docker run -it same_name sh

// run the image that you just built and expose the docker port 3000 to your local machine port 10 e.x. localhost:10

$docker run -p 10:3000 same_name // run the container

// run in detached mode

$docker run -d same_name

$docker run -rm // remove the container after it's stopped

$docker --name container_name image_name

// show running containers

$docker ps OR $docker container ls

// show stopped and running containers

docker ps -a

$docker exec -it the_NAMES_from_docker_ps sh // start a shell session on the detached docker image

// stop a container. The 123 is the CONTAINER ID from docker ps. You can also type $exit in the docker container or CTRL + C

$docker stop 123 or docker container stop 123

// start the container

$docker start 123 OR $docker start -i 123 // to start in interactive mode (yes it's just -i) or docker container start 123

// remove a container

$docker rm 123 or $docker container rm 123

## Volumes
Volumes presist data

// create a docker volume app-data

$docker volume create app-data

// list current volumes

$docker volume ls

// remove docker volume app-data
$docker volume rm app-data

// run the docker container and map the volume app-data to the docker folder /app/data (absolute path)
$docker run -d -p 10:3000 -v app-data:/app/data some_name

// user absolute paths

// share data between host and docker and it presits

docker run -it -v path_on_host:path_on_container

## Copy file Docker-> Host and Host->Docker NOTE these commands are issues on the host

//copy file.txt on the CONTAINER ID 123 to your local host "." (current directory)

$docker cp 123:app/data/file.txt .

//copy local file foo.txt to CONTAINER 123 and into the docker folder app/data

$docker cp foo.txt 123:app/data/

