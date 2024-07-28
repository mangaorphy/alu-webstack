The script starts by assigning the first argument (the domain) to the $domain variable.
It then checks the number of arguments passed ($#) to the script:
If there are two arguments (domain and subdomain), the $sub variable is assigned the second argument.
If there is only one argument (domain), the $sub variable is assigned an array of subdomains: "www" "lb-01" "web-01" "web-02".
The script then enters a for loop that iterates over the $sub array (or the single subdomain if provided as an argument).
For each subdomain in the $sub array, the script performs the following steps:
Constructs the full subdomain name by appending the current subdomain to the $domain variable ("$subdomain.$domain").
Uses the dig command to retrieve the DNS information for the constructed subdomain.
Pipes the output of dig to grep to extract the "ANSWER SECTION" of the DNS response.
Pipes the output further to tail to get the last line of the "ANSWER SECTION", which contains the DNS record type and the destination IP address.
Uses awk to format the output into a readable string, which is stored in the $output variable.
Finally, the script prints the $output variable, which displays the formatted information about the current subdomain.
The key points are:

If a single argument (the domain) is provided, the script will use a default set of subdomains ("www" "lb-01" "web-01" "web-02").
If two arguments (domain and subdomain) are provided, the script will use the specified subdomain.
The script uses a combination of dig, grep, tail, and awk to extract and format the necessary information about each subdomain.
