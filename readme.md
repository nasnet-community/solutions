<!-----

You have some errors, warnings, or alerts. If you are using reckless mode, turn it off to see inline alerts.
* ERRORs: 0
* WARNINGs: 0
* ALERTS: 51

Conversion time: 15.283 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β36
* Wed Jul 10 2024 07:33:03 GMT-0700 (PDT)
* Source doc: OpenVPN on Mikrotik - 30.06.2024 
* This document has images: check for >>>>>  gd2md-html alert:  inline image link in generated source and store images to your server. NOTE: Images in exported zip file from Google Docs may not appear in  the same order as they do in your doc. Please check the images!

----->


<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 0; ALERTS: 51.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>
<a href="#gdcalert3">alert3</a>
<a href="#gdcalert4">alert4</a>
<a href="#gdcalert5">alert5</a>
<a href="#gdcalert6">alert6</a>
<a href="#gdcalert7">alert7</a>
<a href="#gdcalert8">alert8</a>
<a href="#gdcalert9">alert9</a>
<a href="#gdcalert10">alert10</a>
<a href="#gdcalert11">alert11</a>
<a href="#gdcalert12">alert12</a>
<a href="#gdcalert13">alert13</a>
<a href="#gdcalert14">alert14</a>
<a href="#gdcalert15">alert15</a>
<a href="#gdcalert16">alert16</a>
<a href="#gdcalert17">alert17</a>
<a href="#gdcalert18">alert18</a>
<a href="#gdcalert19">alert19</a>
<a href="#gdcalert20">alert20</a>
<a href="#gdcalert21">alert21</a>
<a href="#gdcalert22">alert22</a>
<a href="#gdcalert23">alert23</a>
<a href="#gdcalert24">alert24</a>
<a href="#gdcalert25">alert25</a>
<a href="#gdcalert26">alert26</a>
<a href="#gdcalert27">alert27</a>
<a href="#gdcalert28">alert28</a>
<a href="#gdcalert29">alert29</a>
<a href="#gdcalert30">alert30</a>
<a href="#gdcalert31">alert31</a>
<a href="#gdcalert32">alert32</a>
<a href="#gdcalert33">alert33</a>
<a href="#gdcalert34">alert34</a>
<a href="#gdcalert35">alert35</a>
<a href="#gdcalert36">alert36</a>
<a href="#gdcalert37">alert37</a>
<a href="#gdcalert38">alert38</a>
<a href="#gdcalert39">alert39</a>
<a href="#gdcalert40">alert40</a>
<a href="#gdcalert41">alert41</a>
<a href="#gdcalert42">alert42</a>
<a href="#gdcalert43">alert43</a>
<a href="#gdcalert44">alert44</a>
<a href="#gdcalert45">alert45</a>
<a href="#gdcalert46">alert46</a>
<a href="#gdcalert47">alert47</a>
<a href="#gdcalert48">alert48</a>
<a href="#gdcalert49">alert49</a>
<a href="#gdcalert50">alert50</a>
<a href="#gdcalert51">alert51</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>



# Bypassing Iranian Internet Censorship 


## A Comprehensive Guide to Using Starlink, Mikrotik Router, and OpenVPN for Secure Remote Access


## Introduction

This document provides a step-by-step guide for installing and configuring the OpenVPN service on a Mikrotik router. The main goal is to create a **secure** tunnel to Starlink, allowing **multiple users** to access **uncensored** Starlink internet through OpenVPN from with** no geographical restrictions** while connected to the internal Iranian network. While this method can be applied to other routers, we strongly recommend using the specified devices.


### Glossary



* **Host**: The person who owns, installs and configures the Starlink connection.
* **User**: The person who remotely connects to Starlink using OpenVPN.
* **Host Modem**: The modem that manages traffic between the internal Iranian network and the Mikrotik router.


### Objectives and Setup Steps



1. **Connecting Users to the Host Modem via Internal Internet**: Users can connect to the host modem through the internal internet using an OpenVPN client. This ensures all traffic between the user and the host is encrypted. The steps for this phase are marked in the manual.
2. **Forwarding User Requests to the Mikrotik Router**: Requests from users are transmitted from the host modem to the Mikrotik router.
3. **Split Tunneling on the Mikrotik Router**:
    * **Internal Requests**: These are routed back to the host modem and sent through the internal internet network.
    * **International Requests**: These are directed to Starlink and the global internet network.
4. **Hiding Starlink IP**: The Starlink IP is concealed using a VPS, which is positioned after the Starlink connection. Mikrotik routers are not compatible with VPNs like NordVPN or ExpressVPN.


### Benefits of Following All Steps



* **Access to Internal Services**: Users can access internal services and satellite internet without being identified or having to turn on/off his VPN.
* **Hiding Starlink IP**: The Starlink IP is hidden from users.
* **Simultaneous Use by Multiple Users**: This method allows multiple users to use the Starlink internet at the same time.
* **No Geographical Restrictions**: Users can connect to Starlink from any location.


### Can I Skip Some Steps?

It's recommended to follow all steps carefully. However, if security is less of a concern for you, you can skip the following steps:



* **Skip Split Tunneling**: If you don't want to separate Iranian and international traffic, you can skip the split tunneling steps. But if you do, users will need to turn off their VPN whenever they want to access internal services like banking, since the Starlink IP is non-Iranian.
* **Skip Hiding Starlink IP**: If you don't want to hide the Starlink IP, you can skip these steps. Proper split tunneling makes hiding the IP less critical, but there is a high risk that internal services might detect Starlink usage. Also, users will know they're connected to a Starlink device.
* **Skip Static IP**: You can skip obtaining a static IP, though it means you'll need to update your Mikrotik router configuration more frequently. Without a static IP, if the host modem is off for several hours or the ISP changes the IP, you'll have to update configurations. This usually happens every few months, so having a static IP is not essential.
* **Starlink Device Generation**: This manual is designed for Starlink generations 1 and 2, which usually don't have an adapter in Iran. Users with an adapter or using generation 3 and beyond can connect their Starlink directly to the Mikrotik router via cable, avoiding the WiFi setup steps in this manual. However, completing these steps will allow for wireless connection of the Starlink router to the Mikrotik router.


### **Disadvantages of This Method**



* **Complex Setup**: This method requires precision and skill for setup. It's recommended to use the suggested methods and devices.
* **Need for a Static IP**: The host needs to use a static IP. However, if you can inform users of the new IP whenever it changes, a static IP is not strictly necessary.
* **Increased Internet Usage for Host**: This method will increase the host's internet usage. (Costs can be shared among users, making this method more cost-effective and faster than a normal VPN.)


### **Recommendations**

Depending on your familiarity with networking, OpenVPN, and Mikrotik routers, allocate between 2 hours to 3 days for installing and setting up this system. We recommend using the suggested software, tools, and devices to achieve your desired results more quickly and reliably. If you use other methods or tools, please share your experiences on our forums to help others benefit from different approaches. Our goal is to enhance the knowledge and literature around this topic.


### **Required Tools and Equipment**



* Mikrotik router hap ax2
* Modem and static IP
* Starlink modem and receiver
* VPS with Mikrotik OS v7.x to hide the Starlink IP (optional)
* 2 LAN cables
* Windows PC/laptop
* [Mikrotik Winbox](https://mikrotik.com/download)
* A note-taking tool


### **Topology**


## <p dir="rtl">


<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image1.png" width="" alt="alt_text" title="image_tooltip">
</p>



## Setup



1. Install the Winbox application. We do not recommend using web applications since they might have different default configurations.
2. Connect one of the yellow ports on your ADSL modem to the Lan2 port on the Mikrotik router. Please do not change this port or plug the cable into another port during the setup.
3. Connect the Lan3 port on the Mikrotik router to your computer. Again, do not change this port or plug the cable into another port during the setup.


### **Connect**



* Connect to: 192.168.88.1
* Login: (found on your Mikrotik router)
* Password: (found on your Mikrotik router)
* Click on Connect.
* On your first login, you may be prompted to change your password. Choose a password that is easy to type, as you will need to enter it multiple times in Winbox during the setup.
* Go to the Setting Menu and deselect Hide Password (to make things easier).


#### Milestone 1

If you have trouble logging in, you can find the IP 192.168.88.1 under the Neighbors tab and log in from there.

If this IP does not appear in the neighbors list, please physically reset the router and try again.

Sometimes the IP might not work, and you need to click on the MAC Address column record to replace the IP with the MAC address in the Connect To field. The MAC address associated with IP 192.168.88.1 is obscured in this image.



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")



### **Remove Slave from Interface**

<span style="text-decoration:underline;">In some routers</span>, `wifi2` or `ether2` are set as slaves by default. This setting needs to be disabled.



* Go to **Bridge** (left menu) -> **Ports**
* For `ether2`: Right-click and select **Remove**
* For `wifi2`: Right-click and select **Remove**

**Note**: <span style="text-decoration:underline;">In some cases</span>, `wifi2` and `ether2` might not be listed under Ports. If this is the case, you can proceed to the next step.


#### Milestone 2

If `ether2` and `wifi2` are listed here and you still have internet through LAN despite turning off your WiFi, removing `ether2` and `wifi2` should disconnect your LAN internet.



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")



#### Backup

We recommend creating a backup of your settings after each step. To do this:



* Go to **Files** -> **Backup**


## Wireless and Ethernet Interfaces

In this section, we will create two interfaces: a WiFi interface as a WiFi Station to connect to the Starlink modem and an Ethernet interface to connect to the host modem with a static IP.


### WiFi Station Setup in MikroTik Wireless Router

By enabling Wireless Station Mode, we can set up the WiFi Client. To enable Wireless Station Mode, follow these two steps:


#### DHCP Client Configuration on Wireless Interface



* Go to **IP** -> **DHCP Client** -> click **+** (new)
    * Interface: `wifi2`
    * Use Peer DNS: ✅
    * Use Peer NTP: ✅
    * Add Default Route: No



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image4.png "image_tooltip")



#### Wireless Station Configuration on Wireless Interface

Configure the Wireless Station to connect to the Starlink WiFi SSID:



* Go to **Interfaces** -> Right-click on `wifi2` and enable -> double-click `wifi2` to open -> **General Tab**
    * Mode: `Station`



<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image5.png "image_tooltip")




* Go to **Security Tab**
    * Authentication Type: `WPA PSK`, `WPA2 PSK`
    * Passphrase: Your Starlink Password
    * Click **Apply**



<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image6.png "image_tooltip")




* Click **Scan**
    * Interface: `wifi2`
    * Click **Start**
    * Select your SSID (Starlink)
    * Click **Connect**



<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image7.png "image_tooltip")



#### Milestone 3

If you have followed the steps correctly, the status of `wifi2` should show as `RMB` or `RSMB`. The letter `R` in the status column indicates that the interface is running.



<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image8.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image8.png "image_tooltip")



### **Ethernet Interface Setup**


#### Connect the Ethernet port to your host modem



* Go to **Interface** -> **Interface Tab** -> right-click on `ether2` and select **Enable**.



<p id="gdcalert9" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image9.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert10">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image9.png "image_tooltip")



#### DHCP Client for Ethernet Interface



* Go to **IP** -> **DHCP Client** -> click **+** (new).
* In the **DHCP Tab**:
    * Interface: `ether2`
    * Use Peer DNS: ✅
    * Use Peer NTP: ✅
    * Add Default Route: No



<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image10.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert11">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image10.png "image_tooltip")



### NAT Setup

Here we will define rules for two NATs, one for `wifi2` and one for `ethernet2`. The source NAT will be the VPN-Pool Addresses.


#### NAT for Ethernet Interface



* Go to **IP** -> **Firewall** -> **NAT Tab** -> click **+** (new).
* In the **General Tab**:
    * Chain: `srcnat`
    * Src. Address: `10.100.0.0/24`
    * Out. Interface: `ether2`



<p id="gdcalert11" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image11.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert12">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image11.png "image_tooltip")




* Go to the **Action Tab**:
    * Action: `Masquerade`
    * Click **OK**.



<p id="gdcalert12" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image12.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert13">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image12.png "image_tooltip")
 \



#### NAT for WiFi Interface



* Go to **IP** -> **Firewall** -> **NAT Tab** -> click **+** (new).
* In the **General Tab**:
    * Chain: `srcnat`
    * Src. Address: `10.100.0.0/24`
    * Out. Interface: `wifi2`
* Go to the **Action Tab**:
    * Action: `Masquerade`
    * Click **OK**.


## OpenVPN Server on MikroTik

Now we need to set up the OpenVPN Server on MikroTik.


### VPN Pool Setup


#### Create an IP pool for VPN clients:



* Go to **IP** -> **Pool** -> **Pools Tab** -> click **+** (new).
    * Name: `vpn-pool`
    * Addresses: `10.100.0.2-10.100.0.254`
    * Next Pool: `none`
    * Click **OK**.



<p id="gdcalert13" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image13.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert14">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image13.png "image_tooltip")



#### Create PPP Profile



* Go to **PPP** -> **Profiles Tab** -> click **+** (new).
* In the **General Tab**:
    * Name: `Openvpn` (or any preferred name)
    * Local Address: `10.100.0.1`
    * Remote Address: `vpn-pool`
    * DNS: `8.8.8.8` (or any other DNS server)
    * Click **OK**.



<p id="gdcalert14" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image14.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert15">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image14.png "image_tooltip")



#### Create VPN User



* Go to **PPP** -> **Secrets Tab** -> click **+** (new)
    * Name: `JooJoo` (or any preferred name)
    * Password: Enter a password.
    * Service: `ovpn`
    * Profile: `Openvpn`
    * Click **OK**.



<p id="gdcalert15" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image15.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert16">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image15.png "image_tooltip")



#### Create Certificates


##### Create CA Certificate



* Go to **System** -> **Certificates** -> **Certificates Tab** -> click **+** (new).
* In the **General Tab**:
    * Name: `CA`
    * Common Name: `CA`
    * Key Size: `2048`
    * Days Valid: `3650` (or your preferred duration)



<p id="gdcalert16" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image16.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert17">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image16.png "image_tooltip")




* In the **Key Usage Tab**:
    * Enable `key cert. sign` and `crl sign`.
    * Uncheck other options.
    * Click **OK**.



<p id="gdcalert17" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image17.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert18">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image17.png "image_tooltip")



##### Create Server Certificate



* Go to **System** -> **Certificates** -> **Certificates Tab** -> click **+** (new).
* In the **General Tab**:
    * Name: `Server`
    * Common Name: `Server`
    * Key Size: `2048`
    * Days Valid: `3650`



<p id="gdcalert18" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image18.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert19">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image18.png "image_tooltip")




* In the **Key Usage Tab**:
    * Enable `digital signature`, `key encipherment`, and `tls server`.
    * Uncheck other options.
    * Click **OK**.



<p id="gdcalert19" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image19.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert20">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image19.png "image_tooltip")



##### Create Client Certificate



* Go to **System** -> **Certificates** -> **Certificates Tab** -> click **+** (new).
* In the **General Tab**:
    * Name: `Client`
    * Common Name: `Client`
    * Key Size: `2048`
    * Days Valid: `3650`



<p id="gdcalert20" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image20.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert21">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image20.png "image_tooltip")




* In the **Key Usage Tab**:
    * Enable `tls client`.
    * Uncheck other options.
    * Click **OK**.



<p id="gdcalert21" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image21.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert22">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image21.png "image_tooltip")



#### Signing the Certificates


##### Signing the CA Certificate



* Go to **System** -> **Certificates** -> **Certificates Tab**.
    * Select `CA`
* Click **Sign**.
    * Certificate: `CA`
    * Click **Start** (this may take some time).



<p id="gdcalert22" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image22.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert23">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image22.png "image_tooltip")



##### Signing the Server Certificate



* Go to **System** -> **Certificates** -> **Certificates Tab**.
    * Select `Server`
* Click **Sign**.
    * Certificate: `Server`
    * CA: `CA`
    * Click **Start**.



<p id="gdcalert23" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image23.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert24">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image23.png "image_tooltip")



##### Signing the Client Certificate



* Go to **System** -> **Certificates** -> **Certificates Tab**.
    * Select `Client`
* Click **Sign**.
    * Certificate: `Client`
    * CA: `CA`
    * Click **Start**.



<p id="gdcalert24" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image24.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert25">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image24.png "image_tooltip")



##### Trusting the Certificates



* Go to **System** -> **Certificates** -> **Certificates Tab**.
* Select `CA`, `Server`, and `Client` (one by one).
    * Check the **Trusted** box for each.



<p id="gdcalert25" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image25.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert26">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image25.png "image_tooltip")



### **OpenVPN Server Interface Setup**



* Go to **PPP** -> **Interface Tab** -> **OVPN Server**.
    * Enabled: ✅
    * Port: `1194` (or another free port)
    * Mode: `ip` (This is for layer 3 VPN. For layer 2 VPN, select `ethernet`.)
    * Protocol: `tcp` (UDP is not recommended)
    * Netmask: `24` (CIDR netmask for your LAN subnet)
    * Default Profile: `Openvpn`
    * Certificate: `Server`
    * Uncheck "Require Client Certificate": ❌
    * Authentication: Check `sha1` ✅ and uncheck others ❌
    * Cipher: Check `aes 128 cbc`, `aes 192 cbc`, and `aes 256 cbc` ✅ and uncheck others ❌
    * Click **OK**.

This will configure and enable the OpenVPN server interface on your MikroTik router.


### Exporting the Certificates


#### Exporting the CA Certificate



* Go to **System** -> **Certificates** -> **Certificates Tab**.
    * Select `CA`.
* Click **Export** (leave the passphrase blank).
    * Click **Export** on the new window.



<p id="gdcalert26" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image26.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert27">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image26.png "image_tooltip")



#### Exporting the Client Certificate



* Go to **System** -> **Certificates** -> **Certificates Tab**.
    * Select `Client`.
* Click **Export**.
    * Enter an export passphrase. This passphrase will be needed later to create the OpenVPN file.
    * Click **Export** again to confirm.



<p id="gdcalert27" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image27.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert28">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image27.png "image_tooltip")



#### Transferring the Files



* Go to **Files** and select the three certificate files. Their names should be similar to:
    * `cert_export_CA.crt` (or `CA.crt`)
    * `cert_export_Client.crt` (or `Client.crt`)
    * `cert_export_Client.key` (or `Client.key`)
* Right-click on each file and download them.

<p dir="rtl">


<p id="gdcalert28" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image28.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert29">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image28.png" width="" alt="alt_text" title="image_tooltip">
</p>


**Recommendation**: It's a good idea to click the **Backup** button and create a backup of the settings you've configured so far.


### Create Client Ovpn File


#### Removing the Passphrase from the Client Key



1. **Download and Install OpenSSL**
    * If you are using Windows, download OpenSSL from a trusted source, such as [this website](https://slproweb.com/products/Win32OpenSSL.html).
    * Install OpenSSL.
2. **Navigate to the Folder with the OpenVPN Files**
    * Go to the folder where you downloaded the OpenVPN files in the previous step.
    * Copy the folder path. (For example, by right clicking on the address bar and selecting copy address)

<p dir="rtl">


<p id="gdcalert29" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image29.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert30">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image29.png" width="" alt="alt_text" title="image_tooltip">
</p>




3. **Open OpenSSL**
    * Use the `cd` command to navigate to the folder with the OpenVPN files. For example: \
`cd C:\Users\XXXX\Desktop\OpenVPN`
    * Replace `XXXX` with your actual username in Windows.
4. **Run OpenSSL to Remove the Passphrase**
    * In the Command Prompt, enter the following command (replace `cert_export_Client.key` with your actual file name): \
`openssl rsa -in cert_export_Client.key -out client.key`
    * When prompted, enter the passphrase you previously set for the `Client` file.
    * This will create a new `client.key` file without the passphrase.



<p id="gdcalert30" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image30.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert31">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image30.png "image_tooltip")



#### **_For Linux Users_**



1. **_Install OpenSSL:_**
    * _Install OpenSSL if it's not already installed._
2. **_Import the Client Key:_**
    * _Move the <code>cert_export_Client.key</code> file to your Linux root directory.</em>
    * <em>Run the following command to remove the passphrase: \
<code>openssl rsa -in cert_export_Client.key -out client.key</code></em>
    * <em>When prompted, enter the passphrase you previously set for the <code>Client</code> file.</em>
    * <em>This will create a new <code>client.key</code> file without the passphrase.</em>


#### <strong>Creating the Client OVPN File</strong>



1. **Create a New File**:
    * Go to the folder with the OpenVPN files.
    * Right-click and create a new text file.

<p dir="rtl">


<p id="gdcalert31" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image31.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert32">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image31.png" width="" alt="alt_text" title="image_tooltip">
</p>




    * Rename this file to `client.ovpn`. If using Windows, change the file extension from `.txt` to `.ovpn` using the Command Line.

<p dir="rtl">


<p id="gdcalert32" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image32.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert33">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image32.png" width="" alt="alt_text" title="image_tooltip">
</p>




2. **Edit the OVPN File**:
    * Open the `client.ovpn` file with a text editor like Wordpad.
    * Copy and paste the following configuration into the file. Replace `XX.XX.XX.XX` with your static IP address.


```
client
dev tun
proto tcp
remote XX.XX.XX.XX 1194
resolv-retry infinite
nobind
persist-key
persist-tun
cipher AES-256-CBC
auth SHA1
comp-lzo
verb 3
<ca>
-----BEGIN CERTIFICATE-----
(Insert contents of cert_export_CA.crt here)
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
(Insert contents of cert_export_Client.crt here)
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
(Insert contents of client.key here)
-----END PRIVATE KEY-----
</key>

```



3. **Insert Certificate Contents**:
    * Open each certificate file (`cert_export_CA.crt`, `cert_export_Client.crt`, and `client.key`) with a text editor like Wordpad.
    * Copy the contents of each file and paste them into the corresponding sections in the `client.ovpn` file.

Your `client.ovpn` file is now ready to be used with OpenVPN to connect to your Mikrotik router.

Example of a file:



<p id="gdcalert33" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image33.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert34">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image33.png "image_tooltip")



## Split Tunneling


### Routing Configuration

In this section, we will separate internal Iranian traffic from international traffic to ensure:



* Internal services do not detect the use of Starlink.
* There is no need to disconnect the VPN for simultaneous use of internal and international services.

Based on our settings, internal traffic goes to the host modem, and international traffic goes to Starlink.


#### Create a New Routing Table for International Traffic



* Go to **Routing** -> **Tables** -> click **+**.
    * Name: `to-starlink`
    * FIB: ✅
    * Click **OK**.



<p id="gdcalert34" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image34.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert35">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image34.png "image_tooltip")



#### Create Iran Addresses List

Create a list of Iranian IP addresses based on the IP range of Iran.



1. **Download the IP List**:
    * Download the list of Iranian IPs and name it `Iran_IP_List.rsc`. The `.rsc` format is preferred.
2. **Upload the IP List**:
    * Go to **Files** -> **Upload**.



<p id="gdcalert35" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image35.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert36">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image35.png "image_tooltip")




3. **Import the IP List**:
    * Open a new **terminal in your Winbox** and run the following command: \
`import file-name=Iran_IP_List.rsc`

    

<p id="gdcalert36" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image36.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert37">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image36.png "image_tooltip")


4. **Verify the Address List**:
    * Go to **IP** -> **Firewall** -> **Address Lists Tab**.



<p id="gdcalert37" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image37.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert38">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image37.png "image_tooltip")



#### Milestone 4

Ensure that the list of Iranian addresses is correctly registered and looks similar to the provided example.


#### Enable Remarking and Mangle

We will use the Packet Marking feature of Mikrotik routers to implement Policy-based Routing (PBR), which will split traffic based on our criteria. We want to divide traffic between the VPN Tunnel and the internal internet.



* Go to **IP** -> **Firewall** -> **Mangle Tab** -> click **+**.
* **General Tab**:
    * Chain: `prerouting`
    * Src. Address: VPN Client addresses (This IP pool was created during the NAT setup.)
    * Dst Address List: ❗
    * Dst. Address List: `Iran_IP_List`



<p id="gdcalert38" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image38.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert39">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image38.png "image_tooltip")




* **Action Tab**:
    * Action: `mark routing`
    * New Routing Mark: `to-starlink`
    * Passthrough: ✅
    * Click **OK**.



<p id="gdcalert39" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image39.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert40">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image39.png "image_tooltip")



#### Add New Static Routes

Now we need to connect two Static Routes to the WiFi Interface. The first route directs international traffic to Starlink, and the second route directs internal traffic to the host modem.



1. **Static Route to Starlink IP**:
    * Go to **IP** -> **Routes** -> click **+**.
    * **General Tab**:
        * Dst. Address: `0.0.0.0/0` (as a default route)
        * Gateway: `192.168.1.1` (Starlink IP)
        * Distance: `1`
        * Routing Table: `to-starlink`
    * Note: Scope and Target Scope should auto-populate as Scope: 30 and Target Scope: 10.



<p id="gdcalert40" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image40.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert41">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image40.png "image_tooltip")




2. **Static Route to host modem IP**:
    * Go to **IP** -> **Routes** -> click **+**.
    * **General Tab**:
        * Dst. Address: `0.0.0.0/0` (as a default route)
        * Gateway: `192.168.1.5` (host modem IP)
        * Distance: `10` (This number should be greater than 1 to prioritize between Starlink and the internal internet modem)
        * Routing Table: `main`
    * Note: After confirmation, Scope and Target Scope should auto-populate as Scope: 30 and Target Scope: 10.



<p id="gdcalert41" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image41.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert42">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image41.png "image_tooltip")


This completes the configuration for split tunneling, ensuring efficient and seamless usage of both internal and international services without the need for constant VPN disconnections.


## Hiding Starlink IP

To hide the Starlink IP, we will create an additional hub after Starlink to route traffic through another tunnel. We can use two methods:



1. VPS with Mikrotik Router OS
2. Cloudflare Warp

We recommend using Warp as a last resort, as it may disconnect every few hours. If you cannot purchase a secure VPS, Warp can be an alternative.


### Connect to VPS on Mikrotik Router



* After purchasing a VPS, open a new Winbox window. It is recommended to get your VPS from a secure website outside the country.
* Enter the IP, username, and password, then click Connect. (If your VPS doesn’t have a password, create one.)


### L2TP/IPSEC Setup on VPS with Mikrotik Router


#### 
    **Create IP Pool**:



    * Go to **IP** -> **Pool** -> click **+** (new).
    * Name: `vpn-ipsec`
    * Addresses: `192.168.128.1-192.168.128.254`
    * Next Pool: `none`
    * Click **OK**.



<p id="gdcalert42" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image42.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert43">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image42.png "image_tooltip")



#### 
    **Create PPP Profile**:



    * Go to **PPP** -> **Profiles Tab** -> Default Profile.
    * Name: `default`
    * Local Address: Your VPS IP
    * Remote Address: `vpn-ipsec` (the VPN range created earlier)
    * Click **OK**.



<p id="gdcalert43" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image43.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert44">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image43.png "image_tooltip")



#### 
    **Turn on L2TP Server**:



    * Go to **PPP** -> **Interface** -> **L2TP Server**.
    * Enable: ✅
    * Default Profile: `default-encryption` (or use a default option if not available)
    * Use IPsec: `yes` (or required)
    * IPsec Secret: Enter a password (VPN clients will use this password)
    * Click **OK**.



<p id="gdcalert44" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image44.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert45">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image44.png "image_tooltip")



#### 
    **Create VPN User and PPP Secret**:



    * Go to **PPP** -> **Secrets Tab** -> click **+** (new).
    * Name: `dima` (use your preferred user profile names)
    * Password: Enter a password for the user
    * Click **OK**.



<p id="gdcalert45" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image45.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert46">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image45.png "image_tooltip")



### Route OpenVPN Traffic to VPS to Hide Starlink IP


#### **Connect to L2TP Server**:



    * Go back to the Winbox of the Mikrotik router.
    * Go to **PPP** -> **+** -> **Dial Out Tab**.
    * Connect to: Your VPS IP
    * User: `dima` (VPN user created earlier)
    * Password: VPN user password
    * Use IPsec: ✅
    * IPsec Secret: The IPsec password set earlier
    * Click **OK**.



<p id="gdcalert46" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image46.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert47">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image46.png "image_tooltip")



#### Milestone 5

If L2TP is correctly configured, you should see an `R` (Running) status, either alone or with other letters, in the Status column.


    

<p id="gdcalert47" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image47.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert48">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image47.png "image_tooltip")



#### Create NAT



* Go to **IP** -> **Firewall** -> **NAT Tab** -> click **+** (new).
* **General Tab**:
    * Chain: `srcnat`
    * Src. Address: `192.168.128.0/24` (the IP pool created earlier)

    

<p id="gdcalert48" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image48.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert49">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image48.png "image_tooltip")


* **Action Tab**:
    * Action: `masquerade`
    * Click **OK**.



<p id="gdcalert49" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image49.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert50">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image49.png "image_tooltip")



#### Add Static Route



* Go to **IP** -> **Route** -> click **+** (new).
* **General Tab**:
    * Dst. Address: `0.0.0.0/0`
    * Gateway: `10.112.112.135` (L2TP Server)
    * Distance: `1` (lower number gives higher priority)
    * Click **OK**.

    

<p id="gdcalert50" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image50.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert51">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image50.png "image_tooltip")




#### **Route OpenVPN Traffic to VPS**:



* Go to **IP** -> **Route** -> click **+** (new).
* **General Tab**:
    * Dst. Address: `0.0.0.0/0` (as a default route)
    * Gateway: `172.16.5.1` (Public VPS IP or L2TP Server)
    * Distance: `1`
    * Routing Table: `To-Starlink`
    * Click **OK**.



<p id="gdcalert51" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image51.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert52">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image51.png "image_tooltip")



#### **Change to L2TP**



* Go to **IP** -> **Firewall** -> click **+** (new).
    * Out. Interface: l2tp-out1 (change from wifi2)


#### **Result of Hiding the Starlink IP**

Now go to IP detection websites such as ip-api.com. The final result should show your VPS IP instead of the Starlink IP for host as well as users.
