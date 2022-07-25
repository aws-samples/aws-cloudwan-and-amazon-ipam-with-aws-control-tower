## Architecture



In this example setup, we utilize a management account for deploying the AWS Control Tower landing zone. Three AWS Organizations  (Shared Services organizational unit (OU), Production OU, and Development OU) are created. Three AWS accounts are created. Production account is enrolled to Production OU, Development account is enrolled to Development OU, and finally Network Hub account is enrolled to Shared Services OU. In the Network Hub account, a Cloud WAN core network with three segments (shared services, production, and development) across two regions is created leveraging Cloud WAN. The core network is shared across the Organization leveraging AWS Resource Access Manager (AWS RAM). The CIDRs for VPCs in spoke accounts and shared services are provisioned using the IPAM service. This makes sure that there are non-overlapping CIDRs across your global network infrastructure. The VPCs are connected to the shared core network, which is managed by Cloud WAN.

![image](https://github.com/aws-samples/aws-cloudwan-and-amazon-ipam-with-aws-control-tower/blob/main/cloudwan-controltower.png)


Be sure to:

* Change the title in this README
* Edit your repository description on GitHub

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

