<h1 style="text-align: center;">**How to launch instances**</h1>

```ansible-playbook ec2-launch-detailed.yaml```

The file _ec2-launch-detailed.yaml_ doesn't require an inventory because it is running only under **localhost** (Declared within itself)

This will launch n amount of instances (Adjustable by switching the count variable under the 'Launch instance' task)

The different settings of said instances are declared on the 'vars' section at the start of the file

We can tag the created instances in the appropriately named section, IE:

            ```tags:
                    Name: InstanceName
                    TAG: VALUE```

This ansible script will also SSH into the newly created instances, waiting until the connection has been established, so that we can proceed with the following task

The task 'Configure instances' is equal to setting the **user data** on the Amazon EC2 configuration, and it allows us to execute commands after the instances are fully up

***

<h1 style="text-align: center;">**How to copy files to the running instances**</h1>

```ansible-playbook -i aws_ec2.yml copy_files.yaml```

This command will use the dictionary _aws_ec2.yml_, which forces our program to only copy files to the instances in the *eu_west_1* region, and only with the APP tag value of vue2048