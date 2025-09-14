#Assigment 2
By: Wilkinson John Chan s4727761 <wilkinsonjohn.chan@uq.edu.au>

#Operating instructions
This zip file contains two files
 readme.md (this file)
 dockerfile
docker-compose.yml

## Environmental Setup
This dockerfile and docker-compose.yml is built to run inside the cca2 environment.
If you do not have the supporting files, this environment can be cloned using the following command:

```bash
git clone https://github.com/csenw/cca2.git
```


## Where the files should be placed
The dockerfile should be located under cca2/src/php, and the dockerfile-compose.yml should be placed under cca2 folder, in order for the containers to run correctly.

```bash
mv dockerfile cca2/src/php && mv docker-composer.yml cca2
```

##To Run
Execute the following command to run all the containers.
```bash
docker-compose up -d
```



These build commands are intended to be run within the cca2 directory.

