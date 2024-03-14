# 2Q1P
An Open source photonic quantum gateset.
As of now, more than half of the required parts have been made and tested. I belive this is a sufficant proof of concept to continue on with certanty as there are only two missing parts. These parts are going to be more expensive and with better tolerances than the rest due to the lack of consumer grade versions.
# Todo list
Find proper waveplates and beam joiners to complete.
# Questions to explore later
Can we create an effective single photon source?
  IF so:
    Can we get parts that switch between presets fast enough to create a time-bin qubit?
    Need to learn to use photomultiplier tubes.
# Standards
To standardize across the paper the following values will be used. For path defined qubits, the top path will be |0> and the bottom path will be |1>. Polarization defined qubits have the horizontal polarization as |0> and vertical as |1>. Unless otherwise specified, q[0] is a path defined qubit and q[1] is polarization.
A note on rotations about the bloch sphere
For the purposes of this computer, a photon polarization is equivalent to its mirror, as the polarisers we are working with do not discriminate.
Single Qbit gates
All single qbit gates can be implemented in their normal manner. It must be noted that path defining gates must preserve polarization and polarization defining gates must occur on both paths.
Rotations of the photon can be achieved with birefrigent meterials, half and quarter wave plates seem to be the best options.
![Polarization RX](Utilities\Img\Pol RX.PNG)
A path defined single qbit gate will be difficult with the exception of an X gate, which can be made by four mirrors.
![Path X](Utilities\Img\Path X.PNG)
 The rest will need to have the qubits swap, leading to a large amount of error that will need mitigated. 
![Circut for a path RX](Utilities\Img\Path RX Construction.PNG)

# Path to polarization Cnot
Implementing “Cnot q[0], q[1];” relies on the observation that a path defined photonic qubit will not encounter a polarization change in a path it does not travel. Thus the Cnot can be implemented by simply placing a polarization X gate on the |1> path of a path defined qubit.
![Path to polarization Cnot](Utilities\Img\Pol CX.PNG)
# Polarization to path Cnot
Implementing “Cnot q[1], q[0];” is done by creating a X gate on the path based qbit, however the mirrors to do that are polarized so that only the photons with |1> polarization are reflected.
![Polarization to path Cnot](Utilities\Img\Path CX.PNG)
# Measurement
Unfortunately measurement will require four measurements. Each path will be split into polarizations using polarized mirrors. A photon detector will be added to the end of each of these. Each will measure a separate state, |00>,|01>,|10> or |11>
A successful computation can be determined by having a single, and only a single photon detector activated. If more or no detectors are activated, then this indicates a fault in the photon source, leakage in the apparatus or stray photons infecting the experiment.
As a lower cost option this design can be made made with more readily available parts and most should be within the capabilities of a highschool science class. The light source is any laser and the reader is a set of photoresistors at each output.
This design works by the assumption that although we cannot measure individual photons, they will all interact individually with the apparatus. Thus the percentages of photons that hit each individual photoresistor will be the same as the percentages that hit the photomultipliers.

