# HotelSpring App deployment project

This is a sample app deployment using ansible to deploy nginx as reverse proxy, java and mysql(mariadb).

The app deployed is : https://github.com/khoubyari/spring-boot-rest-example

![infra](https://image.ibb.co/g2LiHc/infra_hotelspring_test.png)

## How to run it

This app is deployed using ansible, you will need to install it on your machine/server first.

On server side, you need to have RedHat 7 or CentOS 7.

You need as well a user that will accept your ssh key (in your authorized_keys) and sudoers to execute some commands as superuser.


### Add server ip and user to your ansible host file.

Into your hosts file in this ansible structure, please add the server ip and the user used.

add line like :

```
[servers]
ServerIP ansible_user=UserOnServer
```

> Replace ServerIP with the IP from your remote server and UserOnServer with the user used on the remote server...

### Add hotelspring to your /etc/hosts

Once your server is started, you need to find the IP from the server where you will be running the app.
Then add the following to your /etc/hosts.

`sudo sh -c "echo 'YourServerIP  hotelspring.com' >> /etc/hosts"`
> Replace YourServerIP with the IP from your server...

### Run Ansible playbook

`ansible-playbook site.yml --ask-vault-pass`

vault password is : qwerty


### Check if app is running.

go to your browser and go to https://hotelspring.com/health

App could takes 15-30 seconds to run after the Ansible run is done.

## Not implemented features

From the test, i didn't know if the jar generation was part of the deployment pipeline, so it's not here, the .jar is locally in roles/appdeployfiles/ , if the test was intended to have the jar generation, i can make it.