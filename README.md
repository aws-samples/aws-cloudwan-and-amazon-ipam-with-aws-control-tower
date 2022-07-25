## Architecture



In this example setup, we utilize a management account for deploying the AWS Control Tower landing zone. Three AWS Organizations  (Shared Services organizational unit (OU), Production OU, and Development OU) are created. Three AWS accounts are created. Production account is enrolled to Production OU, Development account is enrolled to Development OU, and finally Network Hub account is enrolled to Shared Services OU. In the Network Hub account, a Cloud WAN core network with three segments (shared services, production, and development) across two regions is created leveraging Cloud WAN. The core network is shared across the Organization leveraging AWS Resource Access Manager (AWS RAM). The CIDRs for VPCs in spoke accounts and shared services are provisioned using the IPAM service. This makes sure that there are non-overlapping CIDRs across your global network infrastructure. The VPCs are connected to the shared core network, which is managed by Cloud WAN.

![image](https://github.com/aws-samples/aws-cloudwan-and-amazon-ipam-with-aws-control-tower/blob/main/cloudwan-controltower.jpg)


## Prerequisites

The following prerequisites are necessary for following along with this post:

- The default accounts and the OU structure provisioned through AWS Control Tower are present. In other words, the following accounts are present and enrolled in the AWS Control Tower landing zone:
  - Management Account
  - Log Archive and Audit Accounts (in Security OU)
- Create Shared Services OU and a Network Hub Account. Enroll the Network Hub Account to the Shared Services OU. Then create Production OU and a Production Account. Enroll the Production Account to the Production OU. Lastly, create Development OU and a Development Account. Enroll the Development Account to the Development OU.
- Deploy the initial-setup.yml ( ManagementPrep.yml) CloudFormation template in the home Region of the management account. This template creates the AWS Systems Manager parameters and AWS RAM shares to interact with Organizations.

Note : The code provided to provision the infrastructure assumes two AWS Regions (us-east-1 and eu-west-1) for Cloud WAN Core Network and IPAM as an example. Make the appropriate changes to suit your requirements.

## Deployment steps

The deployment of the solution consists of three sections:

- Section-1: Deploy and set up AWS Control Tower in the Management account.
- Section-2: Add the packaged code for AWS Control Tower customizations that sets up IPAM, Cloud WAN core network, and segments in the Network Hub account.
- Section-3: Add the spoke automations required to provision the VPCs leveraging CIDRs assigned from IPAM and connected globally using the Cloud WAN core network.

Please refer to [blog](https://aws.amazon.com/blogs/networking-and-content-delivery/ip-address-management-for-aws-control-tower/) for further details.

A special call out to [Rasika Mantri](https://www.linkedin.com/in/rasikamantri/) for contributing IPAM modules that are leveraged in this post. 

## Author 
Shiva Vaidyanthan - Sr.Cloud Infrastructure Architect - vaidys@amazon.com

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

