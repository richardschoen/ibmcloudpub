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
## List Power Virtual Server workspaces
```
ibmcloud pi workspace list
```
This returns 3 values: ID, Name and CRN. ```CRN``` is used when connecting to an instance.    

## Target the Power Virtual Server workspace
```
ibmcloud pi workspace target crn:v1:bluemix:public:power-iaas:us-south:a/f6472f1dd0ca4a6c946383ac8a4ba1e7:39e8ac5c-8420-4b33-a136-59ce22bda728::
```
Switch to the workspace instance using the ```CRN``` value.

## List the subnets in the targeted workspace
```
ibmcloud pi subnet list
```
After getting the list resilts, the ```Name``` is used when creating an instance.   

## List the available storage tiers in the targeted workspace
```
ibmcloud pi storage-tiers
```
```tier0```    active   Tier 0 (25 IOPs/GB)   
```tier1```    active   Tier 1 (10 IOPs/GB)   
```tier3```    active   Tier 3 (3 IOPs/GB)   
```tier5k```   active   Fixed IOPs (5,000 IOPs)    

## List instances
```
ibmcloud pi instance list
```

## List specific instance details by id
```
ibmcloud pi instance get mobitest-1 b0c0a6b6-b595-4e0a-af70-3dbb180ba6c6
```

## Enable CI on the instance before shutdown and creating a boot image   
```
CALL PGM(QSYS/QAENGCHG) PARM((*ENABLECI))
```

## Disable CI on the instance after booting   
```
CALL PGM(QSYS/QAENGCHG) PARM((*DISABLE)) 
```

