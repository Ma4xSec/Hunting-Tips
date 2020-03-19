![Color_MAX](https://user-images.githubusercontent.com/55370554/76710262-b7dae300-670e-11ea-88e0-e1d95fc353ab.jpg)


## **Note : These tips collected from many resources (Facebook , Twitter , Meduim , Portswigger...etc.) and some scenarios that I have seen while hunting**.

1. jwt decoder --> [jwt.io](https://jwt.io/#debugger-io) </br>

2. Some useful ways of breaking out of a string literal are
  * '-alert(document.domain)-'
  * ';alert(document.domain)//

3. A common behviour in cdn's is that injecting a host header belonging to the
  same account would serve that specific host, you can escalate request
  smuggling using that simple trick

4. If we have site reandering your input as PDF and you can import it as PDF we
   can try SSRF with something like  
   > <iframe src="http://169.254.169.254/latest/meta-data">

5. Secert path in wp sites --> /wp-content/plugins/jsmol2wp/j2s/J/rendersurface/

6. To find the clouding service you can search in youtubbe --> (siteName + cloud)
> verizon media  + cloud </br>
https://www.youtube.com/results?search_query=verizon+media++%2B+cloud

7. Some AWS metadata pathes:
  * http://169.254.169.254/latest/meta-data/local-hostname/
  * http://169.254.169.254/latest/meta-data/iam/security-credential
  * http://169.254.169.254/latest/dynamic/instance-identity/document
  
8. If you wanna find some internal code of companies some sample code or new features try:
> repl.it intext:Example.com

9. If you got access denied message while using awscli try :
> aws s3 ls s3://[bucketname] --nosign-request

10. The HEAD method is the same as POST but without body maybe you will need this trick !!

11. if you found firebase API key in Android app use Pyrebase it's a simple python wrapper for the Firebase API to test Authentication,
DB and storage permissions.

12. Always try to convert parameters to arrays you may get unexpected results maybe xss bypass </br>
    Example **page?path=/abc**  _To_   **page?path['']=/abc** </br>
    
13. To discover domains deployed on Github for subdomain takeover try with google dorks </br>
  * intext:"There isn't a Github Pages site here"
  * intext:"Site not found . Github Pages"
  
14. Payload to test XSS,SQLI and CSTI
  * ' "<svg/onload=prompt(5);>{{7*7}} 
    
15. Extract Subdomains for ip range with nmap
  * nmap IP_range_sn | grep "domain" | awk'{print $5}' 
  
16. if you trying IDOR in APIs and got 401,403 you can try :
  * {"id":[1234]}
  * {"id":{"id":1234}}
  * url?id=real_id&id=victm
  * {"id":"*"}
  
  17. If we have domain like example.com try to make mail with
      max@example.com if there is no validation to the email maybe
      it's give you access or privileges
      
 18. if you test blacklist SSRF you can try to encode 1 or 2 or 3 octs of ip like **0251.254.169.254**
 
 19. If you come across /api.json in AEM instance try cache poisoning (Host, X-Forwarded-Server,X-Forwarded-Host)
 
 20. trik to get uuid of any user try to register with the same username or email may be uuid will leak on the resbonse.
 
 21. [dnsdumpster](https://dnsdumpster.com/) is a FREE domain research tool that can discover hosts related to a domain. Finding visible hosts    from the attackers perspective is an important part of the security assessment process!!!
 
 22. [UDP Port Scanner](https://www.ipvoid.com/udp-port-scan/)
 
 23. Maybe company uses deffrent domains or maybe there are applications on other domains so we can use "Copy Right Singture" on google  (**intext:"Facebook © 2019"**)
 
 24. If an app uses markdown (xss) : click here (**javascript:alert(1)**)
 
 25. If you found "limit" parameter (**/page?limit=10**) you can try to change it
     to long value like (**/page?limit=9999999999999**) --> layer 7 dos atack
     
 26. When you test for SSRF try to change **HTTP/1.1** to **HTTP/0.9**and
     remove the host header (to bypass some fixes and validations)
     
 27. Run UDP scan if port 500 is open run (**ike-probe**) to see if it's vulnerable to Shared Secret Hash Leakage Weakness
 
 28. If you wanna bypass cloudflare protection and find the origin ip try [WhoIsRequest](https://whoisrequest.com/history/)  and check the Domain history data
 
 29. You can enumerate directories in some buckets with Wfuzz
 > http(S)://**bucket-name-address-here**/FUZZ/
 
 and check the 200 status code without content
 
 30. For example to find any subdomain points to yahho on Censys
 > 443.https.tls.certificate.parsed.extensions.subject_alt_name.dns_names:Yahoo.com
 
 31. Some Keywords to search for in JS files:
  * api
  * internal
  * url
  * var=
  * //
  * https://
  * CompanyName.com
  * Location.search
  
32. In url you can try those circumvents: 
  * https://expected-host@evil-host
  * https://evil-host#expected-host
  * https://expected-host.evil-host
  * You can URL-encode characters to confuse the URL-parsing code
  
33. There are some endpoints shows json with the (**content type: Text/html**) CHANGE it to </br> (**Content Type : application/json**)
(the file contains special  character) --> Easy xss

34. If the **GET & POST** methods are only allowed so we can use **X-HTTP-Method-Override** with PUT method leads to RCE.
 
