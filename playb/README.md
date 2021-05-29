Laboratorio
   OC
      ==> ansible-playbook playbooks/lab-oc-cloudbees.yml --ask-vault-pass --user=l0699641 --ask-pass
   
   Mastar
      ==> ansible-playbook playbooks/lab-master-cloudbees.yml --ask-vault-pass --user=l0699641 --ask-pass

   tiempo 4m12.24s Ansible y 1 minuto mas para que termine de iniciar el master

Produccion

   OC
      ==> ansible-playbook -v playbooks/oc-baja-servico-cloudbees.yml  --ask-vault-pass --user=l0699641 --ask-pass
      ==> ansible-playbook -v playbooks/oc-backup-nfs1-cloudbees.yml  --ask-vault-pass --user=l0699641 --ask-pass
      ==> ansible-playbook -v playbooks/oc-upgrade-master-cloudbees.yml  --ask-vault-pass --user=l0699641 --ask-pass

   Master

0) validar conexion:

   ==>   ansible-playbook -v playbooks/id.yml  --ask-vault-pass --user=l0170909 --ask-pass

1) baja-servico-cloudbees   cambiar host=allmaster

   ==>   ansible-playbook -v playbooks/master/baja-servico-cloudbees.yml   --ask-vault-pass --user=l0170909 --ask-pass

2) backup-nfs2-cloudbees    cambiar host=devnfs

   ==>   ansible-playbook -v playbooks/master/backup-nfs2-cloudbees.yml --ask-vault-pass --user=l0170909 --ask-pass 
   
   backup-nfs1-cloudbees    cambiar host=prdnfs
   
   ==>   ansible-playbook -v playbooks/master/backup-nfs1-cloudbees.yml --ask-vault-pass --user=l0170909 --ask-pass

3) upgrade-master-cloudbees cambiar host=devmaster1 devmaster2 devmaster3 intmaster prdmaster

   ==>   ansible-playbook -v playbooks/master/upgrade-master-cloudbees.yml --ask-vault-pass --user=l0170909 --ask-pass

