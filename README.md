## Required 

* After configuring your Vm 

[Steps to configuring your vm with Lemp Stack + phpmyadmin ](config.md)

Install Vagrant on your machine :



### Export your Vm : :

```
vagrant package --base [your machine name]
```
### Add the package.box to your Vagrant box :

```
vagrant box add package.box --name [choose a name]
```
### Check your Vargrant list box :

```
vagrant box list
```
### Create your vagrant file :

```
vagrant init [the choosen name ]
```

### Create your Env:

```
vagrant up
```
```
vagrant shh
```
* Login : Ur login  / password : your password

* Look at config.vm.network and uncomment the ligne , you can also modify the ip adresse with what you want .

```
vagrant reload
```

* Browse Url : The Ip adresse .