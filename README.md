# test_project
test_project
# -*- coding: utf-8 -*-
import paramiko
import commands
import os

flist=open('D:\ssh_client\update_list.txt')
fcontent=flist.readlines()

def backup_files(*flist):
    for file in list(flist[0]):
        CMD="[ -f %s ] && echo 0 || echo 1" % (file.strip('\n'))
        stdin, stdout, stderr = ssh.exec_command(CMD)   
        fname = file.split('/')
        print stdout.read()
        print fname[-1]
        #if (stdout.read() == 0):
        #    sftp.get(file,fname[-1])
        #else:
        #    print "file %s isnot exists" % (file)
        
def update_files(path,*flist):
    pass

def validate_file(old_fname,new_fname):
    pass


ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
try:
    ssh.connect('192.168.199.140',22,'wcl','wcl',timeout=5)
except:
    print 'error'
else:
    sftp = paramiko.SFTPClient.from_transport(ssh.get_transport())
    sftp = ssh.open_sftp()
    backup_files(fcontent)

