# BER / ASN.1

## Overview

Basic Encoding Rules (BER) is a binary encoding standard defined as part of ASN.1 (Abstract Syntax Notation One). It encodes data structures using a Tag-Length-Value (TLV) format and is the encoding used by SNMP, X.509 certificates, LDAP, and many other protocols.

## Conceptual Questions

- What is ASN.1?
- What is BER?
- What is the relationship between ASN.1 and BER?
- What does TLV stand for?
- Explain the Tag-Length-Value format.
- What is a tag in BER?
- What is the length field in BER?
- What is the value field in BER?
- What is the difference between primitive and constructed encodings?
- What are the four tag classes in BER?
- What is the Universal class?
- What is the Application class?
- What is the Context-specific class?
- What is the Private class?
- What Universal tag numbers are assigned to common types?
- What is an INTEGER in BER?
- What is an OCTET STRING in BER?
- What is a NULL in BER?
- What is an OBJECT IDENTIFIER (OID)?
- What is a SEQUENCE in BER?
- What is a SEQUENCE OF in BER?
- What is the difference between SEQUENCE and SEQUENCE OF?
- What is a SET in BER?
- What is short-form length encoding?
- What is long-form length encoding?
- When must long-form length encoding be used?
- What is indefinite-length encoding?
- How is the end-of-contents (EOC) octet used?
- What is DER (Distinguished Encoding Rules)?
- What is the difference between BER and DER?
- Why is DER used for certificates instead of BER?
- What is CER (Canonical Encoding Rules)?
- Why does SNMP use BER?
- What other protocols use BER encoding?
- What is a varbind in SNMP and how is it BER-encoded?

## Deep Dive Questions

- Describe the structure of a BER tag byte.
- What do bits 8 and 7 of the tag byte represent?
- What does bit 6 of the tag byte represent (primitive vs constructed)?
- What do bits 5–1 of the tag byte represent?
- How are high-tag-number forms encoded when the tag number exceeds 30?
- Describe short-form length encoding in detail.
- Describe long-form length encoding in detail: what does the first byte signal, and how do the subsequent bytes encode the length?
- How is a BER INTEGER encoded?
- How are negative integers encoded in BER (two's complement)?
- Why is the minimum number of octets required for INTEGER encoding?
- How is an OID encoded in BER?
- Why does OID encoding use base-128 (base-128 variable-length encoding)?
- How are the first two OID components encoded into a single value?
- How is an OCTET STRING encoded?
- How is NULL encoded?
- How is a SEQUENCE encoded?
- How are nested SEQUENCEs decoded recursively?
- How does a BER decoder determine where a nested structure ends?
- What is the significance of the constructed bit for SEQUENCE?
- How is context-specific tagging used in SNMP PDUs?
- How does IMPLICIT tagging differ from EXPLICIT tagging?
- Describe the complete binary layout of a BER-encoded SNMP GET request.

## Why Questions

- Why use TLV instead of a fixed-width binary format?
- Why use BER instead of JSON or XML for SNMP?
- Why does OID encoding use base-128 encoding?
- Why are the first two OID arcs combined into one encoded value?
- Why must INTEGER encodings use the minimum number of octets?
- Why is DER preferred over BER for cryptographic purposes?
- Why does indefinite-length encoding exist and when would you use it?
- Why is BER self-describing?
- Why is BER considered verbose compared to formats like Protobuf?

## Coding Questions

- Implement a BER encoder for INTEGER.
- Implement a BER decoder for INTEGER.
- Implement a BER encoder for OCTET STRING.
- Implement a BER decoder for OCTET STRING.
- Implement a BER encoder for NULL.
- Implement a BER encoder for OID.
- Implement a BER decoder for OID.
- Implement a BER encoder for SEQUENCE.
- Implement a BER decoder for SEQUENCE.
- Implement a recursive BER parser that handles arbitrary nesting.
- Implement short-form length encoding.
- Implement long-form length encoding.
- Implement a BER decoder that returns a parse tree.
- Implement an encoder for a complete SNMP GET PDU using BER.
- Implement a decoder for a complete SNMP GET response using BER.
- Encode a negative integer in BER.
- Decode a negative integer from BER.
- Encode the OID `1.3.6.1.2.1.1.1.0` in BER.
- Decode a raw BER buffer and print the tag, length, and value for each TLV.

## Edge Cases

- What happens when the length field overflows (length value exceeds 4 bytes)?
- What happens when a nested SEQUENCE claims a length longer than the remaining buffer?
- What happens when a tag byte indicates a high-tag-number form but the encoding is malformed?
- How do you handle indefinite-length encoding in a streaming parser?
- What happens when an INTEGER encoding has unnecessary leading zero or 0xFF bytes?
- What happens when an OID has a leading byte that is not a valid first-arc encoding?
- How do you detect and reject malformed nesting?
- What happens when a context-specific tag is encountered but no schema is available to interpret it?
- How do you handle unknown tag classes?
- What happens when the value length is zero for a type that must have content?

## Debugging Scenarios

- A BER decoder silently returns wrong values for large integers. What is the likely cause?
- An OID decoder returns garbage for OIDs with arcs greater than 127. Why?
- A SEQUENCE decoder stops early and misses nested elements. What is wrong?
- A BER encoder produces output that another implementation rejects. What common violations should you check?
- An SNMP GET response parses successfully in one library but fails in another. How do you diagnose encoding differences?
- Long-form length encoding is accepted by one parser but rejected as malformed by another. What is the likely DER vs BER distinction at play?

## System Design Questions

- Design a generic BER encoder/decoder library in C or C++.
- Design an ASN.1 schema compiler that generates BER encode/decode code.
- Design a protocol fuzzer that generates malformed BER inputs.

## Related Topics

- [SNMP](../snmp/questions.md)
- [DNS](../dns/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
