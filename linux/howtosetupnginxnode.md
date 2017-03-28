1. `sudo yum install git`
2. `wget https://nodejs.org/dist/v6.10.1/node-v6.10.1-linux-x64.tar.xz`
3. `mkdir temp && cd temp && mv ../node*.*z $PWD`
4. `tar xf node-v6.10.1-linux-x64.tar.xz`
5. `cd ~ && mkdir ~/node` 
6. `tar xvf node-v*.tar.gz --strip-components=1 -C ./node`
7. `mkdir ~/node/etc`
8. `echo 'prefix=/usr/local' > node/etc/npmrc`
9. `sudo mv node /opt/`
10. `sudo chown -R root: /opt/node`
11. `sudo ln -s /opt/node/bin/node /usr/local/bin/node`
12. `sudo ln -s /opt/node/bin/npm /usr/local/bin/npm`
13. `sudo visudo`
14. Find line and change to: `Defaults    secure_path = /sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin`
15. Install pm2 and then setup nginx reverse proxy

