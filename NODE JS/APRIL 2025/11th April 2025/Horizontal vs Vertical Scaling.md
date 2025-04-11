
# Horizontal Scaling (Scaling in/out)

Horizontal scaling refers to adding additional nodes or machines to your infrastructure to cope with new demands.

If you are hosting an application on a server and find that it no longer has the capacity or capabilities to handle traffic, adding a server may be your solution.

It is quite similar to delegating workload among several employees instead of one. However, the downside of this may be the added complexity of your operation. You must decide which machine does what and how your new machines work with your old machines.

## Advantages of horizontal scaling

- **Scaling is easier from a hardware perspective** – It eliminates the need to analyze which system specifications you need to upgrade.
- **Fewer periods of downtime** – Because you’re adding a machine, you don’t have to switch the old machine off while scaling. 
- **Increased resilience and fault tolerance** –  Distributing data among several nodes saves you from losing it all.
- **Increased performance** – If you are using horizontal scaling to manage your network traffic, it allows for more endpoints for connections, considering that the load will be delegated among multiple machines.
## Disadvantages of horizontal scaling

- **Increased complexity of maintenance and operation** – Multiple servers are harder to maintain than a single server is. Additionally, you will need to add software for load balancing and possibly virtualization. Backing up your machines may also become a little more complex. You will need to ensure that nodes synchronize and communicate effectively.
- **Increased Initial costs** – Adding new servers is far more expensive than upgrading old ones.


---
# Vertical Scaling (Scaling up/down)

Vertical scaling describes adding more power to your current machines. 

For instance, if your server requires more processing power, vertical scaling would mean upgrading the CPUs. You can also vertically scale the memory, storage, or network speed.

Additionally, vertical scaling may also describe replacing a server entirely or moving a server’s workload to an upgraded one.

## Advantages of vertical scaling

- **Cost-effective** – Upgrading a pre-existing server costs less than purchasing a new one.
- **Less complex process communication** – When a single node handles all the layers of your services, it will not have to synchronize and communicate with other machines to work. This may result in faster responses.
- **Less complicated maintenance** – Not only is maintenance cheaper but it is less complex because of the number of nodes you will need to manage.
## Disadvantages of vertical scaling

- **Higher possibility for downtime** – You will need some considerable downtime to upgrade your machine.
- **Single point of failure** – Risk of losing all your data if a hardware or software failure was to occur.
- **Upgrade limitations** – Every machine has its threshold for RAM, storage, and processing power.


### Use vertical scaling when:

- You’ve verified with your engineers and other stakeholders that increasing a machines capabilities, such CPUs and memory capacity, will deliver the price-performance level your workloads require
- If you’re just starting out; you don’t know how consistent the traffic is or how many users you’ll get
- Want to use your existing system internally and a cloud provider services for the bulk of customer-facing solutions
- Upgrades are few and far between, so there is little downtime to worry about
- You have a legacy app that doesn’t require distributed or high scalability

### Use horizontal scaling when:

- Providing high-quality service requires high performance
- Backup machines are necessary to reduce single points of failure
- You need to run your application or services across different geographical locations at low latency
- Updating, upgrading, and optimizing your system regularly is imperative — all without increasing downtime
- You are sure that your usage, users, or traffic are consistently high or will be growing exponentially soon
- You have the people and resources to buy, install, and maintain additional hardware and software
- You are using a micro-services architecture or containerized applications, which achieve better performance on a distributed system