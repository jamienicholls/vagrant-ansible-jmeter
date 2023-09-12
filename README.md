# vagrant-ansible-jmeter
This box will bring up a working jmeter server. 

### Requirements
- Git
- Vagrant

### To bring up
```
git clone <repo> 
cd vagrant-ansible-jmeter
vagrant up
```

### Usage
In the "projects" folder create a folder and add your ".jmx" file. You can create a new jmeter project by downloading jmeter from [here](https://jmeter.apache.org/download_jmeter.cgi). Save the project into your project folder you created in the projects path.

Connect to the server
```
vagrant ssh 
```
Run the project
```
cd <my-project>
jmeter -n -t <my-project>.jmx -l log.jtl
```
To run the example
```
cd example
jmeter -n -t example-one.jmx -l log.jtl
```