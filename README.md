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

