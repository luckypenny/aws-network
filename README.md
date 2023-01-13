# aws-network
Private IP
- 10.0.0.0 ~ 10.255.255.255 ( 10.0.0.0/8 ) <= in big networks
- 172.16.0.0 ~ 172.31.255.255 ( 172.16.0.0/12 ) <= default VPC included in this range
- 192.168.0.0 ~ 192.168.0.0 ( 192.168.0.0/16 ) <= example: home networks

- as of now : 지금으로서는 
- comes by : 구하다 
- main route table -> VPC level, which cannot delete.

- Total Number of host addresses (IPs) in given. Network = 2^(32-Prefix) = 2^(32-16) = 2 ^ 16 = 65536

# Subnet - IPv4
- AWS reservers 5 IPs address (first 4 and last 1 IP Address) in each subnet
- These 5 IPs are not available for use and cannot be assigned to an instance
- Ex, if CIDR block 10.0.0.0/24, reserved IP are: 
  - 10.0.0.0 : Network address
  - 10.0.0.1 : Reserved by AWS for the VPC router
  - 10.0.0.2 : Reserved by AWS for mapping to Amazon-provided DNS
  - 10.0.0.3 : Reserved by AWS for future use
  - 10.0.0.255 : Network broadcast address. AWS does not support broadcast in a VPC, therefore the address is reserved.
- Exam Tip:
  - if you need 29 IP addresses for EC2 instances, you can't choose a Subnet of size /27 (32 IP)
  - You need as least 64 IP, Subnet size /26 (64-5 = 59 > 29, but 32-5 = 27 < 29)
  
 # IP Addresses b=in VPC
 - EC2 Stop than Public IP는 사라집니다. 이를 방지 하기 위해서 EIP를 사용합니다.
 # IPv6 Addresses
 - AWS VPC also supports IPv6 addresses
 - IPv6 address is 128 bits in size with 8 blocks of 16 bits each
  - Example : 2020:1ed3:1d35:0000:0000:3d3d:0303:3939
 - IPv6 addresses are public and globally unique, and allows resources to communicate with the internet
 - VPC can operate in dual-stack mode where VPC resources can communitate over IPv4, or IPv6, or Both ( 두 주소 다 갖을 수 있다. ) 
 - IPv6 address persists when you stop and start your instance, and is released when you terminate your instance


- IPv4 : default and required for all VPCs; cannot be removed. The VPC/Subnet CIDR block size can be from /16 to 28
- IPv6 : Opt-in only; The VPC CIDR block size is fixed at /56. Subnet block is fixed at /64

### ENI
- Logical component in a VPC that represents a virtual network card
- The ENI can have the following attributes:
  - 보안 그룹을 갖을 수 있다.
  - IPv4 one or more secondary IPv4
  - One Elatic IP (IPv4) per private IPv4
  - One Public IPv4
  - One or more security groups
  - A MAC Address
  
  
### Default VPC를 삭제 하면 다시 만들 수 있다.

