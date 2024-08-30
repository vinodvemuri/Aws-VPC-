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

