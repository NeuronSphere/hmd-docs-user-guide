.. _install_neuronsphere:

Installing the Local Neuronsphere
=================================

Follow these steps to install and configure the local Neuronsphere environment:

1. **Install Prerequisites**
   - Ensure you have the following tools installed:
     - Docker: https://docs.docker.com/get-docker/
     - Docker Compose: https://docs.docker.com/compose/install/
     - Python (<= 3.10): https://www.python.org/downloads/
   - For Windows users, ensure that Windows Subsystem for Linux (WSL) is installed and running. Refer to the [WSL installation guide](https://learn.microsoft.com/en-us/windows/wsl/install).
   - Verify the installations by running:

.. code-block:: bash

     docker --version
     docker-compose --version
     python --version

.. note::
   Additionally, you can use `uv` to install Python 3.10 if it's not already available on your system:
   `uv install python3.10`
   You can use the `uv` package to create a virtual environment and install packages. This method simplifies dependency management:
   
   This step is optional and can be used instead of the standard virtual environment setup.

  .. code-block:: bash

    pip install uv
    uv venv
    uv pip install neuronsphere


2. **Create a Python Virtual Environment**
   - Run the following commands to create and activate a virtual environment:

.. code-block:: bash
    
     python -m venv venv
     source venv/bin/activate  # On Windows, use `venv\\Scripts\\activate`
    

3. **Install Neuronsphere**
   - Install the Neuronsphere package using pip:

.. code-block:: bash

     pip install neuronsphere
  
4. **Set Up HMD_HOME**
   - Create a directory for HMD_HOME:
     `mkdir -p /path/to/hmd_home`
   - Set the `HMD_HOME` environment variable to the absolute path of the directory:
     `export HMD_HOME=/path/to/hmd_home`
   - Add this line to your shell configuration file (e.g., `.bashrc`, `.zshrc`) to persist the variable:
     `export HMD_HOME=/path/to/hmd_home`

5. **Run `hmd configure`**
   - Execute the following command and answer the prompts:
     `hmd configure`
     - Enter your name.
     - Enter your email.
     - Enter a 2-4 letter code for your company to prefix all Neuronsphere tooling created repos (optional).
     - Optionally enter your Docker username and password or press Enter to leave blank.

6. **Verify Configuration**
   - Confirm the existence of the configuration file:
     `ls $HMD_HOME/.config/hmd.env`
   - Ensure the `$HMD_HOME/projects` directory exists. If not, create it and set the environment variable:
     
.. code-block:: bash

     mkdir -p $HMD_HOME/projects
     hmd configure set-env HMD_REPO_HOME $HMD_HOME/projects

7. **Start Neuronsphere**
   - Run the following command to start Neuronsphere:
     `hmd neuronsphere up`
   - Wait for the required Docker images to be pulled.

You are now ready to use the local Neuronsphere environment.

Services Running in the Local Neuronsphere
------------------------------------------

The local Neuronsphere environment includes the following services:

- **Trino**: Accessible at http://localhost:8081. Trino is a distributed SQL query engine designed for running fast analytic queries.
- **JupyterLab**: Accessible at http://localhost:8888. JupyterLab provides an interactive development environment for notebooks, code, and data.
- **Apache Superset**: Accessible at http://localhost:8088. Apache Superset is a modern data exploration and visualization platform.
- **Airflow**: Accessible at http://localhost:175. Airflow is a platform to programmatically author, schedule, and monitor workflows.
- **PostgreSQL**: A relational database system used for structured data storage and retrieval.
- **Gremlin-Compatible Graph Database**: A graph database supporting Gremlin queries for graph-based data modeling.
- **Local DynamoDB**: A local version of Amazon DynamoDB for NoSQL database operations.