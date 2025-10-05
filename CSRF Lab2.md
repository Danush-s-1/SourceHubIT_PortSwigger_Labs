

    -> Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.
    
    -> Send the request to Burp Repeater and observe that if you change the value of the csrf parameter then the request is rejected.
    
    -> Use "Change request method" on the context menu to convert it into a GET request and observe that the CSRF token is no longer verified.

    -> If you're using Burp Suite Professional, right-click on the request, and from the context menu select Engagement tools / Generate CSRF PoC. Enable the option to include an auto-submit script and click "Regenerate".

    -> Alternatively, if you're using Burp Suite Community Edition, use the following HTML template. You can get the request URL by right-clicking and selecting "Copy URL".
    
    <form action="https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email">
        <input type="hidden" name="email" value="anything%40web-security-academy.net">
    </form>
    <script>
            document.forms[0].submit();
    </script>
    
    -> Go to the exploit server, paste your exploit HTML into the "Body" section, and click "Store".
    
    -> To verify if the exploit will work, try it on yourself by clicking "View exploit" and checking the resulting HTTP request and response.
    
    -> Change the email address in your exploit so that it doesn't match your own.
    
    -> Store the exploit, then click "Deliver to victim" to solve the lab.

