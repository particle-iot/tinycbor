# Concise Binary Object Representation (CBOR) Library

This library has been ported from Hiroshi Tokita's [tinycbor](https://github.com/soburi/tinycbor) fork of Intel's [TinyCBOR](https://intel.github.io/tinycbor/current/) library for use on the Particle platforms.

The TinyCBOR library is a small CBOR encoder and decoder library, optimized for very fast operation with very small footprint. The main encoder and decoder functions do not allocate memory.

## Further Reading
For general documentation on the Intel TinyCBOR library see [TinyCBOR Latest API](https://intel.github.io/tinycbor/current/).

---

## Example

See [examples](examples/) for more examples.

```cpp
uint8_t encode_buffer[1024] = {};

// Initialize TinyCBOR library.
TinyCBOR.init();

// Assign buffer to encoder.
TinyCBOR.Encoder.init(encode_buffer, sizeof(encode_buffer));

// Encode a map object with two key/value pairs
TinyCBOR.Encoder.create_map(2);
  TinyCBOR.Encoder.encode_text_stringz("key1");
  TinyCBOR.Encoder.encode_float(3.14); // Value for "key1"
  TinyCBOR.Encoder.encode_text_stringz("key2");
  TinyCBOR.Encoder.encode_int(42); // Value for "key2"
TinyCBOR.Encoder.close_container();

// The encoded buffer is now ready for use
auto encoded_size = TinyCBOR.Encoder.get_buffer_size();

Serial.printlnf("Encoded data size = %u", encoded_size);

```

---

### LICENSE

Unless stated elsewhere, file headers or otherwise, all files herein are licensed under The MIT License (MIT). For more information, please read the LICENSE file.

If you have questions about software licensing, please contact Particle [support](https://support.particle.io/).

---
### LICENSE FAQ

**This firmware is released under The MIT License (MIT), what does that mean for you?**

 * You may use this commercially to build applications for your devices!  You **DO NOT** need to distribute your object files or the source code of your application under The MIT License.  Your source can be released under a non-MIT license.  Your source code belongs to you when you build an application using this library.

**When am I required to share my code?**

 * You are **NOT required** to share your application firmware binaries, source, or object files when linking against libraries or System Firmware licensed under LGPL.

**Why?**

 * This license allows businesses to confidently build firmware and make devices without risk to their intellectual property, while at the same time helping the community benefit from non-proprietary contributions to the shared reference firmware.

**Questions / Concerns?**

 * Particle intends for this firmware to be commercially useful and safe for our community of makers and enterprises.  Please [Contact Us](https://support.particle.io/) if you have any questions or concerns, or if you require special licensing.

_(Note!  This FAQ isn't meant to be legal advice, if you're unsure, please consult an attorney)_

---

### CONTRIBUTE

Want to contribute to this library project? Follow [this link](CONTRIBUTING.md) to find out how.

---

### CONNECT

Having problems or have awesome suggestions? Connect with us [here.](https://community.particle.io/)

---

### Revision History

#### 0.5.3
* Initial file commit
