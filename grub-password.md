---
layout:
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
---

# GRUB password

<pre data-full-width="true"><code>zahasłowanie GRUBa
<strong>grub-mkpasswd-pbkdf2
</strong>
#żeby dopisać użytkownika który może edytować zahasłowanego GRUBa
sudo nano /etc/grub.d/00_header
#i dopisujemy

cat &#x3C;&#x3C; EOF
set superusers="kali"
password_pbkdf2 kali grub.pbkdf2.sha512.10000.03836830149D92288DBAEBC9D7907B4BBA84797847126C1E
EOF

#a w pliku /etc/default/grub
GRUB_DISABLE_OS_PROBER=false

#updatujemy GRUB
update-grub
</code></pre>
