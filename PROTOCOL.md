Buffers are built using RakNet serialization.

## Protocol structure

Default byte order is Big Endian

#### Headers

**message type (unsigned byte)**

* 0x80
* 0x88

**payload length**

2 bytes (unsigned short) on 0x80

4 bytes (unsigned int) on 0x88

#### Payload

Payload structure is a map of 5 elements and is my own representation of the protocol.
It has been reversed with static analysis. It works just perfect but I'm unsure about the logic.

1) **attr_prefix**: unsigned byte
2) **attr_key_len**: unsigned byte
3) **attr_key**: string
4) **attr_type**: signed byte
5) **attr_value**: *

#### Attr prefix

* 0 = standard attr
* 4 = unsigned int
* 8 = string
* 17 = attr_array
* 18 = attr_array

## Standard attr

#### Attr key

Unsigned byte **attr_key_length** + string **attr_key**

#### Attr type

**Known attr types**

* 0 = empty
* 1 = byte
* 2 = byte (bool?)
* 3 = short
* 4 = int
* 5 = long
* 8 = string
* 17 = short + attr_array
* 18 = short + attr_array

#### Attrs array

Each element that has been read as an attr_array, recursively read other attrs using the same logic
