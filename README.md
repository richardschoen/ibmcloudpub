# Useful scripts and info for working with IBM Power Virtual Server

## Creating a cloud enabled image from the Power Cloud CLI   
This command line will create a new IBM i V7R5 instance in the IBM i cloud.   
This is a shared uncapped image on an s922 Power 9 machine using 0.25 CPU with 8gb ram. Using the 3 iops disk.   
```
ibmcloud pi ins create ibmiinstance-1 
--image IBMi-75-06-2924-1 
--subnets public-192_168_231_96-29-VLAN_2280 
--storage-tier tier3 
--sys-type s922 
--processor-type shared 
--processors 0.25  
--memory 8 
--key-name id_rsa_2024_pub   
## --boot-volume-replication-enabled=true
```

## Target the Power Virtual Server workspace
ibmcloud pi workspace target crn:v1:bluemix:public:power-iaas:us-south:a/f6472f1dd0ca4a6c946383ac8a4ba1e7:38e9ac5c-8420-4b33-a136-59ce22bda728::

## List the subnets in the targeted workspace
ibmcloud pi subnet list

ID                                     Name                                 Address
859d86c3-9427-4a89-a352-c64a5941dec9   public-192_168_231_96-29-VLAN_2280   /pcloud/v1/cloud-instances/8fa57f8b05e64ea0be3a10d0d374e94e/networks/859d86c3-9427-4a89-a352-c64a5941dec9

## List the available storage tiers in the targeted workspace
ibmcloud pi storage-tiers

## List instances
ibmcloud pi instance list

## List specific instance details by id
ibmcloud pi instance get mobitest-1 b0c0a6b6-b595-4e0a-af70-3dbb180ba6c6

## Enable CI on the instance
CALL PGM(QSYS/QAENGCHG) PARM((*ENABLECI))

## Disable CI on the instance
CALL PGM(QSYS/QAENGCHG) PARM((*DISABLE))
