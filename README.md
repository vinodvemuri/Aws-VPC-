HOW TO CREATE VPC :Virtual Private Cloud
-
How To Separate Public Server  And Private Server Is Using To Route tables.
Availability Zones Are Public Subnet And Private Subnet.Routes tables only will allows the any trafic.
 (like: Internet,NAT)
VPC Creation Process :
stp1: Go to Your VPCs
stp2: After Create Vpc

stp3: Vpc Settinges
      . Resources to create
  .vpc only              . vpc and more
step4: Name tag-optional
         VpcA -> write this
stp5: Ipv4 CIDR block
  .Ipv4 CIDR manual input
  .IPAM -allocate ipv4 CIDR block
IPV4 CIDR
   244.0.0.0/25 -> write this
   NOTE: CIDR block size must be b/w/16 and/28
          MAX is 16 MIN is 28
step6: Create vpc click After vpc was created succssfully

step7: Go to Route table ( it shows default routetable only for chekbased)
step8: Go to Create a Network Acls (chek based)
step9: After go to the Subnet services (Create sbunet)
  .VPC
  VPC ID
  Create Subnet in this pc
    Vpc-0750ea5ed6ddc355(vpca) -> write this one
                                                        (Create) #Click
step10: Go to the sunet 1 OF 1 -> In settings
        Subnet Name
        PUblicsubnet  -> write
     . Availablity Zone:
        us East(n.virginia)/us-east-1a    ->write
     . IPV4 subnet CIDR block
         244.0.0.0/27      -> write
                                                      (create)
stp11: And also one more create  a Private subnet
       Here Change the IPV4 subnet CIDR block
           244.0.0.32/27
                                                      (create)
 stp12: Go to the internet gatways create one
           wtite the Name Tag
           internet   -> write
                                                     (create internet gatway)
 stp13: We Need to Attach to  a VPC  
          After to vpc
          vpc
          Avilable Vpcs
          Vpc--------   -> write and fill some thing
                                                    (Attach internet gate way)
    NOTE: We need to Attach to the route tables then only it will allows
 step14:  After go to the Route tables
            . Select one Route table 
            . After go the Routes
            . Edit routes
            . And add the route botam one click
            . go to target write the INTERNET GATEWAY and come down Write the some thing
                                                                       (Save the changes)
  step15: One more create Route Table
  Step16: After Creation process done Go to the route tables
       1> Selecte one route table
       2> go to the subnet associations
                                              (Edit Subnet Associations)
      3> Edit the subnet Associations check
      4> And Available Subnets 
          public --> Select this one
          private
                                                   (Save association)
   step17: Same Process do the Private also in the Route tables.
   step18: Go to the instances After lunch instances private and public.
             1> Public server lunch process Subnet was PUblic subnet And Auto Assign public IP was Enable write.
             2> private server lunch process subnet was Private subnet And Auto Assign Private IP was Disable write.
                                                            (Launch instances)
step19: Select one Instance And Connet to the server
           1> After connect to the public srver we can directly able to the acess 
               Using Some Comands:
               -> sudo su -
               ll
              -> yum install git -y
             ->> After using those all comands was connect the private server in the process of public get the out put
                 -> vi keypairc15.pem
                 -> :wq! (this used for saved purpose)
                 -> Chmod 400 "keypair15.pem"
                 -> Shh-i "keypair 15.pem"ecl user@244.0.0.55
                 -> yes
               
           2> But private server was not like that we go to the SSH process in private server.
              Some Of The Steps In How To Connect Private server:
                   1> So We go to the SSH Client
                   2> And copy the "Keypair ----"
                   3> When Keypair save the Note pad one copy and paste the Running of the process in public using some of the commmands.
                   4>We need used the Chmod 400 "keypair15.pem"
                   5> Shh-i "keypair 15.pem"ecl user@244.0.0.55
 step20: Go to VPcs for the provide the internet in the private server
                                                 (create NAT Gateway)
           1> NAT Gatway
             Name: NAT Gateway
             subnet:public subnet (click one)
             Elastic ip allocation :  ----          ( Allocate Elastic)#click
                                                                                (crate NAT Gateway)
  step21:  After go to the route tables 
            Select one 
                      After Go to the Routes                            (Edit Routes)
              Edit routes 
                                     NAT Gatway ( write)
                                     ---------(fill this and write)


              (ADD rule) #click
                                                                            (save the cahnges)

use for comandas public server to private server connect process:
Last login: Fri Aug 30 12:57:44 2024 from 13.48.4.202
[ec2-user@ip-244-0-0-7 ~]$ sudo su -
Last login: Fri Aug 30 13:01:38 UTC 2024 on pts/2
[root@ip-244-0-0-7 ~]# ll
total 0
[root@ip-244-0-0-7 ~]# yum install git -y
Last metadata expiration check: 0:07:12 ago on Fri Aug 30 12:56:51 2024.
Package git-2.40.1-1.amzn2023.0.3.x86_64 is already installed.
Dependencies resolved.
Nothing to do.
Complete!
[root@ip-244-0-0-7 ~]# vi vinod.pem
[root@ip-244-0-0-7 ~]# chmod 400 "vinod.pem"
[root@ip-244-0-0-7 ~]# ssh -i "vinod.pem" ec2-user@244.0.0.45
The authenticity of host '244.0.0.45 (244.0.0.45)' can't be established.
ED25519 key fingerprint is SHA256:AJPKpavev4LYYvXo3bwZYy0YusB8EIZeFTN7sdMpIOI.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '244.0.0.45' (ED25519) to the list of known hosts.
   ,     #_
   ~\_  ####_        Amazon Linux 2023
  ~~  \_#####\
  ~~     \###|
  ~~       \#/ ___   https://aws.amazon.com/linux/amazon-linux-2023
   ~~       V~' '->
    ~~~         /
      ~~._.   _/
         _/ _/
       _/m/'
[ec2-user@ip-244-0-0-45 ~]$ sudo su -
[root@ip-244-0-0-45 ~]# yum install nginx
Amazon Linux 2023 repository                                                                                                      103 kB/s |  27 MB     04:30    
Amazon Linux 2023 Kernel Livepatch repository                                                                                      57 kB/s |  11 kB     00:00    
Dependencies resolved.
==================================================================================================================================================================
 Package                                    Architecture                  Version                                        Repository                          Size
==================================================================================================================================================================
Installing:
 nginx                                      x86_64                        1:1.24.0-1.amzn2023.0.2                        amazonlinux                         32 k
Installing dependencies:
 generic-logos-httpd                        noarch                        18.0.0-12.amzn2023.0.3                         amazonlinux                         19 k
 gperftools-libs                            x86_64                        2.9.1-1.amzn2023.0.3                           amazonlinux                        308 k
 libunwind                                  x86_64                        1.4.0-5.amzn2023.0.2                           amazonlinux                         66 k
 nginx-core                                 x86_64                        1:1.24.0-1.amzn2023.0.2                        amazonlinux                        586 k
 nginx-filesystem                           noarch                        1:1.24.0-1.amzn2023.0.2                        amazonlinux                        9.1 k
 nginx-mimetypes                            noarch                        2.1.49-3.amzn2023.0.3                          amazonlinux                         21 k

Transaction Summary
==================================================================================================================================================================
Install  7 Packages

Total download size: 1.0 M
Installed size: 3.4 M
Is this ok [y/N]: yes
Downloading Packages:
(1/7): generic-logos-httpd-18.0.0-12.amzn2023.0.3.noarch.rpm                                                                      311 kB/s |  19 kB     00:00    
(2/7): libunwind-1.4.0-5.amzn2023.0.2.x86_64.rpm                                                                                  981 kB/s |  66 kB     00:00    
(3/7): nginx-1.24.0-1.amzn2023.0.2.x86_64.rpm                                                                                     1.6 MB/s |  32 kB     00:00    
(4/7): gperftools-libs-2.9.1-1.amzn2023.0.3.x86_64.rpm                                                                            3.4 MB/s | 308 kB     00:00    
(5/7): nginx-core-1.24.0-1.amzn2023.0.2.x86_64.rpm                                                                                 17 MB/s | 586 kB     00:00    
(6/7): nginx-filesystem-1.24.0-1.amzn2023.0.2.noarch.rpm                                                                          424 kB/s | 9.1 kB     00:00    
(7/7): nginx-mimetypes-2.1.49-3.amzn2023.0.3.noarch.rpm                                                                           930 kB/s |  21 kB     00:00    
------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                             4.6 MB/s | 1.0 MB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                          1/1 
  Running scriptlet: nginx-filesystem-1:1.24.0-1.amzn2023.0.2.noarch                                                                                          1/7 
  Installing       : nginx-filesystem-1:1.24.0-1.amzn2023.0.2.noarch                                                                                          1/7 
  Installing       : nginx-mimetypes-2.1.49-3.amzn2023.0.3.noarch                                                                                             2/7 
  Installing       : libunwind-1.4.0-5.amzn2023.0.2.x86_64                                                                                                    3/7 
  Installing       : gperftools-libs-2.9.1-1.amzn2023.0.3.x86_64                                                                                              4/7 
  Installing       : nginx-core-1:1.24.0-1.amzn2023.0.2.x86_64                                                                                                5/7 
  Installing       : generic-logos-httpd-18.0.0-12.amzn2023.0.3.noarch                                                                                        6/7 
  Installing       : nginx-1:1.24.0-1.amzn2023.0.2.x86_64                                                                                                     7/7 
  Running scriptlet: nginx-1:1.24.0-1.amzn2023.0.2.x86_64                                                                                                     7/7 
  Verifying        : generic-logos-httpd-18.0.0-12.amzn2023.0.3.noarch                                                                                        1/7 
  Verifying        : gperftools-libs-2.9.1-1.amzn2023.0.3.x86_64                                                                                              2/7 
  Verifying        : libunwind-1.4.0-5.amzn2023.0.2.x86_64                                                                                                    3/7 
  Verifying        : nginx-1:1.24.0-1.amzn2023.0.2.x86_64                                                                                                     4/7 
  Verifying        : nginx-core-1:1.24.0-1.amzn2023.0.2.x86_64                                                                                                5/7 
  Verifying        : nginx-filesystem-1:1.24.0-1.amzn2023.0.2.noarch                                                                                          6/7 
  Verifying        : nginx-mimetypes-2.1.49-3.amzn2023.0.3.noarch                                                                                             7/7 

Installed:
  generic-logos-httpd-18.0.0-12.amzn2023.0.3.noarch       gperftools-libs-2.9.1-1.amzn2023.0.3.x86_64       libunwind-1.4.0-5.amzn2023.0.2.x86_64                
  nginx-1:1.24.0-1.amzn2023.0.2.x86_64                    nginx-core-1:1.24.0-1.amzn2023.0.2.x86_64         nginx-filesystem-1:1.24.0-1.amzn2023.0.2.noarch      
  nginx-mimetypes-2.1.49-3.amzn2023.0.3.noarch           

Complete!
[root@ip-244-0-0-45 ~]# yum install git
Last metadata expiration check: 0:04:02 ago on Fri Aug 30 13:24:06 2024.
Dependencies resolved.
==================================================================================================================================================================
 Package                                 Architecture                  Version                                           Repository                          Size
==================================================================================================================================================================
Installing:
 git                                     x86_64                        2.40.1-1.amzn2023.0.3                             amazonlinux                         54 k
Installing dependencies:
 git-core                                x86_64                        2.40.1-1.amzn2023.0.3                             amazonlinux                        4.3 M
 git-core-doc                            noarch                        2.40.1-1.amzn2023.0.3                             amazonlinux                        2.6 M
 perl-Error                              noarch                        1:0.17029-5.amzn2023.0.2                          amazonlinux                         41 k
 perl-File-Find                          noarch                        1.37-477.amzn2023.0.6                             amazonlinux                         26 k
 perl-Git                                noarch                        2.40.1-1.amzn2023.0.3                             amazonlinux                         42 k
 perl-TermReadKey                        x86_64                        2.38-9.amzn2023.0.2                               amazonlinux                         36 k
 perl-lib                                x86_64                        0.65-477.amzn2023.0.6                             amazonlinux                         15 k

Transaction Summary
==================================================================================================================================================================
Install  8 Packages

Total download size: 7.1 M
Installed size: 34 M
Is this ok [y/N]: yes
Downloading Packages:
(1/8): git-2.40.1-1.amzn2023.0.3.x86_64.rpm                                                                                       678 kB/s |  54 kB     00:00    
(2/8): git-core-doc-2.40.1-1.amzn2023.0.3.noarch.rpm                                                                               21 MB/s | 2.6 MB     00:00    
(3/8): perl-Error-0.17029-5.amzn2023.0.2.noarch.rpm                                                                               863 kB/s |  41 kB     00:00    
(4/8): perl-File-Find-1.37-477.amzn2023.0.6.noarch.rpm                                                                            1.4 MB/s |  26 kB     00:00    
(5/8): perl-TermReadKey-2.38-9.amzn2023.0.2.x86_64.rpm                                                                            1.8 MB/s |  36 kB     00:00    
(6/8): perl-Git-2.40.1-1.amzn2023.0.3.noarch.rpm                                                                                  1.0 MB/s |  42 kB     00:00    
(7/8): perl-lib-0.65-477.amzn2023.0.6.x86_64.rpm                                                                                  759 kB/s |  15 kB     00:00    
(8/8): git-core-2.40.1-1.amzn2023.0.3.x86_64.rpm                                                                                   16 MB/s | 4.3 MB     00:00    
------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                              23 MB/s | 7.1 MB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                          1/1 
  Installing       : git-core-2.40.1-1.amzn2023.0.3.x86_64                                                                                                    1/8 
  Installing       : git-core-doc-2.40.1-1.amzn2023.0.3.noarch                                                                                                2/8 
  Installing       : perl-lib-0.65-477.amzn2023.0.6.x86_64                                                                                                    3/8 
  Installing       : perl-TermReadKey-2.38-9.amzn2023.0.2.x86_64                                                                                              4/8 
  Installing       : perl-File-Find-1.37-477.amzn2023.0.6.noarch                                                                                              5/8 
  Installing       : perl-Error-1:0.17029-5.amzn2023.0.2.noarch                                                                                               6/8 
  Installing       : perl-Git-2.40.1-1.amzn2023.0.3.noarch                                                                                                    7/8 
  Installing       : git-2.40.1-1.amzn2023.0.3.x86_64                                                                                                         8/8 
  Running scriptlet: git-2.40.1-1.amzn2023.0.3.x86_64                                                                                                         8/8 
  Verifying        : git-2.40.1-1.amzn2023.0.3.x86_64                                                                                                         1/8 
  Verifying        : git-core-2.40.1-1.amzn2023.0.3.x86_64                                                                                                    2/8 
  Verifying        : git-core-doc-2.40.1-1.amzn2023.0.3.noarch                                                                                                3/8 
  Verifying        : perl-Error-1:0.17029-5.amzn2023.0.2.noarch                                                                                               4/8 
  Verifying        : perl-File-Find-1.37-477.amzn2023.0.6.noarch                                                                                              5/8 
  Verifying        : perl-Git-2.40.1-1.amzn2023.0.3.noarch                                                                                                    6/8 
  Verifying        : perl-TermReadKey-2.38-9.amzn2023.0.2.x86_64                                                                                              7/8 
  Verifying        : perl-lib-0.65-477.amzn2023.0.6.x86_64                                                                                                    8/8 

Installed:
  git-2.40.1-1.amzn2023.0.3.x86_64                      git-core-2.40.1-1.amzn2023.0.3.x86_64                 git-core-doc-2.40.1-1.amzn2023.0.3.noarch          
  perl-Error-1:0.17029-5.amzn2023.0.2.noarch            perl-File-Find-1.37-477.amzn2023.0.6.noarch           perl-Git-2.40.1-1.amzn2023.0.3.noarch              
  perl-TermReadKey-2.38-9.amzn2023.0.2.x86_64           perl-lib-0.65-477.amzn2023.0.6.x86_64                

Complete!
