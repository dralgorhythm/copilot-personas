# Threat Modeling Instructions

## <concepts>
1.  **STRIDE**: A mnemonic for security threats (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege).
2.  **Trust Boundary**: A location where program data or execution changes its level of "trust" (e.g., between the internet and a web server).
3.  **Attack Surface**: The sum of the different points (the "attack vectors") where an unauthorized user (the "attacker") can try to enter data to or extract data from an environment.
4.  **Defense in Depth**: A layered security approach where multiple controls are used to protect the system.
5.  **Secure by Design**: Security is a primary concern during the design phase, not an afterthought.
6.  **Fail Secure**: When a system fails, it should default to a secure state (e.g., denying access).
</concepts>

## <best_practices>
1.  **Start Early**: Perform threat modeling during the design phase, before code is written.
2.  **Think Like an Attacker**: Try to identify how the system could be misused or exploited.
3.  **Focus on Assets**: Identify the most valuable assets (data, availability) and prioritize protecting them.
4.  **Keep it Simple**: Don't overcomplicate the model; focus on the most likely and impactful threats.
5.  **Iterate**: Update the threat model as the system evolves and new features are added.
</best_practices>
