# Assigment 1
By: Wilkinson John Chan <wilkinsonjohn.chan@uq.edu.au>

## Environmental Setup
This dockerfile is built to run inside the cca1 environment.
If you do not have the supporting files, this environment can be cloned using the following command:

```bash
git clone https://github.com/csenw/cca1.git && cd cca1
```

These build commands are intended to be run within the cca1 directory.

## To Build
To build this docker image, run the following docker shell command, in the project directory where the dockerfile is present.

```bash
docker build -t a1:Chan .
```

## To Run
```bash
docker run -p 80:80 -d -v src:/var/www/html --name cca1_nginx_php a1:Chan
```

## Credits
This readme.md is inspired by Sean Finn <sean.finn@student.uq.edu.au>. Thank you for the kind words in the dockerfile.
