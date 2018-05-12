# Creating a server

> New Server...

The first step is deploying the server that your database will reside on. Each server is assigned random a subdomain, such as arnold.zenite.io, which is used to access the database using third-party clients ([MySQL Workbench](https://www.mysql.com/products/workbench/), [pgAdmin](https://www.pgadmin.org/), [Robo 3T](https://robomongo.org/) etc.) or using user-created endpoints.

To deploy new a server, click on 'New Server...' button in the navigation, then:

1. Choose a server type:
   * MariaDB
   * PostgreSQL
   * MongoDB
  
2. Choose a server tier.

   > Take careful consideration of your future performance and storage requirements. If necessary, you can scale up the server at a later time, however this will require your server to be shut down and restarted.

3. Choose a server region.

   > Take into consideration the location of the services/users that will connect to the database.

4. Click the "Deploy" button.

The deployment process will start and will take approximately 2 minutes. You can monitor the deployment progress on the server label. After your server becomes available, the server icon in the menu will enable and you will be able to access the server options.
