# AWS Naming & Tagging Conventions
AWS Tagging policy and naming convention for all resources created within any AWS accounts under the AWS Master Account

# Table of Contents
[Terms and Abbreviations](#_Toc500424982)

[Bibliography](#bibliography)

[Executive Summary](#executive-summary)

[AWS Terms and Abbreviations](#aws-terms-and-abbreviations)

[Tagging Overview](#tagging-overview)

[Tagging Best Practices](#tagging-best-practices)

[Resource Groups](#resource-groups)

[Compound Tags](#compound-tags)

[Style Rules](#style-rules)

[Tagging Region Codes](#tagging-region-codes)

[Enterprise Tagging Standards](#enterprise-tagging-standards)

[Environment Names](#environment-names)

[Name Tag Format](#name-tag-format)

[AMI Versioning](#ami-versioning)

[Additional Tags](#additional-tags)

[Operational Tags](#operational-tags)

[Business Tags](#business-tags)

[Security Tags](#security-tags)

[AWS Resource Suffixes 11](#aws-resource-suffixes)

[Name Tag Examples 12](#name-tag-examples)

## Terms and Abbreviations

The following table lists the Terms and Abbreviations that are
referenced within the document.

| Term    | Explanation                                |
| ------- | ------------------------------------------ |
| AMI     | Amazon Machine Image                       |
| AWS     | Amazon Web Services                        |
| AWS IAM | AWS Identity and Access Management Service |
| DB      | Database                                   |
| EBS     | Elastic Block Store                        |
| EC2     | AWS Elastic Compute Cloud                  |
| OS      | Operating System                           |
| PCI     | Payment Card Industry                      |
| PII     | Personally identifiable information        |
| RBAC    | Role-based Access Control                  |
| RDS     | Relational Database Service                |
| S3      | Simple Storage Service                     |
| SNS     | Simple Notification Service                |
| SQS     | Simple Queue Service                       |
| VPC     | Virtual Private Cloud                      |

### Bibliography

The table below contains information about, and (where possible) links
to, supporting documentation.

<table>
<thead>
<tr class="header">
<th>NO.</th>
<th>DESCRIPTION</th>
<th>VERSION</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>“How Should I Tag my AWS resources?” - <a href="https://d0.awsstatic.com/aws-answers/AWS_Tagging_Strategies.pdf" class="uri">https://d0.awsstatic.com/aws-answers/AWS_Tagging_Strategies.pdf</a></td>
<td>June 2, 2017</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>AWS Naming Convention Best Practices (tagging) - <a href="http://www.myrtec.com.au/sites/www.myrtec.com.au/files/attachments/aws_naming_convention_best_practices_-_tagging.pdf" class="uri">http://www.myrtec.com.au/sites/www.myrtec.com.au/files/attachments/aws_naming_convention_best_practices_-_tagging.pdf</a></td>
<td>September 11, 2014</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>AWS now supports 50 tags per resource - <a href="https://aws.amazon.com/blogs/security/now-organize-your-aws-resources-by-using-up-to-50-tags-per-resource/" class="uri">https://aws.amazon.com/blogs/security/now-organize-your-aws-resources-by-using-up-to-50-tags-per-resource/</a></td>
<td>August 15, 2016</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>User defined tag restrictions - <a href="http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/allocation-tag-restrictions.html" class="uri">http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/allocation-tag-restrictions.html</a></td>
<td>LATEST</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Tagging your EC2 resources - <a href="http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html" class="uri">http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html</a></td>
<td>LATEST</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Naming Conventions - <a href="https://en.wikipedia.org/wiki/Naming_convention_(programming)" class="uri">https://en.wikipedia.org/wiki/Naming_convention_(programming)</a></td>
<td>August 3, 2017</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>Elasticache replication group naming limits - <a href="http://docs.aws.amazon.com/cli/latest/reference/elasticache/create-replication-group.html" class="uri">http://docs.aws.amazon.com/cli/latest/reference/elasticache/create-replication-group.html</a></td>
<td>As of 06/09/2017</td>
</tr>
</tbody>
</table>

## AWS Terms and Abbreviations

The following terms and abbreviations will be used through this design and implementation of all Enterprise applications.

| Name                       | Value    |
| -------------------------- | -------- |
| Connectivity               | CONN     |
| Database Layer             | RDS      |
| Productuion Environment    | PROD     |
| Dev Test Environment       | DEV/TEST |
| Pre Production Environment | PPE      |
| Management and Monitoring  | MGMT     |
| Private                    | PRI      |
| Public                     | PUB      |

N.B. In the above table the forward slash character (“/”) is part of the Value and is not being used as a delimiter.

## Tagging Overview

AWS provide the ability to tag resources with descriptive metadata. Tags
simplify resource management at scale and will be used for cost
allocation. As the Enterprise plans to implement multiple applications,
multiple application environments and multiple AWS accounts; tagging
must be applied consistently to allow costs to be separated out into
applications, environments and business units.

Each tag consists of a key and a value, both of which are user-defined
strings. Once defined, tags can be used as a filter when requesting
resources, such as Amazon EC2 instances, based on tag keys or values.
Tags are also reported against in Cost Allocation Reports.

Tags provide identification and classification of AWS resources.
Examples of commonly used tags include application identifier,
environment, or owner.

### Resource Groups

Use resource groups. A Resource Group is a collection of resources that
shares one or more tags. It can span services and can be used to create
a custom console that organizes and consolidates resources on a
per-project basis. In AWS, a resource is an entity such as an EC2
instance, a S3 bucket and so on. Using the resource group tool, custom
consoles can be created that organize and consolidate all resources for
a specific project in a single view. For example, all the resources for
a version of TEAM_A in production can be in one resource group whilst
those resources used for TEAM_B be can be in another resource group
(though the Enterprise's cloud operating model dictates that applications must
exist in different accounts).

### Compound Tags

There is a limit of 50 tags per resource in AWS, as such it is a good
practice to combine several tag keys and values into a single compound
tag. For example, rather than creating 3 keys (tags) called “OwnerName”,
“OwnerPhone”, and “OwnerEmail,” the 3 keys should be combined into 1 key
called “OwnerContact,” which could contain the compound values of Name,
Phone, and Email address using a pipe delimiter.

We will assign the Name Tag as a compound value. We will use the hyphen
as a delimiter. An example of the values assigned to the Name Tag are
shown in examples section at the end of this document.

### Style Rules

  - Tag key names are case-sensitive and can contain mixed-case letters,
    numbers, underscores, and hyphens.

  - Tag key names should use upper CamelCase (a.k.a. Pascal case), a
    convention that combines words/abbreviations by beginning each word
    with a capital letter such as “MiscMetadata” and “SupportEndpoints”.

  - Tag values are case-sensitive and should not use the semi-colon
    (“;”), equal sign (“=”), or pipe (“|”) characters as these are
    used as delimiters in compound values.

  - Compound tag value key names should use Pascal case followed by an
    equal sign (“=”) such as
    KeyName1=value1-value2-value3;KeyName2=value1-value2-value3
    
## Tagging Region Codes

AWS’ regions codes are unique; therefore, they will be abbreviated as
follows:

| Region        | Location      | Partition    | Launched | AWS code         | A1      | A2      | B       |
|---------------|---------------|--------------|----------|------------------|---------|---------|---------|
| US East       | N. Virginia   | `aws`        | 2006     | `us-east-1`      | `usea1` | `use1`  | `usva`  |
| US East       | Ohio          | `aws`        | 2016     | `us-east-2`      | `usea2` | `use2`  | `usoh`  |
| US West       | N. California | `aws`        | 2011     | `us-west-1`      | `uswe1` | `usw1`  | `usca`  |
| US West       | Oregon        | `aws`        | 2009     | `us-west-2`      | `uswe2` | `usw2`  | `usor`  |
| GovCloud US   | Northwest     | `aws-us-gov` | 2011     | `us-gov-west-1`  | `ugwe2` | `usgw2` | `usgov` |
| Canada        | Montreal      | `aws`        | 2016     | `ca-central-1`   | `cace1` | `cac1`  | `caqc`  |
| EU            | Ireland       | `aws`        | 2007     | `eu-west-1`      | `euwe1` | `ew1`   | `ied`   |
| EU            | London        | `aws`        | 2016     | `eu-west-2`      | `euwe2` | `ew2`   | `gblnd` |
| EU            | Frankfurt     | `aws`        | 2014     | `eu-central-1`   | `euce1` | `ec1`   | `dehe`  |
| Asia Pacific  | Singapore     | `aws`        | 2010     | `ap-southeast-1` | `apse1` | `apse1` | `sg`    |
| Asia Pacific  | Sydney        | `aws`        | 2012     | `ap-southeast-2` | `apse2` | `apse2` | `aunsw` |
| Asia Pacific  | Mumbai        | `aws`        | 2016     | `ap-south-1`     | `apso1` | `aps1`  | `inmh`  |
| Asia Pacific  | Tokyo         | `aws`        | 2011     | `ap-northeast-1` | `apne1` | `apne1` | `jp13`  |
| Asia Pacific  | Seoul         | `aws`        | 2016     | `ap-northeast-2` | `apne2` | `apne2` | `kr11`  |
| South America | Saõ Paulo     | `aws`        | 2011     | `sa-east-1`      | `saea1` | `sae1`  | `brsp`  |
| China         | Beijing       | `aws-cn`     | 2013     | `cn-north-1`     | `cnno1` | `cn1`   | `cn11`  |

| Code | Description                         |
|------|-------------------------------------|
| A1   | Abbreviated AWS code (equal length) |
| A2   | Abbreviated AWS code                |
| B    | Concatenated ISO 3166 code          |

### Domain names for regional services

| AWS code         | Domain 1           | Domain 2        |
|------------------|--------------------|-----------------|
| `us-east-1`      | example-va.us      | example.us      |
| `us-west-1`      | example-ca.us      | example-west.us |
| `us-west-2`      | example-or.us      | example-nw.us   |
| `eu-west-1`      | example-d.ie       | example.ie      |
| `eu-west-2`      | example-lnd.net.uk | example.net.uk  |
| `eu-central-1`   | example-he.de      | example.de      |
| `ap-southeast-1` | example.sg         | example.sg      |
| `ap-southeast-2` | example-nsw.net.au | example.net.au  |
| `ap-northeast-1` | example-13.jp      | example.jp      |
| `ap-northeast-2` | example.seoul.kr   | example.ne.kr   |
| `sa-east-1`      | example-sp.net.br  | example.net.br  |
| `cn-north-1`     | example.bj.cn      | example.cn      |

### Capital-delimited codes for variable-width fonts

| AWS code         | A1      | A2    | B     |
|------------------|---------|-------|-------|
| `us-east-1`      | `USea1` | USe1  | USva  |
| `us-west-1`      | `USwe1` | USw1  | USca  |
| `us-west-2`      | `USwe2` | USw2  | USor  |
| `us-gov-west-1`  | `gUSwe1`| gUSw1 | gUSnw |
| `eu-west-1`      | `EUwe1` | Ew1   | IEd   |
| `eu-west-2`      | `EUwe2` | Ew2   | GBlnd |
| `eu-central-1`   | `EUce1` | Ec1   | DEhe  |
| `ap-southeast-1` | `APse1` | APse1 | SG    |
| `ap-southeast-2` | `APse2` | APse2 | AUnsw |
| `ap-northeast-1` | `APne1` | APne1 | JP13  |
| `ap-northeast-2` | `APne2` | APne2 | KR11  |
| `sa-east-1`      | `SAea1` | SAe1  | BRsp  |
| `cn-north-1`     | `CNno1` | Cn1   | CN11  |

### Bold-delimited codes for rich text
| AWS code         | A1        | A2        | A2c       | B         |
|------------------|-----------|-----------|-----------|-----------|
| `us-east-1`      | **us**ea1 | **us**e1  | **US**E1  | **us**va  |
| `us-west-1`      | **us**we1 | **us**w1  | **US**W1  | **us**ca  |
| `us-west-2`      | **us**we2 | **us**w2  | **US**W2  | **us**or  |
| `us-gov-west-1`  | gov**us**we1 | gov**us**w1 | **USg**W1 | gov**us**nw |
| `eu-west-1`      | **eu**we1 | **e**w1   | **E**W1   | **ie**d   |
| `eu-west-2`      | **eu**we2 | **e**w2   | **E**W2   | **gb**lnd |
| `eu-central-1`   | **eu**ce1 | **e**c1   | **E**C1   | **de**he  |
| `ap-southeast-1` | **ap**se1 | **ap**se1 | **AP**SE1 | **sg**    |
| `ap-southeast-2` | **ap**se2 | **ap**se2 | **AP**SE2 | **au**nsw |
| `ap-northeast-1` | **ap**ne1 | **ap**ne1 | **AP**NE1 | **jp**13  |
| `ap-northeast-2` | **ap**ne2 | **ap**ne2 | **AP**NE2 | **kr**11  |
| `sa-east-1`      | **sa**ea1 | **sa**e1  | **SA**E1  | **br**sp  |
| `cn-north-1`     | **cn**no1 | **c**n1   | **C**N1   | **cn**11  |

## AMI Versioning

AMI’s will have names that uniquely identify their use, operating
system, OS version, creation date (reversed), creation version and AWS
resource type prefix ‘AMI’. A “golden image” RedHat Linux 7.1 AMI name
would be as
follows:

| Use                             | Operating System | Version | Creation Date | Version | AWS Resource |
| ------------------------------- | ---------------- | ------- | ------------- | ------- | ------------ |
| GOLD                            | RHEL             | 7.1     | 12/09/2017    | 01      | AMI          |
| GOLD.RHEL.7.1.2017.09.12.01-AMI |

## Business Tags

These can be used to capture business relevant information and which
part of the business is responsible for this resource. Can greatly speed
up the elimination process in an event of failure or
attack.

| Tag            | Description                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| SquadName      | Squad / Business are responsible for resource                                                                                          |
| CostCentre     | Business group to be billed for the AWS resources                                                                                      |
| PartnerContact | Value contains contact information for external managed services partner Pipe separated John Smith| +44 0000 00000 |jsmith@example.com |

## Security Tags

To obtain a full visibility over account surface data we use these
security classification tags in conjunction with the [Additional
Tags](#additional-tags) to map which classification of data is where.
AWS Config Rules can also be set where PCI data can only sit in
Network=Red.

| Tag             | Description                                                                                   |
| --------------- | --------------------------------------------------------------------------------------------- |
| Compliance      | An identifier for workloads designed to adhere to specific compliance e.g. Normal / PII / PCI |
| Permissions     | An identifier for the specific entity that can modify the resource                            |
| LastReviewed    | Last time this instance was reviewed for compliance - YYYY-mm-dd                              |
| ApprovedVersion | Steps which are taken to approve AMI image                                                    |
| ApprovedBy      | Department or software which has approved AMI for use in Organisation X                       |

