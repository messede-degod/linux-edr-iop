## Linux-EDR-IOP
This repo tracks "indicators of presence" for linux EDRs, AVs and Monitoring Tools.

This is a community effort, PRs are encouraged and welcome. 

THCs [hackshell](https://github.com/hackerschoice/hackshell) uses IOPs from this repo and provides a easy way to check for the presense of EDRs on a given system.

Files without absolute paths should be checked in all directories present within $PATH

| vendor  | files  | systemd service name  | website |
|---|---|---|---|
| falco  |   | falco, falco-bpf, falco-custom, falco-kmod| https://falco.org/ |
| wazuh  |   | wazuh-agent| https://wazuh.com/ |
| ossec  | /etc/rc.d/init.d/ossec  |   | https://www.ossec.net/ |
| osquery  | osqueryi  |  osqueryd | https://www.osquery.io/ |
| MS defender  | mdatp  | mdatp  | https://www.microsoft.com/en-us/security/business/endpoint-security/microsoft-defender-endpoint |
| CrowdStrike  |   |  falcon-sensor | https://www.crowdstrike.com/platform/endpoint-security/ |
| CarbonBlack  |   | cbsensor | https://www.broadcom.com/products/carbon-black/threat-detection-and-response/endpoint-detection-and-response |
| McAfee  |   |  MFEcma | 
| Trend Micro  |   |  ds_agent | https://help.deepsecurity.trendmicro.com/20_0/on-premise/agent-install.html# |
| Blackberry  cyPROTECT |  cylance  | cylancesvc | https://docs.blackberry.com/en/unified-endpoint-security/blackberry-ues/setup/setup/Setting-up-BlackBerry-Protect-Desktop/Install_the_Protect_Desktop_agent_for_Linux |
| Blackberry  cyOPTICS |    | cyoptics | https://docs.blackberry.com/en/unified-endpoint-security/blackberry-ues/setup/setup/Steps-to-set-up-BlackBerry-Optics/Install-the-BlackBerry-Optics-agent-on-endpoint-devices |
| SentinelOne  |  /opt/sentinelone/bin/sentinelctl  |  | https://www.sentinelone.com/ |
| Sophos Intercept X  |    | sophoslinuxsensor |
| Sophos SPL  |    | sophos-spl |
| Palo Alto Networks Cortex XDR  |  /opt/traps/bin/cytool  | traps_pmd |
| Bitdefender EDR / GravityZone XDR  |  /opt/bitdefender-security-tools/bin/bdconfigure  | bdsec |
| Cisco Secure Endpoint  |  /opt/cisco/amp/bin/ampcli  |  |
| Cybereason                 |  | cybereason-sensor |
| Elastic Security            | /usr/bin/elastic-agent | elastic-agent |
| Intezer  |  /usr/local/bin/intezer-analyze  |  |
| Webroot Endpoint Protection  | [No Linux Support] | [No Linux Support] |
| ESET Endpoint Security      |  | eraagent |
| ESET AV      |  | eea, eea-user-agent |
| Rapid7 INSIGHT IDR  |  | ir_agent |
| Rapid7 NG AV  |  | armor |
| WithSecure (F-Secure ) Elements Agent | /opt/f-secure/linuxsecurity/bin/activate, /bin/scand |  f-secure-linuxsecurity-activate, emit_scand_service |
| WithSecure (F-Secure ) Elements Connector (for Countercept)| /opt/f-secure/fspms/fspms.conf, /etc/opt/f-secure/fspm/fspms.conf |  |
| WithSecure (F-Secure ) Policy Manager | /opt/f-secure/fspmc/fspmc |  |
| WithSecure (F-Secure ) Linux Security |/opt/f-secure/fsbg/bin/master-switch, /opt/f-secure/fsav/bin/fsims |  |
| IBM QRADAR    | /etc/reaqtahive.d/keeperx | keeperx |
| SonicWall Capture Client  (uses sentinelone under the hood)  | /opt/sentinelone/bin/sentinelctl |  |
| Kaspersky Endpoint Security  | /etc/init.d/kesl, /opt/kaspersky/klnagent/lib/bin/setup/postinstall.pl, /opt/kaspersky/klnagent64/lib/bin/setup/postinstall.pl | kesl |
| Kaspersky Endpoint Security (Elbrus Edition)  | /etc/init.d/kesl-supervisor, /opt/kaspersky/kesl/bin/kesl-setup.pl| kesl-supervisor |
| Kaspersky Industrial CyberSecurity  | /etc/init.d/kics, /opt/kaspersky/kics/bin/kics-setup.pl | kics |
| Kaspersky Embedded Systems Security  | /etc/init.d/kess, /opt/kaspersky/kess/bin/kess-setup.pl | kess |
| TrendMicro - Deep Instinct    | /etc/init.d/ds_agent, /opt/ds_agent/dsa | ds_agent |
| TrendMicro - Server Protect   | /etc/init.d/splx,  /opt/TrendMicro/SProtectLinux/SPLX.util/add_splx_service |  |
| ThreatConnect              | /opt/threatconnect-envsvr/threatconnect-envsvr.jar, /etc/init.d/threatconnect-envsvr |  |
| Filebeat (not AV/EDR, but used to ship logs)| /etc/filebeat/filebeat.yml| filebeat| |
| Secureworks Taegis   EDR     | /opt/secureworks/taegis-agent/bin/taegisctl |  |
| Secureworks redcloak AV  | /opt/secureworks/redcloak/bin/redcloak_start.sh |  |
| Secureworks NGAV | /usr/bin/secureworks/taegis-ngav (directory) | |
| Huntress                  | [No Linux Support] | [No Linux Support] |
| Sumo Logic Cloud SIEM     | /usr/local/SumoCollector/uninstall, /opt/SumoCollector/uninstall, /opt/SumoCollector/config/user.properties |  |
| Sumo Logic OTEL Collector     | /etc/otelcol-sumo/sumologic.yaml | otelcol-sumo |
| Acronis Cyber Protect      | /usr/lib/Acronis/BackupAndRecovery/uninstall/uninstall |  |
| Fortinet FortiEDR        | /opt/FortiEDRCollector/scripts/fortiedrconfig.sh |  |
| Fortinet FortiSIEM      | /opt/fortinet/fortisiem/linux-agent/bin/fortisiem-linux-agent-uninstall.sh, /etc/init.d/fortisiem-linux-agent |  |
| LogRhythm   System   Monitor|  /etc/init.d/scsm, /opt/logrhythm/scsm/config/scsm.ini |  |
| LogRhythm   Axon|  /etc/logrhythm/lragent_config.json, /bin/logrhythm/lr-agent | lr-agent.logrhythm |
| BlackFog                  | [No Linux Support] | [No Linux Support] |
| Qualys EDR Cloud Agent | /usr/local/qualys/cloud-agent/bin/qualys-cloud-agent.sh, /etc/init.d/qualys-cloud-agent  |  |
| ThreatDown (MalwareBytes) Nebula EDR Agent |  | mbdaemon |
| LimaCharlie Agent          | /etc/init.d/limacharlie |  limacharlie |
| Checkpoint                 | /var/log/checkpoint/cpla/cpla.log  | cpla |
| FireEye/Trellix   EDR     | /opt/fireeye/bin/xagt | xagt |
| FireEye/Trellix   Endpoint Security     | /opt/isec/ens/threatprevention/bin/isectpdControl.sh | |
| FireEye/McAfee/Trellix   Agent     | /opt/McAfee/agent/scripts/uninstall.sh, /opt/McAfee/Agent/bin/CmdAgent	 |  |
| FireEye/McAfee/Trellix   SIEM Collector     | /opt/Trellix/siem_collector.conf, /opt/McAfee/siem/mcafee_siem_collector.conf |  |
| Symantec    EDR     | /opt/Symantec/sdcssagent/AMD/system/AntiMalware.ini, /etc/init.d/sisamdagent, /opt/Symantec/symantec_antivirus/uninstall.sh | |
| Symantec Linux Agent| /usr/lib/symantec/status.sh |  |
| Comodo AV  | /opt/COMODO/post_setup.sh |  |
| Comodo Client Security  | | itsm |
| Avast                      | /etc/init.d/avast, /var/lib/avast/Setup/avast.vpsupdate | avast |
| AVG                        | /etc/init.d/avgd, /opt/avg/av/bin/avgsetup |  |
| Tanium                     | /opt/Tanium/TaniumClient/TaniumClient | taniumclient |
| CyberArk                  | /opt/cyberark/epm/bin/epmcli, /opt/cyberark/epm/sbin/epmd | epmd |
| PT Swarm | /var/pt/ptaf-deploy/current/install.sh,  /var/pt/tmp/ptaf-deploy/install.sh, /var/pt/infra/current/deploy.sh |  |
| Splunk   | /opt/splunkforwarder/bin/splunk , /etc/init.d/splunk |  |
|Kseya RocketCyber | /usr/local/rocketcyber/linux-agent-updater | rocketcyber |
| OPSWAT                    | ?? | ?? |
| Absolute Software          | ?? | ?? |
| Raytheon Cyber            | ?? | ?? |
| DeepInstinct               | ?? | ?? |
| Cynet 360                 | ?? | ?? |
| Verdasys/Digital Guardian  | ?? | ?? |