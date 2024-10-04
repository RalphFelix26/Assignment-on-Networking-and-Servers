# Python script to check the status of the subdomains
# Step 1: Install Necessary Libraries
pip install requests tabulate
# Step 2: Python Script
# Create a file subdomain_status_checker.py 
import requests
import time
from tabulate import tabulate
# List of subdomains to check
subdomains = ["http://sub1.awesomeweb", "http://sub2.awesomeweb"]

# Defining function to check the status of subdomains
def check_subdomains():
    status_table = []
    for subdomain in subdomains:
        try:
            response = requests.get(subdomain, timeout=5)
            if response.status_code == 200:
                status_table.append([subdomain, "Up"])
            else:
                status_table.append([subdomain, f"Down (HTTP {response.status_code})"])
        except requests.exceptions.RequestException:
            status_table.append([subdomain, "Down"])
    
    return status_table

if __name__ == "__main__":
    while True:
        
        status_table = check_subdomains()
              
        # To print the status in tabular format
        print(tabulate(status_table, headers=["Subdomain", "Status"], tablefmt="grid"))
                
        time.sleep(60)
