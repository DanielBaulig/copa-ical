# NGINX COPA iCal Proxy

COPA is a local soccer training facility that provides subscription based unlimited training classes. Both my kids go there for soccer practice during soccer off-seasons. COPA uses DaySmart Recreation for training session booking and management. DaySmart Recreation offers a calendar export to seemlessly integrate booked sessions into your existing calendar application. However, the output of the DaySmartSmart Recreation endpoint has a formatting bug and includes unescaped commas in the iCal LOCATION property, leading to the location not showing correctly in my calendar.

I created this NGINX configuration that can be included on any given endpoint
that will proxy requests to DaySmart Recreation and slightly reformat the output
to be spec compliant and make some other minor changes to it, too.

## Usage

Include the configuration on any NGINX endpoint. Then create a calendar subscription in your calendar application (e.g. Apple Calendar) and point it at the endpoint adding the id and k query parameters from the original iCal calendar subscription URL to the path, e.g.

yourdomain.com/yourendpoint/{id}/{k}
