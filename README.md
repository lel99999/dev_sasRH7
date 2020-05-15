# dev_sasRH7
SAS Deployment ON RHEL 7.X

for specific provisioning parts:<br/>
`$vagrant provision --provision-with main`<br/>
`$vagrant provision --provision-with update`<br/>

### Specific Notes for RHEL 7.x
Require the following packages for depencies:<br/>
`$sudo yum install compat-glibc libpng12`<br/> 

### Resource Limit of Open file Descriptors below recommended value of 20480
Check the hard limit with `$ulimit -n`<br/>
Set by     `$sudo ulimit -n 20480`<br/>

To set permanently:<br/>
`$sudo vi /etc/sysctl.conf`<br/>
Add the following line:<br/>
`fs.file-max=500000`<br/>
To apply the limit immediately:<br/>
`$sudo sysctl -p`<br/>
To check:
`$sudo cat /proc/sys/fs/file-max`<br/>

### Modify Hard/Soft Limits on Number of Processes (nproc) and Open Files (nofile)
Check with `$sudo vi /etc/security/limits.conf`<br/>
Change from:<br/>
`*          soft    nproc     1024`<br/>
`*          hard    nproc     1024`<br/>

Change to:<br/>
`*          soft    nproc     20480`<br/>
`*          soft    nofile    20480`<br/>
`*          hard    nproc     20480`<br/>
`*          hard    nofile    20480`<br/>

Edit the /etc/pam.d/lgoin by adding the line:
`session required /lib/security/pom_lmits.so`<br/>

## SASStudio
Login page:<br/>
**http://hostname:port/SASStudio**

### SSL Issues: Errors when trying to enable SSL while using SAS/ACCESS Interface
[SAS SSL errors using SAS/ACCESS Interface Link](https://support.sas.com/kb/54/175.html)
<br/>
[Download PostgreSQL Drivers for SSL](http://ftp.sas.com/techsup/download/hotfix/psqlodbc.html)
