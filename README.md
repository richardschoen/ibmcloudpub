# Useful scripts and info for working with IBM Power Virtual Server

## Creating a cloud enabled image from the cloud CLI   
This command line will create a new IBM i V7R5 instance in the IBM i cloud.   
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
