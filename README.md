selinux-policy-injector
=======================

Injects allow rules into binary SELinux kernel policies

~/sepolicy-inject $ ./sepolicy-inject -s shell -t system -c file -p read -P sepolicy -o sepolicy2
libsepol.policydb_index_others: security:  1 users, 2 roles, 518 types, 14 bools
libsepol.policydb_index_others: security: 1 sens, 1024 cats
libsepol.policydb_index_others: security:  84 classes, 4539 rules, 162 cond rules

~/sepolicy-inject $ sesearch -A -s shell -t system -c file sepolicy
Found 1 semantic av rules:
allow appdomain domain : file { ioctl read getattr lock open } ;

~/sepolicy-inject$ sesearch -A -s shell -t system -c file sepolicy2
Found 2 semantic av rules:
allow shell system : file read ;
allow appdomain domain : file { ioctl read getattr lock open } ;

