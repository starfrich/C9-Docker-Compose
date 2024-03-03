# C9-Docker-Compose
Deploy C9-IDE Inside Docker Container

## Provisioning Your Linux VM

1. Update & Upgrade
```
apt update && apt upgrade -y
```
2. Install Docker
```
curl -fsSL https://get.docker.com | bash -s docker
```
3. Install Docker-Compose
```
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```
4. Clone Repository Ini ke dalam folder home /c9users/
```
$ sudo adduser c9users
$ git clone https://github.com/starfrich/C9-Docker-Compose.git /home/c9users/
```

How to use ?

```
$ sudo su #Login as root or privilege user
$ cd /home/c9users/
$ nano .env #Edit Port, Nama pelanggan setiap kali membuat ingin user baru
$ sudo docker-compose -p kamarudin up -d
```

### Explanation

> File .env
>
> There is 3 variables inside file .env :
> - PORT=
> - PASSWORD_PELANGGAN=
> - NAMA_PELANGGAN=
>
> **PORT=** is used to specify the port where the container will be exposed, so make sure change this variable everytime you crate new c9IDE
>
> **NAMA_PELANGGAN=** is used to set username login, and directory name which will to mount to docker container
>
> **PASSWORD_PELANGGAN=** is used to set password for authenticate to c9Core


**Note:**
>
> ```*sudo docker-compose -p kamarudin up -d*```
>> **sudo** use to call the priviledge user in this case is root user
>>
>> **docker-compose** to execute the docker-compose binary file
>>
>> **-p xxxx** use to specify the project name, this parameter will separated your client container to other project. So make sure you change this parameter to each your container IDE
>>
>> **up** to Create and start containers
>>
>> **-d** to Detached mode: Run containers in the background, print new container names

**Optional Variables:**
>
> There is 2 variables inside file .env :
> - **CPUS=**
> - **MEMORY=**
>
> **CPUS=** is used to specify how much limit CPU core will be used. If limit reached, container will be restart, and terminate all session. i.e. 0.5 is equals to 1/2 of 1 core cpu and 2 is equals of 2 core full of cpus.
>
> **MEMORY=** is used to specify how much limit ram will be used, limit ram is maximum load. If limit reached, container will be restart, and terminate all session.
