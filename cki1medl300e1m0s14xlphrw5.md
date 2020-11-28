## How to setup your own FREE VPN server on cloud (AWS)

# How to setup your own FREE VPN server on cloud (AWS)

Almost all major cloud computing companies like [Google Cloud](https://cloud.google.com/), [Microsoft Azure](https://azure.microsoft.com/) or [Amazon Web Services (AWS)](https://aws.amazon.com/) offer free 12 months services or free credits to newly registered members. We use AWS in this solution. If you don’t have an account on AWS, Please be [registered](https://portal.aws.amazon.com/billing/signup)

<noscript><img alt="AWS EC2 services" class="ef dv dr hy w" src="https://miro.medium.com/max/3612/1*0MpBApKFLtKwPBc3RWySiQ.jpeg" width="1806" height="839" srcSet="https://miro.medium.com/max/552/1*0MpBApKFLtKwPBc3RWySiQ.jpeg 276w, https://miro.medium.com/max/1104/1*0MpBApKFLtKwPBc3RWySiQ.jpeg 552w, https://miro.medium.com/max/1280/1*0MpBApKFLtKwPBc3RWySiQ.jpeg 640w, https://miro.medium.com/max/1456/1*0MpBApKFLtKwPBc3RWySiQ.jpeg 728w, https://miro.medium.com/max/1632/1*0MpBApKFLtKwPBc3RWySiQ.jpeg 816w, https://miro.medium.com/max/1808/1*0MpBApKFLtKwPBc3RWySiQ.jpeg 904w, https://miro.medium.com/max/1984/1*0MpBApKFLtKwPBc3RWySiQ.jpeg 992w, https://miro.medium.com/max/2000/1*0MpBApKFLtKwPBc3RWySiQ.jpeg 1000w" sizes="1000px"/></noscript>

We are going to click on the “Services” top left and then under “Computing” select “EC2”

## What is EC2?

It’s an amazon service let us deploy a virtual machine in the cloud. It will run our vpn server.

Launch EC2 Instance

<noscript><img alt="AWS Launch Instance" class="ef dv dr hy w" src="https://miro.medium.com/max/2228/1*u6_-bCP-f73zR-BW-FOIGg.jpeg" width="1114" height="644" srcSet="https://miro.medium.com/max/552/1*u6_-bCP-f73zR-BW-FOIGg.jpeg 276w, https://miro.medium.com/max/1104/1*u6_-bCP-f73zR-BW-FOIGg.jpeg 552w, https://miro.medium.com/max/1280/1*u6_-bCP-f73zR-BW-FOIGg.jpeg 640w, https://miro.medium.com/max/1400/1*u6_-bCP-f73zR-BW-FOIGg.jpeg 700w" sizes="700px"/></noscript>

We can select wha<span id="rmm"><span id="rmm">t</span></span>ever image we want. They are called AMI or amazon machine images and these are basic. They just have the operating system installed but we want a bit extra to save time so we are going to AWS Marketplace.

<noscript><img alt="AWS Marketplace" class="ef dv dr hy w" src="https://miro.medium.com/max/1512/1*1StS7HZlPTx-62nopkSqdg.jpeg" width="756" height="732" srcSet="https://miro.medium.com/max/552/1*1StS7HZlPTx-62nopkSqdg.jpeg 276w, https://miro.medium.com/max/1104/1*1StS7HZlPTx-62nopkSqdg.jpeg 552w, https://miro.medium.com/max/1280/1*1StS7HZlPTx-62nopkSqdg.jpeg 640w, https://miro.medium.com/max/1400/1*1StS7HZlPTx-62nopkSqdg.jpeg 700w" sizes="700px"/></noscript>

AWS Marketplace will give us stuff beyond the operating system like we’ll have pre-configured tools like OpenVPN.

<noscript><img alt="OpenVPN Access Server" class="ef dv dr hy w" src="https://miro.medium.com/max/5074/1*9RXxB8UFUIbel1YJdlIzEw.jpeg" width="2537" height="775" srcSet="https://miro.medium.com/max/552/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 276w, https://miro.medium.com/max/1104/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 552w, https://miro.medium.com/max/1280/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 640w, https://miro.medium.com/max/1456/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 728w, https://miro.medium.com/max/1632/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 816w, https://miro.medium.com/max/1808/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 904w, https://miro.medium.com/max/1984/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 992w, https://miro.medium.com/max/2160/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 1080w, https://miro.medium.com/max/2700/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 1350w, https://miro.medium.com/max/3240/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 1620w, https://miro.medium.com/max/3780/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 1890w, https://miro.medium.com/max/4320/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 2160w, https://miro.medium.com/max/4800/1*9RXxB8UFUIbel1YJdlIzEw.jpeg 2400w" sizes="100vw"/></noscript>

Type "openvpn" in the search box and choose the first choice OpenVPN Access Server and then select. This will be an Ubuntu server with OpenVPN already installed. It’s free tier 😃.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/2128/1*-5bxPqRi5VVvA7IyoBYlkQ.jpeg" width="1064" height="616" srcSet="https://miro.medium.com/max/552/1*-5bxPqRi5VVvA7IyoBYlkQ.jpeg 276w, https://miro.medium.com/max/1104/1*-5bxPqRi5VVvA7IyoBYlkQ.jpeg 552w, https://miro.medium.com/max/1280/1*-5bxPqRi5VVvA7IyoBYlkQ.jpeg 640w, https://miro.medium.com/max/1400/1*-5bxPqRi5VVvA7IyoBYlkQ.jpeg 700w" sizes="700px"/></noscript>

OpenVPN is a free and open source software but OpenVPN Access Server is a paid commercial option. It gives us two clients for free. You and your friend can connect vpn server for free no worries 😄 Select continue and then we will choose our server type.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/5106/1*OSxx97CjXGhpgr_v-Bc1NQ.jpeg" width="2553" height="1114" srcSet="https://miro.medium.com/max/552/1*OSxx97CjXGhpgr_v-Bc1NQ.jpeg 276w, https://miro.medium.com/max/1104/1*OSxx97CjXGhpgr_v-Bc1NQ.jpeg 552w, https://miro.medium.com/max/1280/1*OSxx97CjXGhpgr_v-Bc1NQ.jpeg 640w, https://miro.medium.com/max/1456/1*OSxx97CjXGhpgr_v-Bc1NQ.jpeg 728w, https://miro.medium.com/max/1632/1*OSxx97CjXGhpgr_v-Bc1NQ.jpeg 816w, https://miro.medium.com/max/1808/1*OSxx97CjXGhpgr_v-Bc1NQ.jpeg 904w, https://miro.medium.com/max/1984/1*OSxx97CjXGhpgr_v-Bc1NQ.jpeg 992w, https://miro.medium.com/max/2000/1*OSxx97CjXGhpgr_v-Bc1NQ.jpeg 1000w" sizes="1000px"/></noscript>

Chose the free tier and go to Review and Launch.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/5098/1*NPzA-1L7SmwDWOlLjpHmvw.jpeg" width="2549" height="1104" srcSet="https://miro.medium.com/max/552/1*NPzA-1L7SmwDWOlLjpHmvw.jpeg 276w, https://miro.medium.com/max/1104/1*NPzA-1L7SmwDWOlLjpHmvw.jpeg 552w, https://miro.medium.com/max/1280/1*NPzA-1L7SmwDWOlLjpHmvw.jpeg 640w, https://miro.medium.com/max/1456/1*NPzA-1L7SmwDWOlLjpHmvw.jpeg 728w, https://miro.medium.com/max/1632/1*NPzA-1L7SmwDWOlLjpHmvw.jpeg 816w, https://miro.medium.com/max/1808/1*NPzA-1L7SmwDWOlLjpHmvw.jpeg 904w, https://miro.medium.com/max/1984/1*NPzA-1L7SmwDWOlLjpHmvw.jpeg 992w, https://miro.medium.com/max/2000/1*NPzA-1L7SmwDWOlLjpHmvw.jpeg 1000w" sizes="1000px"/></noscript>

Click the Launch button.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/1910/1*INzRSng4l4p0_ApObps8_Q.jpeg" width="955" height="577" srcSet="https://miro.medium.com/max/552/1*INzRSng4l4p0_ApObps8_Q.jpeg 276w, https://miro.medium.com/max/1104/1*INzRSng4l4p0_ApObps8_Q.jpeg 552w, https://miro.medium.com/max/1280/1*INzRSng4l4p0_ApObps8_Q.jpeg 640w, https://miro.medium.com/max/1400/1*INzRSng4l4p0_ApObps8_Q.jpeg 700w" sizes="700px"/></noscript>

We need a key pair. If you don’t already have one, make a new one.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/1922/1*4FAVmABg3AUi2M5tRawc-w.jpeg" width="961" height="697" srcSet="https://miro.medium.com/max/552/1*4FAVmABg3AUi2M5tRawc-w.jpeg 276w, https://miro.medium.com/max/1104/1*4FAVmABg3AUi2M5tRawc-w.jpeg 552w, https://miro.medium.com/max/1280/1*4FAVmABg3AUi2M5tRawc-w.jpeg 640w, https://miro.medium.com/max/1400/1*4FAVmABg3AUi2M5tRawc-w.jpeg 700w" sizes="700px"/></noscript>

This is the only chance to download the key. Please do it now 😄. We are going to use it when we connect to our server to configure it. After download click the Launch Instances.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/1954/1*4n01ntoJODYYqabf81aXDw.jpeg" width="977" height="391" srcSet="https://miro.medium.com/max/552/1*4n01ntoJODYYqabf81aXDw.jpeg 276w, https://miro.medium.com/max/1104/1*4n01ntoJODYYqabf81aXDw.jpeg 552w, https://miro.medium.com/max/1280/1*4n01ntoJODYYqabf81aXDw.jpeg 640w, https://miro.medium.com/max/1400/1*4n01ntoJODYYqabf81aXDw.jpeg 700w" sizes="700px"/></noscript>

Click the link and watch the instance status.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/5110/1*AttizIEdvAwNOCf2xYZKdQ.jpeg" width="2555" height="528" srcSet="https://miro.medium.com/max/552/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 276w, https://miro.medium.com/max/1104/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 552w, https://miro.medium.com/max/1280/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 640w, https://miro.medium.com/max/1456/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 728w, https://miro.medium.com/max/1632/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 816w, https://miro.medium.com/max/1808/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 904w, https://miro.medium.com/max/1984/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 992w, https://miro.medium.com/max/2160/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 1080w, https://miro.medium.com/max/2700/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 1350w, https://miro.medium.com/max/3240/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 1620w, https://miro.medium.com/max/3780/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 1890w, https://miro.medium.com/max/4320/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 2160w, https://miro.medium.com/max/4800/1*AttizIEdvAwNOCf2xYZKdQ.jpeg 2400w" sizes="100vw"/></noscript>

Finally, It’s done. Server is running. We are ready 😃

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/1704/1*oXAVzUgWNxqVgnlb1cDRAw.png" width="852" height="400" srcSet="https://miro.medium.com/max/552/1*oXAVzUgWNxqVgnlb1cDRAw.png 276w, https://miro.medium.com/max/1104/1*oXAVzUgWNxqVgnlb1cDRAw.png 552w, https://miro.medium.com/max/1280/1*oXAVzUgWNxqVgnlb1cDRAw.png 640w, https://miro.medium.com/max/1400/1*oXAVzUgWNxqVgnlb1cDRAw.png 700w" sizes="700px"/></noscript>

Right click Instance ID and Connect. This will show you how to connect to your vpn server. We will go with the standalone ssh option.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/2310/1*TpSzzAwTK04OQKW6UquLQA.jpeg" width="1155" height="769" srcSet="https://miro.medium.com/max/552/1*TpSzzAwTK04OQKW6UquLQA.jpeg 276w, https://miro.medium.com/max/1104/1*TpSzzAwTK04OQKW6UquLQA.jpeg 552w, https://miro.medium.com/max/1280/1*TpSzzAwTK04OQKW6UquLQA.jpeg 640w, https://miro.medium.com/max/1400/1*TpSzzAwTK04OQKW6UquLQA.jpeg 700w" sizes="700px"/></noscript>

Copy the example ssh code and launch your terminal program on Linux or Mac or Windows. I am using powershell in Windows 10\. Shift + Right Click the downloaded vpn_server.pem file folder and launch the “Open PowerShell window here” or you can use the “cd” command to go to the folder.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/3900/1*T1dWq_Dp8vIhdTaCfNysUQ.jpeg" width="1950" height="175" srcSet="https://miro.medium.com/max/552/1*T1dWq_Dp8vIhdTaCfNysUQ.jpeg 276w, https://miro.medium.com/max/1104/1*T1dWq_Dp8vIhdTaCfNysUQ.jpeg 552w, https://miro.medium.com/max/1280/1*T1dWq_Dp8vIhdTaCfNysUQ.jpeg 640w, https://miro.medium.com/max/1456/1*T1dWq_Dp8vIhdTaCfNysUQ.jpeg 728w, https://miro.medium.com/max/1632/1*T1dWq_Dp8vIhdTaCfNysUQ.jpeg 816w, https://miro.medium.com/max/1808/1*T1dWq_Dp8vIhdTaCfNysUQ.jpeg 904w, https://miro.medium.com/max/1984/1*T1dWq_Dp8vIhdTaCfNysUQ.jpeg 992w, https://miro.medium.com/max/2000/1*T1dWq_Dp8vIhdTaCfNysUQ.jpeg 1000w" sizes="1000px"/></noscript>

Type “yes” and continue.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/3002/1*1JtunUrhhMi3I9Na-RUV_A.jpeg" width="1501" height="1399" srcSet="https://miro.medium.com/max/552/1*1JtunUrhhMi3I9Na-RUV_A.jpeg 276w, https://miro.medium.com/max/1104/1*1JtunUrhhMi3I9Na-RUV_A.jpeg 552w, https://miro.medium.com/max/1280/1*1JtunUrhhMi3I9Na-RUV_A.jpeg 640w, https://miro.medium.com/max/1400/1*1JtunUrhhMi3I9Na-RUV_A.jpeg 700w" sizes="700px"/></noscript>

Type “yes” again and keep pressing enter for default settings until the server is initializing OpenVPN.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/2560/1*-bqqfRHu5AGO6z608FNI5g.jpeg" width="1280" height="1397" srcSet="https://miro.medium.com/max/552/1*-bqqfRHu5AGO6z608FNI5g.jpeg 276w, https://miro.medium.com/max/1104/1*-bqqfRHu5AGO6z608FNI5g.jpeg 552w, https://miro.medium.com/max/1280/1*-bqqfRHu5AGO6z608FNI5g.jpeg 640w, https://miro.medium.com/max/1400/1*-bqqfRHu5AGO6z608FNI5g.jpeg 700w" sizes="700px"/></noscript>

OpenVPN wants you to login as “openvpnas” rather than “root” and it won’t log back in as root. Just enter the same command as we used earlier to change the user.

```
ssh -i "vpn_server.pem" [openvpnas@ec2-54-154-90-187.eu-west-1.compute.amazonaws.com](mailto:root@ec2-54-154-90-187.eu-west-1.compute.amazonaws.com)</span>
```

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/3880/1*i0RcfuHMvKAYZCYPjZkuuQ.jpeg" width="1940" height="736" srcSet="https://miro.medium.com/max/552/1*i0RcfuHMvKAYZCYPjZkuuQ.jpeg 276w, https://miro.medium.com/max/1104/1*i0RcfuHMvKAYZCYPjZkuuQ.jpeg 552w, https://miro.medium.com/max/1280/1*i0RcfuHMvKAYZCYPjZkuuQ.jpeg 640w, https://miro.medium.com/max/1456/1*i0RcfuHMvKAYZCYPjZkuuQ.jpeg 728w, https://miro.medium.com/max/1632/1*i0RcfuHMvKAYZCYPjZkuuQ.jpeg 816w, https://miro.medium.com/max/1808/1*i0RcfuHMvKAYZCYPjZkuuQ.jpeg 904w, https://miro.medium.com/max/1984/1*i0RcfuHMvKAYZCYPjZkuuQ.jpeg 992w, https://miro.medium.com/max/2000/1*i0RcfuHMvKAYZCYPjZkuuQ.jpeg 1000w" sizes="1000px"/></noscript>

That should work just fine. We are in 😃. Now there is only one thing we have to do here in the command line.

```
sudo passwd openvpn</span>
```

This will change the password for the user OpenVPN. This is our admin user and our client user when we connect to our vpn portal.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/1814/1*5YPbw4hg0Dj0xPPqiikM3A.jpeg" width="907" height="165" srcSet="https://miro.medium.com/max/552/1*5YPbw4hg0Dj0xPPqiikM3A.jpeg 276w, https://miro.medium.com/max/1104/1*5YPbw4hg0Dj0xPPqiikM3A.jpeg 552w, https://miro.medium.com/max/1280/1*5YPbw4hg0Dj0xPPqiikM3A.jpeg 640w, https://miro.medium.com/max/1400/1*5YPbw4hg0Dj0xPPqiikM3A.jpeg 700w" sizes="700px"/></noscript>

Remember this password. This will be your admin password for OpenVPN. After this stage close the terminal or minimize it. Now your server is pretty much ready but there is one thing we want to do. We will get back to AWS and we will look pur public IP address “IPv4 Public IP”

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/4270/1*IkOBiBSByf25KYVHkP5pVg.jpeg" width="2135" height="645" srcSet="https://miro.medium.com/max/552/1*IkOBiBSByf25KYVHkP5pVg.jpeg 276w, https://miro.medium.com/max/1104/1*IkOBiBSByf25KYVHkP5pVg.jpeg 552w, https://miro.medium.com/max/1280/1*IkOBiBSByf25KYVHkP5pVg.jpeg 640w, https://miro.medium.com/max/1456/1*IkOBiBSByf25KYVHkP5pVg.jpeg 728w, https://miro.medium.com/max/1632/1*IkOBiBSByf25KYVHkP5pVg.jpeg 816w, https://miro.medium.com/max/1808/1*IkOBiBSByf25KYVHkP5pVg.jpeg 904w, https://miro.medium.com/max/1984/1*IkOBiBSByf25KYVHkP5pVg.jpeg 992w, https://miro.medium.com/max/2000/1*IkOBiBSByf25KYVHkP5pVg.jpeg 1000w" sizes="1000px"/></noscript>

Copy the Public IPv4 address. Open new tab in your browser and go to the address below.

```
https://<Your Public IP Address>:943/admin</span>
```

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/3074/1*h6qWOyxcdRID4_d7v2tG4w.jpeg" width="1537" height="586" srcSet="https://miro.medium.com/max/552/1*h6qWOyxcdRID4_d7v2tG4w.jpeg 276w, https://miro.medium.com/max/1104/1*h6qWOyxcdRID4_d7v2tG4w.jpeg 552w, https://miro.medium.com/max/1280/1*h6qWOyxcdRID4_d7v2tG4w.jpeg 640w, https://miro.medium.com/max/1456/1*h6qWOyxcdRID4_d7v2tG4w.jpeg 728w, https://miro.medium.com/max/1632/1*h6qWOyxcdRID4_d7v2tG4w.jpeg 816w, https://miro.medium.com/max/1808/1*h6qWOyxcdRID4_d7v2tG4w.jpeg 904w, https://miro.medium.com/max/1984/1*h6qWOyxcdRID4_d7v2tG4w.jpeg 992w, https://miro.medium.com/max/2000/1*h6qWOyxcdRID4_d7v2tG4w.jpeg 1000w" sizes="1000px"/></noscript>

This has a self-signed page so don’t worry about that click advance and continue.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/1434/1*XSwQ7NtuiU9NtOxducLBuQ.jpeg" width="717" height="522" srcSet="https://miro.medium.com/max/552/1*XSwQ7NtuiU9NtOxducLBuQ.jpeg 276w, https://miro.medium.com/max/1104/1*XSwQ7NtuiU9NtOxducLBuQ.jpeg 552w, https://miro.medium.com/max/1280/1*XSwQ7NtuiU9NtOxducLBuQ.jpeg 640w, https://miro.medium.com/max/1400/1*XSwQ7NtuiU9NtOxducLBuQ.jpeg 700w" sizes="700px"/></noscript>

Username: openvpn

Password: that password we just created in terminal.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/3412/1*HAH2EA1v3PgvsgiPMkQ3Bw.jpeg" width="1706" height="930" srcSet="https://miro.medium.com/max/552/1*HAH2EA1v3PgvsgiPMkQ3Bw.jpeg 276w, https://miro.medium.com/max/1104/1*HAH2EA1v3PgvsgiPMkQ3Bw.jpeg 552w, https://miro.medium.com/max/1280/1*HAH2EA1v3PgvsgiPMkQ3Bw.jpeg 640w, https://miro.medium.com/max/1456/1*HAH2EA1v3PgvsgiPMkQ3Bw.jpeg 728w, https://miro.medium.com/max/1632/1*HAH2EA1v3PgvsgiPMkQ3Bw.jpeg 816w, https://miro.medium.com/max/1808/1*HAH2EA1v3PgvsgiPMkQ3Bw.jpeg 904w, https://miro.medium.com/max/1984/1*HAH2EA1v3PgvsgiPMkQ3Bw.jpeg 992w, https://miro.medium.com/max/2000/1*HAH2EA1v3PgvsgiPMkQ3Bw.jpeg 1000w" sizes="1000px"/></noscript>

Click “Agree” and continue.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/3436/1*DLv_Vt6MgoRtJHIKIaS4NQ.jpeg" width="1718" height="1020" srcSet="https://miro.medium.com/max/552/1*DLv_Vt6MgoRtJHIKIaS4NQ.jpeg 276w, https://miro.medium.com/max/1104/1*DLv_Vt6MgoRtJHIKIaS4NQ.jpeg 552w, https://miro.medium.com/max/1280/1*DLv_Vt6MgoRtJHIKIaS4NQ.jpeg 640w, https://miro.medium.com/max/1456/1*DLv_Vt6MgoRtJHIKIaS4NQ.jpeg 728w, https://miro.medium.com/max/1632/1*DLv_Vt6MgoRtJHIKIaS4NQ.jpeg 816w, https://miro.medium.com/max/1808/1*DLv_Vt6MgoRtJHIKIaS4NQ.jpeg 904w, https://miro.medium.com/max/1984/1*DLv_Vt6MgoRtJHIKIaS4NQ.jpeg 992w, https://miro.medium.com/max/2000/1*DLv_Vt6MgoRtJHIKIaS4NQ.jpeg 1000w" sizes="1000px"/></noscript>

We are in. There is one thing i want you to change. Under configuration we are going to the “VPN Settings”.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/3426/1*W-Ollujms49hTm-HlryMAA.jpeg" width="1713" height="1027" srcSet="https://miro.medium.com/max/552/1*W-Ollujms49hTm-HlryMAA.jpeg 276w, https://miro.medium.com/max/1104/1*W-Ollujms49hTm-HlryMAA.jpeg 552w, https://miro.medium.com/max/1280/1*W-Ollujms49hTm-HlryMAA.jpeg 640w, https://miro.medium.com/max/1456/1*W-Ollujms49hTm-HlryMAA.jpeg 728w, https://miro.medium.com/max/1632/1*W-Ollujms49hTm-HlryMAA.jpeg 816w, https://miro.medium.com/max/1808/1*W-Ollujms49hTm-HlryMAA.jpeg 904w, https://miro.medium.com/max/1984/1*W-Ollujms49hTm-HlryMAA.jpeg 992w, https://miro.medium.com/max/2000/1*W-Ollujms49hTm-HlryMAA.jpeg 1000w" sizes="1000px"/></noscript>

To make sure all your internet traffic is safe and secure going through this vpn wherever you are. Under Routing we will see an option that says “Should client internet traffic be routed through the VPN?”. We want that so we are going to select the option and “Save Settings”.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/3426/1*akKYdtPlybR2LD2JybXNow.jpeg" width="1713" height="341" srcSet="https://miro.medium.com/max/552/1*akKYdtPlybR2LD2JybXNow.jpeg 276w, https://miro.medium.com/max/1104/1*akKYdtPlybR2LD2JybXNow.jpeg 552w, https://miro.medium.com/max/1280/1*akKYdtPlybR2LD2JybXNow.jpeg 640w, https://miro.medium.com/max/1456/1*akKYdtPlybR2LD2JybXNow.jpeg 728w, https://miro.medium.com/max/1632/1*akKYdtPlybR2LD2JybXNow.jpeg 816w, https://miro.medium.com/max/1808/1*akKYdtPlybR2LD2JybXNow.jpeg 904w, https://miro.medium.com/max/1984/1*akKYdtPlybR2LD2JybXNow.jpeg 992w, https://miro.medium.com/max/2000/1*akKYdtPlybR2LD2JybXNow.jpeg 1000w" sizes="1000px"/></noscript>

One last step hit this “Update Running Server” to make sure the changes take place.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/3428/1*1D0-aUbcipbX3CQbILszNg.jpeg" width="1714" height="248" srcSet="https://miro.medium.com/max/552/1*1D0-aUbcipbX3CQbILszNg.jpeg 276w, https://miro.medium.com/max/1104/1*1D0-aUbcipbX3CQbILszNg.jpeg 552w, https://miro.medium.com/max/1280/1*1D0-aUbcipbX3CQbILszNg.jpeg 640w, https://miro.medium.com/max/1456/1*1D0-aUbcipbX3CQbILszNg.jpeg 728w, https://miro.medium.com/max/1632/1*1D0-aUbcipbX3CQbILszNg.jpeg 816w, https://miro.medium.com/max/1808/1*1D0-aUbcipbX3CQbILszNg.jpeg 904w, https://miro.medium.com/max/1984/1*1D0-aUbcipbX3CQbILszNg.jpeg 992w, https://miro.medium.com/max/2000/1*1D0-aUbcipbX3CQbILszNg.jpeg 1000w" sizes="1000px"/></noscript>

That’s it, 😃 as far as the server goes you’re done but we are not done yet. We still have clients to connect. We want to connect to this right and want to use it. Go to the browser url bar and click the below url with your own virtual server public addresses.

```
[https://<Your Public IP Address>:943/](https://54.154.90.187:943/)</span>
```

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/2184/1*HrDtYXPwgunfi2wxmvJYHQ.jpeg" width="1092" height="616" srcSet="https://miro.medium.com/max/552/1*HrDtYXPwgunfi2wxmvJYHQ.jpeg 276w, https://miro.medium.com/max/1104/1*HrDtYXPwgunfi2wxmvJYHQ.jpeg 552w, https://miro.medium.com/max/1280/1*HrDtYXPwgunfi2wxmvJYHQ.jpeg 640w, https://miro.medium.com/max/1400/1*HrDtYXPwgunfi2wxmvJYHQ.jpeg 700w" sizes="700px"/></noscript>

It’s taking us to the user portal before that was the admin portal where we make changes and stuff. Here it’s for clients for people who want to connect. Good news is it’s the same login information 😃.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/2172/1*2RQapFb5EyTmITONRDk5qQ.jpeg" width="1086" height="1112" srcSet="https://miro.medium.com/max/552/1*2RQapFb5EyTmITONRDk5qQ.jpeg 276w, https://miro.medium.com/max/1104/1*2RQapFb5EyTmITONRDk5qQ.jpeg 552w, https://miro.medium.com/max/1280/1*2RQapFb5EyTmITONRDk5qQ.jpeg 640w, https://miro.medium.com/max/1400/1*2RQapFb5EyTmITONRDk5qQ.jpeg 700w" sizes="700px"/></noscript>

Choose your favorite whatever device you have, whatever device you want to connect to vpn download that client so I have windows here so i’m going to select windows.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/1058/1*mM3GuWLB6I6xbhe3CYd5yQ.jpeg" width="529" height="492" srcSet="https://miro.medium.com/max/552/1*mM3GuWLB6I6xbhe3CYd5yQ.jpeg 276w, https://miro.medium.com/max/1058/1*mM3GuWLB6I6xbhe3CYd5yQ.jpeg 529w" sizes="529px"/></noscript>

Windows doesn’t like it but i don’t care. Click “More info” and “Run anyway”.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/1068/1*y4wOCOKUZUWzdkZiKbqitg.jpeg" width="534" height="496" srcSet="https://miro.medium.com/max/552/1*y4wOCOKUZUWzdkZiKbqitg.jpeg 276w, https://miro.medium.com/max/1068/1*y4wOCOKUZUWzdkZiKbqitg.jpeg 534w" sizes="534px"/></noscript>

You can’t boss me around windows get in your lane Bill Gates 😃

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/978/1*yov_mIu2E8bJQmp2Zyy49A.jpeg" width="489" height="380" srcSet="https://miro.medium.com/max/552/1*yov_mIu2E8bJQmp2Zyy49A.jpeg 276w, https://miro.medium.com/max/978/1*yov_mIu2E8bJQmp2Zyy49A.jpeg 489w" sizes="489px"/></noscript>

Next — Accept — Next — Install and finish

Start the “OpenVPN Connect” application in your computer and then agreed the terms in the first screen.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/788/1*eGMlXXnYWpTWHLppZyrC8w.jpeg" width="394" height="680" srcSet="https://miro.medium.com/max/552/1*eGMlXXnYWpTWHLppZyrC8w.jpeg 276w, https://miro.medium.com/max/788/1*eGMlXXnYWpTWHLppZyrC8w.jpeg 394w" sizes="394px"/></noscript>

The beautiful part is that it’s already pre-configured. It imported your profile if you downloaded it from that page. All we have to do is hit connect.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/802/1*pZ7f10l0WuhCk9PW2YSvAQ.jpeg" width="401" height="684" srcSet="https://miro.medium.com/max/552/1*pZ7f10l0WuhCk9PW2YSvAQ.jpeg 276w, https://miro.medium.com/max/802/1*pZ7f10l0WuhCk9PW2YSvAQ.jpeg 401w" sizes="401px"/></noscript>

Once more same Username same Password.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/784/1*4vwbmB3w74OasYFRvJG6MQ.jpeg" width="392" height="684" srcSet="https://miro.medium.com/max/552/1*4vwbmB3w74OasYFRvJG6MQ.jpeg 276w, https://miro.medium.com/max/784/1*4vwbmB3w74OasYFRvJG6MQ.jpeg 392w" sizes="392px"/></noscript>

We are connected 😃 but am I secure? How do I know this is working? Let’s go test it out. We will open up a new tab in our browser here we will go to google and we will type in “what’s my ip” and let’s see where we are at 😄.

<noscript><img alt="Image for post" class="ef dv dr hy w" src="https://miro.medium.com/max/1720/1*beG1Sdx01zJtGMB8Ly4Mpw.jpeg" width="860" height="413" srcSet="https://miro.medium.com/max/552/1*beG1Sdx01zJtGMB8Ly4Mpw.jpeg 276w, https://miro.medium.com/max/1104/1*beG1Sdx01zJtGMB8Ly4Mpw.jpeg 552w, https://miro.medium.com/max/1280/1*beG1Sdx01zJtGMB8Ly4Mpw.jpeg 640w, https://miro.medium.com/max/1400/1*beG1Sdx01zJtGMB8Ly4Mpw.jpeg 700w" sizes="700px"/></noscript>

That’s not my home IP Address by the way. That’s the only that we’ve been using so far. That’s our openvpn server all our internet traffic is going through this guy we just created. If you want to use your phone ios/android, open the browser in your phone, type the link below, enter the username and password and get the phone app. That’s it.

```
[https://<Your Public IP Address>:943/](https://54.154.90.187:943/)</span>
```

You have got a vpn server. You are a boss. That’s pretty cool. This is doing two amazing things. Your computer, your phone or whatever you connect to this vpn server you are getting access to a virtual private cloud in amazon or a VPC. When you are working in AWS, you are creating servers and websites and all kinds of stuff, you can have that safely tucked away in a virtual private network or virtual private cloud. What we just did here today gives you a secure way to connect to your virtual private cloud in AWS. You are not accessing public IPs. You are securely accessing your virtual network and you are logging in devices via their private IP addresses. Not only that because we changed our options all internet traffic is going through the server. Keeping us nice, safe and encrypted. We can be wherever we want because I don’t know if you noticed. I’m in Ireland according to our vpn server. That’s where I put him in amazon. Wherever amazon is i can be there too 😎.