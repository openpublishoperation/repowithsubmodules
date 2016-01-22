# Provisioning the GIT repos - (VSC task)

After all the following steps are completed, Open Publishing will automatically build and publish the updated content from a monitored docset to MSDN, TechNet, or VS.com web sites. You should have got the information listed in the [repo creation page](../partnerdocs/repo-creation.md) from the partner.

You can get a sample of the files to be added to the repo from this site.
 
## 1. Making the repo an Open Publishing repo


### 1.1. Adding the Publishing Service Configuration File: .openpublishing.publish.config.json
This file needs to be under the repository. This file tells Open Publishing how to build and publish the content found in the GIT repo. **This file needs to be placed in the live branch in order for the repo to be provisioned.**

- **build_entry_point**: Indicate how to run the build. User can either use the build tool OP provides or use their own tools to build the content. Leave it blank to use Open Publishing tool. 
- **git_repository_url_open_to_public_contributors** - This URL would need to be defined if the above value is set to true. It can be the same Git repo if the whole project is public. It can also be a separated public repo for external contribution while keeing the internal repo private. Example: "git_repository_url_open_to_public_contributors": "https://github.com/Microsoft/Virtualization-Documentation",
- **docsets_to_publish**: A collection of docsets that need to be published.
	- **docset_name** - Provide the name of the docset. This docset need to provisioned on portal at first, otherwise the content under the docset won't be published.
		- For different docsets the names should be different.
		- For docsets that are just different in locale or version, the name should be same. Otherwise, the fallback logic won't work.
	- **build_output_subfolder** - The relative output sub folder of the build tool. Content that has been built will be put there. Only content under that folder will be published. So this value depends on the build tools.  
	- **version** - Version of current content. Start from 0.
	- **locale** - Just leave it as 'en-us' as localized repos are created/configured using the [.localization-config file](../partnerdocs/repo-creation.md). 
	- **open_to_public_contributors** - The value can be true or false. Here true means your content would accept community contribution, so there would be a button showing on the rendered page which directs external users to a repository to submit their pull requests.
		- Set to true if you want your customers to contribute to the content.
		- Set to false if you do not want your customers to contribute to the content.
	- **type_mapping** - As we can only build conceptual content right now, it should be "Conceptual": "Content".
- **notification_subscribers** - Provide the email array of some ones who want to receive the notification. Separate each of the users or distribution lists by a comma. Example: "notification_subscribers": ["mayast@microsoft.com", "yanz@microsoft.com", "fenxu@microsoft.com"]
- **branches_to_filter** - You can exclude any branches from building. Recommended if people are new to Open Publishing to protect the "live" branch, so content does not get published by mistake.	 


### 1.2. Provisioning on the portal
- Once you have the publish configuration file under the repository and make sure you also have the live branch contains that configuration file, go to [portal](https://op-portal-prod.azurewebsites.net) to have the repo monitored.
- Open Publishing portal will only parse the configuration file under live branch when doing provision.
- "Base Path": It can be configured via the portal. This field would be the common base path for all the topics in this docset, and is eventually part of the rendering URL.

## 2. Adding the Build Tools Configuration
The Open Publishing service provides the entry point for how to build the content. Users can either use their own build tools or use the build tool provided by Open Publishing service.

Open Publishing currently has two build tools. The first build tool only has a simple function to build Markdown content. The is a powerful build tool called DocasCode (link will follow). In addition to Markdown it can build documentation from specific language source code.   

### 2.1 Assign the build tools provided by Open Publishing

#### 2.1.1 Simple Build Tool for Markdown
Two files need to be added under the repository folder **Tools/Nuget**. They are [Nuget.Config](https://github.com/Microsoft/openpublishing-docs/blob/master/Tools/NuGet/Nuget.Config) and [nuget.exe](https://github.com/Microsoft/openpublishing-docs/blob/master/Tools/NuGet/nuget.exe).

The following global build configuration files need to be added at the root of the repository.

- **.openpublishing.build.mdproj**: The build target of msbuild. User can also inject custom steps using msbuild language or just copy it from this repo to use that.
- **[packages.config](../partnerdocs/repo-config.md#packages-config)**: Indicates the version of build tool. Tool with different versions will have different capabilities. By default, the latest version will always be used. However, if you user like to use a previous version (they might not need all the functionality that is available and might make your build slower), then they can specify the version here. The engineering team will maintain a list of all the packages available and main features for each.

The following files should be also added to each docset:

  - **docfx.json**
  - **[TOC.md](../partnerdocs/repo-config.md#TOC-md)**

2.1.2 **DocasCode**
	- Coming Soon~

### 2.2. How to use the external tool to build the markdown content
	- Coming Soon~

