# Creating a server

> Navigation: New Server...

The first step is deploying the server that your database will reside on. Each server is assigned an address, such as arnold.zenite.io, which is used to access the database using third-party clients (MySQL Workbench, pgadmin, robo3t etc.) or using HTTPS endpoints. To deploy a server, do the following actions:

1. Choose a server type:
   * MariaDB
   * PostgreSQL
   * MongoDB
  
2. Choose a server tier.

   > Take careful consideration of your future performance and storage requirements. If necessary, you can scale up the server at a later time, however this requires your server to be shut down and restarted.

3. Choose a server region.

   > Take into consideration the location of the services/users that will connect to the database.

4. Click "Deploy".

> The deployment process will start and will take approximately 2 minutes. After your server becomes available, the server icon in the menu will enable and you will be able to access the server.
