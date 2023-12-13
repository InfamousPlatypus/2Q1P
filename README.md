# 2Q1P
An Open source photonic quantum gateset.
As of now, more than half of the required parts have been made and tested. I belive this is a sufficant proof of concept to continue on with certanty as there are only two missing parts. These parts are going to be more expensive and with better tolerances than the rest due to the lack of consumer grade versions.
# Todo list
Get the hand drawings into CAD. This is going to take some time.
Confirm errors.
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
Rotations of the photon can be achieved by placing mirrors at angles to each other. For example, two mirrors at 180 degrees from each other and 45 degrees to the direction of the beam will produce a 90 degree polarization change, thus making an X gate.
A path defined single qbit gate can be simply made by partially transparent mirrors. The amount of silvering will correspond to a certain operation. Thus a 50% mirror sending the beam to a directing mirror will provide a hadamard gate. Unfortunately this will induce a 90 degree rotation into the polarization defined qbit if the state is changed. This can be remedied by two mirrors to produce another 90 degree rotation.

# Path to polarization Cnot
Implementing “Cnot q[0], q[1];” relies on the observation that a path defined photonic qubit will not encounter a polarization change in a path it does not travel. Thus the Cnot can be implemented by simply placing a polarization X gate on the |1> path of a path defined qubit.
# Polarization to path Cnot
Implementing “Cnot q[1], q[0];” is done by creating a X gate on the path based qbit, however the mirrors to do that are polarized so that only the photons with |1> polarization are reflected.
# Measurement
Unfortunately measurement will require four measurements. Each path will be split into polarizations using polarized mirrors. A photon detector will be added to the end of each of these. Each will measure a separate state, |00>,|01>,|10> or |11>
A successful computation can be determined by having a single, and only a single photon detector activated. If more or no detectors are activated, then this indicates a fault in the photon source, leakage in the apparatus or stray photons infecting the experiment.
