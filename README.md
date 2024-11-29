# ModbusADU
> [!WARNING]
> This README is a work-in-progress and may contain incomplete information or errors, however, the library itself is functional.

This is a library for managing Modbus RTU and TCP application data units (ADUs).
It is intended to be used with other libraries, but it can be used on its own.

---

Creating an instance of `ModbusADU` creates a structure with essentially the following form:
| Field                  | Length        | Description                                      |
| :--------------------- | :-----------: | :----------------------------------------------- |
| Transaction Identifier | 2 Bytes       | Identification of a Modbus request               |
| Protocol Identifier    | 2 Bytes       | 0 = Modbus protocol                              |
| Length                 | 2 Bytes       | Number of following bytes, excluding error check |
| Unit Itentifier        | 1 Byte        | Identification of a remote slave/server device   |
| Function Code          | 1 Byte        | Function of message: read, write, other          |
| Data                   | 1 - 252 Bytes | Contents depend on function code                 |
| Error Check            | 2 Bytes       | Cyclic redundancy check (CRC) code               |

---

This structure can be accessed as any of 4 byte-type arrays:
| Array | First Field            |
| :---- | :--------------------- |
| rtu   | Unit Identifier        |
| tcp   | Transaction Identifier |
| pdu   | Function Code          |
| data  | Data                   |

---

It can also be accessesd using the following methods:

- setTransactionId()
- setProtocolId()
- setLength()
- setUnitId();
- setFunctionCode();
- setDataRegister();

