# Static-routing
CCNA lab 
==========================
Static Routing
-----------------------
Confifure IP addrees R1,R2,R3,R4 and R5
======================================
R1
-----------
en
conf t
int fa0/0
ip add 10.0.0.1 255.255.255.0
no shut
int fa0/1
ip add 10.0.1.1 255.255.255.0
no shut
int fa1/0
ip add 10.0.2.1 255.255.255.0
no shut
int fa1/1
ip add 10.0.3.1 255.255.255.0
no shut
end
wr

R2
-----------
en
conf t
int fa0/0
ip add 10.0.0.2 255.255.255.0
no shut
int fa0/1
ip add 10.1.0.2 255.255.255.0
no shut

R3
-------------
en
conf t
int fa0/1
ip add 10.1.0.1 255.255.255.0
no shut
int fa0/0
ip add 10.1.1.2 255.255.255.0
no shut

R4
-----------
en
conf t
int fa0/0
ip add 10.1.1.1 255.255.255.0
no shut
int fa0/1
ip add 10.1.2.1 255.255.255.0
no shut
int fa1/0
ip add 10.1.3.1 255.255.255.0
no shut
int fa1/1
ipp add 203.0.113.1 255.255.255.0
no shut
end
wr

R5
----------
en
conf t
int fa0/1
ip add 10.1.3.2 255.255.255.0
no shut
int fa0/0
ipp add 10.0.3.2 255.255.255.0
no shut 
end 
wr


Configure static routes all Rs
allow to connect all networks
================================
R1
------------
en 
conf t
ip route 10.1.0.0 255.255.255.0 10.0.0.2
ip route 10.1.1.0 255.255.255.0 10.0.0.2
ip route 10.1.2.0 255.255.255.0 10.0.0.2
ip route 10.1.3.0 255.255.255.0 10.0.0.2
do wr
R2
------------
en 
conf t
ip route 10.0.1.0 255.255.255.0 10.0.0.1
ip route 10.0.2.0 255.255.255.0 10.0.0.1
ip route 10.1.1.0 255.255.255.0 10.0.0.1
ip route 10.1.2.0 255.255.255.0 10.1.0.0
ip route 10.1.3.0 255.255.255.0 10.1.0.0
ip route 10.0.3.0 255.255.255.0 10.0.0.1
ip route 203.0.113.0 255.255.255.0 10.1.0.0
do wr

R3
--------------
ip route 10.0.0.0 255.255.255.0 10.1.1.1
ip route 10.0.1.0 255.255.255.0 10.1.1.1
ip route 10.0.2.0 255.255.255.0 10.1.1.1
ip route 10.0.3.0 255.255.255.0 10.1.1.1
ip route 10.1.3.0 255.255.255.0 10.1.1.1
ip route 10.1.2.0 255.255.255.0 10.1.1.1
ip route 203.0.113.0 255.255.255.0 10.1.1.1
do wr

R4
--------------------------
p route 10.0.0.0 255.255.255.0 10.1.1.2
ip route 10.0.1.0 255.255.255.0 10.1.1.2
ip route 10.0.2.0 255.255.255.0 10.1.1.2
ip route 10.0.3.0 255.255.255.0 10.1.1.2
ip route 10.1.0.0 255.255.255.0 10.1.1.2
Ip route 10.0.1.0 255.255.255.0 10.1.3.2
ip route 10.0.2.0 255.255.255.0 10.1.3.2
do wr

R5
-------------------
ip route 10.1.2.0 255.255.255.0 10.1.3.1
ip route 203.0.113.0 255.255.255.0 10.1.3.1
ip route 10.1.1.0 255.255.255.0 10.1.3.1
ip route 10.0.1.0 255.255.255.0 10.0.3.1
ip route 10.0.2.0 255.255.255.0 10.0.3.1
ip route 10.1.0.0 255.255.255.0 10.1.3.1
ip route 10.0.0.0 255.255.255.0 10.0.3.1
do wr

Verify Connectivity between PC1,PC2 and PC3
 and verify the phat traffic takes>
============================================
ping 10.1.2.10 from PC1


To reach the ISP connected on R4 set Defualt Route
on R1,R2,R3,R4 and R5
====================================================
R1
=========
en 
conf t
ip route 0.0.0.0 0.0.0.0 10.0.0.2
ip route 0.0.0.0 0.0.0.0 10.0.3.2
do wr

R2
=========
en 
conf t
ip route 0.0.0.0 0.0.0.0 10.1.0.1
do wr

R3
=========
en 
conf t
ip route 0.0.0.0 0.0.0.0 10.1.1.1
do wr

R4
=========
en 
conf t
ip route 0.0.0.0 0.0.0.0 203.0.113.2
do wr

R5
=========
en 
conf t
ip route 0.0.0.0 0.0.0.0 10.1.3.1
do wr


Check every Router
==============

Show ip route
