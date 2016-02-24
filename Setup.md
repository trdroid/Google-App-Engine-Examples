### Prerequisites

* Java 7 SDK
* Python 2.7
* Google Cloud SDK (requires Python 2.7)

<b> Google Cloud SDK </b>

The Google Cloud SDK contains the tools and libraries for developing, testing, and deploying applications for the Google Cloud platform. The App Engine is one of many components of the Google Cloud Platform.

### Installing the Google Cloud SDK

> curl https://sdk.cloud.google.com | bash

The installation directory that I provided during the installation is /home/droid/software/google-cloud

It also asks for the path to the rc file and adds itself to the PATH

> software/google-cloud$ ls

    google-cloud-sdk

> software/google-cloud$ ls google-cloud-sdk/

    bin  completion.bash.inc  completion.zsh.inc  install.bat  install.sh  lib  LICENSE  path.bash.inc  path.zsh.inc  platform  properties  README  RELEASE_NOTES

### Exploring the <i>gcloud</i> command

In a new terminal window, check the following

> droid@droidserver:~/onGit/GAE$ gcloud -h

    Usage: gcloud [optional flags] <group | command>
      group may be           auth | components | compute | config | container |
                             dataproc | deployment-manager | dns | preview |
                             projects | source | sql | topic
      command may be         docker | feedback | help | info | init | version
    
    The *gcloud* CLI manages authentication, local configuration, developer
    workflow, and interactions with the Google Cloud Platform APIs.
    
    commonly used flags:
      --account ACCOUNT      Google Cloud Platform user account to use for
                             invocation.
      --configuration CONFIGURATION
                             The configuration to use for this command invocation.
      --format FORMAT        The format for printing command output resources.
      --help                 Display detailed help.
      --project PROJECT_ID   Google Cloud Platform project ID to use for this
                             invocation.
      --quiet, -q            Disable all interactive prompts.
      --verbosity VERBOSITY  Override the default verbosity for this command.  This
                             must be a standard logging verbosity level: [debug,
                             info, warning, error, critical, none] (Default:
                             [warning]).
      -h                     Print a summary help and exit.
      -v, --version          Print version information and exit. This flag is only
                             available at the global level.
    
    other flags:
      Run: `gcloud --help`
      for the full list of available flags for this command.
    
    command groups:
      auth                   Manage oauth2 credentials for the Google Cloud SDK.
      components             List, install, update, or remove Google Cloud SDK
                             components.
      compute                Read and manipulate Google Compute Engine resources.
      config                 View and edit Google Cloud SDK properties.
      container              Deploy and manage clusters of machines for running
                             containers.
      dataproc               Create and manage Google Cloud Dataproc clusters and
                             jobs.
      deployment-manager     Manage deployments of cloud resources.
      dns                    Manage your Cloud DNS managed-zones and record-sets.
      preview                Manage Preview CLI command groups.
      projects               Manage your Projects.
      source                 Cloud git repository commands.
      sql                    Manage Cloud SQL databases.
      topic                  gcloud supplementary help.
    
    commands:
      docker                 Provides the docker CLI access to the Google Container
                             Registry.
      feedback               Provide feedback to the Google Cloud SDK team.
      help                   Prints detailed help messages for the specified
                             commands.
      info                   Display information about the current gcloud
                             environment.
      init                   Initialize or reinitialize gcloud.
      version                Print version information for Cloud SDK components.

The <i>gcloud</i> command can be used to interact with the Cloud Platform as an administrator and also to
* install and update components
* deploy applications
* perform maintenance tasks
    
### Authenticating with Cloud SDK

Authenticate with the Cloud SDK using the following command.

> onGit/GAE$ gcloud auth login

    Your browser has been opened to visit:
    
        https://accounts.google.com/o/oauth2/auth?redirect_uri=http%3A%2F%2Flocalhost%3A8085%2F&prompt=select_account&response_type=code&client_id=32555940559.apps.googleusercontent.com&scope=https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcloud-platform+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fappengine.admin+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcompute&access_type=offline
    
    
    Created new window in existing browser session.

This opens a browser window asking to signin to Google. Once signed in, a permission screen is displayed.

<img src="_misc/Permissions%20screen.png"/>

Once allowed, the following page is displayed

<img src="_misc/After%20Allowing%20the%20Permission%20to%20the%20Cloud%20SDK.png"/>

More than one account can be added using the same command i.e. <i>gcloud auth login</i> and by signing in with a different account.

The credentials provided to <i>gcloud</i> are remembered for each authenticated account. The credentials for the active account are used automatically with the subsequent commands. 

<b> Viewing All Accounts, Including the Active one </b>

> onGit/GAE$ gcloud auth list

    Loading legacy configuration file: [/home/droid/.config/gcloud/properties]
    This configuration file is deprecated and will not be read in a future
    gcloud release.  gcloud will automatically migrate your current settings to the
    new configuration format the next time you set a property by running:
      $ gcloud config set PROPERTY VALUE
    You may also run:
      $ gcloud init
    to create a new configuration and walk you through initializing some basic
    settings.  You can find more information on named configurations by running:
      $ gcloud topic configurations
    
    Credentialed accounts:
     - emailAddressProvided@gmail.com (active)
    
    To set the active account, run:
      $ gcloud config set account ``ACCOUNT''

<b> To switch the Active account </b>

> gcloud config set account another.account.authenticated@gmail.com


### Clearing Credentials

To clear the credentials for an account, revoke its authentication

> onGit/GAE$ gcloud auth revoke

    Loading legacy configuration file: [/home/droid/.config/gcloud/properties]
    This configuration file is deprecated and will not be read in a future
    gcloud release.  gcloud will automatically migrate your current settings to the
    new configuration format the next time you set a property by running:
      $ gcloud config set PROPERTY VALUE
    You may also run:
      $ gcloud init
    to create a new configuration and walk you through initializing some basic
    settings.  You can find more information on named configurations by running:
      $ gcloud topic configurations
    
    Revoked credentials for emailAddressProvided@gmail.com
    No credentialed accounts.
    
    To login, run:
      $ gcloud auth login ``ACCOUNT''

### View Installed Components

> onGit/GAE$ gcloud components list

    Loading legacy configuration file: [/home/droid/.config/gcloud/properties]
    This configuration file is deprecated and will not be read in a future
    gcloud release.  gcloud will automatically migrate your current settings to the
    new configuration format the next time you set a property by running:
      $ gcloud config set PROPERTY VALUE
    You may also run:
      $ gcloud init
    to create a new configuration and walk you through initializing some basic
    settings.  You can find more information on named configurations by running:
      $ gcloud topic configurations
    
    
    Your current Cloud SDK version is: 97.0.0
    The latest available version is: 97.0.0
    
    ┌─────────────────────────────────────────────────────────────────────────────────┐
    │                                    Components                                   │
    ├───────────────┬─────────────────────────────────┬───────────────────┬───────────┤
    │     Status    │               Name              │         ID        │    Size   │
    ├───────────────┼─────────────────────────────────┼───────────────────┼───────────┤
    │ Not Installed │ Cloud Datastore Emulator        │ gcd-emulator      │  38.1 MiB │
    │ Not Installed │ Cloud Pub/Sub Emulator          │ pubsub-emulator   │  10.1 MiB │
    │ Not Installed │ gcloud Alpha Commands           │ alpha             │   < 1 MiB │
    │ Not Installed │ gcloud Beta Commands            │ beta              │   < 1 MiB │
    │ Not Installed │ gcloud app Java Extensions      │ app-engine-java   │ 101.4 MiB │
    │ Not Installed │ gcloud app Python Extensions    │ app-engine-python │   7.2 MiB │
    │ Not Installed │ kubectl                         │ kubectl           │           │
    │ Installed     │ BigQuery Command Line Tool      │ bq                │   < 1 MiB │
    │ Installed     │ Cloud SDK Core Libraries        │ core              │   3.7 MiB │
    │ Installed     │ Cloud Storage Command Line Tool │ gsutil            │   2.6 MiB │
    │ Installed     │ Default set of gcloud commands  │ gcloud            │           │
    └───────────────┴─────────────────────────────────┴───────────────────┴───────────┘
    
     
    To install or remove components at your current SDK version [97.0.0], run:
      $ gcloud components install COMPONENT_ID
      $ gcloud components remove COMPONENT_ID
    
    To update your SDK installation to the latest version [97.0.0], run:
      $ gcloud components update


### Install Google App Engine Component

The App Engine Component provides necessary tools (implemented in Python which explains the dependency on Python 2.7) to run and test applications locally, and to deploy them to the Cloud Platform. 

> onGit/GAE$ gcloud components install app-engine-java

    Loading legacy configuration file: [/home/droid/.config/gcloud/properties]
    This configuration file is deprecated and will not be read in a future
    gcloud release.  gcloud will automatically migrate your current settings to the
    new configuration format the next time you set a property by running:
      $ gcloud config set PROPERTY VALUE
    You may also run:
      $ gcloud init
    to create a new configuration and walk you through initializing some basic
    settings.  You can find more information on named configurations by running:
      $ gcloud topic configurations
    
    
    
    Your current Cloud SDK version is: 97.0.0
    Installing components from version: 97.0.0
    
    ┌────────────────────────────────────────────────────┐
    │        These components will be installed.         │
    ├──────────────────────────────┬─────────┬───────────┤
    │             Name             │ Version │    Size   │
    ├──────────────────────────────┼─────────┼───────────┤
    │ gcloud app Java Extensions   │  1.9.32 │ 101.4 MiB │
    │ gcloud app Python Extensions │  1.9.32 │   7.2 MiB │
    └──────────────────────────────┴─────────┴───────────┘
    
    For the latest full release notes, please visit:
      https://cloud.google.com/sdk/release_notes
    
    Do you want to continue (Y/n)?  Y

    ╔════════════════════════════════════════════════════════════╗
    ╠═ Creating update staging area                             ═╣
    ╠════════════════════════════════════════════════════════════╣
    ╠═ Installing: gcloud app Java Extensions                   ═╣
    ╠════════════════════════════════════════════════════════════╣
    ╠═ Installing: gcloud app Python Extensions                 ═╣
    ╠════════════════════════════════════════════════════════════╣
    ╠═ Creating backup and activating new installation          ═╣
    ╚════════════════════════════════════════════════════════════╝
    
    Performing post processing steps...done.
    
    Update done!
    
> onGit/GAE$ gcloud components list

    Loading legacy configuration file: [/home/droid/.config/gcloud/properties]
    This configuration file is deprecated and will not be read in a future
    gcloud release.  gcloud will automatically migrate your current settings to the
    new configuration format the next time you set a property by running:
      $ gcloud config set PROPERTY VALUE
    You may also run:
      $ gcloud init
    to create a new configuration and walk you through initializing some basic
    settings.  You can find more information on named configurations by running:
      $ gcloud topic configurations
    
    
    Your current Cloud SDK version is: 97.0.0
    The latest available version is: 97.0.0
    
    ┌─────────────────────────────────────────────────────────────────────────────────┐
    │                                    Components                                   │
    ├───────────────┬─────────────────────────────────┬───────────────────┬───────────┤
    │     Status    │               Name              │         ID        │    Size   │
    ├───────────────┼─────────────────────────────────┼───────────────────┼───────────┤
    │ Not Installed │ Cloud Datastore Emulator        │ gcd-emulator      │  38.1 MiB │
    │ Not Installed │ Cloud Pub/Sub Emulator          │ pubsub-emulator   │  10.1 MiB │
    │ Not Installed │ gcloud Alpha Commands           │ alpha             │   < 1 MiB │
    │ Not Installed │ gcloud Beta Commands            │ beta              │   < 1 MiB │
    │ Not Installed │ kubectl                         │ kubectl           │           │
    │ Installed     │ BigQuery Command Line Tool      │ bq                │   < 1 MiB │
    │ Installed     │ Cloud SDK Core Libraries        │ core              │   3.7 MiB │
    │ Installed     │ Cloud Storage Command Line Tool │ gsutil            │   2.6 MiB │
    │ Installed     │ Default set of gcloud commands  │ gcloud            │           │
    │ Installed     │ gcloud app Java Extensions      │ app-engine-java   │ 101.4 MiB │
    │ Installed     │ gcloud app Python Extensions    │ app-engine-python │   7.2 MiB │
    └───────────────┴─────────────────────────────────┴───────────────────┴───────────┘
    
     
    To install or remove components at your current SDK version [97.0.0], run:
      $ gcloud components install COMPONENT_ID
      $ gcloud components remove COMPONENT_ID
    
    To update your SDK installation to the latest version [97.0.0], run:
      $ gcloud components update

<i> The following did not work </i>

> droid@droidserver:~/onGit/GAE$ dev_appserver --help

    dev_appserver: command not found
    
> onGit/GAE$ app-engine-java --help
    
    app-engine-java: command not found

### Download the App Engine SDK

https://cloud.google.com/appengine/downloads#Google_App_Engine_SDK_for_Java



