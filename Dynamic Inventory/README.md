# aws-ec2.yml is a playbook from which we can get ec2-info and can create new ec2_instances

AWS crediantials are stored into secret.yml file
to create ansible vault
    ansible-vault create secret.yml
vim editor is opened type following
    AWS_ACCESS_KEY_ID: XXXXXXXXXXXXXXXX
    AWS_SECRET_KEY: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

to get only instances:
    ansible-playbook aws-ec2.yml --ask-vault-pass

bydefault playbook will fetch only ec2-info, to launch ec2 intance
    ansible-playbook aws-ec2.yml --ask-vault-pass --tags=ec2-create

we can install aws-cli and use command aws configure to setup creds for aws, after this we do not need secret file or to export variables

# ec2.py and ec2.ini
these files are given by official ansible to act as dynamic inventory for aws, boto should be 

    ./ec2.py 
    or
    python3 ec2.py


    ansible -i ec2.py -m ping --private-key=key.pem tag_Name_web --ssh-extra-args='-o StrictHostKeyChecking=no'