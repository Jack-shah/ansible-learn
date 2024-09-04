i have perfomred this project using  my windows.
installed wsl  on in           from powershell > wsl --install # this will install a linux machine on windows laptop
installed python on it
installed pip
using pip installed the ansible 

now the main task come into picture

#task is to install docker and some secuity app on aws ubuntu instance

####################################
first  for anisble to work we have to set password less ssh method(keypair must be downloaded while creating ec2 instance)

i have the keypar on my windows directory  /downoload/test.pem                  it will be used for first time ssh with keypair
then i copied it from windows directory to my prpject dir on wsl ie /root/myproject/day8/  using copy command  #cp /mnt/c/Users/Wajid\ Ali/Downloads/test.pem  .                we have used /mnt as file was on windows directory system

create rsa key for passowrd less authetication
 ssh-keygen -t rsa
yes
yes

 it will create id_rsa and id_rs.pub  key  files   in  ~/.ssh/

copy the public key #cat id_rsa.pub                            and copy

now ssh into you aws instance using  keypair            test.pem file     # ssh -i test.pem ubuntu@<public ip of aws instance>

now  goto  ~./ssh  folder        and  paste the copied  public key in  authorise _keys file
vi authorised_keys           and paste the key.  and save it

Now we can easily ssh into aws instance without passowrd or ssh file

#######################
then create an inventory.ini file in the project folder and add the ip of the aws instance on which we have to instance docker......
 created the playbook file in the same folder..............

