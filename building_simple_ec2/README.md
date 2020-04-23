## This is simple custom AMI builder json file

## It's very important we mention the filter criteria.

owner is the [canonical]
```json 
search all the filter fields in the aws console for the ami, that the short-cut
name you have to get from the above ami search tab, with creation date

      "source_ami_filter": {
        "filters": {
        "virtualization-type": "hvm",
        "name": "ubuntu-eks/k8s_1.13/images/hvm-ssd/ubuntu-bionic-18.04-amd64-server-*",
        "root-device-type": "ebs"
        },
        "owners": ["099720109477"],
        "most_recent": true
      }
```
## How to run
```text
Fire the command "packer build ubuntu.json"
It bakes the image and outputs the AMI id, See the AMI tab and check "owned by me" tag
Now launch an ec2 machine with the newly created AMI - ami-XXXX
aws ec2 run-instances --image-id ami-XXXX --count 1 --instance-type t2.micro --key-name MyKeyPair 
```

[canonical]: <https://help.ubuntu.com/community/EC2StartersGuide>