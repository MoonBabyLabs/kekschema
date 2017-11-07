# kek JSON Schema

Reliably share, collaborate, manage and access your structured content in any environment or application workflow. Kek removes the headache from managing content through a distributed network of machines. The kek schema contains a blockchain revision history and consistent structure applicable to most structured content pieces. Following the schema and open format will provide developers and content creators the ability to reliably manage content across multiple locations simultaneously because every revision can say who wrote a given update at a certain location and specified time.

## Getting Started

### Development Packages & Application Plugins

You will want to reference the kek open format and use an development package to create your kek files. They could be created by hand but you will more than likely be creating your kek files through a content management system or document editor like word or some other tool. You can go to http://kekdocs.com/developer/packages to see a list of available packages that are available for applications and languages. You are encouraged to create a package if you don't see it for your desired application or language. It is straightforward to create in any language that can speak directly to the underlying machine as you will need to get the mac address and the current process id.

## kek Properties

### Required properties
#### id
The id is a 12 byte (20 char) global unique identifier consisting of 4 bytes representing seconds since Unix epoch, 3 byte machine identifier, 2 byte process id, and 3 byte counter starting with a random value. Go Reference sample: https://github.com/rs/xid

#### revisions
A blockchain instance of every revision that this kek content piece has had saving the new data, the user who edited, the location where it was saved and the unix timestamp when it was updated. You can also include a 3rd party signature string along with comments as well.

[See Revision Block Properties for revisions details](#revision-block-properties)

### Optional properties

#### title


#### description

#### current_state

## Revision Block Properties



## License
This project is licensed under the MIT License - see the LICENSE file for details