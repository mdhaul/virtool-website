---
title: "Setup"
description: "Setup a Virtool installation using the web interface"
menu:
  manual:
    parent: "Getting Started"
    weight: 30
---

# Run

After installing Virtool, the server can be started by issuing the following command in the Virtool install directory.

```shell
./run
```

Use `./run --help` to see an overview of additional command line arguments Virtool can accept.

By default, the server listens at `localhost:9950`. When you visit this address for the first time, you will have to complete a one-time setup interface.

!["Setup page overview"](overview.png)

This will allow you to configure the essential settings required for Virtool to run. Click the **Setup** button to begin.

# Connect to a Proxy

If you connect to the internet through a proxy, you can configure it here.

**You can skip this step if you don't use a proxy**.

!["Successful proxy configuration](proxy.png)

{{< note title="Important" color="red" >}}
HTTPS proxies are not currently supported.
{{< /note >}}

# Connect to MongoDB

MongoDB must be [installed and running](setup.md#MongoDB) before you can use Virtool.

Once MongoDB is ready, you can configure a connection to it using a [MongoDB connection string and database name](https://docs.mongodb.com/manual/reference/connection-string). When setup is complete, a new database will be created using the provided name.

![MongoDB default placeholder parameters](mongo_empty.png)

The placeholder values can be used by clicking {{< icon "fas fa-plug" >}} **Connect** without changing the form. You can also specify a different address, authentication, or authentication database for your connection by changing the connection string.

Virtool will return an error if there is already a database with the provided **Database Name**.

![MongoDB alternate connection parameters](mongo_filled.png)

You will see something like the following when the connection is successful:

![MongoDB successful connection](mongo_success.png)

{{< note title="Important" color="red" >}}

We highly recommend enabling authentication for MongoDB.

The MongoDB connection string is stored in plaintext in the application configuration file. [Configure Virtool using environmental variables](/docs/manual/gs_configuration) to keep your connection string safe.

{{< /note >}}

# Set Data Location {#data_path}

The data location is where Virtool stores bioinformatic data including uploaded Illumina libraries, imported sample data, and reference indexes. The path should be located on a storage device that offers good speed, capacity, and redundancy.

Paths beginning with `/` will be assumed to be absolute paths. All other paths will be interpreted relative to the Virtool installation directory.

![Data path form with default placeholder value](data.png)

By default the path will be set to `data` and will be created in the Virtool installation directory. This configuration should only be used for testing purposes. Use a path on a separate RAID volume or network attached storage (NAS) to store data securely.

![Data path form with custom value](data_filled.png)

When the data path has been successfully configured, you should see something like this:

![Data path configuration successfull](data_success.png)

{{< note >}}

**Errors will occur if:**

- the executing user does not have permission to write the data path
- the data path already exists and is not empty

{{< /note >}}

# Set Watch Location {#watch_path}

The primary method for making Illumina FASTQ files available to Virtool for sample creation is by uploading them through the web interface.

It is also possible to set a path accessible to the server that will be watched for new read files. Any FASTQ files dropped in this watch directory will be pulled into Virtool and made available for sample creation.

By default the data path will be set to `watch` and will be created in the Virtool installation directory.

![Watch path form with default placeholder value](watch.png)

When the watch location has been successfully configured, you will see something like this:

![Watch path configured successfully](watch_success.png)

# Save and Restart

Once all setup sections have been completed, a summary will be displayed and a {{< icon "fas fa-redo-alt" >}} **Save and Restart** button will be be enabled.

![Server setup summary](finish.png)

Clicking the button will apply all of the summarized actions and restart the server. You can login for the first time with the user profile you created during setup.

![Server restarting after setup](loading.png)

# Manual Setup

It is possible to configure Virtool without completing the graphical setup process.

Passing the `--no-setup` argument when running Virtool will skip the setup process and use default configuration values or values from [manual configuration sources](/docs/manual/gs_configuration/).

# Add First User {#first_user}

Once the server has been setup, you have to create an initial user. This user will be automatically given an administrative role.

This form will appear if no users are present in the configured database:

![Empty user form](user.png)

Fill out the form with an administrator username and password and click {{< icon "fas fa-user-plus" >}} **Create User**:

![Filled out user form](user_filled.png)

The Virtool application should load and automatically log in as the new user:

![First user successfully created](user_success.png)

{{< note title="Important" color="red" >}}
We strongly recommend **not** making the account a generic adminstrative account.

Doing so defeats Virtool's built-in auditing, which is designed in accordance with [ISO 17025:2005](https://www.iso.org/standard/39883.html). Each account should correspond to an individual user.
{{< /note >}}
