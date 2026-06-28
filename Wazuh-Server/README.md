# Wazuh Server

## Wazuh Architecture
The Wazuh has 3 central components
1. Wazuh Server
2. Wazuh Indexer
3. Wazuh Dashboard

![Alt text](Images/wazuh-components.png)

As installing them separately requires a lot of resources. We will install these components in a single machine.

## Installation
Here is the one-line code to install Wazuh.


```curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a```


If it is not working, it is due to the version number. You can refer to Wazuh Documentation, which I will provide below.

After installation is done, the default credentials will be provided along with the web interface URL.
```
INFO: --- Summary ---
INFO: You can access the web interface https://<WAZUH_DASHBOARD_IP_ADDRESS>
    User: admin
    Password: <ADMIN_PASSWORD>
INFO: Installation finished.
```

## Use Case
| **Endpoint security** | **Threat intelligence** | **Security operations** | **Cloud security** |
| --- | --- | --- | --- |
| Configuration assessment | Threat hunting | Incident response | Container security |
| Malware detection | Log data analysis | Regulatory compliance | Posture management |
| File integrity monitoring | Vulnerability detection | IT hygiene | Workload protection |

# Reference
- https://documentation.wazuh.com/current/quickstart.html
