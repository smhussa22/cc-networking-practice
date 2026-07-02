# DNS

## Core Concepts

- What is DNS?
- Walk through opening google.com.
- Recursive vs iterative resolution.
- Why is DNS hierarchical?

## DNS Header

- QR
- Opcode
- AA
- TC
- RD
- RA
- RCODE

## Sections

- Question
- Answer
- Authority
- Additional

## Records

- A
- AAAA
- MX
- TXT
- SRV
- PTR
- CNAME

## Caching

- TTL
- Why cache?
- Negative caching

## Compression

- Compression pointers
- Why pointers exist
- Pointer loops
- Compression attacks

## Advanced

- EDNS
- DNSSEC
- UDP vs TCP
- Truncated responses
- Why port 53?

## Coding

- DNS parser
- DNS serializer
- Compression pointer decoder
- Recursive resolver

## Edge Cases

- Malformed packets
- Infinite pointer loop
- Compression attack