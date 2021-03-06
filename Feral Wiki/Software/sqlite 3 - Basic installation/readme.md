
In SSH do the commands described in this FAQ. If you do not know how to SSH into your slot use this FAQ: [SSH basics - Putty](https://www.feralhosting.com/faq/view?question=12)

Your FTP / SFTP / SSH login information can be found on the Slot Details page for the relevant slot.

Use this link in your Account Manager to access the relevant slot:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/0%20Generic/slot_detail_link.png)

You login information for the relevant slot will be shown here:

![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/0%20Generic/slot_detail_ssh.png)

Sqlite installation
---

A very basic guide to manual installation of sqlite 3.

~~~
mkdir -p ~/programs
[[][/[][ ! "$(grep '~/programs/bin' ~/.bashrc)" ]] && echo 'export PATH=~/programs/bin:$PATH' >> ~/.bashrc ; source ~/.bashrc
~~~

~~~
wget -qO ~/sqlite3.tar.gz http://www.sqlite.org/2013/sqlite-autoconf-3080002.tar.gz
tar xf ~/sqlite3.tar.gz && cd ~/sqlite-*/
./configure --prefix=$HOME/programs && make && make install
cd && rm -rf ~/sqlite-*/ ~/sqlite3.tar.gz
~~~

For some applications you will have to link to this location, for example:

~~~
env CPPFLAGS="-I$HOME/programs/include" LDFLAGS="-L$HOME/programs/lib" ./configure --prefix=$HOME/programs
~~~

### Just the Binary

~~~
wget -qO ~/sqlite.deb http://ftp.uk.debian.org/debian/pool/main/s/sqlite/sqlite_2.8.17-8_amd64.deb
dpkg-deb -x ~/sqlite.deb ~/sqlitetmp
cp -rf ~/sqlitetmp/usr/bin/. ~/programs/bin
~~~