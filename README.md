# ansible_ovirt_DR
An ansible script to recover oVirt setup

# Before running this script
* You must have a running oVirt setup
* Execute `source hacking/env-setup`
* Run the following command for the script to start:
   ./bin/ansible-playbook ~/ansible/playbooks/setup_demo.yml --ask-vault-pass

# Known issues
The script use SSO token on every command since there is a known issue [1].
The problem is that once oVirt use password '1' and the password
attribute is set as it should not be logged, so it's obfuscated, everywhere where possible,
so every '1' in the output is replaced by '******', and if you take a look at the generated token
you can see it contains some '*****', which means it contained '1', but was replaced by '*****',
so it became invalid token.

Suggested workarounds:
  1) Do not use password '1', but something different.
  2) Wait for the fix

[1] https://github.com/ansible/ansible/issues/19278



