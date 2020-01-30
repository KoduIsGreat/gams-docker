# GAMS 25.0.3 docker image
The [GAMS](https://www.gams.com/) model as a docker image.
* **This is not intended to be used for application development**
# Prerequisites 
1. Install [Docker](https://www.docker.com/products/docker-desktop) see [documentation](https://docs.docker.com/)
* **Note this will require to enable virtualization in your bios if you are on windows**


# Quick start
1. `git clone https://repoenv.rti.org/scm/watermd/gams-docker.git`
2. `cd  gams-docker`
3. extract model inputs into  gams-docker/sourceandstudies/
4. `docker-compose up -d`
5. `docker exec -ti rti-gams-25.0.3 bash`
6. inside container run `gams`

# Detailed start-up
Assuming the folder structure
```
 - C:\ 
     - Users
        - <Username>
            - Documents  <- current directory
```

A) clone the repository `git clone https://repoenv.rti.org/scm/watermd/gams-docker.git`

B) cd into cloned directory `cd  gams-docker`

C) Extract model input / files to a `sourceandstudies` directory located in the repository you just cloned. 

```
 - C:\ 
   - Users\
     - <Username>
       - Documents
         - gams-docker <- current directory
           - sourceandstudies <- extract here
```

D) run `docker-compose up`, this will start the container and listen on tty for input 
you should see something like what is below. Alternatively if you add the `-d` flag to this command it 
will allow you to run the container in the background while keeping it open so you dont have to run
step E in a different terminal.

``` 
adamshelton@RTI-102350 MINGW64 /c/Repositories/gams (master)
$ docker-compose up
Starting gams_gams_1 ... done
Attaching to gams_gams_1

```

E) now run `docker exec -ti rti-gams-25.0.3 bash`(in a different terminal if you did not do `-d`) this will launch the bash shell inside the running container
inside the working directory of the container which is /workspace, if you run `ls` you will notice all the contents of 
sourceandstudies have been copied to this directory.

F) you can now invoke gams as you would normally if you were not in a container