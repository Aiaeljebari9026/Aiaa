import boto3

aws_access_key_id = 'Aia'
aws_secret_access_key = 'Aia'
region = 'Norte de virginia'  


ec2 = boto3.resource('ec2',
                     aws_access_key_id=aws_access_key_id,
                     aws_secret_access_key=aws_secret_access_key,
                     region_name=region)


instance = ec2.create_instances(
    ImageId='20124396924', 
    MinCount=1,
    MaxCount=1,
    InstanceType='EC2',  
    KeyName='olom',  
    SecurityGroupIds=['voclabs/user244**6=aia'],
    UserData='#!/bin/bash\napt-get update -y && apt-get upgrade -y', 
    TagSpecifications=[
        {
            'ResourceType': 'instance',
            'Tags': [
                {
                    '****': 'Aia',
                    'Acces*': 'MiServidor'
                }
            ]
        }
    ]
)

instance_id = instance[0].id
print('i-0033dc7634c3a5483', instance_id)
