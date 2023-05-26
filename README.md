# AWS-CLI

-Some commands to create tools aws using a terminal.

-To know more commands run:   ` ec2 aws help    `

-Before start these commands you must give access to your computer. (access key, and edit permissions IAM) 

## command - create ec2:
   ```
aws ec2 run-instances \
--image-id ami-032930428bf1abbff \
--count 1 \
--instance-type t2.micro \
--key-name Myxxxx \
--security-group-ids sg-xxxxx0e48105xxxx \
--subnet-id subnet-xxxxd4008bxxxxxx
   ```
-You must write a security group and a subnet you want to use.

-The image I'm using is us-east 1 (virginia) 

<details>
<summary>Some commands will generate a json message, like this example bellow: </summary>
<pre>
{
    "Groups": [],
    "Instances": [
        {
            "AmiLaunchIndex": 0,
            "ImageId": "ami-032930428bf1abbff",
            "InstanceId": "i-0d09e8ec59f2be0e2",
            "InstanceType": "t2.micro",
            "KeyName": "Myxxx",
            "LaunchTime": "2023-05-25T14:54:27.000Z",
            "Monitoring": {
                "State": "disabled"
            },
            "Placement": {
                "AvailabilityZone": "us-east-1a",
                "GroupName": "",
                "Tenancy": "default"
            },
            "PrivateDnsName": "ip-172-31-30-130.ec2.internal",
            "PrivateIpAddress": "172.31.30.130",
            "ProductCodes": [],
            "PublicDnsName": "",
            "State": {
                "Code": 0,
                "Name": "pending"
            },
            "StateTransitionReason": "",
            "SubnetId": "subnet-xxxxx4008b2xxxxxx",
            "VpcId": "vpc-xxxxf8611c8xxxxxx",
            "Architecture": "x86_64",
            "BlockDeviceMappings": [],
            "ClientToken": "xxxxxxxxx-207f-xxxxx-86bc-xxxxxxxxxx",
            "EbsOptimized": false,
            "EnaSupport": true,
            "Hypervisor": "xen",
            "NetworkInterfaces": [
                {
                    "Attachment": {
                        "AttachTime": "2023-05-25T14:54:27.000Z",
                        "AttachmentId": "eni-attach-xxxxxxxxxxxxxx",
                        "DeleteOnTermination": true,
                        "DeviceIndex": 0,
                        "Status": "attaching",
                        "NetworkCardIndex": 0
                    },
                    "Description": "",
                    "Groups": [
                        {
                            "GroupName": "linux2",
                            "GroupId": "sg-xxxxxxxxxxxxxx"
                        }
                    ],
                    "Ipv6Addresses": [],
                    "MacAddress": "0a:44:31:19:11:cf",
                    "NetworkInterfaceId": "eni-xxxxxxxxxxxxx",
                    "OwnerId": "287978908334",
                    "PrivateDnsName": "ip-172-31-30-130.ec2.internal",
                    "PrivateIpAddress": "172.31.30.130",
                    "PrivateIpAddresses": [
                        {
                            "Primary": true,
                            "PrivateDnsName": "ip-172-31-30-130.ec2.internal",
                            "PrivateIpAddress": "172.31.30.130"
                        }
                    ],
                    "SourceDestCheck": true,
                    "Status": "in-use",
                    "SubnetId": "subnet-xxxxxxxxxxxxxxxxxx",
                    "VpcId": "vpc-xxxxxxxxxxxxxxxxxx",
                    "InterfaceType": "interface"
                }
            ],
            "RootDeviceName": "/dev/xvda",
            "RootDeviceType": "ebs",
            "SecurityGroups": [
                {
                    "GroupName": "linux2",
                    "GroupId": "sg-xxxxxxxxxxxxxx"
                }
            ],
            "SourceDestCheck": true,
            "StateReason": {
                "Code": "pending",
                "Message": "pending"
            },
            "VirtualizationType": "hvm",
            "CpuOptions": {
                "CoreCount": 1,
                "ThreadsPerCore": 1
            },
            "CapacityReservationSpecification": {
                "CapacityReservationPreference": "open"
            },
            "MetadataOptions": {
                "State": "pending",
                "HttpTokens": "optional",
                "HttpPutResponseHopLimit": 1,
                "HttpEndpoint": "enabled",
                "HttpProtocolIpv6": "disabled",
                "InstanceMetadataTags": "disabled"
            },
            "EnclaveOptions": {
                "Enabled": false
            },
            "PrivateDnsNameOptions": {
                "HostnameType": "ip-name",
                "EnableResourceNameDnsARecord": false,
                "EnableResourceNameDnsAAAARecord": false
            }
        }
    ],
    "OwnerId": "xxxxxxxxxxxxxxxx",
    "ReservationId": "r-xxxxxxxxxxxxxx"
}
</pre>
</details>

   
 ## Command - create S3 bucket 
 
List Buckets - `aws s3 ls`

Access help api s3 - `aws s3api help`

Create bucket - `aws s3api create-bucket --bucket bucket-name-never-used --region us-east-1`

Delete bucket - `aws s3api delete-bucket --bucket bucket-name-never-used`

## command - create db instance 
   ```
aws rds create-db-instance \
    --db-instance-identifier table-tools-devops \
    --db-instance-class db.t2.micro \
    --engine mysql \
    --master-username admin \
    --master-user-password secret99 \
    --allocated-storage 12
   ```

Stop db - `aws rds stop-db-instance --db-instance-identifier table-tools-devops`

Start db stopped - `aws rds start-db-instance --db-instance-identifier table-tools-devops`

Delete db without snapshot- `aws rds delete-db-instance --db-instance-identifier table-tools-devops --skip-final-snapshot`
