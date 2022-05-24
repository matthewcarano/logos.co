---
title: Main page
---
## Logos is the world’s first Network State

Logos is the world’s first Network State designed to enable new types of applications and institutions that uphold basic human rights.

Logos is a movement to create a self-sovereign crypto network: a decentralised technology stack that maximises the cost of surveillance and coercion 
while minimising the cost of exit, voice and loyalty. Logos has the ambitious mandate of building a complete decentralized technology stack for communication, storage and smart contracts that upholds our 
basic human rights and defends against tyranny.

Logos enables a parallel socioeconomic system, through its decentralized technology stack through the deployment new types of applications, public 
goods and social institutions atop of it. This aims to bringing greater freedom, transparency and stability to its members through voluntary participation.

Logos is the first decentralised autonomous organisation (DAO) dedicated to the construction of a user-owned, self-sovereign network that we can conduct our lives upon as we move deeper into the information age.
We believe that through advancements in cryptography, peer-to-peer networks and smart contracts, we can build a complete decentralized infrastructure stack for communication, storage and logic that upholds our basic human rights and defends against tyranny.

Logos’ network of infrastructure is permissionless, private, and censorship-resistant: designed to enable new types of applications, public goods and social institutions that bring greater freedom, transparency and stability to the modern world.
Logos is built and operated entirely by its community. It will exist as a parallel socioeconomic system, existing peacefully alongside our existing economies and institutions.

We invites technologists, creatives, and policy experts, along with anyone passionate about our mission to participate in its creation, and help govern its future. Because together, we’re creating a more trustworthy social fabric to lead us into a brighter future.

```
def init(self):
				self.evidence = (0, 0)
        self.confidence = (0, L)

def step(self):
        if self.color == ConsensusAgent.NONE:
            return

        vote_count = self.query_nodes()
        total_votes = sum(vote_count)
        if total_votes == 0:
            return
        self.evidence = (self.evidence[0] + vote_count[0], self.evidence[1] + total_votes)
        self.confidence = (self.confidence[0] + total_votes, self.confidence[1] + total_votes)

        conf = self.confidence[0] / self.confidence[1]
        e1 = vote_count[0] / total_votes
        e2 = self.evidence[0] / self.evidence[1]
        e = e1 * (1-conf) + e2 * conf
        alpha = self.evidence_alpha * (1-conf) + self.evidence_alpha2 * conf

        if e > alpha:
            self.color = ConsensusAgent.YES
        elif e < 1 - alpha:
            self.color = ConsensusAgent.NO
        else:
            self.k = min(int(self.k * 2), self.initial_k * 4)```