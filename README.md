Ansible playbook to deploy on a single host: JBoss EAP Domain Controller + Host. This playbook includes:

* 4 roles
	1. JBoss - in domain mode
        2. JBoss - in host mode, connecting to the domain controller using an admin user
        3. EWS - Apache with mod_cluster
        4. JBoss - Data Grid. Ideally the application running within EAP, will connect using HotRod to the Grids.

This setup will have 2 replicated caches configured. Replication because, eventually there will be another 2 hosts. Certain aspects are assumed within this playbook :

1. Server is subscribed to the RHN
2. No changes are to be made to the templates and files located within this playbook.
3. No software is included ( might be for testing ). Log into https://access.redhat.com to download the relevant software. There is a vars ( variable ) file located within each role. You may need to edit this file to include the correct name of each software file.
4. Due to the hellish nature of XML, text processing tools ( SED,AWK etc ) are just not comprehensive enough and certain tasks are too convuluted with said tools. In its place I have downloaded xsh, which is an XML shell. This is provided by the perl-CPAN package which can be installed on any system.
# ansible-jboss
