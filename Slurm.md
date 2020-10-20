
# Slurm Setup Guide



## Install Slurm

```
sudo apt update
sudo apt search slurm
sudo apt install slurm-wlm
sudo apt install slurm-wlm-doc
```

## Install Mariadb for Slurm Accounting

```
apt-get install mariadb-server
systemctl enable mysql
systemctl start mysql
mysql -u root

create database slurm_acct_db;
create user 'slurm'@'localhost';
set password for 'slurm'@'localhost' = password('slurmdbpass');
grant usage on *.* to 'slurm'@'localhost';
grant all privileges on slurm_acct_db.* to 'slurm'@'localhost';
flush privileges;
exit;
```
