# cordapp-example



Membership Attestation

flow start CreateNetwork

flow start RequestMembership authorisedParty: NetworkOperator, networkId: 40692ba7-a254-4ca6-a5d3-ef68afc5341c

flow start QueryAllMembers

Insurance: 
flow start ActiveMembers membershipId: f465100e-afe5-4839-9cb3-606df13702d8

CarePro:
flow start ActiveMembers membershipId: 856cd065-25a3-4f4c-9eb4-d876279d4575


flow start CreateNetworkSubGroup networkId: 40692ba7-a254-4ca6-a5d3-ef68afc5341c, groupName: APAC_Insurance_Alliance, groupParticipants: [9cc6abf7-e20e-4404-be8c-4bcec1a668e0, f465100e-afe5-4839-9cb3-606df13702d8, 856cd065-25a3-4f4c-9eb4-d876279d4575]


flow start AssignBNIdentity firmType: InsuranceFirm, membershipId: f465100e-afe5-4839-9cb3-606df13702d8, bnIdentity: APACIN76CZX

flow start AssignPolicyIssuerRole membershipId: f465100e-afe5-4839-9cb3-606df13702d8, networkId: 40692ba7-a254-4ca6-a5d3-ef68afc5341c

flow start AssignBNIdentity firmType: CareProvider, membershipId: 856cd065-25a3-4f4c-9eb4-d876279d4575, bnIdentity: APACCP44OJS

flow start IssuePolicy networkId: 40692ba7-a254-4ca6-a5d3-ef68afc5341c, careProvider: CarePro, insuree: PeterLi

run vaultQuery contractStateType: net.corda.samples.businessmembership.states.InsuranceState



//flow start AssignBNIdentity firmType: CareProvider, membershipId: 9cc6abf7-e20e-4404-be8c-4bcec1a668e0, bnIdentity: APACCP44OJS
