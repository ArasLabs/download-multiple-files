# Download Multiple Files

In an out-of-the-box instance of Aras Innovator, it is only possible to download one file at a time. Due to the implementation of the download method, it is also not possible to use concurrent executions of the **aras.downloadFile** method to download more than one file at a time.

This project contains two sample methods that demonstrate a technique to allow your users to download multiple files at once. Rather than downloading all of the files individually, these methods create a .zip file on the server and upload that .zip to the Aras Vault, so that all of the files can be downloaded at once in one .zip file.

## History

Release | Notes
--------|--------
[v1.1.0](https://github.com/ArasLabs/download-multiple-files/releases/tag/v1.1.0) | Confirmed support for Aras 11.0 SP15.
[v1.0.0](https://github.com/ArasLabs/download-multiple-files/releases/tag/v1) | Initial Release

#### Supported Aras Versions

Project | Aras
--------|------
[v1.1.0](https://github.com/ArasLabs/download-multiple-files/releases/tag/v1.1.0) | 11.0 SP15, 11.0 SP14, 11.0 SP12
[v1.0.0](https://github.com/ArasLabs/download-multiple-files/releases/tag/v1) | 11.0 SP12

_While this project was built and tested using 11.0 SP12, it should work with any service pack of 11.0._

_Note: If you are using a version of Aras Innovator older than 11.0 SP7, please check out the [Collective Downloading](https://github.com/ArasLabs/collective-downloading) project for an alternative way of downloading multiple files._

## Installation

#### Important!
**Always back up your code tree and database before applying an import package or code tree patch!**

### Pre-requisites

1. Aras Innovator installed
2. Any version of the Product Engineering solution installed (11.0R1+)
3. Aras Package Import tool
4. **Download Multiple Files** import package

### Install Steps

#### Codetree Installation

**NOTE: This code tree patch makes modifications to the Innovator\Server\method-config.xml file. If you have previously made modifications to this file, you will want to manually copy over the changes rather than following the steps below.**

1. Backup your code tree and store the archive in a safe place.
2. Copy the `Innovator` folder in your local `..\download-multiple-files\` folder
3. Paste this to the root of your install directory
* By default, you root directory is `C:\Program Files\Aras\Innovator\`

#### Database Installation
1. Backup your database and store the BAK file in a safe place.
2. Open up the Aras Package Import tool.
3. Enter your login credentials and click **Login**
  * _Note: You must login as root for the package import to succeed!_
4. Enter the package name in the TargetRelease field.
  * Optional: Enter a description in the Description field.
5. Enter the path to your local `..\DownloadMultipleFiles\Import\imports.mf` file in the Manifest File field.
6. Select **aras.labs.downloadMultipleFiles** in the Available for Import field.
7. Select Type = **Merge** and Mode = **Thorough Mode**.
8. Click **Import** in the top left corner.
9. Close the Aras Package Import tool.

You are now ready to try out Download Selected Files actions

### Usage
1. Login as admin
2. Open the Document File ItemType
3. Navigate to the Actions relationship tab
4. Add the **Download Selected Files (Relationships Grid)** action
5. Save this ItemType
6. Open a document, select multiple files, and run the new **Download Selected Files** action

_NOTE: You can follow these steps for any RelationshipType that has File as it's related ItemType.
You can also follow these steps to add the **Download Selected Files (Main Grid)** action to the File ItemType itself if your administrators do any work with Files directly._


## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request

## Credits

Created by Christopher Gillis for Aras Labs. @cgillis-aras

## License

Published to Github under the MIT license. See the [LICENSE file](./LICENSE.md) for license rights and limitations.
