# OpenStack

## Installing OpenStack in ubuntu using MicroStack 
```
sudo snap install microstack --beta
```

<img width="981" alt="Screenshot 2025-03-24 at 1 00 26 AM" src="https://github.com/user-attachments/assets/2fd9adda-4a92-4e8a-9d67-aaa682fc9798" />


### 1. Initialize MicroStack
```
sudo microstack init --auto --control
```
This command:

* Sets up OpenStack services.
* Configures networking.
* Enables an internal bridge for virtual machines.


<img width="981" alt="Screenshot 2025-03-24 at 1 01 30 AM" src="https://github.com/user-attachments/assets/6ffc814d-6285-4412-8f97-f62433d2596f" />



### 3. Access OpenStack Dashboard
Once initialized, you can access the Horizon web dashboard:

-> Find the dashboard IP address:
```
ip a | grep inet
```
for example:-

<img width="981" alt="Screenshot 2025-03-24 at 1 02 28 AM" src="https://github.com/user-attachments/assets/86a58386-c152-466f-b3ba-e5d1d7f1a369" />


-> for password 
```
sudo snap get microstack config.credentials.keystone-password
```

-Go to web browser and search this above IP address:
```
http://<your-ip>:80
```


<img width="1001" alt="Screenshot 2025-03-24 at 1 03 22 AM" src="https://github.com/user-attachments/assets/3fd6133c-8444-449a-af9e-01657011660a" />


## Log in using the default credentials:

* Username: admin
* password: (from above)

<img width="978" alt="Screenshot 2025-03-24 at 1 04 12 AM" src="https://github.com/user-attachments/assets/0286e811-dee4-4ea7-a678-0c44eb56ea88" />
