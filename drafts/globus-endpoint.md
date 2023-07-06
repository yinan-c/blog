# Setting up Globus endpoint for your servers

Yinan, June 2023

This instruction is for setting up a [Globus](https://app.globus.org/) endpoint for your servers. I have tested two clusters/supercomputers that I use. In principle, you should test it on your clusters.

> With Globus, you can easily, reliably and securely move, share, & discover data no matter where it lives – from a supercomputer, lab cluster, tape archive, public cloud or laptop. Access and manage all your data, even protected data, from anywhere, using your existing identities, with just a web browser.[](https://www.globus.org/what-we-do)

## 1. Login to the cluster with trusted X11 forwarding enabled:
`ssh -YC username@hostname`
 
## 2. Install Globus connect on the cluster. 
On servers that do not run GridFTP , you have to install the Globus Connect client software in your user space as:

```
wget https://downloads.globus.org/globus-connect-personal/linux/stable/globusconnectpersonal-latest.tgz
tar xzf globusconnectpersonal-latest.tgz
cd globusconnectpersonal-3.2.2/ 
```

## 3. Execute the globus client on cli mode as: 
`./globusconnectpersonal -setup --no-gui`
 
## 4. A login url will be displayed on terminal
Copy and paste it in your browser. Assuming that you already have a Globus account, login to your globus using the displayed url.
 
## 5. Provide a label for future reference 
An authorization code will be displayed in your browser. Copy it and paste it on the cluster next to the prompt `Enter the auth code:`. Then provide a name for this collection as "Input a value for the Endpoint Name:"
 
*If everything went well then you should get a message "setup completed successfully"*

## 6. ([source](https://github.com/Supercomputing/DailyTasks/wiki/Using-Globus-Online-from-the-command-line)) Access $SCRATCH etc.
Now you only have access to files in $home, in order to access files in other places like SCRATCH, add the following lines in  `~/.globusonline/lta/config-paths`

```
~/,0,1
/path/to/directory,0,1 
```

where `1` means read/write permitted.
From now on you can use the cluster to transfer data via Globus. Everytime you use Globus, you need to start the client on the cluster in order to activate it as an endpoint:
`./globusconnectpersonal -start`

Then you should be able to use your cluster account from the Globus web interface in your browser and browse the data from the collection name you provided in step 5.

Extra tip: If you want the program to run in the background without the session on, you can try using the `nohup ./globusconnectpersonal -start &` command. 

Your endpoint will be online on Globus as long as the process is running in the background without ssh-ing your server.

To kill the process:
`ps aux | grep globusconnectpersonal`
`kill -9 PID`

## Thanks
A collarborator of mine, IT support for Oxford clusters - Glamdring and Globus.
