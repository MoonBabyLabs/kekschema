# kek JSON Schema

Reliably share, collaborate, manage and access your structured content in any environment or application workflow. Kek removes the headache from managing content through a distributed network of machines. The kek schema contains a blockchain revision history and consistent structure that will apply to any content piece. Following the schema and open format will provide developers and content creators the ability to reliably manage content across multiple locations simultaneously because every revision block will know who wrote a given update at a certain location and specified time.

## Getting Started

### Development Packages & Application Plugins

You will want to reference the kek open format and use an development package to create your kek files. They could be created by hand but you will more than likely be creating your kek files through a content management system or document editor like word or some other tool. You can go to http://kekdocs.com/developer/packages (coming soon) to see a list of available packages that are available for applications and languages. You are encouraged to create a package if you don't see it for your desired application or language. It is straightforward to create in any language that can speak directly to the underlying machine as you will need to get the mac address and the current process id.

## kek Properties

### Required properties
#### id
(string) (length: 20 characters) The id is a 12 byte global unique identifier consisting of 4 bytes representing seconds since Unix epoch, 3 byte machine identifier, 2 byte process id, and 3 byte counter starting with a random value. Go Reference sample: https://github.com/rs/xid

#### revisions
A blockchain instance of every revision that this kek content piece has had saving the new data, the user who edited, the location where it was saved and the unix timestamp when it was updated. You can also include a 3rd party signature string along with comments as well.

[See Revision Block Properties for revisions details](#revision-block-properties)

### Optional properties

#### title
(string) (maxLength: 128 characters) The kek content item title.

#### description
(string) (maxLength: 256 characters) The description for the kek content item.


## Revision Block Properties
### Required properties
#### hash
(string) The hash is a 256 sha hash that consists of the index + the previous block's hash + the data property + an autoincrementing nonce value. The hash property is the most resource heavy item in the schema.

#### author
(object) The creator of the new block data. The object contains 2 strings: the author value and the source that provided the author value. There is also an additional optional comments property that may provide more details about the author property. Avoid putting any contact or personal info into the author object. Put the identifier behind an access wall. The author will thank you.
##### Author required properties
* *id* (string) A unique identifier associated to the author.
* *source* (string) The location where you can find this author association.

##### Author optional properties
* *comment* (string) optional field to add additional info about the author association.
* *phone* (string) optional field for a contact phone number.
* *email* (string) optional field for the author's contact email address.
* *location* (object) An object that may contain address, city, region_code, postal_code, and country_code properties.

#### mac_address
(string) The mac address where the content block is being written whether a server, pc, phone, tablet, etc.

#### index
(number) The current index for the block in the chain. Then index starts at 0 and will autoincrement for every block. It should always be the revision chain length - 1.

#### timestamp
(number) The unix timestamp when the block was added to the chain.
#### data
(object) The modified content for the content item. You should have an old object that has the items are being modified and a matching new object structure that contains the value changes. You can set removed content attributes to null or false.

### Optional properties
#### signature
(object) You can use a third party or in house signature in order to verify the authenticity of the revision block. This is good to have when you want to assure that an outside source can verify the contents of the block.
##### signature properties
* **source:** (string) A uri string to the location that generated the signature token. The source should provide the link to reach out to the token provider to verify accuracy.
* **token:** (string) The token provided by the originating source. Must be a string.

#### comment
(string) Any relevant comments to attribute to this block modification.

## License
This project is licensed under the MIT License - see the LICENSE file for details