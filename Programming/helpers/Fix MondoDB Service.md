If `sudo systemctl status mongod` shows `Failed` run these commands
```bash
sudo rm -rf /tmp/mongodb-27017.sock
sudo service mongod start
sudo chown -R mongodb:mongodb /var/lib/mongodb
sudo chown mongodb:mongodb /tmp/mongodb-27017.sock
```

Back to [[MongoDB]]