# dev_sasRH7
SAS Deployment ON RHEL 7.X

for specific provisioning parts:<br/>
`$vagrant provision --provision-with main`<br/>
`$vagrant provision --provision-with update`<br/>

### Specific Notes for RHEL 7.x
Require the following packages for depencies:<br/>
`$sudo yum install compat-glibc libpng12`<br/> 

### Resource Limit of Open file Descriptors below recommended value of 20480
Check with `$ulimit -n`<br/>
Set by     `$sudo ulimit -n 20480`<br/>

To set permanently:<br/>
`$sudo vi /etc/sysctl.conf`<br/>
Add the following line:<br/>
`fs.file-max=500000`<br/>
To apply the limit immediately:<br/>
`$sudo sysctl -p`<br/>
To check:
`$sudo cat /proc/sys/fs/file-max`<br/>

### Modify Hard/Soft Limits on Number of Processes
Check with `$sudo vi /etc/security/limits.conf`<br/>
Change from:<br/>
`*          soft    nproc     1024`<br/>
`*          hard    nproc     1024`<br/>

Change to:<br/>
`*          soft    nproc     20480`<br/>
`*          hard    nproc     20480`<br/>

## SASStudio
Login page:<br/>
**http://hostname:port/SASStudio**
