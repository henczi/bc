# Self-assessment questions
Created for the purpose of preparing for the midterm of the 2018 Spring “Blockchain Technologies and Applications” course.

    Last modified: 2018.05.04.

Contacts: Imre Kocsis (ikocsis@mit.bme.hu) and Attila Klenik (klenik@mit.bme.hu)


    Note: you are not expected to read through all the “suggested readings and sources”. Rather, exactly as the wording says: we suggest that you read these if you want to gain a deeper understanding of the subjects and to use the references as a source for working out the self-assessment questions.

Working out these questions for yourself makes it highly likely that you will be able to pass the mid-term with ease. (Note: the mid-term itself will be naturally in Hungarian; a single choice test format is to be expected.)

## Blockchain-based Distributed Ledger Technology

Suggested readings and sources
1. NISTIR 8202 Draft: https://csrc.nist.gov/CSRC/media/Publications/nistir/8202/draft/documents/nistir8202-draft.pdf 
2. Microsoft Project Bletchley overview (up to the “Code Name “Bletchley” Overview”): https://github.com/Azure/azure-blockchain-projects/blob/master/bletchley/bletchley-whitepaper.md
3. World Economic Forum: Realizing the Potential of Blockchain, June 2017. http://www3.weforum.org/docs/WEF_Realizing_Potential_Blockchain.pdf

Self-assessment questions
1. What is a distributed ledger?

    > A főkönyv nem egy helyen, egy 3. fél által közpintilag van kezelve, hanem minden résztvevőnél van egy példány, amik ~szinkronban vannak egymással

2. From the point of view of trust, what is the key distinguishing property of Distributed Ledger Technologies (DLT) compared to systems relying on a central party?

    > Nem kell 3. félben megbízni

3. What is the relationship between DLTs and Blockchain technologies?

    > Blockchain technológiák DLT-t használnak

4. Provide a high level description of the Blockchain data structure! 

    > ?

5. What are the common properties of Blockchain-based DLT technologies?

    > Elosztott főkönyv - nem módosítható tranzakciós napló, csoportos konszenzus - megbízhatóság, aláírt tranzakciók

6. What are smart contracts and what is their purpose?

    > Programozható tranzakciós logika, a főköny állapotának változtatására

7. What are the three high-level, conceptual phases of transaction processing in a Blockchain-based DLT?

    > Felhasználói kérés -> konszenzus -> főkönyv frissítés

8. In what sense are Blockchain-based DLTs similar to classic database replication?

    > ?Konkurens hozzáférés?

9. What is the expected impact of DLT in the “4th industrial revolution”?

    > Kulcsfontosságú szerep - Megbízható tranzakció közvetlen 2 vagy több résztvevő közt


## Bitcoin

Suggested readings and sources

1. “Official” Bitcoin developer documentation: https://bitcoin.org/en/developer-documentation 
2. Wikipedia :)

Self-assessment questions

1. What are the main parts of a Bitcoin transaction? What is an unspent transaction output? (UTXO)?

    > Verzió | Bemenetek | Kimenetek | Záridő

    > A címzett által elkölthető (szabály) Satoshi mennyiség


2. Draw and describe the structure of the transaction graph encoded by the Bitcoin ledger!

    > 
    ```
    TX0: (In0) (Out1)   (Out1)
              / 40k          \ 50k
    TX1:    (In0) (Out0)  TX2:(In0) (Out0) (Out1)
                  / 30k            / 20k         \ 20k
    TX3:      (In0) (Out0)  TX4: (In0) (Out0)  TX5: (In0) (Out0)
                    [UTXO]                / 10k           / 10k
             -----------------------------               /  
            /                ----------------------------
    TX6:  (In0)           (In1)  (Out0)
                                 [UTXO]  
    ```


3. At the conceptual level - how does public key encryption work?

    > 
    1. Generálunk egy privát és egy hozzá tartozó publikus kulcsot
    1. A publikus kulcsot megosztjuk
    1. Az üzenet küldője a publikus kulcs segítségével kódolja az üzenetet
    1. Elküldi
    1. A privát kulcs segítségével dekódolható az üzenet


4. At the conceptual level - how do digital signatures work?

    > 
    1. Generálunk egy privát és egy hozzá tartozó publikus kulcsot
    1. A publikus kulcsot megosztjuk
    1. Az üzenetet aláírjuk a privát kulcs segítségével
    1. Elküldjük az üzenetet
    1. A publikus kulcs segítségével ellenőrizhető az aláírás 'valódisága' 


5. What is an “address” in Bitcoin?

    > A publikus kulcs hashe


6. Describe at a conceptual level that in the simplest Bitcoin transaction type - “paying” to a public key hash - how nodes validate the “right to spend” of the specified inputs.

    > 


7. Describe the steps (rough workflow) of Bob paying an amount of Satoshis to Alice for a product or service!

    > 


8. What do we refer to by saying that transactions in Bitcoin (and Ethereum) are only pseudonymous, but not anonymous?

    > Bár az összes tranzakció nyilvános, de azokhoz nem köthető egyértelműen személy vagy cég


9. What is a wallet?

    > Menedzseli a bitcoin "számlát". Letrehozza (megossza) megossza, elkölthető kimeneteket keres, Tranzakciót készít, aláír, megoszt


10. What is a transaction fee in Bitcoin? How does it influence the verification time of a transaction submitted to the Bitcoin newtwork?

    > A blokk létrehozója számára elkülönített összeg, hogy a tranzakció belekerüljön a blokkba. Nagyobb tranzakciós illeték esetén hamarabb bekerül a tranzakció egy blokkba, így hamarabb válik érvényessé az adott tranzakció


11. Why is it bad practice to “wire back” funds to an address used earlier?

    > Privát kulcs használata. +Több cím esetén kevésbé köthető egy személyhez vagy céghez.


12. What is preimage resistance in the context of cryptographic functions? Why is it generally important?

    > A függvény minden kimenetére igaz, hogy belátható időn belül nem lehet olyan bemenetet találni, amire a függvény ugyanazt a kimenetet adja.


13. What is preimage resistance in the context of cryptographic functions? Why is it generally important?

    > -||-


14. What is the strict avalanche criterion in the context of cryptographic functions?

    > A bemenet egyetlen bit változása esetén a kimenet minden bitje 50% valószínűséggel változik meg.


15. What is the cryptographic puzzle that nodes in a Bitcoin network race each other to solve?

    > Olyan 'Nonce' érték találása, amitől a block header hash kissebb lesz a 'Target' értéknél


16. What is the economic incentive for nodes to remain honest? Why does it work?

    > A nyertes (aki először talál megfelelő Nonce értéket), kap Bitcoint


17. What happens with blocks that are “found”/”closed”?

    > ?? Bekerül a blokkláncba


18. Why do we call this consensus approach Proof of Work? What does the existence of a “found” block “prove” (in the probabilistic sense)?

    > Rengeteg felesleges számítást végeznek a varsengés közben.


19. What is the block time goal in Bitcoin?

    > 1 blokk / 10 perc


20. Is the evolving chain of blocks in a Bitcoin P2P system strictly a chain? Why?

    > Nem. Közel egy időben többen is találhatnak megfelelő Nonce-t


21. Why do we say that transaction finality is probabilistic in Bitcoin? Why is it deterministic in Hyperledger?

    > Mindig a leghosszabb blokkláncot tekintjük érvényesnek. ??


22. Is “mining” Bitcoin with off the shelf PCs profitable? Why?

    > Nem. PC-nek kicsi a számítási teljesítménye.


23. What is double spending? How does Bitcoin avoid it?

    > Ugyanannak a pénznek a kétszeres elköltése. A coin újra elkültéséhez a kérdéses blokktól az 'aktuális' blokkig tartó láncnál hosszabb láncot kell létrehozni. Ez ~6 hosszú blokklánc (~1óra) felett közel lehetetlen.




## Ethereum

Suggested readings and sources
1. The White Paper: https://github.com/ethereum/wiki/wiki/White-Paper 
2. The Yellow Paper: https://ethereum.github.io/yellowpaper/paper.pdf 


Self-assessment questions

1. What is the single biggest innovation of Ethereum over Bitcoin?

    > Szkriptelés!! Minden jobb ha lehet szkriptelni...

    > Smart contract


2. Describe the account model of Ethereum!

    > Egyenleg fiókhoz, 

    > Külsőleg birtokolt fiók | Szerződéses fiók


3. Compare it to the account model of Bitcoin! (Trick question...)

    > Bitcoin account nincs


4. What is the block time in Ethereum?

    > 15mp


5. What is the EVM? Why don’t we develop directly for it?

    > Ethereum virtuális gép. Bytekód. Azért mert nem vagyunk mazochisták


6. How does the life cycle of an Ethereum smart contract look like?

    > Kód megírása -> fordítás EVM bytekódra -> feltöltés és futtatás a blokkláncon


7. What is the difference between “gas” and “ether”? What is their relationship?

    > Ether a pénz, Gas az belső cucc ...


8. Describe the smart contract execution workflow of Ethereum step by step!

    > ??


9. Describe how we can define custom “token” ledgers on top of the Ethereum ledger!

    > address - uint256 mapping


10. Does an Ethereum smart contract have to define a token? Why?

    > Nem? Beépített típus.


11. What is the ERC20 token standard? Why is it important?

    > Tokenek implementására szóló standard.
    Megmondja, hogy a tokenek a címek közt, hogyan kerülnek átvitelre.




## Permissioned and/or private/consortial Blockchains

Suggested readings and sources

1. NISTIR 8202 Draft: https://csrc.nist.gov/CSRC/media/Publications/nistir/8202/draft/documents/nistir8202-draft.pdf 

Self-assessment questions
1. What is the difference between permissioned and unpermissioned Blockchains?

    > Ki írhatja?

    > Permissioned: Csak meghatározott résztvevők írhatnak a főkönyvbe


2. What is the difference between public and consortial/private Blockchains?

    > Ki olvashatja?

    > public: bárki olvashatja a főkönyvet


3. Define key use cases for the 3 “most meaningful” combinations and argue about their rationale!

    > Public - Permissionless : Bitcoin, Ethereum

    > Public - Permissioned : Land titles, Medicial records

    > Private - Permisioned : Trading system


4. What combinations can be implemented using Ethereum? (Hint: Enterprise Ethereum Alliance, Quorum)

    > Public - permissioned / permissionless ??


5. What combinations can be implemented using Hyperledger Fabric? (hint: there’s no native cryptocurrency notion!)

    > ??


6. For consortial, permissioned Blockchains - why is it not important for the Blockchain technology to possess a native cryptocurrency?

    > úgyis ismerik egymást ... ??


7. What can be the main reasons for choosing a consortial, permissioned technology over a public, unpermissioned network for supply chain and asset tracking use cases?

    > Konkurrencia ne tudja nyomon követni..



## Hyperledger Fabric and Composer

Suggested readings and sources

1. The Hyperledger Fabric 1.1 documentation: https://hyperledger-fabric.readthedocs.io/en/release-1.1/ 
2. The architecture paper: https://arxiv.org/abs/1801.10228v1 


Self-assessment questions

1. What are “channels” in Hyperledger Fabric?

    > Biztosítják, hogy csak a résztvevők láthassák a tranzakciót


2. What are “chaincodes” in Hyperledger Fabric? What is their relationship with channels?

    > Okos szerződések (smart contract), egy-egy csatornára vannak telepítve


3. Describe the basic programming model of Hyperledger Fabric chaincodes! (the common properties across the supported languages)

    > Go, JavaScript (1.1-)

    >


4. Can we implement a UTXO-style cryptocurrency in Fabric with chaincodes?

    > Igen, https://github.com/hyperledger-archives/fabric/tree/master/examples/chaincode/go/utxo


5. And does it make sense to do so? :) Why?

    > Há'hogyne... Memáméne


6. Draw/describe the basic relationships of organizations, peers, ledgers and chaincodes in Hyperledger Fabric!

    > 


7. Is the system pseudonymous?

    > 


8. What does it mean that the system implements an “execute-order-validate” architecture? (I.e. describe the key steps of transaction processing and consensus)

    > 


9. Why is this better for the intended usage, than “Proof of Work” (mining)?

    > 



## Basic integration aspects

Suggested readings and sources

1. A pretty good description of oracles: https://hackernoon.com/oracles-help-smart-contracts-resolve-subjective-events-d81639d8291c
2. Composer documentation on integration: https://hyperledger.github.io/composer/latest/integrating/integrating-index 
3. The pitfalls of “calling out” from smart contracts: https://hyperledger.github.io/composer/latest/integrating/call-out.html 

Self-assessment questions

1. With some exceptions (e.g. Hyperledger Composer), smart contracts in Blockchain platforms don’t support “calling out” to external systems and services from a smart contract execution, as this can lead to consensus failures. Why?

    > külső hívás eredménye változhat (időzóna, tűzfal, autentikáció); rekurzió


2. Instead, we generally use so-called oracles. What are these? What trust considerations have to be made?

    > Kapcsolatot biztosít a valós világ és a blokklánc közt. 

