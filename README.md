# AI-driven biometric privacy using modified cycle GANs

## Motivation
In case of security break and fingerprint leakage, user’s original fingerprints should not be compromised

Even if the architecture and the key associated with a user is leaked, one should not be able to trace back the real fingerprint of any user

## Abstract
We use Cycle GANs to convert RF to FF of a user. The fingerprint type of RF and FF are different.

Cycle GANs preserve the inter user and intra user scores of fingerprint matching. They also result in FFs look real, with similar distortions and orientations as RFs. 
We use the latent space of RFs to change the output image of Cycle GANs. A unique key is associated with each RF. The latent space of RF is modified using the key to prepare unique FF.

The key serves two purpose. 
1. To provide a layer of protection in case of data leak. Even if the architecture is invertible, one will need the key associated with the user to trace back to his RF.  
2. To associate multiple FFs with the same RF. One single RF can be changed to multiple FF using different keys. The user can be given different keys as per the requirement.

Heat map is used to crop the FF. Cropping is required to remove noise outside the fingerprint, and to improve the difference score between user’s RF and FF. The center part of fingerprint impression which helps in fingerprint classification is used for subsequent steps.

During conversion, a random key is selected. The latent space of RF and key is input to the ResNet which changes the input latent space to the required FF type.

The ration in which to add the latent space of RF and key is optimized using linear regression.

The final output image has been tested using frequency spectrum for fake image detection. 

Neural nets are used for the architecture, invertibility is not possible. RF of the user is thus safe.  

## Results
Intra user- Results show that intra user scores of a user are preserved

Inter user- Results show that inter user scores of users are preserved

Frequency spectrum- The fake fingerprints are not distinguishable from real fingerprint using frequency graph. Both RF and FF give same frequency spectrum.

DET Graph- The results are shown graphically using DET graph. We can decide on the threshold using this graph.

![Result](results/fp.png)
