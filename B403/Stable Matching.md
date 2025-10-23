#### Notation

| Applicant | 1st    | 2nd    | 3rd |
| --------- | ------ | ------ | --- |
| Amy       | Apple  | Google | IBM |
| Ted       | Google | Apple  | IBM |
| Adam      | Google | Apple  | IBM |

| Company | 1st | 2nd | 3rd  |
| ------- | --- | --- | ---- |
| Google  | Amy | Ted | Adam |
| Apple   | Ted | Amy | Adam |
| IBM     | Amy | Ted | Adam |

**Pairing**: (\[Applicant\], \[Company\])
**Conditions** (partially):
Google: Amy > Ted, Ted > Adam
Amy: Apple > Google, Google > IBM

**Stable Match** - (Amy, Google), (Ted, Apple), (Adam, IBM) OR (Ted, Google), (Amy, Apple), (Adam, IBM)

Possibly no stable match
Possibly multiple stable matches
Applicants don't know other applicants or companies preferences, same for companies

#### Gale-Sharpley Algorithm
- Each company makes an offer to the top of their list
- Applicants say yes to any offer better than what they already have (accepting if no offer)
```psuedo
while (some company is free and hasn't proposed to every applicant) {  
	Choose such a company: C  
	A is the top applicant to whom C has not yet proposed.  
	Company C proposes to A  
	if (A is free)  
		(C,A) are matched.  
	else if (A prefers C to current offer C’)  
		(C,A) are matched
		C’ is set to be free.  
	else  
		A rejects C.  
}  
Return S as the set of matches
```
**Worst Case** - $O(n^2)$

All companies and applicants get matched
- Proof by contradiction
- Assume all companies and applicants didn't get a match
- $\exists$ C and A free
	- C didn't offer A
		- Contradiction because of the while loop in the algorithm, in worst case C will send an offer to every applicant
	- OR C offered A but A rejected
		- Contradiction because A rejects C if A already has a better offer, so A must not be free

The matching is stable
**Proof** (by contradiction) - 
Assume there exists not a stable match in the output:
	$\exists$ (C, A) and (C', A)
		A prefers C' over C
		C' prefers A over A'
	Two possibilities
		1.) C' didn't offer A
			Contradiction, because C' moves from top of its list and A>A' for C'
		 2.) C' made an offer to A but A rejected it
			 Contradiction, because A moves to the company at the top of its list and C'>C for A, so it must have a better offer from some company C''

**Valid Match** - (C, A) is a valid match for if there is a stable matching in which (C, A) are matched

Those who propose (companies) get the best valid match, those who accept/reject get the worst stable match
	GS algorithm outputs a match in which every company gets the best valid applicant (verses the applicants get the best valid company).




