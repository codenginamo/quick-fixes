Install PM2
Now we will install PM2, which is a process manager for Node.js applications. PM2 provides an easy way to manage and daemonize applications (run them as a service).

We will use Node Packaged Modules (NPM), which is basically a package manager for Node modules that installs with Node.js, to install PM2 on our app server. Use this command to install PM2:

`sudo npm install pm2@latest -g`

### Manage Application with PM2

PM2 is simple and easy to use. We will cover a few basic uses of PM2.

Start Application
The first thing you will want to do is use the pm2 start command to run your application, hello.js, in the background:

`pm2 start hello.js`
This also adds your application to PM2's process list, which is outputted every time you start an application:

Output:

```
┌──────────┬────┬──────┬───────┬────────┬─────────┬────────┬─────────────┬──────────┐
│ App name │ id │ mode │ pid   │ status │ restart │ uptime │ memory      │ watching │
├──────────┼────┼──────┼───────┼────────┼─────────┼────────┼─────────────┼──────────┤
│ hello    │ 0  │ fork │ 30099 │ online │ 0       │ 0s     │ 14.227 MB   │ disabled │
└──────────┴────┴──────┴───────┴────────┴─────────┴────────┴─────────────┴──────────┘
```

As you can see, PM2 automatically assigns an App name (based on the filename, without the .js extension) and a PM2 id. PM2 also maintains other information, such as the PID of the process, its current status, and memory usage.

Applications that are running under PM2 will be restarted automatically if the application crashes or is killed, but an additional step needs to be taken to get the application to launch on system startup (boot or reboot). Luckily, PM2 provides an easy way to do this, the startup subcommand.

The startup subcommand generates and configures a startup script to launch PM2 and its managed processes on server boots. You must also specify the init system you are running on, which is systemd, in our case:

sudo pm2 startup systemd
You should see output like the following, which indicates that the pm2 service has been installed.

Output:
```
[PM2] Generating system init script in /etc/systemd/system/pm2.service
[PM2] Making script booting at startup...
[PM2] -systemd- Using the command:
      su root -c "pm2 dump && pm2 kill" && su root -c "systemctl daemon-reload && systemctl enable pm2 && systemctl start pm2"
[PM2] Dumping processes
[PM2] Stopping PM2...
[PM2] All processes have been stopped and deleted
[PM2] PM2 stopped
[PM2] Done.
```

Now your pm2-managed applications should start automatically on boot.

Other PM2 Usage (Optional)
PM2 provides many subcommands that allow you to manage or look up information about your applications. Note that running pm2 without any arguments will display a help page, including example usage, that covers PM2 usage in more detail than this section of the tutorial.

Stop an application with this command (specify the PM2 App name or id):

`pm2 stop example`
Restart an application with this command (specify the PM2 App name or id):

`pm2 restart example`
The list of applications currently managed by PM2 can also be looked up with the list subcommand:

`pm2 list`
More information about a specific application can be found by using the info subcommand (specify the PM2 App name or id)::

`pm2 info example`
The PM2 process monitor can be pulled up with the monit subcommand. This displays the application status, CPU, and memory usage:

`pm2 monit`
Now that your Node.js application is running, and managed by PM2, let's set up the reverse proxy.

