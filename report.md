# lab6-microservices

Author: Andrew Mackay  
NIP: 737069  
Date: 12/01/2020

## 1. Launch of Eureka Service Registration Server

First, we launch Eureka's registration server on port 1111. The log output is:

 ![Eureka registration launch](screenshots/registration_launch.png)

 Now, we can access the server on port 1111 to check the services registered.
 Since we have only launched the register service, there will be no services
 registered:

![Eureka registration no services](screenshots/eureka_no_services.png)


## 2. Launching the Accounts Service

The next step is to launch the accounts service on port 2222 on a new terminal. 
The log output is:

![Accounts service launch](screenshots/accounts_launch.png)

If we check the log output of the registration service, we can check that the
accounts service has been detected and registered:

![Accounts service registration log](screenshots/accounts_launch_registration.png)

The Eureka server now displays the new registered service:

![Eureka registration 1 service](screenshots/eureka_one_service.png)

We can also access the port 2222 on our browser and observe that the accounts
service is running:

![Accounts server](screenshots/accounts_server.png)

## 3. Launching the Web Service

In a similar way to the accounts service, the web service is launched on port
3333 on a new terminal:

![Web service launch](screenshots/web_launch.png)

Once it's launched, the log output of the Eureka registration service displays:

![Web service registration log](screenshots/web_launch_registration.png)

The Eureka server now displays the new registered service and the accounts
service:

![Eureka registration 2 services](screenshots/eureka_two_services.png)

And if we access the port 3333 on our browser, we can check that the web service
is up and running:

![Web server](screenshots/web_server.png)

## 4. Launching the Second Accounts Service

To launch a second accounts services, first we have to modify the server's port
value in the service's application.yml file from 2222 to 4444. Then, we can
launch it in exactly the same way as the first accounts service, on a new 
terminal:

![Second accounts service launch](screenshots/second_accounts_launch.png)

Once it's launched, the Eureka registration service outputs:

![Second accounts service registration log](screenshots/second_accounts_launch_registration.png)

The Eureka server will now display 2 types of services, but the accounts
service line will have 2 instances:

![Eureka registration 3 services](screenshots/eureka_three_services.png)

## 5. Killing the First Accounts Service

If we kill the first accounts service, the Eureka server displays the service
as *down*, and then it dissappears and only shows 2 services like before.

![Eureka registration killed accounts](screenshots/eureka_killed_accounts.png)

At the same time, the log output of the registration service is:

![Registation log killed accounts](screenshots/accounts_killed_log.png)

Because there is another accounts service registered on port 4444, the application
continues working since they both have access to the same database. We can check
that a account details web page is still accesible from the web server:

![Owner account](screenshots/owner.png)
