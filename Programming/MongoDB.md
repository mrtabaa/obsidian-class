#### Linux:

- [ ] Install [MongoDB Community Server](https://www.mongodb.com/try/download/community) (Debian / Ubuntu)
- [ ] Install [MongoDB Compose](https://www.mongodb.com/try/download/compass) (Ubuntu)
- [ ] Install [MongoDB Shell](https://www.mongodb.com/try/download/shell) (Debian / Ubuntu)
- [ ] [Enable Replication/Replica](https://stackoverflow.com/a/77932054/3944285)

- [ ] Check if server is running 
```bash
sudo systemctl status mongod
```

If server/service  is `Active: failed`
	[[Fix MondoDB Service]]

 **If not running**, start the server 
```bash
sudo systemctl enable mongod
sudo systemctl start mongod
```

##### Uninstall
```bash
sudo service mongod stop
sudo apt-get purge mongodb-org*
sudo rm -r /var/log/mongodb /var/lib/mongodb
```

Back to [[Linux apps & update]]
OR
Back to [[Project Steps]]
#### Windows
1. Install MongoDB Server Community
2. Install **Nuget Gallery** in VSCode.
3. Install official VSCode MongoDB extension (works like campus).

Back to [[Project Steps]]