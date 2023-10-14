# find-win-block-traffic
Procedure to find blocking rules within Windows

Windows does not enable logging of blocked traffic.

Turn it on in powershell:

auditpol /set /subcategory:"Filtering Platform Packet Drop" /success:enable /failure:enable  
auditpol /set /subcategory:"Filtering Platform Connection" /success:enable /failure:enable  

Export the current state of the firewall:

netsh wfp show state

This creates a XML file that dumps the current filters.

Open Windows Event Viewer and Browse to Windows Logs > Security

Note - Under "Keyword" look for "🔒 Audit Failure"

Select one of the events and search for the filter runtime ID - FilterRTID

Open the previously created XML file and search for the FilterRTID number. This is the filter! 

Scrolling up within the XML will provide the rule info.

Happy Troubleshooting! 

👾     👾     👾
          💥
🚀


Procedure to see logged in user in powershell:
net user
