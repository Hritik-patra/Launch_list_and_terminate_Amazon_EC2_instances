# Launch_list_and_terminate_Amazon_EC2_instances
You can use the AWS Command Line Interface (AWS CLI) to launch, list, and terminate Amazon Elastic Compute Cloud (Amazon EC2) instances. If you launch an instance that isn't within the AWS Free Tier, you are billed after you launch the instance and charged for the time that the instance is running, even if it remains idle.

Note: For additional command examples, see the AWS CLI reference guide.
# Topic
Topics

    -Prerequisites
    -Launch your instance
    -Add a block device to your instance
    -Add a tag to your instance
    -Connect to your instance
    -List your instances
    -Terminate your instance
    -References
# Prerequisites
To run the ec2 commands in this topic, you need to:

    -Install and configure the AWS CLI. For more information, see Install or update the latest version of the AWS CLI and Authentication and access credentials.

    -Set your IAM permissions to allow for Amazon EC2 access. For more information about IAM permissions for Amazon EC2, see IAM policies for Amazon EC2 in the Amazon EC2 User Guide for Linux Instances.

    -Create a key pair and a security group.

    -Select an Amazon Machine Image (AMI) and note the AMI ID. For more information, see Finding a Suitable AMI in the Amazon EC2 User Guide for Linux Instances.
# Launch your instance
    -To launch an Amazon EC2 instance using the AMI you selected, use the aws ec2 run-instances

    -command. You can launch the instance into a virtual private cloud (VPC).

    -Initially, your instance appears in the pending state, but changes to the running state after a few minutes.

    -The following example shows how to launch a t2.micro instance in the specified subnet of a VPC. Replace the italicized parameter values with your own.
Code will be in Ec2.py (lunch your instance section)

# Add a block device to your instance
    Each instance that you launch has an associated root device volume. You can use block device mapping to specify additional Amazon Elastic Block Store (Amazon EBS) volumes or instance store volumes to attach to an       instance when it's launched.

    To add a block device to your instance, specify the --block-device-mappings option when you use run-instances.

    The following example parameter provisions a standard Amazon EBS volume that is 20 GB in size, and maps it to your instance using the identifier /dev/sdf.

   -First line code in (Add a block device to your instance section first line code)
     The following example adds an Amazon EBS volume, mapped to /dev/sdf, based on an existing snapshot. A snapshot represents an image that is loaded onto the volume for you. When you specify a snapshot, you don't have to specify a volume size; it will be large enough to hold your image. However, if you do specify a size, it must be greater than or equal to the size of the snapshot.

    -Second line code in (Add a block device to your instance section second line code)

    The following example adds two volumes to your instance. The number of volumes available to your instance depends on its instance type.
    
    -Third line code in (Add a block device to your instance section third line code)
   The following example creates the mapping (/dev/sdj), but doesn't provision a volume for the instance.
    -Fourth line code in (Add a block device to your instance section Fourth line code)

    For more information, see Block Device Mapping in the Amazon EC2 User Guide for Linux Instances.

# Add a tag to your instance
    A tag is a label that you assign to an AWS resource. It enables you to add metadata to your resources that you can use for a variety of purposes. For more information, see Tagging Your Resources in the Amazon EC2       User Guide for Linux Instances.

    The following example shows how to add a tag with the key name "Name" and the value "MyInstance" to the specified instance, by using the aws ec2 create-tags
    command.

    Follow the add a tag to your instance secotion in EC2.py

# Connect to your instance

    When your instance is running, you can connect to it and use it just as you'd use a computer sitting in front of you. For more information, see Connect to Your Amazon EC2 Instance in the Amazon EC2 User Guide for       Linux Instances
# List your instances
    You can use the AWS CLI to list your instances and view information about them. You can list all your instances, or filter the results based on the instances that you're interested in.

    The following examples show how to use the aws ec2 describe-instances

    command.

    The following command lists all your instances.

    -Fowllow the (List your instance section of first line)

    The following command filters the list to only your t2.micro instances and outputs only the InstanceId values for each match.

    -Follow the (List your instance section of second line)

    The following command lists any of your instances that have the tag Name=MyInstance.
    
    -Follow the (List your instance section of third line)
    
    The following command lists your instances that were launched using any of the following AMIs: ami-x0123456, ami-y0123456, and ami-z0123456.

     -Follow the (List your instance section of fourth line)
     
# Terminate your instance

    Terminating an instance deletes it. You can't reconnect to an instance after you've terminated it.

    As soon as the state of the instance changes to shutting-down or terminated, you stop incurring charges for that instance. If you want to reconnect to an instance later, use stop-instances instead of terminate-         instances. For more information, see Terminate Your Instance in the Amazon EC2 User Guide for Linux Instances.

    To delete an instance, you use the command aws ec2 terminate-instances
    to delete it.

    -Follow the Terminate your section of Ec2.py
