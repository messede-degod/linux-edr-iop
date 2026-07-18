## Linux-EDR-IOP
This repo tracks "indicators of presence" for linux EDRs, AVs and Monitoring Tools. It is an attempt to allow sysadmins to find out what security tools are installed on systems in order to prevent vendor conflicts.

This is a community effort, PRs are encouraged and welcome.

Files without absolute paths should be checked in all directories present within $PATH

| vendor | files | systemd service name | website |
|---|---|---|---|
| falco | | falco, falco-bpf, falco-custom, falco-kmod | https://falco.org/docs/setup/packages/ |
| wazuh | | wazuh-agent | https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html |
| ossec | /etc/rc.d/init.d/ossec, /etc/init.d/ossec | | https://www.ossec.net/docs/docs/manual/installation/index.html |
| osquery | osqueryi | osqueryd | https://osquery.readthedocs.io/en/stable/installation/install-linux/ |
| MS defender | mdatp | mdatp | https://learn.microsoft.com/en-us/defender-endpoint/linux-support-install |
| CrowdStrike | | falcon-sensor | https://www.crowdstrike.com/tech-hub/endpoint-security/installing-falcon-sensor-for-linux/ |
| CarbonBlack | | cbsensor, cbagentd, cbdaemon | https://techdocs.broadcom.com/us/en/carbon-black/cloud/carbon-black-cloud-sensors/index/cbc-sensor-installation-guide-tile/GUID-CF1B8557-84FB-41C4-89C2-C76EDD920EC0-en.html |
| Trellix ENS Agent (formerly McAfee) | /etc/init.d/cma | MFEcma, cma | https://docs.trellix.com/bundle/endpoint-security-v10-7-13-installation-guide-linux/page/GUID-9C3C9484-DDEA-443C-91B7-3C1342E3C5B4.html |
| Trend Micro | /etc/init.d/ds_agent, /opt/ds_agent/dsa, /opt/ds_agent/ds_agent, /opt/ds_agent/dsa_control | ds_agent | https://help.deepsecurity.trendmicro.com/20_0/on-premise/agent-install.html# |
| Arctic Wolf Aurora Endpoint Security (formerly BlackBerry Cylance PROTECT) | cylance, /opt/cylance/desktop/cylance | cylancesvc | https://docs.arcticwolf.com/en/aurora-endpoint-security/aurora-endpoint-security-setup/aurora-endpoint-security-setup-guide/setting-up-aurora-protect-desktop/installing-the-aurora-protect-desktop-agent-for-linux/install-the-linux-agentmanually |
| Arctic Wolf Aurora Focus (formerly BlackBerry CylanceOPTICS) | | cyoptics | https://docs.arcticwolf.com/en/aurora-endpoint-security/cylancehybrid/installing-the-agents-that-communicate-with-cylancehybrid/installing-agents-on-linux-devices/install-the-aurora-focus-agent-on-the-linux-device |
| SentinelOne | /opt/sentinelone/bin/sentinelctl, /opt/SentinelOne/bin/sentinelctl | | https://alskyline.com/kb/deploy-sentinelone-agent-cli |
| Sophos Intercept X | | sophoslinuxsensor | https://docs.sophos.com/esg/sls/help/en-us/gettingStarted/installSensor/Installing_SLS_from_Sophos_Repo/index.html |
| Sophos SPL | | sophos-spl | https://docs.sophos.com/esg/spl/en-us/help/ServerProtectionAgentTroubleshooting/index.html |
| Palo Alto Networks Cortex XDR | /opt/traps/bin/cytool | traps_pmd | https://docs-cortex.paloaltonetworks.com/r/Cortex-XDR/8.7/Cortex-XDR-Agent-Administrator-Guide/Install-the-Cortex-XDR-agent-for-Linux |
| Bitdefender EDR / GravityZone XDR | /opt/bitdefender-security-tools/bin/bdconfigure | bdsec | https://www.bitdefender.com/business/support/en/77212-157515-bitdefender-endpoint-security-tools-for-linux-quick-start-guide.html |
| Cisco Secure Endpoint | /opt/cisco/amp/bin/ampcli | | https://www.cisco.com/c/en/us/support/docs/security/amp-endpoints/215256-cisco-amp-for-endpoints-mac-linux-cli.html |
| Cybereason | | cybereason-sensor | https://docs.cybereason.com/en/latest/sensorTasks/sensorsForLinux.html |
| Elastic Security | /usr/bin/elastic-agent | elastic-agent | https://www.elastic.co/docs/reference/fleet/install-elastic-agents |
| Intezer | /usr/local/bin/intezer-analyze, intezer-cli, intezer_linux_endpoint_scanner.sh | | https://github.com/intezer/analyze-cli |
| ESET Endpoint Security | | eraagent | https://help.eset.com/protect_install/13.0/en-US/component_installation_agent_linux.html |
| ESET AV | | eea, eea-user-agent | https://help.eset.com/eeau/13.1/en-US/installation.html |
| Rapid7 INSIGHT IDR | | ir_agent | https://docs.rapid7.com/insight-agent/linux-installation/ |
| Rapid7 NG AV | | armor | https://docs.rapid7.com/insight-agent/ngav-install/ |
| WithSecure Elements Agent (formerly F-Secure) | /opt/f-secure/linuxsecurity/bin/activate, /bin/scand | f-secure-linuxsecurity-activate, emit_scand_service, f-secure-linuxsecurity-scand.service, f-secure-linuxsecurity-fsicd.service, f-secure-linuxsecurity-lspmd.service, f-secure-linuxsecurity-statusd.service, f-secure-linuxsecurity-webserver.service, f-secure-linuxsecurity-rmmd.service | https://support.withsecure.com/userguides/data/pdf/fsls64-adminguide-eng.pdf |
| WithSecure Elements Connector (for Countercept) (formerly F-Secure) | /opt/f-secure/fspms/fspms.conf, /etc/opt/f-secure/fspms/fspms.conf | | https://support.withsecure.com/userguides/data/pdf/ws_elements_connector_eng.pdf |
| WithSecure Policy Manager (formerly F-Secure) | /opt/f-secure/fspmc/fspmc | | https://support.withsecure.com/userguides/data/pdf/fspm-16.00-adminguide-eng.pdf |
| WithSecure Linux Security (formerly F-Secure) | /opt/f-secure/fsbg/bin/master-switch, /opt/f-secure/fsav/bin/fsims | | https://support.withsecure.com/userguides/data/pdf/fsls64-adminguide-eng.pdf |
| IBM QRadar EDR (formerly ReaQta) | /etc/reaqtahive.d/keeperx, /etc/reaqtahive.d/keeperx.env | keeperx | https://www.ibm.com/docs/en/security-qradar/security-edr/saas?topic=agent-installing-qradar-edr-linux-endpoints |
| SonicWall Capture Client (uses sentinelone under the hood) | /opt/sentinelone/bin/sentinelctl, /opt/SentinelOne/bin/sentinelctl | | https://www.sonicwall.com/support/knowledge-base/how-to-download-and-install-capture-client/kA1VN0000000Go50AE |
| Kaspersky Endpoint Security | /etc/init.d/kesl, /opt/kaspersky/klnagent/lib/bin/setup/postinstall.pl, /opt/kaspersky/klnagent64/lib/bin/setup/postinstall.pl | kesl | https://support.kaspersky.com/kes-for-linux/12.3.0 |
| Kaspersky Endpoint Security (Elbrus Edition) | /etc/init.d/kesl-supervisor, /opt/kaspersky/kesl/bin/kesl-setup.pl | kesl-supervisor | https://support.kaspersky.com/help/KES4LinuxElbrus/10.1.2/en-US/220087.htm |
| Kaspersky Industrial CyberSecurity | /etc/init.d/kics, /opt/kaspersky/kics/bin/kics-setup.pl | kics | https://support.kaspersky.com/kics-for-linux-nodes/2.0 |
| Kaspersky Embedded Systems Security | /etc/init.d/kess, /opt/kaspersky/kess/bin/kess-setup.pl | kess | https://support.kaspersky.com/kess-linux/3.4.0 |
| TrendMicro - Server Protect | /etc/init.d/splx, /opt/TrendMicro/SProtectLinux/SPLX.util/add_splx_service | splx | https://docs.trendmicro.com/en-us/documentation/serverprotect-for-linux/ |
| ThreatConnect | /opt/threatconnect-envsvr/threatconnect-envsvr.jar, /etc/init.d/threatconnect-envsvr | threatconnect-envsvr | https://knowledge.threatconnect.com/docs/threatconnect-environment-server-installation-guide |
| Filebeat (not AV/EDR, but used to ship logs) | /etc/filebeat/filebeat.yml | filebeat | https://www.elastic.co/docs/reference/beats/filebeat/filebeat-installation-configuration |
| Secureworks Taegis EDR | /opt/secureworks/taegis-agent/bin/taegisctl | | https://docs.taegis.secureworks.com/taegis_agent/linux_install/ |
| Secureworks redcloak AV | /opt/secureworks/redcloak/bin/redcloak_start.sh | redcloak | https://docs.taegis.secureworks.com/integration/connectEndpoint/red_cloak_endpoint_agent_install/ |
| Secureworks NGAV | /usr/bin/secureworks/taegis-ngav (directory) | | https://docs.taegis.secureworks.com/integration/connectEndpoint/taegis_ngav/ |
| Sumo Logic Cloud SIEM | /usr/local/SumoCollector/uninstall, /opt/SumoCollector/uninstall, /opt/SumoCollector/config/user.properties | | https://www.sumologic.com/help/docs/send-data/installed-collectors/linux/ |
| Sumo Logic OTEL Collector | /etc/otelcol-sumo/sumologic.yaml | otelcol-sumo | https://www.sumologic.com/help/docs/send-data/opentelemetry-collector/install-collector/linux/ |
| Acronis Cyber Protect | /usr/lib/Acronis/BackupAndRecovery/uninstall/uninstall | | https://kb.acronis.com/content/56010 |
| Fortinet FortiEDR | /opt/FortiEDRCollector/scripts/fortiedrconfig.sh | | https://docs.fortinet.com/document/fortiedr/7.2.3/administration-guide/551398/installing-a-fortiedr-collector-on-linux |
| Fortinet FortiSIEM | /opt/fortinet/fortisiem/linux-agent/bin/fortisiem-linux-agent-uninstall.sh, /etc/init.d/fortisiem-linux-agent | fortisiem-linux-agent | https://docs.fortinet.com/document/fortisiem/7.5.0/linux-agent-installation-guide/201446/fortisiem-linux-agent |
| Exabeam System Monitor (formerly LogRhythm) | /etc/init.d/scsm, /opt/logrhythm/scsm/config/scsm.ini | | https://docs.logrhythm.com/sysmon/docs/install-a-system-monitor-on-unix-linux |
| Exabeam Axon (formerly LogRhythm Axon) | /etc/logrhythm/lragent_config.json, /bin/logrhythm/lr-agent, /opt/logrhythm/conf/agent_information.json | lr-agent.logrhythm | https://docs.exabeam.com/en/site-collector/all/administration-guide/set-up-collectors/set-up-linux-file-collector.html |
| Qualys EDR Cloud Agent | /usr/local/qualys/cloud-agent/bin/qualys-cloud-agent.sh, /etc/init.d/qualys-cloud-agent | qualys-cloud-agent | https://docs.qualys.com/en/ca/install-guide/linux/installation/ca_install_steps.htm |
| ThreatDown Nebula EDR Agent (formerly Malwarebytes) | | mbdaemon | https://support.threatdown.com/hc/en-us/articles/4413802216467-Add-Linux-endpoints-in-Nebula |
| LimaCharlie Agent | /etc/init.d/limacharlie | limacharlie | https://docs.limacharlie.io/2-sensors-deployment/endpoint-agent/linux/installation/ |
| Checkpoint | /var/log/checkpoint/cpla/cpla.log | cpla | https://sc1.checkpoint.com/documents/R81.10/WebAdminGuides/EN/CP_R81.10_HarmonyEndpointWebManagement_AdminGuide/Topics-HEPWM-R81.10/Harmony-Endpoint-for-Linux-Deploying.htm |
| Trellix EDR (formerly FireEye HX) | /opt/fireeye/bin/xagt | xagt | https://docs.trellix.com/bundle/agent_35_ag/page/UUID-1b8ae3d0-e446-c88a-82e5-a4046bbf9334.html |
| Trellix Endpoint Security - Threat Prevention (formerly FireEye/McAfee) | /opt/isec/ens/threatprevention/bin/isectpdControl.sh, /opt/McAfee/ens/tp/bin/mfetpcli | mfetpd | https://docs.trellix.com/bundle/endpoint-security-v10-7-22-installation-guide-linux/page/UUID-12d6205f-a8b8-1861-9e9f-95a757c40daf.html |
| Trellix Agent (formerly FireEye/McAfee Agent) | /opt/McAfee/agent/scripts/uninstall.sh, /opt/McAfee/Agent/bin/CmdAgent, /opt/McAfee/cma/bin/cmdagent, /opt/Trellix/cma/bin/cmdagent | cma | https://docs.trellix.com/bundle/trellix-agent-5.8.x-product-guide/page/UUID-d0d530fc-9ebf-d313-67b9-5274dcfe56e5.html |
| Trellix SIEM Collector (formerly FireEye/McAfee) | /opt/Trellix/siem_collector.conf, /opt/McAfee/siem/mcafee_siem_collector.conf | mcafee_siem_collector | https://docs.trellix.com/bundle/siem-collector-linux-install-guide/page/GUID-2788BC0E-FA2A-4FE2-BA53-A4C77FF47DAE.html |
| Symantec EDR | /opt/Symantec/sdcssagent/AMD/system/AntiMalware.ini, /etc/init.d/sisamdagent, /opt/Symantec/symantec_antivirus/uninstall.sh | sisamdagent | https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection/all/symantec-single-agent-for-linux-guide/installing-the-client-for-linux-v95193124-d21e2986.html |
| Symantec Linux Agent | /usr/lib/symantec/status.sh | | https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-security/sescloud/Installing-the-Symantec-Agent-and-enrolling-devices/creating-and-installing-a-symantec-linux-agent-ins-v133371951-d4155e8363.html |
| Comodo AV | /opt/COMODO/post_setup.sh | | https://help.comodo.com/topic-167-1-330-4246-.html |
| Xcitium Client Security (formerly Comodo Client Security) | | itsm | https://help.comodo.com/topic-463-1-1037-16070-Install-Xcitium-Client---Security-for-Linux.html |
| Avast | /etc/init.d/avast, /var/lib/avast/Setup/avast.vpsupdate | avast | https://businesshelp.avast.com/Content/Products/AfB_Antivirus/Linux/InstallingAvastBusinessAntivirusLinux.htm |
| AVG | /etc/init.d/avgd, /opt/avg/av/bin/avgsetup | | https://web.archive.org/web/20150522133834/http://aa-download.avg.com/filedir/doc/AVG_Anti-Virus_for_Linux/avg_alb_uma_en_2011_1.pdf |
| Tanium | /opt/Tanium/TaniumClient/TaniumClient | taniumclient | https://help.tanium.com/bundle/ug_client_cloud/page/client/deploy_package_linux.html |
| CyberArk | /opt/cyberark/epm/bin/epmcli, /opt/cyberark/epm/sbin/epmd | cyberark-epm, epmd | https://docs.cyberark.com/epm/latest/en/content/installation/linux-agentcommands.htm |
| PT Application Firewall | /var/pt/ptaf-deploy/current/install.sh, /var/pt/tmp/ptaf-deploy/install.sh, /var/pt/infra/current/deploy.sh | | https://help.ptsecurity.com/en-US/projects/af3/3.7.4/help |
| Splunk | /opt/splunkforwarder/bin/splunk, /etc/init.d/splunk, /etc/systemd/system/SplunkForwarder.service | SplunkForwarder | https://help.splunk.com/en/splunk-enterprise/forward-and-process-data/universal-forwarder-manual/9.4/install-the-universal-forwarder/install-a-nix-universal-forwarder |
| Kaseya RocketCyber (formerly RocketCyber) | /usr/local/rocketcyber/linux-agent-updater | rocketcyber | https://help.rocketcyber.kaseya.com/help/Content/deployment/installing-rocketcyber-agent-for-linux.html |
| Cynet 360 |  | cyservice | https://help.cynet.com/en/articles/88-single-endpoint-installation-linux |
| Fortra Digital Guardian (formerly Verdasys) | /dgagent/dgctl, /var/tmp/dgagent/install.log | dgdaemon | https://hstechdocs.helpsystems.com/releasenotes/Content/_ProductPages/Digital%20Guardian/Digital%20Guardian_linux.htm |
| Webroot Endpoint Protection | [No Linux Support] | [No Linux Support] | https://www.webroot.com/us/en/business/products/endpoint-protection |
| Absolute Software | [No Linux Support] | [No Linux Support] | https://www.absolute.com |
| Huntress | /usr/share/huntress/huntress-agent, /usr/share/huntress/huntress-updater, /usr/share/huntress/uninstall.sh | huntress-agent, huntress-updater | https://support.huntress.io/hc/en-us/articles/42457934554003-Linux-Installation-and-System-Requirements |
| BlackFog | ?? | ?? | https://www.blackfog.com/adx-protect-enterprise/ |
| OPSWAT | opswat-gears-od | opswatclient | https://docs.opswat.com/mdendpoint/operating/MetaDefender-Endpoint-System-Requirementsj25 |
| Raytheon Cyber (now Forcepoint — Forcepoint One Endpoint has no Linux agent) | [No Linux endpoint agent] | [No Linux endpoint agent] | https://help.forcepoint.com/F1E/en-us/v26/ep_install/ep_install.pdf |
| DeepInstinct | ?? | ?? | https://kb.msp360.com/managed-backup-service/integrations/deep-instinct/linux-dclient-installation |
| ClamAV | clamd, freshclam, clamonacc, clamdscan, /etc/clamav/clamd.conf, /etc/clamav/freshclam.conf, /etc/clamd.d/ | clamav-daemon, clamav-freshclam, clamd@scan | https://docs.clamav.net/ |
| Dr.Web for Linux | /opt/drweb.com/bin/drweb-ctl, /etc/opt/drweb.com/ | drweb-configd | https://download.geo.drweb.com/pub/drweb/unix/workstation/11.0/documentation/html/en/ |
| Sysmon for Linux (Microsoft Sysinternals) | /usr/bin/sysmon, /opt/sysmon | sysmon | https://github.com/microsoft/SysmonForLinux |
| AIDE | aide, /etc/aide.conf, /etc/aide/aide.conf, /var/lib/aide/aide.db | aide.service, aide.timer| https://aide.github.io/ |
| auditd (Linux Audit - base OS component) | /usr/sbin/auditd, /etc/audit/auditd.conf, /etc/audit/rules.d/ | auditd | https://man7.org/linux/man-pages/man8/auditd.8.html |
| Tripwire (Open Source) | tripwire, twadmin, twprint, siggen, /etc/tripwire/, /var/lib/tripwire/*.twd | | https://github.com/Tripwire/tripwire-open-source |
| Tripwire Enterprise Agent | /usr/local/tripwire/te/agent | twdaemon | https://www.tripwire.com/products/tripwire-enterprise |
| Seqrite Endpoint Security (Quick Heal) | /usr/lib/Seqrite/Seqrite | | https://docs.seqrite.com/docs/seqrite-endpoint-protection-epp-cloud/deployment/installing-seqrite-client/installing-seqrite-client-on-linux/ |
| WatchGuard EDR / EPDR (formerly Panda Adaptive Defense 360) | /opt/panda-security/endpoint/ | management-agent | https://www.watchguard.com/help/docs/help-center/en-US/Content/en-US/Endpoint-Security/troubleshooting/tshoot-linux.html |
| ThreatLocker | threatlockerctl | | https://threatlocker.kb.help/linux-agent-installing-and-uninstalling-process/ |
| Velociraptor | /usr/local/bin/velociraptor_client, /etc/velociraptor/client.config.yaml | velociraptor_client | https://docs.velociraptor.app/docs/deployment/clients/ |
| GRR Rapid Response | /usr/lib/grr/, /etc/fleetspeak-client/ | fleetspeak-client | https://github.com/google/grr |
| Binalyze AIR | /opt/binalyze/air/agent/air, /etc/environment.d/binalyze-air-agent.conf | Binalyze.AIR.Agent | https://kb.binalyze.com/air/setup/responder-deployment |
| HarfangLab EDR (agent "Hurukai") | hurukai | | https://harfanglab.io/medias/2026/04/harfanglab-secure-user-guidance-1.2.pdf |
| NetWitness Endpoint (RSA) | nwe-agent, /opt/rsa/nwe-agent/bin/nwe-agent | | https://community.netwitness.com/s/article/IntroductiontoEndpointAgentInstallation |
| Sysdig Secure agent | /opt/draios, /opt/draios/etc/dragent.yaml, /etc/default/dragent, /etc/sysconfig/dragent | dragent | https://docs.sysdig.com/en/sysdig-secure/classic-hosts-packages-agent/ |
| Datadog Agent (Cloud Security Management / CWS) | /opt/datadog-agent, /etc/datadog-agent/datadog.yaml, /etc/datadog-agent/security-agent.yaml, /etc/datadog-agent/system-probe.yaml | datadog-agent, datadog-agent-security, datadog-agent-sysprobe | https://docs.datadoghq.com/security/cloud_security_management/setup/agent/linux/ |
| Lacework (now Fortinet FortiCNAPP) | /var/lib/lacework/config/config.json | datacollector | https://docs.lacework.net/onboarding/agent-administration |
| Wiz runtime sensor | /opt/wiz/sensor/, /var/lib/wiz/ | wiz-sensor, wiz-disk-scanner | https://www.wiz.io/blog/wiz-runtime-sensor-for-linux |
| Prisma Cloud Compute Defender (formerly Twistlock) | /var/lib/twistlock/, /opt/twistlock/fsmon | twistlock | https://docs.prismacloud.io/en/compute-edition/22-12/admin-guide/install/install-defender/install-defender |
| Aqua Security Enforcer | /opt/aquasec, /var/lib/aquasec | | https://github.com/aquasecurity/deployments |
| Tetragon (Isovalent/Cilium) | /usr/local/bin/tetragon, /usr/local/bin/tetra, /etc/tetragon/, /var/run/tetragon/tetragon.sock | tetragon | https://tetragon.io/docs/installation/package/ |
| Tracee (Aqua) | tracee | | https://aquasecurity.github.io/tracee/latest/docs/install/ |
| Uptycs (osquery-based) | /opt/osquery/bin/osqueryd, /etc/osquery/ | osqueryd | https://support.uptycs.com/portal/en/kb/articles/osqueryd-flags-and-command-line-guide |
| Microsoft Azure Arc (Connected Machine agent; Defender for Servers) | /opt/azcmagent/bin/azcmagent, /opt/GC_Ext/, /opt/GC_Service/, /var/opt/azcmagent/ | himdsd, gcad, extd | https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-overview |
| Tenable Nessus Agent | /opt/nessus_agent, /opt/nessus_agent/sbin/nessuscli, /opt/nessus_agent/sbin/nessusd | nessusagent | https://docs.tenable.com/agent/Content/InstallNessusAgentLinux.htm |
| BeyondTrust Privilege Management for Unix & Linux (PMUL) | /usr/sbin/pbmasterd, /usr/sbin/pblocald, /usr/sbin/pblogd, /usr/local/bin/pbrun, /opt/pbul, /opt/pbul/policies/pb.conf | | https://docs.beyondtrust.com/epm-ul/docs/install-process |
| Delinea / Centrify Server Suite | /etc/centrifydc/, /usr/share/centrifydc/bin, /opt/centrify/bin/adclient | centrifydc | https://docs.delinea.com/online-help/server-suite/install/deployment/install-agents/index.htm |
| Zscaler Client Connector | /opt/zscaler, /var/log/zscaler/ | zsaservice, zstunnel | https://help.zscaler.com/client-connector/customizing-zscaler-client-connector-install-options-linux |
| Netskope Client | /opt/netskope/stagent/, /opt/netskope/stagent/uninstall.sh, /opt/netskope/stagent/data/nscacert.pem, nsclient | stagentd, stagentapp | https://docs.netskope.com/en/netskope-client-for-linux/ |
| Cloudflare WARP / Zero Trust | /usr/bin/warp-cli, /usr/bin/warp-svc | warp-svc | https://developers.cloudflare.com/warp-client/get-started/linux/ |
| JumpCloud agent | /opt/jc/, /opt/jc/bin/jumpcloud-agent, /opt/jc/jcagent.conf | jcagent | https://jumpcloud.com/support/install-the-linux-agent |
| Automox | /opt/amagent | amagent | https://docs.automox.com/product/Product_Documentation/Agents/Agent_Installation/Installing_the_Automox_Agent_on_Linux.htm |
| Teleport | /usr/local/bin/teleport, /etc/teleport.yaml | teleport | https://goteleport.com/docs/ |
| Okta Advanced Server Access / Privileged Access (sftd) | /etc/sftd/, /var/lib/sftd | sftd | https://help.okta.com/asa/en-us/content/topics/adv_server_access/docs/install-agent.htm |
| Fleet (fleetd / Orbit - osquery manager) | /opt/orbit/, /opt/orbit/osquery.flags | orbit | https://fleetdm.com/docs/using-fleet/fleetd |
| Fluent Bit | /opt/fluent-bit/bin/fluent-bit, /etc/fluent-bit/ | fluent-bit | https://docs.fluentbit.io/manual/installation/linux |
| Cribl Edge | /opt/cribl-edge | cribl-edge | https://docs.cribl.io/edge/deploy-linux/ |
| syslog-ng (One Identity) | /usr/sbin/syslog-ng, /etc/syslog-ng/syslog-ng.conf | syslog-ng | https://www.syslog-ng.com/products/open-source-log-management/ |
| NXLog | /opt/nxlog/, /opt/nxlog/etc/nxlog.conf, /usr/bin/nxlog, /etc/nxlog/nxlog.conf | nxlog | https://docs.nxlog.co/agent/current/install/debian.html |
| OpenText ArcSight SmartConnector | /opt/arcsight/connectors/ | | https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors-25.1/ |
| Graylog Sidecar | /usr/bin/graylog-sidecar, /etc/graylog/sidecar/sidecar.yml | graylog-sidecar | https://go2docs.graylog.org/current/getting_in_log_data/install_sidecar_on_linux.htm |
| Snare Enterprise Agent (Prophecy International) | /etc/audit/snare.conf, /usr/sbin/SnareDispatchHelper | | https://prophecyinternational.atlassian.net/wiki/spaces/LAXDOC/pages/979861531/Overview+of+Snare+for+Linux |
| Google SecOps / Chronicle BindPlane agent (observIQ OTel) | /opt/observiq-otel-collector | observiq-otel-collector | https://docs.cloud.google.com/chronicle/docs/ingestion/use-bindplane-agent |
| NinjaOne | /opt/NinjaRMMAgent, /opt/NinjaRMMAgent/programfiles | | https://www.ninjaone.com/docs/new-to-ninjaone/agent-installation/linux-device-agent-installation/ |
| N-able N-central / N-sight RMM | | rmmagent | https://documentation.n-able.com/N-central/userguide/Content/Deploying/Agent/Agents_InstallRHELinuxAgents.html |
