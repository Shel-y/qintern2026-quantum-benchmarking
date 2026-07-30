# Project's Monitor Tool & IaC Artifact
- **LINK:** [qintern2026_26-project-infrastructure](https://github.com/ajlrza/qintern2026-project-infrastructure).

The project repository above contains the software utilized for monitoring of the algorithms' performance under local hardware metrics, AWS instance metrics, and AWS instance attributes.

The metrics and attributes are listed below along with their specific syntax from ```psutil``` documentation and ```Boto3``` documentation

#### LOCAL HARDWARE METRICS:

* CPU Percentage
* RAM
* Disk I/O Latency

#### AWS INSTANCE METRICS [EC2]:
* CPU utilization ```CPUUtilization```
* RAM ```mem_used_percent```
* Network I/O Latency ```NetworkIn```, ```NetworkOut```
* Disk I/O Latency ```DiskReadOps```, ```DiskWriteOps```

#### AWS INSTANCE ATTRIBUTES [EC2]:
* Instance Type ```InstanceType```
* Virtual CPU Information ```VCpuInfo```
* RAM ```MemoryInfo['SizeInMIB']```
* Processor ```ProcessorInfo```
* GPU ```GpuInfo```
* Hypervisor ```Hypervisor```

#### AWS INSTANCE ATTRIBUTES [SV1]:
* Job ARN ```jobArn```
* Device ARN ```deviceArn```
* Quantum Task ARN ```quantumTaskArn```
* Algorithm Specification ```algorithmSpecification```
* Shots ```shots```
* Timestamp ```createdAt```, ```endedAt```
* Action Metadata ```actionMetadata```
