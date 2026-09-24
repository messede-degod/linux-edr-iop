## Linux-EDR-IOP
This repo tracks "indicators of presence" for linux EDRs, AVs and Monitoring Tools. It is an attempt to allow sysadmins to find out what security tools are installed on systems in order to prevent vendor conflicts.

This is a community effort, PRs are encouraged and welcome.

Files without absolute paths should be checked in all directories present within $PATH

Entries are grouped by category below. Categories are a convenience for triage, not a strict taxonomy — several vendors span more than one (e.g. cloud workload agents that also do EDR), and are listed under their primary function.

### Contents
- [EDR / XDR / endpoint protection platforms](#edr--xdr--endpoint-protection-platforms)
- [Antivirus, rootkit & malware scanners (open source / on-demand)](#antivirus-rootkit--malware-scanners-open-source--on-demand)
- [Open-source host security, HIDS & eBPF runtime security](#open-source-host-security-hids--ebpf-runtime-security)
- [File integrity monitoring (FIM)](#file-integrity-monitoring-fim)
- [DFIR & forensics agents](#dfir--forensics-agents)
- [Cloud workload protection (CWPP / CNAPP)](#cloud-workload-protection-cwpp--cnapp)
- [Network security monitoring, IDS / IPS & deception](#network-security-monitoring-ids--ips--deception)
- [Web application & hosting-panel security (WAF, cPanel/Plesk stacks)](#web-application--hosting-panel-security-waf-cpanelplesk-stacks)
- [SIEM, log shippers & telemetry collectors](#siem-log-shippers--telemetry-collectors)
- [Monitoring & observability agents](#monitoring--observability-agents)
- [Endpoint management, RMM & software deployment](#endpoint-management-rmm--software-deployment)
- [Remote access & remote support agents](#remote-access--remote-support-agents)
- [Configuration management & Linux fleet management](#configuration-management--linux-fleet-management)
- [Vulnerability management, live patching & compliance](#vulnerability-management-live-patching--compliance)
- [Cloud provider management & monitoring agents](#cloud-provider-management--monitoring-agents)
- [Identity, PAM & privileged access](#identity-pam--privileged-access)
- [Zero trust / SASE / NAC clients](#zero-trust--sase--nac-clients)
- [Microsegmentation & workload isolation](#microsegmentation--workload-isolation)
- [DLP & insider threat monitoring](#dlp--insider-threat-monitoring)
- [Data & database activity monitoring](#data--database-activity-monitoring)
- [Backup & data protection agents](#backup--data-protection-agents)
- [OT / ICS / IoT agents](#ot--ics--iot-agents)
- [Vendors with no Linux agent](#vendors-with-no-linux-agent)

### EDR / XDR / endpoint protection platforms
| vendor | files | systemd service name | website |
|---|---|---|---|
| MS defender | mdatp, /opt/microsoft/mdatp/sbin/wdavdaemon, /opt/microsoft/mdatp/sbin/wdavdaemonclient | mdatp | https://learn.microsoft.com/en-us/defender-endpoint/linux-support-install |
| CrowdStrike | /opt/CrowdStrike/falconctl | falcon-sensor | https://www.crowdstrike.com/tech-hub/endpoint-security/installing-falcon-sensor-for-linux/ |
| CarbonBlack | /opt/carbonblack/psc/bin/cbagentd, /var/opt/carbonblack/psc/cfg.ini | cbagentd (Carbon Black Cloud); cbdaemon, cbsensor (legacy CB Response) | https://techdocs.broadcom.com/us/en/carbon-black/cloud/carbon-black-cloud-sensors/index/cbc-sensor-installation-guide-tile/GUID-CF1B8557-84FB-41C4-89C2-C76EDD920EC0-en.html |
| Trellix ENS Agent (formerly McAfee) | /etc/init.d/cma | MFEcma, cma | https://docs.trellix.com/bundle/endpoint-security-v10-7-13-installation-guide-linux/page/GUID-9C3C9484-DDEA-443C-91B7-3C1342E3C5B4.html |
| Trend Micro | /etc/init.d/ds_agent, /opt/ds_agent/dsa, /opt/ds_agent/ds_agent, /opt/ds_agent/dsa_control | ds_agent | https://help.deepsecurity.trendmicro.com/20_0/on-premise/agent-install.html# |
| Arctic Wolf Aurora Endpoint Security (formerly BlackBerry Cylance PROTECT) | cylance, /opt/cylance/desktop/cylance | cylancesvc | https://docs.arcticwolf.com/en/aurora-endpoint-security/aurora-endpoint-security-setup/aurora-endpoint-security-setup-guide/setting-up-aurora-protect-desktop/installing-the-aurora-protect-desktop-agent-for-linux/install-the-linux-agentmanually |
| Arctic Wolf Aurora Focus (formerly BlackBerry CylanceOPTICS) | | cyoptics | https://docs.arcticwolf.com/en/aurora-endpoint-security/cylancehybrid/installing-the-agents-that-communicate-with-cylancehybrid/installing-agents-on-linux-devices/install-the-aurora-focus-agent-on-the-linux-device |
| SentinelOne | /opt/sentinelone/bin/sentinelctl, /opt/SentinelOne/bin/sentinelctl | sentinelone | https://alskyline.com/kb/deploy-sentinelone-agent-cli |
| Sophos Intercept X | /usr/local/bin/sophoslinuxsensor, /etc/sophos/runtimedetections.yaml | sophoslinuxsensor | https://docs.sophos.com/esg/sls/help/en-us/gettingStarted/installSensor/Installing_SLS_from_Sophos_Repo/index.html |
| Sophos SPL | /opt/sophos-spl/, /etc/default/sophos-spl, /etc/sysconfig/sophos-spl | sophos-spl | https://docs.sophos.com/esg/spl/en-us/help/ServerProtectionAgentTroubleshooting/index.html |
| Palo Alto Networks Cortex XDR | /opt/traps/bin/cytool, /etc/panw/cortex.conf | traps_pmd | https://cortex-docs.paloaltonetworks.com/cortex-xdr-agent/8.7/cortex-xdr-agent-for-linux/install-the-cortex-xdr-agent-for-linux |
| Bitdefender EDR / GravityZone XDR | /opt/bitdefender-security-tools/bin/bdconfigure, /opt/bitdefender-security-tools/etc/vhist.dat, /etc/audit/rules.d/bd_ausecd.rules | bdsec (bdsec* family) | https://www.bitdefender.com/business/support/en/77212-157515-bitdefender-endpoint-security-tools-for-linux-quick-start-guide.html |
| Cisco Secure Endpoint | /opt/cisco/amp/bin/ampcli | | https://www.cisco.com/c/en/us/support/docs/security/amp-endpoints/215256-cisco-amp-for-endpoints-mac-linux-cli.html |
| Cybereason | | cybereason-sensor | https://nest.cybereason.com/documentation |
| Elastic Security | /usr/bin/elastic-agent, /opt/Elastic/Agent/, /opt/Elastic/Agent/elastic-agent.yml | elastic-agent | https://www.elastic.co/docs/reference/fleet/installation-layout |
| Intezer | /usr/local/bin/intezer-analyze, intezer-cli, intezer_linux_endpoint_scanner.sh | | https://github.com/intezer/analyze-cli |
| ESET Endpoint Security | | eraagent | https://help.eset.com/protect_install/13.0/en-US/component_installation_agent_linux.html |
| ESET AV | /opt/eset/eea/, /var/opt/eset/eea/ | eea, eea-user-agent | https://help.eset.com/eeau/13.1/en-US/installation.html |
| Rapid7 INSIGHT IDR | /opt/rapid7/ir_agent/, /opt/rapid7/ir_agent/components/insight_agent/ | ir_agent | https://docs.rapid7.com/insight-agent/linux-installation/ |
| Rapid7 NG AV | /opt/rapid7/ir_agent/components/armor_linux | armor | https://docs.rapid7.com/insight-agent/ngav-install/ |
| WithSecure Elements Agent (formerly F-Secure) | /opt/f-secure/linuxsecurity/bin/activate, /opt/f-secure/linuxsecurity/bin/lsctl, /opt/f-secure/linuxsecurity/bin/fsanalyze, /etc/opt/f-secure/linuxsecurity/ | f-secure-linuxsecurity-scand.service, f-secure-linuxsecurity-fsicd.service, f-secure-linuxsecurity-lspmd.service, f-secure-linuxsecurity-statusd.service, f-secure-linuxsecurity-webserver.service, f-secure-linuxsecurity-rmmd.service, fsbg.service, fsbg-statusd.service, fsbg-pmd.service, fsbg-updated.service | https://support.withsecure.com/userguides/data/pdf/fsls64-adminguide-eng.pdf |
| WithSecure Elements Connector (for Countercept) (formerly F-Secure) | /opt/f-secure/fspms/fspms.conf, /etc/opt/f-secure/fspms/fspms.conf | | https://support.withsecure.com/userguides/data/pdf/ws_elements_connector_eng.pdf |
| WithSecure Policy Manager (formerly F-Secure) | /opt/f-secure/fspmc/fspmc | | https://support.withsecure.com/userguides/data/pdf/fspm-16.00-adminguide-eng.pdf |
| WithSecure Linux Security (formerly F-Secure) | /opt/f-secure/fsbg/bin/master-switch, /opt/f-secure/fsav/bin/fsims | | https://support.withsecure.com/userguides/data/pdf/fsls64-adminguide-eng.pdf |
| IBM QRadar EDR (formerly ReaQta) | /etc/reaqtahive.d/keeperx, /etc/reaqtahive.d/keeperx.env | keeperx | https://www.ibm.com/docs/en/security-qradar/security-edr/saas?topic=agent-installing-qradar-edr-linux-endpoints |
| SonicWall Capture Client (uses sentinelone under the hood) | /opt/sentinelone/bin/sentinelctl, /opt/SentinelOne/bin/sentinelctl | | https://www.sonicwall.com/support/knowledge-base/how-to-download-and-install-capture-client/kA1VN0000000Go50AE |
| Kaspersky Endpoint Security | /etc/init.d/kesl, /opt/kaspersky/kesl/bin/kesl-control, /opt/kaspersky/klnagent/lib/bin/setup/postinstall.pl, /opt/kaspersky/klnagent64/lib/bin/setup/postinstall.pl, /opt/kaspersky/klnagent64/bin/klnagchk | kesl, kesl-supervisor | https://support.kaspersky.com/KES4Linux/12.0.0/en-US/245017.htm |
| Kaspersky Endpoint Security (Elbrus Edition) | /etc/init.d/kesl-supervisor, /opt/kaspersky/kesl/bin/kesl-setup.pl | kesl-supervisor | https://support.kaspersky.com/help/KES4LinuxElbrus/10.1.2/en-US/220087.htm |
| Kaspersky Industrial CyberSecurity | /etc/init.d/kics, /opt/kaspersky/kics/bin/kics-setup.pl | kics | https://support.kaspersky.com/kics-for-linux-nodes/2.0 |
| Kaspersky Embedded Systems Security | /etc/init.d/kess, /opt/kaspersky/kess/bin/kess-setup.pl | kess | https://support.kaspersky.com/kess-linux/3.4.0 |
| TrendMicro - Server Protect | /etc/init.d/splx, /etc/init.d/splxhttpd, /opt/TrendMicro/SProtectLinux/, /opt/TrendMicro/SProtectLinux/SPLX.util/add_splx_service, /opt/TrendMicro/SProtectLinux/tmsplx.xml | splx, splxhttpd | https://docs.trendmicro.com/en-us/documentation/article/serverprotect-for-linux-rh6-ag-aspx-use-splx |
| Secureworks Taegis EDR | /opt/secureworks/taegis-agent/bin/taegisctl, /opt/secureworks/taegis-agent/bin/taegis, /opt/secureworks/taegis-agent/var/status/ | | https://docs.taegis.secureworks.com/taegis_agent/linux_install/ |
| Secureworks redcloak AV | /opt/secureworks/redcloak/bin/redcloak_start.sh | redcloak | https://docs.taegis.secureworks.com/integration/connectEndpoint/red_cloak_endpoint_agent_install/ |
| Secureworks NGAV | /usr/bin/secureworks/taegis-ngav (directory) | | https://docs.taegis.secureworks.com/integration/connectEndpoint/taegis_ngav/ |
| Fortinet FortiEDR | /opt/FortiEDRCollector/scripts/fortiedrconfig.sh | | https://docs.fortinet.com/document/fortiedr/7.2.3/administration-guide/551398/installing-a-fortiedr-collector-on-linux |
| Qualys EDR Cloud Agent | /usr/local/qualys/cloud-agent/bin/qualys-cloud-agent.sh, /etc/init.d/qualys-cloud-agent | qualys-cloud-agent | https://docs.qualys.com/en/ca/install-guide/linux/installation/ca_install_steps.htm |
| ThreatDown Nebula EDR Agent (formerly Malwarebytes) | /opt/malwarebytes/, /opt/malwarebytes/bin/ea-cli, /var/log/mbdaemon.log | mbdaemon | https://support.threatdown.com/hc/en-us/articles/4413802216467-Add-Linux-endpoints-in-Nebula |
| LimaCharlie Agent | /etc/init.d/limacharlie, /bin/rphcp, /opt/limacharlie, /etc/hcp, /etc/hcp_conf, /etc/hcp_hbs, /etc/limacharlie/installation_key | limacharlie | https://docs.limacharlie.io/2-sensors-deployment/endpoint-agent/linux/installation/ |
| Checkpoint | /var/log/checkpoint/cpla/cpla.log | cpla | https://sc1.checkpoint.com/documents/R81.10/WebAdminGuides/EN/CP_R81.10_HarmonyEndpointWebManagement_AdminGuide/Topics-HEPWM-R81.10/Harmony-Endpoint-for-Linux-Deploying.htm |
| Trellix EDR (formerly FireEye HX) | /opt/fireeye/bin/xagt | xagt | https://docs.trellix.com/bundle/agent_35_ag/page/UUID-1b8ae3d0-e446-c88a-82e5-a4046bbf9334.html |
| Trellix Endpoint Security - Threat Prevention (formerly FireEye/McAfee) | /opt/McAfee/ens/tp/bin/mfetpcli, /opt/McAfee/ens/esp/bin/mfeespd (10.6.6+), /opt/isec/ens/esp/bin/isecespd, /opt/isec/ens/threatprevention/bin/isectpdControl.sh (10.6.5 and earlier) | mfetpd, isectpd (legacy) | https://docs.trellix.com/bundle/endpoint-security-v10-7-22-installation-guide-linux/page/UUID-12d6205f-a8b8-1861-9e9f-95a757c40daf.html |
| Trellix Agent (formerly FireEye/McAfee Agent) | /opt/McAfee/agent/scripts/uninstall.sh, /opt/McAfee/Agent/bin/CmdAgent, /opt/McAfee/cma/bin/cmdagent, /opt/Trellix/cma/bin/cmdagent | cma | https://docs.trellix.com/bundle/trellix-agent-5.8.x-product-guide/page/UUID-d0d530fc-9ebf-d313-67b9-5274dcfe56e5.html |
| Symantec EDR | /opt/Symantec/sdcssagent/AMD/system/AntiMalware.ini, /etc/init.d/sisamdagent, /opt/Symantec/symantec_antivirus/uninstall.sh, /usr/lib/symantec/status.sh | sisamdagent, sisidsagent, sisipsagent, cafagent | https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection/all/symantec-single-agent-for-linux-guide/installing-the-client-for-linux-v95193124-d21e2986.html |
| Symantec Linux Agent | /usr/lib/symantec/status.sh | | https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-security/sescloud/Installing-the-Symantec-Agent-and-enrolling-devices/creating-and-installing-a-symantec-linux-agent-ins-v133371951-d4155e8363.html |
| Comodo AV | /opt/COMODO/post_setup.sh | | https://help.comodo.com/topic-167-1-330-4246-.html |
| Xcitium Client Security (formerly Comodo Client Security) | /opt/COMODO/ (shared with the Endpoint Manager Communication Client) | ?? (the itsm service belongs to the Endpoint Manager Communication Client - see RMM section) | https://help.comodo.com/topic-463-1-1037-16070-Install-Xcitium-Client---Security-for-Linux.html |
| Avast | /etc/init.d/avast, /etc/avast/, /var/lib/avast/Setup/avast.vpsupdate | avast, avast.target | https://businesshelp.avast.com/Content/Products/AfB_Antivirus/Linux/InstallingAvastBusinessAntivirusLinux.htm |
| AVG | /etc/init.d/avgd, /opt/avg/av/bin/avgsetup | | https://web.archive.org/web/20150522133834/http://aa-download.avg.com/filedir/doc/AVG_Anti-Virus_for_Linux/avg_alb_uma_en_2011_1.pdf |
| Positive Technologies MaxPatrol EDR / PT XDR | ?? | ?? | https://help.ptsecurity.com/en-US/projects/edr/5.1/help/3135367435 |
| Kaseya RocketCyber (formerly RocketCyber) | /usr/local/rocketcyber/linux-agent-updater | rocketcyber | https://help.rocketcyber.kaseya.com/help/Content/deployment/installing-rocketcyber-agent-for-linux.html |
| Cynet 360 |  | cyservice | https://help.cynet.com/en/articles/88-single-endpoint-installation-linux |
| Huntress | /usr/share/huntress/huntress-agent, /usr/share/huntress/huntress-updater, /usr/share/huntress/uninstall.sh | huntress-agent, huntress-updater, huntress-rio | https://support.huntress.io/hc/en-us/articles/42457934554003-Linux-Installation-and-System-Requirements |
| BlackFog | ?? | ?? | https://www.blackfog.com/adx-protect-enterprise/ |
| OPSWAT | opswat-gears-od | opswatclient | https://docs.opswat.com/mdendpoint/operating/MetaDefender-Endpoint-System-Requirementsj25 |
| DeepInstinct | ?? | ?? | https://kb.msp360.com/managed-backup-service/integrations/deep-instinct/linux-dclient-installation |
| Dr.Web for Linux | /opt/drweb.com/bin/drweb-ctl, /etc/opt/drweb.com/ | drweb-configd | https://download.geo.drweb.com/pub/drweb/unix/workstation/11.0/documentation/html/en/dw_8_console_controldesk.htm |
| Seqrite Endpoint Security (Quick Heal) | /usr/lib/Seqrite/Seqrite, /usr/lib/Seqrite/ | | https://docs.seqrite.com/docs/seqrite-endpoint-protection-epp-cloud/deployment/installing-seqrite-client/installing-seqrite-client-on-linux/ |
| Seqrite EDR (Quick Heal) | /usr/lib/Seqrite/, /opt/Seqrite (client build share) | | https://docs.seqrite.com/docs/seqrite-edr/getting-started/ |
| WatchGuard EDR / EPDR (formerly Panda Adaptive Defense 360) | /opt/panda-security/endpoint/ | management-agent | https://www.watchguard.com/help/docs/help-center/en-US/Content/en-US/Endpoint-Security/troubleshooting/tshoot-linux.html |
| ThreatLocker | threatlockerctl | | https://threatlocker.kb.help/linux-agent-installing-and-uninstalling-process/ |
| HarfangLab EDR (agent "Hurukai") | hurukai | | https://harfanglab.io/medias/2026/04/harfanglab-secure-user-guidance-1.2.pdf |
| NetWitness Endpoint (RSA) | nwe-agent, /opt/rsa/nwe-agent/bin/nwe-agent | | https://community.netwitness.com/s/article/IntroductiontoEndpointAgentInstallation |
| Darktrace cSensor | ?? | ?? | https://darktrace.com/ |
| AhnLab V3 Net (Unix/Linux Server) | /usr/local/v3net, v3netd | | https://help.ahnlab.com/V3Net/V3Net_Linux/en_US/start.htm |
| Sangfor Endpoint Secure (Athena EPP) | /Sangfor/EDR/agent/, /Sangfor/EDR/agent/bin, eps_uninstall.sh | agentd | https://www.sangfor.com/cybersecurity/products/edr-endpoint-security |
| Qihoo 360 enterprise | /opt/360safe/360entclient | service360safe_linux | https://www.360.cn/ |
| QAX / Qi-Anxin Tianqing (奇安信天擎) | qaxsafe, qaxsafed, /etc/init.d/serviceqaxsafe | serviceqaxsafe | https://en.qianxin.com/product/detail/165 |
| Hauri ViRobot | /usr/local/ViRobot/ (legacy) | | https://company.hauri.net/product/anti_virus.html |
| NSFOCUS UES / EDR | NSFOCUS-Agent-Linux_*.run, /etc/.nsfmhp/ | nsfocusagent | https://www.nsfocus.com.cn/html/2019/207_1230/89.html |
| Alert Logic Agent (Fortra) | /etc/init.d/al-agent, /var/alertlogic/lib/agent/bin/al-agent, /var/alertlogic/etc/ | al-agent | https://docs.alertlogic.com/prepare/alert-logic-agent-linux.htm |
| Arctic Wolf Agent (Wazuh-based; distinct from Aurora/Cylance) | /var/arcticwolfnetworks/agent/, /var/arcticwolfnetworks/agent/bin/scout-client | | https://docs.arcticwolf.com/bundle/m_arctic_wolf_agent/page/arctic_wolf_agent_processes_that_run_on_linux.html |
| Coro | /var/csa/ (CoroInstaller_*.run) | coro-agent | https://docs.coro.net/agent/deploy-linux/ |
| eScan (MicroWorld) | mwadmin, mwav, escan (packages) | | https://www.escanav.com/ |
| Sophos Anti-Virus for Linux (legacy, retired 2023; distinct from Intercept X / SPL) | /opt/sophos-av/, /opt/sophos-av/bin/savdctl, /opt/sophos-av/bin/savconfig, /opt/sophos-av/bin/savscan, /opt/sophos-av/etc/, /etc/init.d/sav-protect, /etc/init.d/sav-rms | sav-protect, sav-rms | https://www.sophos.com/en-us/support/knowledgebase |
| Antiy IEP (安天智甲) | ?? | ?? | https://www.antiy.com/IEP.html |
| Venustech (启明星辰) endpoint | ?? | ?? | https://www.venustech.com.cn/ |
| Stellar Cyber Open XDR (Linux server sensor) | /opt/aella/, /opt/aelladata/, /var/aella/, /var/log/aella/, aellads (package); processes aella_audit, aella_conf, aella_ctrl, aella_flow, aella_mon | ?? | https://docs.stellarcyber.ai/6.3.x/Installation/On-Prem/Installing-Agent-Sensor-Linux.htm |
| LevelBlue USM Anywhere Agent (formerly AT&T / AlienVault; osquery-based) | alienvault-agent (package), /etc/osquery/, /var/lib/osquery/ | ?? | https://docs.levelblue.com/documentation/usm-anywhere/agents/alienvault-agents |
| Morphisec Linux Server Protection | ?? | ?? | https://www.morphisec.com/products/morphisec-linux-server-protection |
| Red Canary Linux EDR (eBPF sensor, falls back to auditd) | /opt/redcanary/, /opt/redcanary/config.json, canary-forwarder (package) | cfsvcd | https://docs.redcanary.com/docs/system-and-network-requirements-for-linux-edr |
| Datto Endpoint Security / Datto EDR (built on Infocyte) | /opt/infocyte/agent (default; overridable with --install-dir), *.linux-amd64.bin installer | HUNTAgent | https://edr.datto.com/help/Content/03-deploying-managing-datto-endpoint-security-agent/deployment-options/agent-installing.htm |
| Heimdal Endpoint Security (Ubuntu/Debian agent) | heimdal (package), /usr/share/heimdal-utils/dotnet/, /etc/apt/sources.list.d/heimdal.list, /usr/share/keyrings/heimdal-keyring.gpg | heimdal-clienthost | https://support.heimdalsecurity.com/hc/en-us/articles/4433189823773-Installing-the-HEIMDAL-Agent-Ubuntu |
| TEHTRIS EDR (Optimus) | ?? | ?? | https://tehtris.com/en/platform/edr-endpoint-detection-response/ |

### Antivirus, rootkit & malware scanners (open source / on-demand)
| vendor | files | systemd service name | website |
|---|---|---|---|
| ClamAV | clamd, freshclam, clamonacc, clamdscan, /etc/clamav/clamd.conf, /etc/clamav/freshclam.conf, /etc/clamd.d/ | clamav-daemon, clamav-freshclam, clamav-clamonacc, clamav-daemon.socket, clamav-freshclam-once.timer; clamd@scan (RHEL/Fedora template unit) | https://docs.clamav.net/ |
| rkhunter | /usr/bin/rkhunter, /etc/rkhunter.conf, /etc/cron.daily/rkhunter | (none - cron-driven) | https://github.com/crunchsec/rkhunter |
| chkrootkit | /usr/sbin/chkrootkit, /etc/chkrootkit/chkrootkit.conf, /etc/cron.daily/chkrootkit | (none - cron-driven) | https://chkrootkit.org/ |
| Linux Malware Detect (LMD / maldet) | /usr/local/maldetect/, /usr/local/sbin/maldet, /usr/local/maldetect/conf.maldet, /etc/cron.daily/maldet | maldet (inotify monitor; scanning via cron) | https://github.com/rfxn/linux-malware-detect |

### Open-source host security, HIDS & eBPF runtime security
| vendor | files | systemd service name | website |
|---|---|---|---|
| falco | /etc/falco/falco.yaml, /etc/falco/config.d/ | falco (alias to active driver unit), falco-kmod, falco-modern-bpf, falco-custom, falco-kmod-inject, falcoctl-artifact-follow | https://falco.org/docs/setup/packages/ |
| wazuh | /var/ossec/, /var/ossec/bin/wazuh-control | wazuh-agent | https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html |
| ossec | /etc/rc.d/init.d/ossec, /etc/init.d/ossec | | https://www.ossec.net/docs/docs/manual/installation/index.html |
| osquery | osqueryi, /opt/osquery/bin/osqueryd, /opt/osquery/bin/osqueryctl, /etc/osquery/osquery.conf, /var/log/osquery/ | osqueryd | https://osquery.readthedocs.io/en/stable/installation/install-linux/ |
| Sysmon for Linux (Microsoft Sysinternals) | /usr/bin/sysmon, /opt/sysmon | sysmon | https://github.com/microsoft/SysmonForLinux |
| auditd (Linux Audit - base OS component) | /usr/sbin/auditd, /etc/audit/auditd.conf, /etc/audit/rules.d/ | auditd | https://man7.org/linux/man-pages/man8/auditd.8.html |
| Tetragon (Isovalent/Cilium) | /usr/local/bin/tetragon, /usr/local/bin/tetra, /etc/tetragon/, /var/run/tetragon/tetragon.sock | tetragon | https://tetragon.io/docs/installation/package/ |
| Tracee (Aqua) | tracee | | https://aquasecurity.github.io/tracee/latest/docs/install/ |
| Fleet (fleetd / Orbit - osquery manager) | /opt/orbit/, /opt/orbit/osquery.flags | orbit | https://fleetdm.com/docs/using-fleet/fleetd |
| ByteDance Elkeid | /etc/elkeid/elkeid-agent, /etc/elkeid/elkeidctl, /etc/elkeid/specified_env, /etc/init.d/elkeid-agent | elkeid-agent | https://elkeid.bytedance.com/en/docs/ |
| Chaitin CloudWalker (牧云; Collie community edition) | install dir chosen at setup (docs use /data/cloudwalker), /etc/systemd/system/cloudwalker-agent.service | cloudwalker-agent | https://bbs.chaitin.cn/topic/79 |

### File integrity monitoring (FIM)
| vendor | files | systemd service name | website |
|---|---|---|---|
| AIDE | aide, /etc/aide.conf, /etc/aide/aide.conf, /var/lib/aide/aide.db | dailyaidecheck.service, dailyaidecheck.timer, dailyaidecheck-buildcache.service (Debian/Ubuntu); aide-check.service, aide-check.timer (Fedora/RHEL) | https://aide.github.io/ |
| Tripwire (Open Source) | tripwire, twadmin, twprint, siggen, /etc/tripwire/, /var/lib/tripwire/*.twd | | https://github.com/Tripwire/tripwire-open-source |
| Tripwire Enterprise Agent | /usr/local/tripwire/te/agent | twdaemon | https://www.tripwire.com/products/tripwire-enterprise |
| Samhain | /usr/sbin/samhain, /etc/samhain/samhainrc, /etc/samhainrc | samhain | https://www.la-samhna.de/samhain/ |
| CimTrak Integrity Suite (Cimcor) | ?? (install path chosen at setup) | ?? | https://www.cimcor.com/cimtrak |

### DFIR & forensics agents
| vendor | files | systemd service name | website |
|---|---|---|---|
| Velociraptor | /usr/local/bin/velociraptor_client, /etc/velociraptor/client.config.yaml | velociraptor_client | https://docs.velociraptor.app/docs/deployment/clients/ |
| GRR Rapid Response | /usr/lib/grr/, /etc/fleetspeak-client/ | fleetspeak-client | https://github.com/google/grr |
| Binalyze AIR | /opt/binalyze/air/agent/air, /etc/environment.d/binalyze-air-agent.conf | Binalyze.AIR.Agent | https://kb.binalyze.com/air/setup/responder-deployment |

### Cloud workload protection (CWPP / CNAPP)
| vendor | files | systemd service name | website |
|---|---|---|---|
| Sysdig Secure agent | /opt/draios, /opt/draios/etc/dragent.yaml, /etc/default/dragent, /etc/sysconfig/dragent | dragent | https://docs.sysdig.com/en/sysdig-secure/classic-hosts-packages-agent/ |
| Datadog Agent (Cloud Security Management / CWS) | /opt/datadog-agent, /etc/datadog-agent/datadog.yaml, /etc/datadog-agent/security-agent.yaml, /etc/datadog-agent/system-probe.yaml | datadog-agent, datadog-agent-security, datadog-agent-sysprobe | https://docs.datadoghq.com/security/cloud_security_management/setup/agent/linux/ |
| Lacework (now Fortinet FortiCNAPP) | /var/lib/lacework/config/config.json, /var/lib/lacework/datacollector, /var/log/lacework/datacollector.log | datacollector | https://docs.fortinet.com/document/lacework-forticnapp/latest/administration-guide/496893/starting-stopping-or-restarting-the-linux-agent |
| Wiz runtime sensor | /opt/wiz/sensor/, /opt/wiz/sensor/host-store/, /var/lib/wiz/ | wiz-sensor, wiz-disk-scanner | https://www.wiz.io/blog/wiz-runtime-sensor-for-linux |
| Prisma Cloud Compute Defender (formerly Twistlock) | /var/lib/twistlock/, /opt/twistlock/fsmon | twistlock | https://docs.prismacloud.io/en/compute-edition/22-12/admin-guide/install/install-defender/install-defender |
| Aqua Security Enforcer | /opt/aquasec, /var/lib/aquasec | | https://github.com/aquasecurity/deployments |
| Uptycs (osquery-based) | /opt/osquery/bin/osqueryd, /etc/osquery/ | osqueryd | https://support.uptycs.com/portal/en/kb/articles/osqueryd-flags-and-command-line-guide |
| Alibaba Cloud Security Center (aegis) | /usr/local/aegis/aegis_client/, /usr/local/aegis/aegis_update/, AliYunDun, AliYunDunUpdate | aegis | https://www.alibabacloud.com/help/en/security-center/user-guide/security-center-agent-processes |
| Tencent Cloud Host Security (Yunjing) | /usr/local/qcloud/YunJing/, YDService, YDLive | | https://www.tencentcloud.com/document/product/296/12236 |
| Huawei Cloud HSS (HostGuard) | /usr/local/hostguard/ | hostguard | https://support.huaweicloud.com/intl/en-us/usermanual-hss2.0/hss_01_0375.html |
| Sweet Security (eBPF runtime sensor) | ?? | ?? | https://sweet.security/product |
| Fidelis Halo (formerly CloudPassage Halo) | /opt/cloudpassage/, /etc/init.d/cphalod | cphalod | https://fidelissecurity.com/fidelis-halo-cloud-native-application-protection-platform-cnapp/ |
| Upwind sensor | /etc/upwind/, /etc/upwind/agent.yaml, /etc/upwind/agent-hostconfig.yaml, /etc/upwind/agent.env | upwind-agent, upwind-agent-hostconfig, upwind-agent-scanner + .timer, upwind-agent-update + .timer | https://docs.upwind.io/public/getting-started/install-sensor/host/install |
| Spyderbat Nano Agent (eBPF) | /opt/spyderbat/, /opt/spyderbat/etc/, /opt/spyderbat/etc/muid | nano_agent | https://docs.spyderbat.com/installation/spyderbat-nano-agent/linux-vm |

### Network security monitoring, IDS / IPS & deception
| vendor | files | systemd service name | website |
|---|---|---|---|
| Suricata | /usr/bin/suricata, /usr/local/bin/suricata, /etc/suricata/suricata.yaml, /etc/suricata/rules/, /var/log/suricata/ | suricata | https://docs.suricata.io/ |
| Snort | /usr/sbin/snort, /usr/local/bin/snort, /etc/snort/snort.conf, /etc/snort/snort.lua, /etc/init.d/snort | snort (v2; v3 has no upstream unit) | https://docs.snort.org/ |
| Zeek (formerly Bro) | /opt/zeek/bin/zeek, /opt/zeek/bin/zeekctl, /opt/zeek/etc/, /usr/local/zeek | zeek.target, zeek-manager.service, zeek-logger@.service, zeek-proxy@.service, zeek-worker@.service, zeek-archiver.service, zeek-setup.service (generated by the Zeek systemd generator, misc/systemd-generator) | https://docs.zeek.org/en/master/advanced/deployment/systemd.html |
| Fail2ban | fail2ban-server, fail2ban-client, /etc/fail2ban/, /var/run/fail2ban/fail2ban.sock | fail2ban | https://github.com/fail2ban/fail2ban |
| CrowdSec (+ firewall bouncer) | /usr/bin/crowdsec, /usr/bin/cscli, /etc/crowdsec/, crowdsec-firewall-bouncer, /etc/crowdsec/bouncers/ | crowdsec, crowdsec-firewall-bouncer | https://docs.crowdsec.net/ |
| OpenCanary (Thinkst) | opencanaryd, /etc/opencanaryd/opencanary.conf | opencanary | https://opencanary.readthedocs.io/ |

### Web application & hosting-panel security (WAF, cPanel/Plesk stacks)
Common on shared-hosting and control-panel servers; several of these hook Apache/nginx or run inotify watchers over user home directories.

| vendor | files | systemd service name | website |
|---|---|---|---|
| Imunify360 / ImunifyAV (CloudLinux; web hosting server security) | /usr/bin/imunify360-agent, /usr/bin/imunify-antivirus, /etc/sysconfig/imunify360/imunify360.config, /etc/sysconfig/imunify360/imunify360.config.d/, /etc/sysconfig/imunify360/integration.conf, /etc/imunify360/whitelist/, /etc/imunify360/blacklist/, /var/imunify360/ (imunify360.db, imunify360-resident.db, cleanup_storage/), /var/log/imunify360/, /opt/imunify360/venv/, /opt/imunify360-webshield/, /etc/imunify360-webshield/webshield.conf | imunify360, imunify360-webshield, imunify-antivirus + imunify-antivirus.socket (ImunifyAV) | https://docs.imunify360.com/installation/ |
| PT Application Firewall | /var/pt/ptaf-deploy/current/install.sh, /var/pt/tmp/ptaf-deploy/install.sh, /var/pt/infra/current/deploy.sh | | https://help.ptsecurity.com/en-US/projects/af3/3.7.4/help |
| ConfigServer Security & Firewall (CSF / LFD) | /etc/csf/, /etc/csf/csf.conf, /usr/sbin/csf, /usr/sbin/lfd, /usr/local/csf/bin/, /var/lib/csf/, /etc/init.d/csf, /etc/init.d/lfd | csf, lfd | https://configserver.com/configserver-security-and-firewall/ |
| ConfigServer eXploit Scanner (cxs) | /etc/cxs/, /etc/cxs/cxs.ignore, /etc/cxs/cxswatch.conf, /etc/cxs/cxswatch.sh, /etc/cxs/cxsftp.sh, /etc/cxs/cxscgi.sh, /usr/sbin/cxs | cxswatch | https://configserver.com/configserver-exploit-scanner/ |
| BitNinja | /opt/bitninja/, /etc/bitninja/, /var/lib/bitninja/, /var/lib/bitninja-reliable-auto-update/main.json, /var/log/bitninja/ | bitninja, bitninja-reliable-auto-update | https://doc.bitninja.io/docs/installation/install_bitninja/ |
| Monarx | /etc/monarx-agent.conf, monarx-agent (package), monarx-protect PHP module | monarx-agent | https://support.monarx.com/en/articles/10874528-monarx-installation |
| Patchman (now CloudLinux) | patchman-client (package; install paths not publicly documented) | ?? | https://docs.imunify360.com/patchman/ |
| Atomicorp ASL / Atomic OSSEC (Atomic Workload Protection) | /var/asl/, /var/asl/bin/asl, /etc/asl/config | asl, ossec-hids (ASL replaces and manages OSSEC) | https://wiki.atomicorp.com/wiki/index.php/Using_ASL |
| ModSecurity (OWASP; WAF module driven by Imunify360, cPanel, Plesk) | /etc/modsecurity/modsecurity.conf, /etc/modsecurity.d/, /etc/apache2/conf.d/modsec/, /usr/lib/apache2/modules/mod_security2.so, /var/log/modsec_audit.log | (none - Apache/nginx module) | https://github.com/owasp-modsecurity/ModSecurity |
| Wallarm node | /opt/wallarm/, /opt/wallarm/etc/wallarm/node.yaml, /opt/wallarm/etc/wallarm/go-node.yaml, /opt/wallarm/var/log/wallarm/, /etc/wallarm/ (pre-5.x layout) | wallarm | https://docs.wallarm.com/installation/native-node/all-in-one/ |

### SIEM, log shippers & telemetry collectors
| vendor | files | systemd service name | website |
|---|---|---|---|
| ThreatConnect | /opt/threatconnect-envsvr/threatconnect-envsvr.jar, /etc/init.d/threatconnect-envsvr | threatconnect-envsvr | https://knowledge.threatconnect.com/docs/threatconnect-environment-server-installation-guide |
| Filebeat (not AV/EDR, but used to ship logs) | /etc/filebeat/filebeat.yml | filebeat | https://www.elastic.co/docs/reference/beats/filebeat/filebeat-installation-configuration |
| Sumo Logic Cloud SIEM | /usr/local/SumoCollector/uninstall, /opt/SumoCollector/uninstall, /opt/SumoCollector/config/user.properties | | https://www.sumologic.com/help/docs/send-data/installed-collectors/linux/ |
| Sumo Logic OTEL Collector | /etc/otelcol-sumo/sumologic.yaml | otelcol-sumo | https://www.sumologic.com/help/docs/send-data/opentelemetry-collector/install-collector/linux/ |
| Fortinet FortiSIEM | /opt/fortinet/fortisiem/linux-agent/bin/fortisiem-linux-agent-uninstall.sh, /etc/init.d/fortisiem-linux-agent | fortisiem-linux-agent | https://docs.fortinet.com/document/fortisiem/7.5.0/linux-agent-installation-guide/201446/fortisiem-linux-agent |
| Exabeam System Monitor (formerly LogRhythm) | /etc/init.d/scsm, /opt/logrhythm/scsm/config/scsm.ini | | https://docs.logrhythm.com/sysmon/docs/install-a-system-monitor-on-unix-linux |
| Exabeam Axon (formerly LogRhythm Axon) | /etc/logrhythm/lragent_config.json, /bin/logrhythm/lr-agent, /opt/logrhythm/conf/agent_information.json | lr-agent.logrhythm | https://docs.exabeam.com/en/site-collector/all/administration-guide/set-up-collectors/set-up-linux-file-collector.html |
| Trellix SIEM Collector (formerly FireEye/McAfee) | /opt/Trellix/siem/siem_collector.conf, /opt/McAfee/siem/siem_collector.conf, /var/lib/trellix/bookmarks/ft_bookmarks | mcafee_siem_collector | https://docs.trellix.com/bundle/siem-collector-linux-install-guide/page/GUID-2788BC0E-FA2A-4FE2-BA53-A4C77FF47DAE.html |
| Splunk | /opt/splunkforwarder/bin/splunk, /etc/init.d/splunk, /etc/systemd/system/SplunkForwarder.service | SplunkForwarder | https://help.splunk.com/en/splunk-enterprise/forward-and-process-data/universal-forwarder-manual/9.4/install-the-universal-forwarder/install-a-nix-universal-forwarder |
| Fluent Bit | /opt/fluent-bit/bin/fluent-bit, /etc/fluent-bit/ | fluent-bit | https://docs.fluentbit.io/manual/installation/linux |
| Cribl Edge | /opt/cribl-edge | cribl-edge | https://docs.cribl.io/edge/deploy-linux/ |
| syslog-ng (One Identity) | /usr/sbin/syslog-ng, /etc/syslog-ng/syslog-ng.conf | syslog-ng | https://www.syslog-ng.com/products/open-source-log-management/ |
| NXLog | /opt/nxlog/, /opt/nxlog/etc/nxlog.conf, /usr/bin/nxlog, /etc/nxlog/nxlog.conf | nxlog | https://docs.nxlog.co/agent/current/install/debian.html |
| OpenText ArcSight SmartConnector | /opt/arcsight/connectors/ | | https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors-25.1/ |
| Graylog Sidecar | /usr/bin/graylog-sidecar, /etc/graylog/sidecar/sidecar.yml | graylog-sidecar | https://go2docs.graylog.org/current/getting_in_log_data/install_sidecar_on_linux.htm |
| Snare Enterprise Agent (Prophecy International) | /etc/audit/snare.conf, /usr/sbin/SnareDispatchHelper | | https://prophecyinternational.atlassian.net/wiki/spaces/LAXDOC/pages/979861531/Overview+of+Snare+for+Linux |
| Google SecOps / Chronicle BindPlane agent (observIQ OTel) | /opt/observiq-otel-collector | observiq-otel-collector | https://docs.cloud.google.com/chronicle/docs/ingestion/use-bindplane-agent |
| Elastic Beats - Auditbeat / Metricbeat / Packetbeat (siblings of Filebeat; Auditbeat wraps auditd + FIM) | /etc/auditbeat/auditbeat.yml, /etc/metricbeat/metricbeat.yml, /etc/packetbeat/packetbeat.yml, /var/lib/auditbeat/, /usr/share/auditbeat/ | auditbeat, metricbeat, packetbeat | https://www.elastic.co/docs/reference/beats/auditbeat/ |
| Logpoint AgentX (OSSEC + osquery based) | /opt/logpoint/ossec/, /opt/logpoint/osquery/, /opt/logpoint/ossec/cert/ | ?? | https://docs.logpoint.com/docs/logpointagentx/en/latest/Installing%20AgentX.html |

### Monitoring & observability agents
| vendor | files | systemd service name | website |
|---|---|---|---|
| Dynatrace OneAgent | /opt/dynatrace/oneagent/, /var/lib/dynatrace/oneagent/ | oneagent | https://docs.dynatrace.com/docs/ingest-from/dynatrace-oneagent/installation-and-operation/linux/installation/install-oneagent-on-linux |
| New Relic Infrastructure agent | /usr/bin/newrelic-infra, /etc/newrelic-infra.yml, /etc/newrelic-infra/, /var/db/newrelic-infra/ | newrelic-infra | https://docs.newrelic.com/docs/infrastructure/infrastructure-agent/linux-installation/package-manager-install/ |
| Zabbix Agent / Agent 2 | /usr/sbin/zabbix_agentd, /usr/sbin/zabbix_agent2, /etc/zabbix/zabbix_agentd.conf, /etc/zabbix/zabbix_agent2.conf, /etc/zabbix/zabbix_agentd.d/, /etc/zabbix/zabbix_agent2.d/, /var/log/zabbix/, /var/run/zabbix/ | zabbix-agent, zabbix-agent2 | https://www.zabbix.com/documentation/current/en/manual/installation/install_from_packages |
| Netdata Agent | /usr/sbin/netdata, /etc/netdata/netdata.conf, /etc/netdata/edit-config, /usr/libexec/netdata/ (plugins: apps.plugin, go.d.plugin, ebpf.plugin), /var/lib/netdata/, /var/cache/netdata/, /var/log/netdata/; static/kickstart installs under /opt/netdata/ (/opt/netdata/etc/netdata/, /opt/netdata/usr/sbin/netdata) | netdata, netdata-updater.timer (static/kickstart installs) | https://learn.netdata.cloud/docs/netdata-agent/installation/linux |
| Nagios NRPE | /usr/local/nagios/etc/nrpe.cfg, /etc/nagios/nrpe.cfg, /etc/nagios/nrpe.d/, /usr/local/nagios/bin/nrpe, /usr/sbin/nrpe | nrpe (RHEL family), nagios-nrpe-server (Debian family) | https://github.com/NagiosEnterprises/nrpe |
| Icinga 2 | /usr/sbin/icinga2, /etc/icinga2/icinga2.conf, /etc/icinga2/features-enabled/, /var/lib/icinga2/ | icinga2 | https://icinga.com/docs/icinga-2/latest/doc/02-installation/ |
| Checkmk agent | /usr/bin/check_mk_agent, /usr/bin/cmk-agent-ctl, /etc/check_mk/, /usr/lib/check_mk_agent/, /var/lib/cmk-agent/ | check-mk-agent.socket, check-mk-agent@.service, check-mk-agent-async.service, cmk-agent-ctl-daemon; check_mk (legacy xinetd) | https://docs.checkmk.com/latest/en/agent_linux.html |
| Prometheus node_exporter | /usr/local/bin/node_exporter, /usr/bin/prometheus-node-exporter (Debian family), /var/lib/node_exporter/textfile_collector/ | node_exporter, prometheus-node-exporter | https://github.com/prometheus/node_exporter |
| Telegraf (InfluxData) | /usr/bin/telegraf, /etc/telegraf/telegraf.conf, /etc/telegraf/telegraf.d/, /var/log/telegraf/ | telegraf | https://docs.influxdata.com/telegraf/v1/install/ |
| collectd | /usr/sbin/collectd, /etc/collectd.conf, /etc/collectd/collectd.conf.d/, /var/lib/collectd/ | collectd | https://collectd.org/documentation.shtml |
| Munin node | /usr/sbin/munin-node, /etc/munin/munin-node.conf, /etc/munin/plugins/, /var/lib/munin-node/ | munin-node | https://guide.munin-monitoring.org/en/latest/installation/index.html |
| Sensu Go agent | /usr/sbin/sensu-agent, /etc/sensu/agent.yml, /etc/default/sensu-agent, /etc/sysconfig/sensu-agent, /var/lib/sensu/ | sensu-agent | https://docs.sensu.io/sensu-go/latest/operations/deploy-sensu/install-sensu/ |
| Microsoft SCOM agent for UNIX/Linux (SCX / OMI) | /opt/microsoft/scx/, /opt/microsoft/scx/bin/tools/scxadmin, /etc/opt/microsoft/scx/, /etc/opt/microsoft/scx/ssl/, /var/opt/microsoft/scx/log/, /etc/opt/omi/, /var/opt/omi/log/ | omid, scx-cimd (legacy) | https://learn.microsoft.com/en-us/system-center/scom/manage-security-administer-crossplat-agent |
| LogicMonitor Collector | /usr/local/logicmonitor/agent/, /usr/local/logicmonitor/agent/conf/agent.conf, /usr/local/logicmonitor/agent/bin/sbshutdown | logicmonitor-agent, logicmonitor-watchdog (also /etc/init.d/logicmonitor.collector, logicmonitor.watchdog) | https://www.logicmonitor.com/support/installing-collectors |
| Pandora FMS software agent | /etc/pandora/pandora_agent.conf, /usr/share/pandora_agent/, /etc/init.d/pandora_agent_daemon | pandora_agent_daemon | https://pandorafms.com/manual/en/documentation/02_installation/05_configuration_agents |
| ManageEngine Site24x7 server agent | /opt/site24x7/monagent/, /opt/site24x7/monagent/conf/monagent.cfg, /opt/site24x7/monagent/bin/monagent, /opt/site24x7/monagent/plugins/ | site24x7monagent | https://www.site24x7.com/help/getting-started/server-monitoring-agent.html |
| Centreon Monitoring Agent (CMA) | /usr/bin/centagent, /etc/centreon-monitoring-agent/ | centreon-monitoring-agent (unit file centagent.service) | https://docs.centreon.com/docs/cma/ |
| ITRS Geneos Netprobe | /opt/itrs/geneos/ (path chosen at install), netprobe.linux_64, netprobe.sh | (site-defined; installed as a service per ITRS quickstart) | https://docs.itrsgroup.com/docs/geneos/7.8.0/collection/netprobe/installation/quickstart-linux-and-other-platforms/index.html |

### Endpoint management, RMM & software deployment
| vendor | files | systemd service name | website |
|---|---|---|---|
| Tanium | /opt/Tanium/TaniumClient, /opt/Tanium/TaniumClient/TaniumClient, /opt/Tanium/TaniumClient/tanium-init.dat | taniumclient | https://help.tanium.com/bundle/ug_client_cloud/page/client/deploy_package_linux.html |
| JumpCloud agent | /opt/jc/, /opt/jc/bin/jumpcloud-agent, /opt/jc/jcagent.conf | jcagent | https://jumpcloud.com/support/install-the-linux-agent |
| Automox | /opt/amagent | amagent | https://docs.automox.com/product/Product_Documentation/Agents/Agent_Installation/Installing_the_Automox_Agent_on_Linux.htm |
| NinjaOne | /opt/NinjaRMMAgent, /opt/NinjaRMMAgent/programfiles | | https://www.ninjaone.com/docs/new-to-ninjaone/agent-installation/linux-device-agent-installation/ |
| N-able N-central / N-sight RMM | | rmmagent | https://documentation.n-able.com/N-central/userguide/Content/Deploying/Agent/Agents_InstallRHELinuxAgents.html |
| HCL BigFix (formerly IBM Endpoint Manager / Tivoli) | /opt/BESClient/, /opt/BESClient/BESLib/, /var/opt/BESClient/, /var/opt/BESClient/besclient.config, /etc/init.d/besclient | besclient | https://help.hcl-software.com/bigfix/11.0/platform/Platform/Installation/c_red_hat_installation_instructi.html |
| ManageEngine Endpoint Central (formerly Desktop Central) | /usr/local/manageengine/uems_agent/, /usr/local/manageengine/uems_agent/logs/ | dcservice, dcondemand | https://www.manageengine.com/products/desktop-central/onboarding/how-to/how_to_install_linuxagent.html |
| Ivanti Neurons agent | /opt/ivanti/cloudagent/, /opt/ivanti/cloudagent/run/agent, stagentd | ivanticloudagent | https://help.ivanti.com/ht/help/en_US/CLOUD/vNow/agents.htm |
| Atera | /usr/lib/atera-agent/, /etc/atera-agent/, /var/spool/atera-agent/, /var/log/atera-agent/, /etc/systemd/system/AteraAgent.service | AteraAgent | https://support.atera.com/hc/en-us/articles/6266534935580-Install-Atera-s-Linux-Agent |
| Datto RMM (formerly CentraStage) | /usr/local/share/CentraStage/ (RHEL family), /opt/CentraStage/ (Debian family) | CagService | https://rmm.datto.com/help/en/Content/3NEWUI/Devices/AddADevice/InstallLinux.htm |
| ConnectWise Automate (formerly LabTech) | /usr/local/ltechagent/, /usr/local/ltechagent/ltechagent | ltechagent | https://docs.connectwise.com/ConnectWise_Automate |
| ConnectWise ScreenConnect access agent (formerly ConnectWise Control) | /opt/connectwisecontrol-\<instance-id\>/, /opt/screenconnect-\<instance-id\>/ | screenconnect-\<instance-id\> | https://docs.connectwise.com/ScreenConnect_Documentation/Get_started/Remote_access_guide/Install_an_access_agent |
| SolarWinds Platform Agent (swiagent) | /opt/SolarWinds/Agent/, /opt/SolarWinds/Agent/bin/swiagentd, /opt/SolarWinds/Agent/bin/swiagentaid.sh | swiagentd | https://documentation.solarwinds.com/en/success_center/orionplatform/content/core-deploy-a-linux-agent-manually.htm |
| Pulseway | /usr/sbin/pulsewayd, /etc/pulseway/config.xml, /etc/systemd/system/pulseway.service | pulseway | https://intercom.help/pulseway/en/articles/2971801-how-to-install-and-configure-pulseway-linux-agent-on-ubuntu-os |
| Scalefusion (Linux agent, package tux-agent) | /var/log/tux-agent/ (install dir and binary ??) | ?? | https://help.scalefusion.com/docs/enrolling-linux-devices |
| Syncro | syncro (CLI, path ??) | syncro | https://docs.syncrosecure.com/agents-alerts-automations/work-with-the-syncro-linux-agent |
| Kaseya VSA 10 / VSA X | /usr/sbin/vsax-registration, /etc/vsax/config.xml | vsax | https://help.vsa10.kaseya.com/help/Content/1-Modules/devices/deploy-linux.htm |
| Kaseya VSA 9 (legacy agent) | /opt/Kaseya/\<agent-instance-guid\>/, /opt/Kaseya/\<agent-instance-guid\>/bin/KcsUninstaller, /etc/init.d/kagent* | (SysV init script, kagent*) | https://help.vsa9.kaseya.com/help/Content/VSA/6908.htm |
| Action1 | /opt/action1/, /var/opt/action1/, /var/log/action1/ | action1_agent | https://www.action1.com/documentation/agent-installation/adding-endpoints-manually/linux/ |
| Level | /usr/local/bin/level, /var/lib/level/ | Level (unit file Level.service) | https://docs.level.io/en/articles/9926362-linux-install |
| SuperOps | /opt/superopsrmm/ (unverified - from a third-party uninstall script) | ?? | https://support.superops.com/en/articles/8355161-managing-linux-os-devices |
| Xcitium / ITarian Endpoint Manager Communication Client | /opt/COMODO/, /etc/systemd/system/itsm.service, /run/comodo/ | itsm | https://scripts.xcitium.com/frontend/web/topic/uninstall-endpoint-manager-communication-client-in-linux-devices |
| Tactical RMM | /usr/local/bin/tacticalagent, /opt/tacticalagent/, /etc/tacticalagent, /var/log/tacticalagent.log, /opt/tacticalmesh/meshagent (bundled MeshCentral agent) | tacticalagent, meshagent | https://docs.tacticalrmm.com/install_agent/ |
| MeshCentral MeshAgent | /usr/local/mesh_services/meshagent/, /usr/local/mesh_services/meshagent/meshagent, /usr/local/mesh_services/meshagent/meshagent.msh, /usr/local/mesh_daemons/ (non-systemd hosts) | meshagent | https://docs.meshcentral.com/meshcentral/agents/ |
| Microsoft Intune for Linux | /opt/microsoft/intune/bin/intune-portal, /opt/microsoft/intune/bin/intune-agent, /opt/microsoft/intune/bin/intune-daemon, /usr/bin/intune-portal, /run/intune/daemon.socket, /var/lib/intune/, ~/.local/state/intune/, /opt/microsoft/identity-broker/bin/microsoft-identity-broker, /opt/microsoft/identity-broker/bin/microsoft-identity-device-broker | intune-daemon (+ intune-daemon.socket), microsoft-identity-device-broker; user units (systemd --user): intune-agent (+ intune-agent.timer), microsoft-identity-broker (broker 2.x only - 3.x is D-Bus activated) | https://learn.microsoft.com/en-us/intune/user-help/company-portal/intune-app-linux |
| Omnissa Workspace ONE Intelligent Hub (formerly VMware) | /opt/omnissa/ws1-hub/, /opt/vmware/ws1-hub/ (pre-rebrand), /opt/omnissa/ws1-hub/bin/ws1HubUtil, /usr/bin/ws1HubUtil, /var/log/ws1-hub/ | ?? | https://docs.omnissa.com/bundle/LinuxDeviceManagement/page/Command-lineUtilitiesforWorkspaceONEIntelligentHubonLinux.html |
| Hexnode UEM | ?? | hexnode_agent | https://www.hexnode.com/mobile-device-management/help/linux-device-enrollment-in-hexnode-uem/ |
| Ivanti Endpoint Manager (formerly LANDesk; distinct from Ivanti Neurons) | /opt/landesk/, /opt/landesk/etc/landesk.conf, /opt/landesk/log/, /etc/init.d/cba8 (legacy agent), /usr/LANDesk/common/ (legacy 9.x agent) | ?? (legacy: cba8 SysV init script; pds2d runs as user ldnobody) | https://help.ivanti.com/ld/help/en_US/LDMS/11.0/Windows/client-c-linux.htm |
| Quest KACE SMA agent | /opt/quest/kace/bin/ (AMPAgent, AMPctl, AMPTools, AMPWatchDog, konea), /var/quest/kace/, /var/quest/kace/amp.conf, /var/log/quest/kace/ | konea | https://support-public.cfm.quest.com/80859_KACE_SMA_15.0_AdminGuide_en-US_1.pdf |

### Remote access & remote support agents
| vendor | files | systemd service name | website |
|---|---|---|---|
| TeamViewer (full client & TeamViewer Host) | /opt/teamviewer/, /opt/teamviewer/tv_bin/teamviewerd, /usr/bin/teamviewer, /etc/teamviewer/global.conf, /var/log/teamviewer15/ | teamviewerd | https://www.teamviewer.com/en/global/support/knowledge-base/teamviewer-remote/download-and-installation/linux/ |
| AnyDesk | /usr/bin/anydesk, /usr/share/anydesk/, /etc/anydesk/system.conf, /etc/anydesk/service.conf, /var/log/anydesk.trace, ~/.anydesk/ | anydesk | https://support.anydesk.com/docs/install-anydesk |
| RustDesk | /usr/share/rustdesk/rustdesk, /usr/bin/rustdesk, /root/.config/rustdesk/, ~/.config/rustdesk/ | rustdesk | https://rustdesk.com/docs/en/client/linux/ |
| Splashtop Streamer | /opt/splashtop-streamer/, /opt/splashtop-streamer/SRFeature, /opt/splashtop-streamer/config/global.conf, /usr/bin/splashtop-streamer | SRStreamer | https://support-splashtopbusiness.splashtop.com/hc/en-us/articles/360035513772-Download-Splashtop-Streamer-for-Linux |
| BeyondTrust Remote Support Jump Client (formerly Bomgar) | /opt/beyondtrust/sra-pin-*/ (default service-mode dir), /opt/bomgar/bomgar-pec-*/ (legacy) | ?? | https://docs.beyondtrust.com/rs/docs/deploy-jump-clients |
| Zoho Assist (unattended agent) | /var/log/ZohoAssist/ (install dir ??; deb package zohoassist) | ?? | https://www.zoho.com/assist/help/unattended-access/linux.html |

### Configuration management & Linux fleet management
Several of these ship by default on distro images (insights-client and subscription-manager on RHEL, landscape-common on Ubuntu), so an installed package alone does not mean the host is enrolled - check for config/registration files.

| vendor | files | systemd service name | website |
|---|---|---|---|
| Canonical Landscape client | /usr/bin/landscape-client, /usr/bin/landscape-config, /etc/landscape/client.conf, /var/lib/landscape/client/, /var/log/landscape/ | landscape-client | https://documentation.ubuntu.com/landscape/ |
| Red Hat Insights client (now Red Hat Lightspeed) | /usr/bin/insights-client, /etc/insights-client/insights-client.conf, /var/lib/insights/, /var/log/insights-client/ | insights-client (timer), insights-client-boot | https://docs.redhat.com/en/documentation/red_hat_lightspeed/1-latest/ |
| Red Hat rhc / yggdrasil (remote host configuration) | /usr/bin/rhc, /etc/rhc/, /usr/sbin/rhcd (RHEL 9 and earlier), /usr/bin/yggd, /etc/yggdrasil/config.toml, /usr/libexec/rhc/ (RHEL 10) | rhcd (RHEL 9 and earlier); yggdrasil, rhc-server (RHEL 10) | https://docs.redhat.com/en/documentation/red_hat_lightspeed/1-latest/html/remote_host_configuration_and_management/ |
| Red Hat Satellite / Katello client | /etc/rhsm/ca/katello-server-ca.pem (Satellite-specific), /etc/rhsm/rhsm.conf, /etc/pki/consumer/, /usr/sbin/katello-package-upload, /usr/sbin/katello-tracer-upload | rhsmcertd; goferd (legacy katello-agent, removed in Satellite 6.15) | https://docs.redhat.com/en/documentation/red_hat_satellite/ |
| SUSE Multi-Linux Manager / Uyuni (Salt Bundle) | /usr/lib/venv-salt-minion/, /etc/venv-salt-minion/minion, /etc/venv-salt-minion/minion.d/susemanager.conf, /etc/venv-salt-minion/pki/minion/, /var/log/venv-salt-minion.log | venv-salt-minion | https://documentation.suse.com/multi-linux-manager/5.1/en/docs/client-configuration/contact-methods-saltbundle.html |
| Salt minion | /usr/bin/salt-minion, /opt/saltstack/salt/ (onedir, 3006+), /etc/salt/minion, /etc/salt/minion.d/, /etc/salt/pki/minion/, /var/log/salt/minion | salt-minion | https://docs.saltproject.io/salt/install-guide/en/latest/ |
| Puppet agent / OpenVox agent | /opt/puppetlabs/puppet/bin/puppet, /opt/puppetlabs/bin/puppet, /etc/puppetlabs/puppet/puppet.conf, /etc/puppetlabs/puppet/ssl/, /opt/puppetlabs/puppet/cache/ or /var/opt/puppetlabs/puppet/cache/, /var/log/puppetlabs/ | puppet; pxp-agent (Puppet Enterprise) | https://help.puppet.com/core/current/ |
| Chef Infra Client | /opt/chef/bin/chef-client (Chef 18 and earlier), /hab/ (Chef 19, Habitat-packaged; exact path ??), /etc/chef/client.rb, /etc/chef/client.pem, /var/chef/cache/ | chef-client + chef-client.timer (created by the chef_client_systemd_timer resource, not the package) | https://docs.chef.io/client/ |
| CFEngine | /var/cfengine/bin/cf-agent, /var/cfengine/bin/cf-execd, /var/cfengine/inputs/promises.cf, /var/cfengine/policy_server.dat, /var/cfengine/ppkeys/ | cfengine3, cf-execd, cf-serverd, cf-monitord | https://docs.cfengine.com/docs/lts/ |
| Ansible Automation Platform / AWX receptor (execution & hop nodes) | /etc/receptor/receptor.conf, /var/run/receptor/receptor.sock (AAP 2.4 and earlier: /var/run/awx-receptor/receptor.sock), /var/log/receptor/receptor.log | receptor | https://docs.redhat.com/en/documentation/red_hat_ansible_automation_platform/ |
| ansible-pull | ~/.ansible/pull/\<fqdn\>/ (default checkout), cron entry (site-defined) | (none - usually run from cron) | https://docs.ansible.com/ansible/latest/cli/ansible-pull.html |

### Vulnerability management, live patching & compliance
| vendor | files | systemd service name | website |
|---|---|---|---|
| Tenable Nessus Agent | /opt/nessus_agent, /opt/nessus_agent/sbin/nessuscli, /opt/nessus_agent/sbin/nessusd | nessusagent | https://docs.tenable.com/agent/Content/InstallNessusAgentLinux.htm |
| Lynis (CISOfy) | /usr/sbin/lynis, /usr/bin/lynis, /etc/lynis/, /etc/cron.daily/lynis | (none - on-demand) | https://cisofy.com/documentation/lynis/ |
| OpenSCAP (oscap) | /usr/bin/oscap, /usr/share/xml/scap/ssg/content/ | (none - on-demand) | https://www.open-scap.org/ |
| SecPod Saner CVEM / SanerNow agent | ?? | ?? | https://docs.secpod.com/docs/how-to-download-saner-agent-in-linux/ |
| KernelCare / TuxCare live patching (CloudLinux) | /usr/bin/kcarectl, /usr/bin/kcare-uname, /etc/sysconfig/kcare/kcare.conf, /var/cache/kcare/, /usr/libexec/kcare/, /proc/kcare/ | (none - periodic auto-update, checks every ~4h) | https://docs.tuxcare.com/live-patching-services/ |

### Cloud provider management & monitoring agents
| vendor | files | systemd service name | website |
|---|---|---|---|
| Microsoft Azure Arc (Connected Machine agent; Defender for Servers) | /opt/azcmagent/bin/azcmagent, /opt/GC_Ext/, /opt/GC_Service/, /var/opt/azcmagent/ | himdsd, gcad, extd | https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-overview |
| Microsoft Azure Monitor Agent (AMA) | /etc/opt/microsoft/azuremonitoragent/, /var/opt/microsoft/azuremonitoragent/, /etc/default/azuremonitoragent | azuremonitoragent | https://learn.microsoft.com/en-us/azure/azure-monitor/agents/azure-monitor-agent-manage |
| AWS Systems Manager Agent (SSM) | /usr/bin/amazon-ssm-agent, /etc/amazon/ssm/, /var/lib/amazon/ssm/, /var/log/amazon/ssm/ | amazon-ssm-agent | https://docs.aws.amazon.com/systems-manager/latest/userguide/manually-install-ssm-agent-linux.html |
| Amazon CloudWatch Agent | /opt/aws/amazon-cloudwatch-agent/, /opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json | amazon-cloudwatch-agent | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/install-CloudWatch-Agent-on-EC2-Instance.html |
| Google Cloud Ops Agent | /etc/google-cloud-ops-agent/config.yaml, /opt/google-cloud-ops-agent/, /var/log/google-cloud-ops-agent/ | google-cloud-ops-agent, google-cloud-ops-agent-fluent-bit, google-cloud-ops-agent-opentelemetry-collector | https://cloud.google.com/stackdriver/docs/solutions/agents/ops-agent/installation |

### Identity, PAM & privileged access
| vendor | files | systemd service name | website |
|---|---|---|---|
| CyberArk | /opt/cyberark/epm/bin/epmcli, /opt/cyberark/epm/sbin/epmd | cyberark-epm, epmd | https://docs.cyberark.com/epm/latest/en/content/installation/linux-agentcommands.htm |
| BeyondTrust Privilege Management for Unix & Linux (PMUL) | /usr/sbin/pbmasterd, /usr/sbin/pblocald, /usr/sbin/pblogd, /usr/local/bin/pbrun, /opt/pbul, /opt/pbul/policies/pb.conf | | https://docs.beyondtrust.com/epm-ul/docs/install-process |
| Delinea / Centrify Server Suite | /etc/centrifydc/, /usr/share/centrifydc/bin, /opt/centrify/bin/adclient | centrifydc | https://docs.delinea.com/online-help/server-suite/install/deployment/install-agents/index.htm |
| Teleport | /usr/local/bin/teleport, /etc/teleport.yaml | teleport | https://goteleport.com/docs/ |
| Okta Advanced Server Access / Privileged Access (sftd) | /etc/sftd/, /var/lib/sftd | sftd | https://help.okta.com/asa/en-us/content/topics/adv_server_access/docs/install-agent.htm |
| One Identity Safeguard Authentication Services (VAS / Vintela) | /opt/quest/bin/vastool, /etc/opt/quest/vas/vas.conf, vasd | | https://support.oneidentity.com/technical-documents/safeguard-authentication-services/ |
| senhasegura / Segura (PEDM / EPM) | secpack-installer-*.run, senhasegura.go (kernel module) | | https://docs.senhasegura.io/docs/how-to-install-the-senhasegura-epm-linux-agent |
| StrongDM (relay / gateway node) | sdm (sdm relay / sdm gateway) | | https://www.strongdm.com/docs/admin/nodes/linux/ |

### Zero trust / SASE / NAC clients
| vendor | files | systemd service name | website |
|---|---|---|---|
| Zscaler Client Connector | /opt/zscaler, /opt/zscaler/.config.ini, /var/log/zscaler/ | zsaservice, zstunnel | https://help.zscaler.com/client-connector/customizing-zscaler-client-connector-install-options-linux |
| Netskope Client | /opt/netskope/stagent/, /opt/netskope/stagent/uninstall.sh, /opt/netskope/stagent/.eetk, /opt/netskope/stagent/data/nscacert.pem, nsclient | stagentd, stagentapp | https://docs.netskope.com/en/netskope-client-for-linux/ |
| Cloudflare WARP / Zero Trust | /usr/bin/warp-cli, /usr/bin/warp-svc | warp-svc | https://developers.cloudflare.com/warp-client/get-started/linux/ |
| Fortinet FortiClient (Linux) | /opt/forticlient, /opt/forticlient/fctsched, /usr/bin/forticlient | forticlient | https://docs.fortinet.com/document/forticlient/6.0.5/administration-guide/795692/linux |
| Cato Networks SDP client | cato-sdp | cato-client | https://support.catonetworks.com/hc/en-us/sections/7955161653277-Cato-Client-Installation-Guides |
| Genians Genian NAC / ZTNA agent | /usr/local/Geni, /usr/share/genias/GenianDB, /var/log/genians, /var/run/genians | | https://docs.genians.com/release/en/install/linux-agent.html |
| Sangfor aTrust (ZTNA client; distinct from Endpoint Secure) | /lib/systemd/system/eaio_service.service (EAIO component) | eaio_service | https://www.sangfor.com/support/security-advisory/local-privilege-escalation-vulnerability-sangfor-atrust-client |

### Microsegmentation & workload isolation
| vendor | files | systemd service name | website |
|---|---|---|---|
| Illumio VEN | /opt/illumio_ven/, /opt/illumio_ven/illumio-ven-ctl, /var/log/illumio_install.log | illumioven | https://product-docs-repo.illumio.com/Tech-Docs/Core/23.5/Admin/out/en/ven-administration-guide-23-5/ |
| Cisco Secure Workload (formerly Tetration) | /usr/local/tet (installer tetration_linux_installer.sh) | tet-sensor, tet-enforcer | https://www.cisco.com/c/en/us/td/docs/security/workload_security/secure_workload/user-guide/3_10/cisco-secure-workload-user-guide-on-prem-v310/install-linux-agents-for-deep-visibility-and-enforcement.html |
| ColorTokens Xshield | /etc/opt/colortokens/lgm/, /var/opt/colortokens/lgm/log/ | | https://docs.xshield.colortokens.com/article/556-agent-files |
| Akamai Guardicore Segmentation | GuardicorePlatformAgent-*.sh (installer; paths gated) | | https://techdocs.akamai.com/guardicore-platform-agent/docs/install-aztc |
| TrueFort Fortress | ?? | ?? | https://truefort.com/ |

### DLP & insider threat monitoring
| vendor | files | systemd service name | website |
|---|---|---|---|
| Fortra Digital Guardian (formerly Verdasys) | /dgagent/dgctl, /var/tmp/dgagent/install.log | dgdaemon | https://hstechdocs.helpsystems.com/releasenotes/Content/_ProductPages/Digital%20Guardian/Digital%20Guardian_linux.htm |
| Proofpoint ITM (formerly ObserveIT) | /opt/observeit/agent | | https://prod.docs.oit.proofpoint.com/installation_guide/unix_linux_agent_deployment.htm |
| Code42 Incydr / CrashPlan (Mimecast) | /usr/local/crashplan/, /usr/local/crashplan/bin/Code42Service, /usr/local/crashplan/Code42Service.pid, /var/lib/crashplan | | https://mimecastsupport.zendesk.com/hc/en-us/articles/42666055578259-Stop-and-start-the-Code42-service |
| Teramind (UAM / DLP, stealth agent) | tmagent (package), TMROOTDIR install dir | | https://kb.teramind.co/en/articles/8790992 |
| Endpoint Protector by CoSoSys (Netwrix) | EPPClient | | https://docs.netwrix.com/docs/endpointprotector/admin/agent |
| Cyberhaven (DDR / data lineage; Linux sensor exists, deployment docs are customer-gated) | ?? | ?? | https://www.cyberhaven.com/product/how-it-works |

### Data & database activity monitoring
| vendor | files | systemd service name | website |
|---|---|---|---|
| IBM Security Guardium S-TAP | /usr/local/guardium/guard_stap/ (guard_tap.ini, guardctl, guard_stap), /dev/guard_ktap | | https://www.ibm.com/docs/en/gdp/12.x?topic=luiuusta-linux-unix-install-s-tap-agents-installation-flow |
| Imperva Agent (SecureSphere / Data Security Fabric) | /opt/imperva, /opt/imperva/ragent/bin/rainit, /opt/imperva/ragent/bin/cli | | https://docs-cybersec.thalesgroup.com/bundle/v14.8-agent-release-notes/page/59030.htm |

### Backup & data protection agents
| vendor | files | systemd service name | website |
|---|---|---|---|
| Acronis Cyber Protect | /usr/lib/Acronis/BackupAndRecovery/uninstall/uninstall | | https://kb.acronis.com/content/56010 |
| Veeam Agent for Linux | /usr/lib/systemd/system/veeamservice.service, veeamsnap (kernel module) | veeamservice | https://helpcenter.veeam.com/docs/agentforlinux/userguide/installation_process.html |
| Commvault (File System Agent) | /opt/commvault, /opt/commvault/Base, cvd, cvlaunchd | | https://docs.commvault.com/2023e/commcell-console/ |
| Rubrik Backup Service (RBS) | rubrik-agent | rubrik-agent | https://docs.rubrik.com/en-us/9.0/ug/rbs/rbs_installing_linux.html |
| Cohesity Agent | /opt/cohesity, /var/log/cohesity | cohesity-agent | https://docs.cohesity.com/baas/Dashboard/Protection/AgentLinux.htm |
| Veritas NetBackup Client | /usr/openv/netbackup/bin/ (bpcd, vnetd, nbdisco, vopied), /usr/openv/pack/install.history | | https://www.veritas.com/content/support/en_US/doc/27801100-136237906-0/v118646263-136237906 |

### OT / ICS / IoT agents
| vendor | files | systemd service name | website |
|---|---|---|---|
| Nozomi Arc (OT/ICS endpoint sensor) | ?? | ?? | https://www.nozominetworks.com/platform/arc |
| TXOne StellarProtect (OT/ICS) | ?? | ?? | https://www.txone.com/products/endpoint-protection/stellar/ |
| Microsoft Defender for IoT micro-agent | defender-iot-micro-agent | defender-iot-micro-agent | https://learn.microsoft.com/en-us/azure/defender-for-iot/device-builders/ |

### Vendors with no Linux agent
Listed so they can be ruled out during triage.

| vendor | files | systemd service name | website |
|---|---|---|---|
| Webroot Endpoint Protection | [No Linux Support] | [No Linux Support] | https://www.webroot.com/us/en/business/products/endpoint-protection |
| Absolute Software | [No Linux Support] | [No Linux Support] | https://www.absolute.com |
| Raytheon Cyber (now Forcepoint — Forcepoint One Endpoint has no Linux agent) | [No Linux endpoint agent] | [No Linux endpoint agent] | https://help.forcepoint.com/F1E/en-us/v26/ep_install/ep_install.pdf |
| Stormshield Endpoint Security (SES Evolution) | [No Linux support - Windows only] | [No Linux support - Windows only] | https://www.stormshield.com/products-services/products/endpoint-protection/stormshield-endpoint-security/ |
| Blackpoint Cyber CompassOne / SNAP-Defense | [No Linux support - Windows and macOS only] | [No Linux support - Windows and macOS only] | https://blackpointcyber.com/solutions/ |
| Barracuda RMM (formerly Managed Workplace) | [No Linux agent - Linux monitored agentless via SNMP from Onsite Manager] | [No Linux agent] | https://documentation.campus.barracuda.com/wiki/spaces/BRMM20251/pages/8753937/Device+Manager+and+Support+Assistant+-+Hosted |
| Rippling device management | [No Linux support - Windows and macOS only] | [No Linux support - Windows and macOS only] | https://www.rippling.com/blog/rippling-mdm-review |
| Kandji (now Iru) | [No Linux support - Apple, Windows and Android only] | [No Linux support - Apple, Windows and Android only] | https://support.kandji.io/kb/device-requirements |
| Addigy | [No Linux support - Apple only] | [No Linux support - Apple only] | https://docs.addigy.com/interface/Add_Devices/ |
| Mosyle | [No Linux support - Apple only] | [No Linux support - Apple only] | https://business.mosyle.com/ |
| Miradore (cloud MDM; the separate on-premise Miradore Management Suite does have a Linux client) | [No Linux support] | [No Linux support] | https://www.miradore.com/faq/ |
