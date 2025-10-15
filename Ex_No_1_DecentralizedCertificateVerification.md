### Experiment 1: Decentralized Certificate Verification
## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
return certificates[certHash];
}
}
```
# Expected Output:
```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```
### Output:

# TRUE VALUE:
<img width="1842" height="821" alt="Screenshot 2025-10-15 152648" src="https://github.com/user-attachments/assets/9ae5dce8-41e7-44f7-a3c3-e4a56d4f83fd" />

<img width="346" height="685" alt="Screenshot 2025-10-15 152803" src="https://github.com/user-attachments/assets/03c8ed33-8068-47cc-9409-e8ab95d717fa" />



# FALSE VALUE:

<img width="1842" height="821" alt="Screenshot 2025-10-15 152648" src="https://github.com/user-attachments/assets/9ae5dce8-41e7-44f7-a3c3-e4a56d4f83fd" />

<img width="353" height="679" alt="Screenshot 2025-10-15 152734" src="https://github.com/user-attachments/assets/31eb3f09-cf1c-4a58-8754-83ae3268d03f" />


# Result:
thus the smart contract is deployed and verification of academic certificates on Ethereum is done successfully.
