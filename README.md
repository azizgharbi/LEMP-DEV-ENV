## Required 

### After configuring your Vm 

* [Steps to configure your vm with Lemp Stack + phpmyadmin ](config.md)

* Install Vagrant on your machine.



### Export your Vm: 

```
vagrant package --base [your machine name]
```
### Add the package.box to your Vagrant box:

```
vagrant box add package.box --name [choose a name]
```
### Check your Vargrant list box:

```
vagrant box list
```

### Create your vagrant file:

```
vagrant init [the choosen name ]
```

### Create your Env:

```
vagrant up
```
```
vagrant ssh
```
* Login : Your login  / password : Your password

If you want to preview on the web browser:

* Uncomment the ligne "config.vm.network" 

* You can also modify the ip adresse with any of your choice

```
vagrant reload
```

* Insert your Ip adresse in the Browser's adresse bar

### Commands that might help you :

```
vagrant -h 
```