# Roadmap for vulcanizer features

This is not a guarantee of any feature, but a rough plan on where we will develop further.

## v0.1.0 - [Released](https://github.com/github/vulcanizer/releases/tag/v0.1.0)

Release of basic functionality for the basic client with a idiomatic API containing structs for data returned and a possible error.

Functionality:
* Get health status of a cluster
* Get nodes of a cluster
* Get indices of a cluster
* Get settings of a cluster
* Get snapshots of a cluster
* Get details of a snapshot
* Drain a server - set shard allocation rules so that data moves off of the server
* Fill a server - remove shard allocations rules so that data moves on to the server
* Fill all servers - remove all shards allocation exclusion rules
* Set a cluster setting
* Enable or disable cluster allocation entirely


## v0.2.0 - [Released](https://github.com/github/vulcanizer/releases/tag/v0.2.0)

Handle more cases around repositories and snapshots.

Functionality:
* Verify a repository
* Delete a snapshot

## v0.3.0 - [Released](https://github.com/github/vulcanizer/releases/tag/v0.3.0)

Even more cases around repositories and snapshots.

Functionality:
* List repositories
* Take snapshots
* Restore snapshots

## v0.4.0 - [Released](https://github.com/github/vulcanizer/releases/tag/v0.4.0)

Add functionality for managing indices.

Functionality:
* Delete index
* Get pretty index settings
* Get machine readable index settings
* Set index settings
* Get pretty index mappings
* Analyze text with built in analyzers
* Analyze text based on a field
* Additional client options for HTTPS, timeout, HTTP basic auth, and TLS configuration

## v0.5.0 - [Released](https://github.com/github/vulcanizer/releases/tag/v0.5.0)

Functionality:
* Open index
* Close index
* List/add/update/remove aliases
* List shards
* Display shard recovery information
* New client configuration options: user, password, path, protocol, TLS verification
Sure, let's go through the README and outline the step-by-step process for deploying the `vulcanizer` project.

### Step-by-Step Deployment Process

1. **Install Go**:
   - Ensure you have Go installed on your machine. You can download and install it from [golang.org](https://golang.org/dl/).

2. **Get the Project**:
   - Use the `go get` command to download the `vulcanizer` project into your `$GOPATH`.
   ```sh
   go get github.com/github/vulcanizer
   ```

3. **Navigate to the Project Directory**:
   - Change directory to the project directory within your `$GOPATH`.
   ```sh
   cd $GOPATH/src/github.com/github/vulcanizer
   ```

4. **Bootstrap the Project**:
   - Run the bootstrap script to set up the project.
   ```sh
   ./script/bootstrap
   ```

5. **Build the Project**:
   - Compile the project and install the `vulcanizer` binary to `$GOPATH/bin`.
   ```sh
   ./script/build
   ```

6. **Run Tests**:
   - Execute the test suite to ensure everything is set up correctly.
   ```sh
   ./script/test
   ```

7. **Configuration**:
   - Create a configuration file at `~/.vulcanizer.yaml` with your cluster information.
   ```yml
   local:
     host: localhost
     port: 9200
   staging:
     host: 10.10.2.1
     port: 9201
   production:
     host: 10.10.1.1
     port: 9202
   ```

8. **Using the Command Line Application**:
   - You can now use the `vulcanizer` binary to manage your Elasticsearch cluster. Here are some example commands:
   ```sh
   # Query for cluster health on the "local" cluster
   vulcanizer health --cluster local

   # Query for nodes against the node 10.10.2.1 and port 9202
   vulcanizer nodes --host 10.10.2.1 --port 9202
   ```

### Additional Information

- **Supported Elasticsearch Versions**:
  - Integration tests are set up to run against the latest v5 and v6 versions of Elasticsearch.

- **Development**:
  - To compile the project and install the `vulcanizer` binary:
    ```sh
    ./script/build
    ```
  - To run the tests:
    ```sh
    ./script/test
    ```

- **Contributing**:
  - This repository is open to contributions. Please see the CONTRIBUTING.md and CODE_OF_CONDUCT.md for more details.

- **License**:
  - This project is released under the MIT LICENSE.

By following these steps, you should be able to deploy and use the `vulcanizer` project to manage your Elasticsearch cluster. If you have any specific questions or run into issues, feel free to ask!