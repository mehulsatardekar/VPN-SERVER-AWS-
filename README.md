# VPN-SERVER-AWS- 
## Setting up vpn(virtual-private-network) using Amazon's aws cloud service.

**So before we begin we will understand what vpn is and why do start using it:** :collision: :man_technologist:

> **A VPN, or Virtual Private Network**, allows you to create a secure connection to another network over the Internet. VPNs can be used to access region-restricted websites, shield your browsing activity from prying eyes on public Wi-Fi, and more.They originally were just a way to connect business networks together securely over the internet or allow you to access a business network from home.**VPNs** essentially forward all your network traffic to the network, which is where the benefits – like accessing local network resources remotely and bypassing Internet censorship – all come from. Most operating systems have integrated **VPN** support.

**How Does It Help Me?** :grinning: :thinking:

>In very simple terms, a VPN connects your PC, smartphone, or tablet to another computer (called a server) somewhere on the internet, and allows you to browse the internet using that computer’s internet connection. So if that server is in a different country, it will appear as if you are coming from that country, and you can potentially access things that you couldn’t normally.

**So how does this help you? Good question! You can use a VPN to**:

- Bypass geographic restrictions on websites or streaming audio and video.
- Watch streaming media like Netflix and Hulu.
- Protect yourself from snooping on untrustworthy Wi-Fi hotspots.
- Gain at least some anonymity online by hiding your true location.
- Protect yourself from being logged while torrenting.

**So I thought how hard can it be to setup a VPN server (because I didn't want to pay $5 per month) for a web developer.  I found out you could easily do this on [AWS (Amazon Web Services) ](http://https://aws.amazon.com/console/ "AWS (Amazon Web Services) ")for free using [OpenVPN](http://https://openvpn.net/ "OpenVPN"). I started setting it up and a couple of mins later I had it up and running.**

------------


**openvpn** is a popular open-source tool that is well tested and give you a production ready VPN solution. :earth_asia:

# **AWS console**
if you don't  have an account on aws (amazon web services), go ahead and create one. it's free, but you will need to have your credit card info handy.

once signed up, login and under the services menu look for ec2 (you can type and it will filter the services as you type).

<img src="https://raw.githubusercontent.com/mehulsatardekar/VPN-SERVER-AWS-/master/Desktop/aws-pics/1.png" alt="drawing" style="width:400px;"/>

**Click on EC2 and you will be redirected to its dashboard. Click launch instance button under create instance section.**

# Select the OpenVPN

**Once in the dashboard, click AWS Marketplace menu from left and type OpenVPN, then press enter.**

<img src="https://raw.githubusercontent.com/mehulsatardekar/VPN-SERVER-AWS-/master/Desktop/aws-pics/3.png" alt="drawing" style="width:400px;"/>

**Click on select button on the first one with the free tier eligible badge.**</br>

# Selecting instance type

**On the next page click continue and select t2.micro from instance type list.**</br>
<img src="https://raw.githubusercontent.com/mehulsatardekar/VPN-SERVER-AWS-/master/Desktop/aws-pics/5.png" alt="drawing" style="width:400px;"/>

**make sure you allow protocols rules as per your choice**

<img src="https://raw.githubusercontent.com/mehulsatardekar/VPN-SERVER-AWS-/master/Desktop/aws-pics/8.png" alt="drawing" style="width:400px;"/>

**At this stage click on Review and Launch button.**

# Launch the instance

**Select general purpose SSD from the pop up and click next. Now click Launch and you'll see a pop up asking you to select a key pair. This is to let you access the instance later on.**

<img src="https://raw.githubusercontent.com/mehulsatardekar/VPN-SERVER-AWS-/master/Desktop/aws-pics/11.png" alt="drawing" style="width:400px;"/>

**Select create a new key pair (or an existing if you already have one), enter a name and click download key pair.**

**Save the .pem file somewhere safe as this is like a back door to your server :smile:. Click Launch Instance and wait for the instance to go to running state.**

**Click on view instance to see the instance list.**

<img src="https://raw.githubusercontent.com/mehulsatardekar/VPN-SERVER-AWS-/master/Desktop/aws-pics/12.png" alt="drawing" style="width:400px;"/>

**Select your instance and click connect.**

# **Preparation**

**You'll see a set of instructions on a popup on how to connect to your instance.**

<img src="https://raw.githubusercontent.com/mehulsatardekar/VPN-SERVER-AWS-/master/Desktop/aws-pics/14.png" alt="drawing" style="width:400px;"/>


**I already have Ubuntu set up i and we can use that. Otherwise you can use PuTTY or even the web browser connection.**

**Before we do anything we need to set the permissions for our private key 👉🏽 .pem 👈🏽 file, otherwise it wouldn't allow you to connect. If you're using a Linux or Mac machine, simply run the following command:**

**For the rest of you who are like me, right click on the .pem file and click SECURITY > ADVANCE. Then change the owner to yourself, click disable inheritance and remove all permissions. Click add and add yourself and give full control**

# Connecting

**Once that's done, open a command prompt, type bash and then enter the following command:**

> **SUDO SSH -I "{NAME-OF-FILE}.PEM" OPENVPNAS@{SERVERADDRESS}.COMPUTE.AMAZONAWS.COM**

**Don't forget to replace the file name with whatever you've chosen previously and replace the name of server with what you got from the instruction popup.**

**Type yes for the agreement, then just hit enter to have all the defaults confirmed. Once you reached to the end, change the password for the user which will be used to login:**
  
>  **sudo passwd openvpn**

**Enter a new password twice and you're all set. Open a browser window and type   https://{server address}:943/admin  and login with openvpn and the password you just set.**

# Finish up a few settings

**Once in the admin dashboard of OpenVPN, click configuration and apply the following changes:**


 - Change the toggle for Should client Internet traffic be routed through the VPN? to **Yes**
-   Change the toggle for Have clients use specific DNS servers to Yes
-   Select custom DNS server and set the first box to **1.1.1.1** (CloudFlare DNS 🦄) and the second to **8.8.8.8**

**Now save the settings, wait for the pop up on the top and click apply the changes to server.**

# You're good to go :trophy:

**You're all set. You can now connect to your very own VPN server and enjoy a private surf of the net 😎. On the first page of the browser window you opened earlier, there are five options to download the OpenVPN client for different platform. If you click on windows, you will get an installer with your server address pre-configured. Just enter your user name and password and boom.**

**YOU CAN CONNECT TO THE MOBILE ALSO JUST PASSED THE OVPN KEY TO OPENVPN MOBILE APP AND SET THE CONFIGURATION AND THERE YOU GO.. or more info about connecting to mobile read it on openvpn client how to connect openvpn to the mobile.**

:rocket: **if you like please star my github repo** :star2: :fire:
