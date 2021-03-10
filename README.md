# Membership Attestation

//Step1: Create the network 
flow start CreateNetwork

//Step2: 2 non-member makes the request to join the network. 
flow start RequestMembership authorisedParty: NetworkOperator, networkId: ba5891eb-c015-41e5-8dac-8a78ba29d413

//Step3: go back to the admin node, and query all the membership requests. 
flow start QueryAllMembers


//Step4: Admin active membership, two times, ONLY the membership activation 
Insurance: 
flow start ActiveMembers membershipId: 0011cb64-2541-4e05-8f06-cfc8fa9d7a3e

CarePro:
flow start ActiveMembers membershipId: b0ee7814-79df-452a-b852-c9f647261bc5

//Step5: Admin create subgroup and add group members. 
flow start CreateNetworkSubGroup networkId: ba5891eb-c015-41e5-8dac-8a78ba29d413, groupName: APAC_Insurance_Alliance, groupParticipants: [e472e1f3-7420-4974-bab5-ac74c7c8ed45, 0011cb64-2541-4e05-8f06-cfc8fa9d7a3e, b0ee7814-79df-452a-b852-c9f647261bc5]

//Step6: Admin assign business identity to a member. 
flow start AssignBNIdentity firmType: InsuranceFirm, membershipId: 0011cb64-2541-4e05-8f06-cfc8fa9d7a3e, bnIdentity: APACIN76CZX

//Step7: Admin assign business identity related ROLE to the member.
flow start AssignPolicyIssuerRole membershipId: 0011cb64-2541-4e05-8f06-cfc8fa9d7a3e, networkId: ba5891eb-c015-41e5-8dac-8a78ba29d413

//Step8: Admin assign business identity to the second member 
flow start AssignBNIdentity firmType: CareProvider, membershipId: b0ee7814-79df-452a-b852-c9f647261bc5, bnIdentity: APACCP44OJS

//Query to check
run vaultQuery contractStateType: net.corda.core.contracts.ContractState

-------------------Network setup is done, and business flow begins--------------------------

/* Step9: The insurance Company will issue a policy to insuree. 
 * The flow initiator (the insurance company) has to be a member of the Business network, has to have a insuranceIdentity, and has to have issuer Role, and has to have issuance permission. 
 */
flow start IssuePolicy networkId: ba5891eb-c015-41e5-8dac-8a78ba29d413, careProvider: CarePro, insuree: PeterLi
   
//Step10: Query the state in the CarePro node. 
run vaultQuery contractStateType: net.corda.samples.businessmembership.states.InsuranceState



//flow start AssignBNIdentity firmType: CareProvider, membershipId: 9cc6abf7-e20e-4404-be8c-4bcec1a668e0, bnIdentity: APACCP44OJS
