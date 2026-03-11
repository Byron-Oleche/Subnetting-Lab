## Subnetting Lab

# Small Business Network Design – HR & IT Departments

## Objective
I designed a network in Cisco Packet Tracer connecting the HR and IT departments
of a small business, allowing both departments to communicate through a central router.

## Skills Learned
- IP addressing and subnetting
- Router and switch configuration
- Selecting the correct cable types
- Configuring IP addresses on end devices including printers
- Testing connectivity using ping

## Tools Used
- Cisco Packet Tracer

---

## Scenario
A small business needed their HR and IT departments connected on the same network.
I was given the network address 192.168.20.0 and tasked with subnetting it,
configuring all devices including networked printers, and verifying communication
between both departments.

---

## Network Design

I split the network into two subnets:
- HR Department  → 192.168.20.0/26
- IT Department  → 192.168.20.64/26

Devices I used:
- 1 Router (Cisco 2911)
- 2 Switches (Cisco 2960)
- 4 PCs (2 per department)
- 2 Printers (1 per department)

---

## Steps

### Step 1 – Built the Topology
I added a router, two switches, four PCs and two printers to the workspace
and arranged them by department.

<img width="702" height="360" alt="Step1" src="https://github.com/user-attachments/assets/e38d99d5-6d20-4f02-bb2d-ecdfe3c52477" />

### Step 2 – Connected the Devices
I used straight-through cables to connect each PC and printer to its
department switch, then connected each switch to the router.

<img width="757" height="445" alt="Step2" src="https://github.com/user-attachments/assets/dc4ea7b2-bce0-4b40-b5ab-fe21d6a7df76" />

### Step 3 – Calculated the Subnets
I was given the network address 192.168.20.0 and needed two subnets,
one for HR and one for IT. Each subnet needed to support at least 3 devices
(2 PCs and 1 printer).

Used a /26 prefix which gives 62 usable hosts per subnet, more than enough
for each department.

HR Department → 192.168.20.0/26
- Network:   192.168.20.0
- Gateway:   192.168.20.1
- Usable:    192.168.20.2 – 192.168.20.62
- Broadcast: 192.168.20.63

IT Department → 192.168.20.64/26
- Network:   192.168.20.64
- Gateway:   192.168.20.65
- Usable:    192.168.20.66 – 192.168.20.126
- Broadcast: 192.168.20.127
  
### Step 4 – Configured the Router
I went into the router CLI and assigned IP addresses to both interfaces
then brought them up with no shutdown.

<img width="654" height="516" alt="Step4" src="https://github.com/user-attachments/assets/59fa2cea-fd8c-4f29-812e-835625677088" />

<img width="661" height="433" alt="Step4 1" src="https://github.com/user-attachments/assets/57d1f570-4a26-4e86-b234-e3f93d76a43f" />


### Step 5 – Configured the PCs and Printers
I manually assigned each device its IP address, subnet mask, and default
gateway through the desktop settings.

HR Department:
- HR-PC1:      192.168.20.2  | Mask 255.255.255.192 | Gateway 192.168.20.1
- HR-PC2:      192.168.20.3  | Mask 255.255.255.192 | Gateway 192.168.20.1
- HR-Printer:  192.168.20.4  | Mask 255.255.255.192 | Gateway 192.168.20.1

IT Department:
- IT-PC1:      192.168.20.66 | Mask 255.255.255.192 | Gateway 192.168.20.65
- IT-PC2:      192.168.20.67 | Mask 255.255.255.192 | Gateway 192.168.20.65
- IT-Printer:  192.168.20.68 | Mask 255.255.255.192 | Gateway 192.168.20.65

  This is one example
  <img width="470" height="401" alt="Step5" src="https://github.com/user-attachments/assets/f7ac5d95-21ad-4480-b8e0-68177cc9be7d" />


### Step 6 – Tested Connectivity
I opened the command prompt on IT-PC1 and pinged HR-PC1 and the HR-Printer.
Both pings were successful, confirming full communication across departments.

<img width="464" height="407" alt="SuccessFul" src="https://github.com/user-attachments/assets/8c246458-2aa7-4613-b279-5613f4e15488" />


---

## Outcome
Both departments are fully connected with shared networked printers. All PCs
and printers can reach each other through the router.
