<h2>1. A-Record Exercise</h2>

![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/462a4274-7afb-47ed-a802-46305c264066)
- Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
- Connect/log into Client-1 as an admin (mydomain\jane_admin)
- From Client-1 try to ping “mainframe” notice that it fails
- Nslookup “mainframe” notice that it fails (no DNS record)

<hr>
<br>

![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/1fefc611-a769-4abe-8700-9d9ca4739dc6)
- Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address

<hr>
<br>


![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/1781c262-efdf-478d-b157-0c35ea61944b)
- Go back to Client-1 and try to ping it. Observe that it works

<hr>
<br>


<h2>2. Local DNS Cache Exercise</h2>

![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/7867fb60-3aff-4c7f-8e5c-0881b215279a)
- Go back to DC-1 and change mainframe’s record address to 8.8.8.8

<hr>
<br>


![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/6734eafc-e6a5-4b0f-96b7-b6d7a59ec8d8)
- Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address

<hr>
<br>

![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/9f85daf9-6217-4975-bea4-c59bc375a536)
- Observe the local dns cache (ipconfig /displaydns)

<hr>
<br>

![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/038dad33-29e7-4c2d-9b1e-8e98a313f634)
- Flush the DNS cache (ipconfig /flushdns). Observe that the cache is empty
- Attempt to ping “mainframe” again. Observe the address of the new record is showing up

<hr>
<br>

<h2>3. CNAME Record Exercise</h2>

![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/04244090-b0d6-461b-92c7-86c007417eeb)
- Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com”

<hr>
<br>

![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/e1fd5b34-1959-459a-974d-27bae7b56da2)
- Go back to Client-1 and attempt to ping “search”, observe the results of the CNAME record

<hr>
<br>

![image](https://github.com/LawrenceDavy/configure-ad/assets/24421979/97ed15d4-8f23-433c-900d-c2dca4d908de)
- On Client-1, nslookup “search”, observe the results of the CNAME record
