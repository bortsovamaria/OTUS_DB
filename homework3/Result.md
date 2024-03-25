# Результат

1. [VirtualBox - Ubuntu ](install_postgres_ubuntu.png) - screen

        sudo sh -c 'echo "deb https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'


        wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -


        sudo apt-get update

        sudo apt-get -y install postgresql-15

## 2. 
    sudo service postgresql start

## 3.
    sudo -i -u postgres
    psql
    create role testuser login password 'testuser';
    create database testdb with owner testuser;
    exit
    sudo gedit pg_hba.conf (edit to local all all md5)
    sudo -i -u posetgres
    psql -h localhost -p 5432 -U testuser testdb  master

    ->
        testdb=>


## 4. 
[Dbeaver ](dbeaver.png) - screen

    alter user postgres password 'postgres';
    connect with postgres or testuser

    