<h1>Computer certificate</h1>
<p>Computer certificate enrollment is the process of issuing digital certificates to computers, including servers and clients, to enable secure communication, verify device identities, and encrypt data exchanges. These certificates are used in various scenarios, such as website access, remote desktop connections, VPNs, Wi-Fi connections, email encryption, and signing documents</p>

<h3>*Installing and setting up Active Directory Certificate Services(ADCS) on Member Server(MS1)</h3>

<p>1. To install Active Directory Certificate Services (AD CS) on Member Server; From the server manager-dashboard, go to Manage > Add roles and features</p>
<p align="center"><img src="https://i.imgur.com/0mxYiYL.png" height="50%" width="50%" alt="image"/>

<p>2. On the before you begin screen, just click NEXT</p>
<p align="center"><img src="https://i.imgur.com/K3ceoI5.png" height="50%" width="50%" alt="image"/>

<p>3. On the Installation Type screen, make sure the Role-based or feature-based installation is selected, then click NEXT.</p>
<p align="center"><img src="https://imgur.com/a/Uv4atcr" height="50%" width="50%" alt="image"/>

<p>4. On the Select destination server screen, make sure the select a server from the server pool is server is selected and select the server you are trying to install Adds from the server pool, then click NEXT.</p>
<p align="center"><img src="https://i.imgur.com/Wg9RMPR.png" height="50%" width="50%" alt="image"/>

<p>5. On the select server roles screen, select Active Directory Certificate Services(its actually the first on the list) and click NEXT </p>
<p align="center"><img src="https://i.imgur.com/zk5EC9x.png" height="50%" width="50%" alt="image"/>

<p>6. Add Roles and Features Wizard pops up, just click on Add features from the pop-up screen.</p>
<p align="center"><img src="https://i.imgur.com/SXG0wkL.png" height="50%" width="50%" alt="image"/>

<p>7. Back on the Select server roles page, the ADCS is now selected(box ticked), click NEXT</p>
<p align="center"><img src="https://i.imgur.com/rO1XUSx.png" height="50%" width="50%" alt="image"/>

<p>8. On the Select features page, just click NEXT</p>
<p align="center"><img src="https://i.imgur.com/VUGZgPL.png" height="50%" width="50%" alt="image"/>

<p>9. On the Active Directory Certificate Services page, click NEXT.</p>
<p align="center"><img src="https://i.imgur.com/aV0AwLx.png" height="50%" width="50%" alt="image"/>

<p>10. On the Select role services, click on the Certificate Authority and click NEXT.</p>
<p align="center"><img src="https://i.imgur.com/ils7LPX.png" height="50%" width="50%" alt="image"/>

<p>11. On the Confirm Installation Selections page, click INSTALL.</p>
<p align="center"><img src="https://i.imgur.com/GnCM4UL.png" height="50%" width="50%" alt="image"/>

<p>12. On the Installation Progress page, the feature installation is now shown as completed, click CLOSE.</p>
<p align="center"><img src="https://i.imgur.com/86OIFXc.png" height="50%" width="50%" alt="image"/>

<h3>*Configuration</h3>
<P>1. On the Server manager-dashboard, click on notification then click on Configure Active Directory, this opens the ADCS Configuration</P>
<p align="center"><img src="https://i.imgur.com/NidRXW3.png" height="50%" width="50%" alt="image"/>

<p>2. On the ADCS Configuration>Credentials page, click NEXT</p>
<p align="center"><img src="https://i.imgur.com/cKi3vSx.png" height="50%" width="50%" alt="image"/>

<p>3. On the ADCS Configuration>Role Services page, select Certificate Authority, click NEXT</p>
<p align="center"><img src="https://i.imgur.com/eN41Jez.png" height="50%" width="50%" alt="image"/>

<p>4. On the ADCS Configuration>Setup Type page, the Standalone CA is selected, click NEXT</p>
<p align="center"><img src="https://i.imgur.com/5BPdl9f.png" height="50%" width="50%" alt="image"/>

<p>5. On the ADCS Configuration>CA Type page, select Root CA and click NEXT</p>
<p align="center"><img src="https://i.imgur.com/trcyD9V.png" height="50%" width="50%" alt="image"/>

<p>6. On the ADCS Configuration>Private Key, select Create a new private key and click NEXT</p>
<p align="center"><img src="https://i.imgur.com/4sMPLvw.png" height="50%" width="50%" alt="image"/>

<p>7. On the ADCS Configuration>Cryptography for CA page, left it at the default(you can increase the key length because a longer key length provides stronger security, as it makes it harder for attackers to break the encryption), then click NEXT</p>
<p align="center"><img src="https://i.imgur.com/D3NC1bf.png" height="50%" width="50%" alt="image"/>

<p>8. On the ADCS Configuration>CA Name, leave it at default, then click NEXT</p>
<p align="center"><img src="https://i.imgur.com/soGZV5q.png" height="50%" width="50%" alt="image"/>

<p>9. On the ADCS Configuration>Validity Period page, leave it 5 years which is the default, click NEXT</p>
<p align="center"><img src="https://i.imgur.com/BNm5Vzr.png" height="50%" width="50%" alt="image"/>

<p>10. On the ADCS Configuration>CA Database page, leave the database locations as default and click NEXT</p>
<p align="center"><img src="https://i.imgur.com/dwONQ8w.png" height="50%" width="50%" alt="image"/>

<p>11. On the ADCS Configuration>Confirmation page, click CONFIGURE</p>
<p align="center"><img src="https://i.imgur.com/uz9n01A.png" height="50%" width="50%" alt="image"/>

<p>12. On the ADCS Configuration>Results page, configuration succeeded is now displayed, click CLOSE.</p>
<p align="center"><img src="https://i.imgur.com/GFu0rcl.png" height="50%" width="50%" alt="image"/>

<h3>NOTE: After installing and configuring the certificate Authority on MS1, then opening it, I found out there was no Certificate templates to be used. So I performed the same above processes on the ADDS Server and on the ADCS Configuration>Setup Type page, I chose the Enterprise CA in the stead of the Standalone CA.</h3>
<p align="center"><img src="https://i.imgur.com/ziQlRuH.png" height="50%" width="50%" alt="image"/>

<p>13. After the installation and configuration is completed on the ADDS Server, I opened Certificate Authority and there I found the Certificate templates that was missing on MS1</p>
<p align="center"><img src="https://i.imgur.com/PgMm9ze.png" height="50%" width="50%" alt="image"/>

<br>

<h2>Creating a GPO to issue the certificate to organization computers on ADDS server</h2>
<p>1. To issue certificates to computers in your organization, you need a GPO for this to work; From Server Manager-dashboard>Tools>Group Policy Management. Right-click Group Policy Object, click New</p>
<p align="center"><img src="https://i.imgur.com/4rH2Atf.png" height="50%" width="50%" alt="image"/>

<p>2. On the New GPO page, input a descriptive name and click OK</p>
<p align="center"><img src="https://i.imgur.com/22ymq2K.png" height="50%" width="50%" alt="image"/>

<p>3. On the Group Policy Management>Group Policy Object, Right-click on the new GPO created and click on Edit</p>
<p align="center"><img src="https://i.imgur.com/YNzsRi2.png" height="50%" width="50%" alt="image"/>

<p>4. On the Group Policy Management Editor page, go to this path <b><i>Computer Configuration > Policies > Windows Settings > Security Settings > Public Key Policies.</i></b></p>
<p align="center"><img src="https://i.imgur.com/hiITIxs.png" height="50%" width="50%" alt="image"/>

<p>5. Double click on Certificate Service Client auto-enrollment and enable it</p>
<p align="center"><img src="https://i.imgur.com/drdAYHA.png" height="50%" width="50%" alt="image"/>

<p>6. Enable the “Renew expired certificates, update pending certificates, and remove revoked certificates” and “Update certificates that use certificate templates” check-boxes, click Apply then OK.</p>
<p align="center"><img src="https://i.imgur.com/1QKJ4kk.png" height="50%" width="50%" alt="image"/>

<p>7. Back on the Group Policy Management Editor page, go to this path Computer Configuration > Policies > Windows Settings > Security Settings > Public Key Policies. After expanding Public Key Policies, Right-click on Automatic Certificate Request Setting>New>Automatic Certificate Request. This opens up the Setup wizard</p>
<p align="center"><img src="https://i.imgur.com/qIWtPza.png" height="50%" width="50%" alt="image"/>

<p>8. On the Welcome to the  Automatic Certificate Request setup Wizard, click NEXT.</p>
<p align="center"><img src="https://i.imgur.com/CoFyPJp.png" height="50%" width="50%" alt="image"/>

<p>9. On the Certificate Template page, select Computer and click NEXT.</p>
<p align="center"><img src="https://i.imgur.com/XUrvS73.png" height="50%" width="50%" alt="image"/>

<p>10. On the Completing the Automatic Certificate Request setup Wizard, click FINISH</p>
<p align="center"><img src="https://i.imgur.com/03fZhRv.png" height="50%" width="50%" alt="image"/>

<br>

<h3>*Linking the GPO</h3>
<p>1. Next is to link the GPO. On the Group Policy Management page, right-click on the domain and click on Link an existing GPO</p>
<p align="center"><img src="https://i.imgur.com/Pimstge.png" height="50%" width="50%" alt="image"/>

<p>2. On the Select GPO page, select the GPO edited for certificates and click OK</p>
<p align="center"><img src="https://i.imgur.com/e1OzekZ.png" height="50%" width="50%" alt="image"/>

<p>3. After that, a <b><i>"gpupdate /force"</i></b> in powershell to force this update</p>
<p align="center"><img src="https://i.imgur.com/jzVDMGi.png" height="50%" width="50%" alt="image"/>

<br>

<h2>Verifying that the certificate is issued</h2>
<p><b>Method 1: Login to any VM in your organization</b></p>
<p>1. On the member server(MS1), typed Win + R. And typed mmc and click OK</p>
<p align="center"><img src="https://i.imgur.com/oRsMcTV.png" height="50%" width="50%" alt="image"/>

<p>2. The console opens, right click on File and select Add/Remove Snap-in</p>
<p align="center"><img src="https://i.imgur.com/cOlIMSP.png" height="50%" width="50%" alt="image"/>

<p>3. On the Add or Remove Snap-ins page, select Certificates and click Add</p>
<p align="center"><img src="https://i.imgur.com/OQJw6He.png" height="50%" width="50%" alt="image"/>

<p>4. On the Certificates snap-in page, select Computer account and click NEXT</p>
<p align="center"><img src="https://i.imgur.com/JP1Z6PU.png" height="50%" width="50%" alt="image"/>

<p>5. On the Select Computer page, make sure the Local computer, then click FINISH</p>
<p align="center"><img src="https://i.imgur.com/TtdJQtu.png" height="50%" width="50%" alt="image"/>

<p>6. On the Console1 page, expand Certificates (Local Computer) > Personal > Certificates and there the certificate issued is</p>
<p align="center"><img src="https://i.imgur.com/EgnKBJX.png" height="50%" width="50%" alt="image"/>

<br>

<p><b>On Windows 10</b> - I repeated the above steps on windows 10, and found the certificate issued to win-10</p>
<p align="center"><img src="https://i.imgur.com/Kj6J3Bo.png" height="50%" width="50%" alt="image"/>

<br>

<p><b>On Windows 11</b> - I repeated the above steps on windows 10, and found the certificate issued to win-11</p>
<p align="center"><img src="https://i.imgur.com/twUoGN8.png" height="50%" width="50%" alt="image"/>

<br>

<p><b>Method 2: Login to the Server ADDS</b></p>
<p> On the ADDS, to find the certificates that have been issued, from the Server manger-dashboard, click on Tools > Certificate Authority > Issued Certificates, there the list of certificates issued are </p>
<p align="center"><img src="https://i.imgur.com/IfYm5q6.png" height="50%" width="50%" alt="image"/>

<br>
