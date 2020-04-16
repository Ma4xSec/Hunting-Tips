![Color_MAX](https://user-images.githubusercontent.com/55370554/76710262-b7dae300-670e-11ea-88e0-e1d95fc353ab.jpg)

## **Note : Those tips collected from many resources (Facebook , Twitter , Meduim , Portswigger...etc.) and some scenarios that I have seen while hunting.Sorry, I don't put the names of the writer of these tips because they are so many, but they are very much appreciated**.
                            **Try the imposssible, that’s the only way amazing things happen**
1. [jwt decoder](https://jwt.io/#debugger-io) </br>

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

35. Always create two accounts and see if you can get the objects of the other account by changing out the id parameters from account 1 with those from account 2 while using the same session cookie as account 1 **IDOR**

36.  If you find an application where some type of PIN is using to unlock the app or verify identity and if that request can't be captured by proxy then it's possible that application is storing pin internally. Find that file and delete or edit to bypass PIN protection.

37. If you found apk file  on the server download it and change the extention to .zip and extract it. Read the source files maybe you find several hidden endpoints

38. Some CSRF tips
- change single character
- send empty value of token
- clickjaking
- remove it from the requests
- use another user's valid token
- Csrf protection by Referer header ? Remove the header , Add in form *<meta name="Referer" content="no-reference">*
- try to decrypt hash (maybe CSRF token is a hash)
- Analyze Token (with burp)
- Sometimes Anti-CSRF token is composed of two parts, one of them remains static while the other one dynamic.          "837456mzy29jkd911139" for one request the other time "837456mzy29jkd337221" if you notice, "837456mzy29jkd" part of the token   remain same, send the request with only the static part.
- Sometimes anti-csrf check is dependent on User-Agent as well. If you try to use mobile/tablet user agent, application may not even check for anti-csrf token
- try change csrf token value to true or 1 maybe will working
- try create new account maybe csrf token same for all account try harder

39. Some web sites are tolerant of alternate HTTP request methods when performing an action so try other methods !!

40. However, the response containing a redirect might still include some sensitive data .

41. IDORs Tips:
- Don’t ignore encoded and hashed IDs try to decoding or cracking
- Try creating a few accounts to analyze how these IDs are created. You might be able to find a pattern that will allow you to     predict IDs belonging to other users
-  it might be possible to leak random or hashed IDs via another API endpoint, on other public pages in the application (profile page of other users, etc), or in a URL via referer
- Offer the application an ID, even if it doesn’t ask for it, If no IDs are used in the application generated request, try adding it to the request. Try appending id, user_id, message_id or other object reference params and see if it makes a difference to the application’s behavior.
> GET /api_v1/messages --> GET /api_v1/messages?user_id=ANOTHER_USERS_ID
- HPP (HTTP parameter pollution): supplying multiple values for the same parameter can also lead to IDOR. Applications might not anticipate the user submitting multiple values for the same parameter and by doing so, you might be able to bypass the access control set forth on the endpoint.
> GET /api_v1/messages?user_id=ANOTHER_USERS_ID

to
>GET /api_v1/messages?user_id=YOUR_USER_ID&user_id=ANOTHER_USERS_ID

or
> GET /api_v1/messages?user_ids[]=YOUR_USER_ID&user_ids[]=ANOTHER_USERS_ID

- Sometimes, switching around the file type of the requested file may lead to the server processing authorization differently. For example, try adding .json to the end of the request URL and see what happens.



42. While hunting on a Node js target always pass '%ff' as URL like https://target.com/%ff, Most times it causes an error that leaks full path of the site and some bb programs accept it as a valid issue.

43. For example an application might configure rules like the following:
DENY: POST, /admin/deleteUser, managers 
This rule denies access to the POST method on the URL /admin/deleteUser, for users in the managers group. Maybe we can bypass it using some non-standard headers like 
> X-Original-URL and X-Rewrite-URL Example:

might be possible to bypass the access controls using a request like the following:

> POST / HTTP/1.1 </br>
X-Original-URL: /admin/deleteUser

44. IDORs are everywhere don't focus only on parameters try to change anything like :
> /downloads/2.txt (set 2.txt to 1.txt)

> /Private-Posts/1234 (set 1234 to 4567)

You can try everywhere dude !!

45. I will explain what i mean with example , If i want to update my password mybe i will go through 3 steps to update it 
- load the current info (username,password,email).
- Submit changes.
- Review the changes and confirm. 

Sometimes, a web site will implement rigorous access controls over some of these steps, but ignore others
suppose access controls are correctly applied to the first and second steps, but not to the third step. Effectively, the web site assumes that a user will only reach step 3 if they have already completed the first steps, which are properly controlled. Here, an attacker can gain unauthorized access to the function by skipping the first two steps and directly submitting the request for the third step with the required parameters

46. Check the errors source code man !

47. In APIs the difference between a PUT and a POST request is that put overwrites whatever is there previously

48. When you get 403 status code try to brute force dirs & files

49. I don't know if this tip working always but when you get 403 and you brute force and for example if you got directory "max" so the url will look like https://www.example.com/max the tip here is to try to put slash after the name of directory so it will look like this  https://www.example.com/max/ 
> the link that i got this tip from </br>
https://medium.com/@mehedi1194/how-i-get-my-first-swag-from-sidn-sensitive-data-expose-fc8e202fef85

50. Host Header Tips:
 - change host header to any value maybe it will redirect you to the local host if it's the first virtual host in the server configration file
 - try to inject the Host Header with values like 
 > - dev.example.com </br>
 >  - stage.example.com </br>
 >  - test.example.com </br>
   
 - you can try to inject the host header with some values manually 
  > - dev </br>
  > - stage </br>
  > - test </br>
  > - localhost </br>
  > - staging </br> 
  > - development </br>
  > - secure </br>
  > - uat </br>
  > - status </br>

or you can use [virtual host discovry](https://github.com/jobertabma/virtual-host-discovery) to automate the proccess 

- try xss on the host header (low impact)
- try host header injection in reset password (high impact)

51. Race condition bugs are mostly on those endpoints which deal with adding/removing/changing of a particular resource .

52. If you find a website with a login page without a registration feature, try to bruteforce it using dirsearch, dirbuster, etc. Websites that only display a login page and no registration feature indicate that the website can only be accessed by an internal team, and usually such websites have lots of bugs.

53. Try **X-Forwarded-Host** or **X-Host** headers in host header attacks (reset password,etc..)

54. try blind SSRF in the **Referer** header 

55. Try to put link after the url like **https://www.example.com/www.evil.com** maybe it will get the content of evil.com and it will be SSRF or will redirect you to evil.com and it will Open redirection (found it 2 times as SSRF)

56. Try arrays with the json data  for example reset password 
>  {"Email":"max@yahoo.com"} so you can try to set it to {"Email":["evil@yahoo.com","max@yahoo.com"]} 

happend with me and i got 2 emails on evil@yahoo.com and max@yahoo.com and it was nice trick 

57. Some Path Traversal & LFI Tips:
- if the server checks for some path like **/var/www/html**
> https://www.example.com?path=/var/www/html/photo.png

so we can try
> https://www.example.com?path=/var/www/html/../../../etc/passwd

- If the server checks for extention like .png we can use null byte 
>  https://www.example.com?path=shell.php%00.png

- try // and \/
- try ....//
- try  non-standard encoding like
> ..%c0%af..%c0%af..%c0%afetc/passwd </br>
or double encoding </br>
..%252f..%252f..%252fetc/passwd

- If you're playing with windows server you can use ../ or ..\ 


58. I'll tell you small tip it will help you reduce potential cases to search for JWT on  
>  JWT are used for Authorization not for Authentication.

59. API Penetration Testing Tools,Tips,Guides,Checklists and Tutorials :-

- [beginners guide restful api part 1](https://payatu.com/beginners-guide-restful-api-vapt-part-1/)
- [beginners guide restful api part 2](https://payatu.com/beginners-guide-restful-api-vapt-part-2/)
- [authentication schemes rest api](https://payatu.com/authentication-schemes-rest-api/)
- [9 Types of Tests To Perform On Your APIs](https://nordicapis.com/9-types-of-tests-to-perform-on-your/)
- [Api Testing](https://www.guru99.com/api-testing.html)
- [Testing rest api manually](https://www.guru99.com/testing-rest-api-manually.html)
- [https://blog.securelayer7.net/web-services-api-penetration-testing-part-1/](https://blog.securelayer7.net/web-services-api-penetration-testing-part-1/)
- [Web Services and API Penetration Testing Part #2](https://blog.securelayer7.net/web-services-api-penetration-testing-part-2/)
- [API Security Testing : Rules And Checklist](https://www.testbytes.net/blog/api-security-testing-rules-and-checklist/)
- [https://www.qasymphony.com/blog/automated-api-testing-tutorial/](https://www.qasymphony.com/blog/automated-api-testing-tutorial/)
- [API Security Checklist](https://github.com/shieldfy/API-Security-Checklist)
[API Security Testing – How to Hack an API and Get Away with It (Part 1 of 3)](https://smartbear.com/blog/test-and-monitor/api-security-testing-how-to-hack-an-api-part-1/)
[API Security Testing – How to Hack an API and Get Away with It (Part 2 of 3)](https://smartbear.com/blog/test-and-monitor/api-security-testing-how-to-hack-an-api-part-2/)
- [API Security Testing – How to Hack an API and Get Away with It (Part 3 of 3)](https://smartbear.com/blog/test-and-monitor/api-security-testing-how-to-hack-an-api-part-3/)
- [Hack Your API First – learn how to identify vulnerabilities in today’s internet connected devices with Pluralsight](https://www.troyhunt.com/hack-your-api-first-learn-how-to/)
- [Exploiting Api’s with Postman and Google Chrome](https://medium.com/bugbountywriteup/exploiting-apis-with-postman-and-google-chrome-ade13ce74e2b)
- [API security testing - tips to prevent getting pwned](https://assertible.com/blog/api-security-testing-tips-to-prevent-getting-pwned)
- [API Testing Tutorial – Quick Guide on the Basics](https://reqtest.com/testing-blog/api-testing-tutorial/)
- [Astra](https://github.com/flipkart-incubator/Astra)
- [ Susanoo is REST API security testing framework](https://github.com/ant4g0nist/Susanoo)
- [syntribos is a python API security testing too](https://github.com/openstack/syntribos)
- [Fuzzapi is a tool used for REST API pentesting](https://github.com/Fuzzapi/fuzzapi)
- [The DevSecOps toolset for REST APIs](https://github.com/BBVA/apitest)
- [20 Best API Testing Tools in 2020: REST & SOAP Web Services ](https://www.guru99.com/top-6-api-testing-tool.html)
- [REST Assured: Penetration Testing REST APIs Using Burp Suite: Part 1 – Introduction & Configuration](https://www.mindpointgroup.com/blog/cyber-security/rest-assured-penetration-testing-rest-apis-using-burp-suite-part-1-introduction-configuration/)
- [REST Assured: Penetration Testing REST APIs Using Burp Suite: Part 2 – Testing
by Kory Ponting](https://www.mindpointgroup.com/blog/cyber-security/rest-assured-penetration-testing-rest-apis-using-burp-suite-part-2-testing/)
- [REST Assured: Penetration Testing REST APIs Using Burp Suite: Part 3 – Reporting](https://www.mindpointgroup.com/blog/rest-assured-penetration-testing-rest-apis-using-burp-suite-part-3-reporting/)
- [Simplifying API Pentesting With Swagger Files](https://rhinosecuritylabs.com/application-security/simplifying-api-pentesting-swagger-files/)

60. Try to encode character of the parameter maybe it will bypass the WAF
> ?page='-alert()-'  to    ?pa%67e='-alert()-'

you can encode characters manully from here [ASCII Encoding Reference-W3Schools](https://www.w3schools.com/tags/ref_urlencode.ASP)

61. To bypass Rate Limit try to add random parameter on the last endpoint
>  https://blabla.com/page1/page2?bypass


62.If you wanna use amass faster you can use it on the passive mode 
> amass enum -d blabla.com -passive 

63. Recon tool for github to search for sensitive info [gitrob](https://github.com/michenriksen/gitrob)

64. You can use ffuf to bruteforce s3 bucket 
> ffuf -u http://FUZZ.company.s3.amazonaws.com -w bucket.txt


ـــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــــ

If you have any improvments feel free to drop them [MrMax](https://twitter.com/MrMax404).




