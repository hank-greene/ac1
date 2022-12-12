# ac1
Create an AWS VPC using CLI.

## last step to configure git
https://gist.github.com/developius/c81f021eb5c5916013dc
git remote set-url origin git@github.com:username/your-repository.git


https://brad-simonin.medium.com/create-an-aws-vpc-and-subnet-using-the-aws-cli-and-bash-a92af4d2e54b


  1. adds a new VPC
  2. names the VPC
  3. adds dns support
  4. adds a dns hostname
  5. creates an internet gateway
  6. names the internet gateway
  7. creates the subnet
  8. names the subnet
  9. enables public ip on the subnet
 10. creates the security group for the subnet
 11. names the security group
 12. enables port 22 for ssh
 13. creates the route table
 14. names the route table
 15. adds route to the internet gateway
 16. adds the route table to the subnet

 1. adds a new VPC
 hg> aws ec2 create-vpc --cidr-block 10.0.0.0/16
{
    "Vpc": {
        "CidrBlock": "10.0.0.0/16",
        "DhcpOptionsId": "dopt-4f7dfb35",
        "State": "pending",
        "VpcId": "vpc-039f245cebc7080bc",
        "OwnerId": "639362923438",
        "InstanceTenancy": "default",
        "Ipv6CidrBlockAssociationSet": [],
        "CidrBlockAssociationSet": [
            {
                "AssociationId": "vpc-cidr-assoc-0f4e9eb1f04d70fa9",
                "CidrBlock": "10.0.0.0/16",
                "CidrBlockState": {
                    "State": "associated"
                }
            }
        ],
        "IsDefault": false
    }
}

"VpcId": "vpc-039f245cebc7080bc"

2. names the VPC
  aws ec2 create-tags --resources <vpc-id> --tags Key=<tag-key>,Value=<tag-value>
  aws ec2 create-tags --resources vpc-039f245cebc7080bc --tags Key=Name,Value=AC1

3. adds dns support
  aws ec2 modify-vpc-attribute --vpc-id $AWS_VPC_ID --enable-dns-support "{\"Value\":true}"
  aws ec2 modify-vpc-attribute --vpc-id vpc-039f245cebc7080bc --enable-dns-support "{\"Value\":true}"

4. adds a dns hostname
  aws ec2 modify-vpc-attribute --vpc-id "$vpcId" --enable-dns-hostnames "{\"Value\":true}")
  aws ec2 modify-vpc-attribute --vpc-id vpc-039f245cebc7080bc --enable-dns-hostnames "{\"Value\":true}"

5. creates an internet gateway
  sudo apt-get install jq

  export gateway_response=$(aws ec2 create-internet-gateway --output json)
  export gatewayId=$(echo -e "$gateway_response" |  /usr/bin/jq '.InternetGateway.InternetGatewayId' | tr -d '"')

  echo $gatewayId
  igw-09499d5669cd460f9

6. names the internet gateway
  aws ec2 create-tags --resources "$gatewayId" --tags Key=Name,Value="$gatewayName"
  aws ec2 create-tags --resources igw-09499d5669cd460f9 --tags Key=Name,Value=AC1_Gateway

7. creates the subnet








  ## Reference Links

https://betterprogramming.pub/creating-a-vpc-with-autoscaling-in-aws-cli-45708c953ab5

https://cloud.google.com/anthos/clusters/docs/multi-cloud/aws/how-to/create-aws-vpc

https://towardsaws.com/provisioning-instances-via-aws-cli-c511a9a5eba6

https://eclipsys.ca/fr/launch-an-ec2-instance-with-a-static-website-using-awscli-in-10-min-freetier/

https://cloud.google.com/anthos/clusters/docs/multi-cloud/aws/how-to/create-aws-vpc

https://okigiveup.net/book-reviews/

https://okigiveup.net/

https://vaneyckt.io/posts/creating_an_ec2_instance_in_a_vpc_with_the_aws_cli/

https://serverfault.com/questions/648332/how-to-list-all-vpc-dependencies-in-aws-cli


https://www.golinuxcloud.com/aws-cli-tutorial/

free kindle ... aws
https://www.amazon.com/gp/product/B007S33NT2/ref=cm_cr_ryp_prd_ttl_sol_0

