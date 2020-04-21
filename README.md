# dev_sasRH7
SAS Deployment ON RHEL 7.X

for specific provisioning parts:
`$vagrant provision --provision-with main`<br/>
`$vagrant provision --provision-with update`<br/>

### Specific Notes for RHEL 7.x
Require the following packages for depencies:<br/>
`$sudo yum install compat-glibc libpng12`<br/> 

### Resource Limit of Open file Descriptors below recommended value of 20480
`$sudo vi /etc/sysctl.conf`<br/>
Add the following line:<br/>
`fs.file-max=500000`<br/>
To apply the limit immediately:<br/>
`$sudo sysctl -p`<br/>
To check:
`$sudo cat /proc/sys/fs/file-max`<br/>
