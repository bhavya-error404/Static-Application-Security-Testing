
# Cleartext Submission of Sensitive Data

## 1. App Transport Security Bypass
Application Transport Security (ATS) ensures secure communication between the app and the backend. 
It is provided in iOS.

**Implementation:**

Add NSAppTransport key in information property list file (info.plist). The value type will be dictionary. In the key named NSAppTransport
specify the dictionry items you want to allow or disallow. For example allowing random web views(these will be treated as exception i.e. insecure web views)

1. Allowing some insecure views
>   \<key>NSAppTransportSecurity\</key>
> 
>   \<dict>
> 
>    \<key>NSAllowsArbitraryLoadsInWebContent\</key>
>
>    \<true/>
> 
>   \</dict>

2. Disabling ATS for all domains  
   `<key>NSAppTransportSecurity</key>`  
`<dict>`  
`<key>NSAllowsArbitraryLoads</key>`  
`<true/>`  
`</dict>`  

3. Disabling ATS for some domains
   <key>NSAppTransportSecurity</key>
<dict>
  <key>NSExceptionDomains</key>
  <dict>
    <key>example.com</key>
    <dict>
      <!--Include to allow subdomains-->
      <key>NSIncludesSubdomains</key>
      <true/>
      <!--Include to allow HTTP requests-->
      <key>NSTemporaryExceptionAllowsInsecureHTTPLoads</key>
      <true/>
      <!--Include to specify minimum TLS version-->
      <key>NSTemporaryExceptionMinimumTLSVersion</key>
      <string>TLSv1.2</string>
    </dict>
  </dict>
</dict>

