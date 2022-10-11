# Serialization
**Serialization** is a mechanism of converting the state of an object into a byte stream. 

**Deserialization** is the reverse process where the byte stream is used to recreate the actual Java object in memory. This mechanism is used to persist the object.

Serialization is used to save/persist the state of a Java object. It can be used to send Java objects across the network. This is only possible for those that implements the *java.io.Serializable* interface.

**transient** is a keyword in Java. If you define any data member as transient it will NOT be serialized. So if you don’t want to save value of a non-static data member then make it transient.

Remember:
- Only non-static data members are saved via Serialization process.
- Static data members and transient data members are NOT saved via Serialization process.
- Constructor of object is never called when an object is deserialized.
- Associated objects must be implementing *java.io.Serializable* interface.