### Avoid Arbitrary External Calls

Arbitrary external calls are low-level calls where both the destination address and the call data—encompassing the function to be invoked and its parameters—can be manipulated. To bolster the security of your code, establish a firm rule against permitting completely arbitrary calls within your contracts. 

This precaution helps mitigate vulnerabilities, such as the risk of privilege escalation if the calling contract has special permissions in other contracts or the potential for draining tokens stored in the contract or misusing token approvals.