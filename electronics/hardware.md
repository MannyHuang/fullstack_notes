# hardware

## storage
- SRAM (Static random access memory)
	- no refreshing cycle
	- data and address bus directly accessible
	- fundamental storage elements: registers (occupy more - ea than caps)
	- need dc power to retain memory
- SDRAM (Synchronous Dynamic Access memory)
	- needs frequent refreshing
	- performance depends on access time and clock cycle - ordination
	- fundamental storage elements: caps
	- high power consumption due to refreshing








======================================================================================
ECE231 Introduction to Electronics
======================================================================================
1.Amplifiers:
	1.Circuit Models for Amplifiers
	2.Frequency Response of Amplifiers
	3.STC ccts
	4.Bode Plots
	5.Ideal Op-amp
	6.Inverting Configurations
	7.Non-inverting Configurations
	8.Integrators and Differentiators
	9.DC Imeprfections
	10.Effect of Finite Open-Loop Gain annd Bandwidth On CCT performance
	11.Large Signal Operation of Op-amp
	12.Difference and Instrumentation Amplifier
2.Diodes:
	1.The ideal diode
	2.Simple Diode CCTs
	3.Terminal characteristic of Junction Diodes
	4.Diode Models:
		1.Exponential
		2.Contant-voltage-drop
		3.ideal
	5.small-signal diode model:
		1.derivation and application
	6.Rectifier CCTS
		1.half-wave
		2.full-wave
		3.bridge
		4.peak
		5.precision half-wave
	7.Limiting and Clamping CCTS
	8.Introduction to semiconductor physics
		1.monolithic circuit: 
			1.circuit fabricated in a single silicon crystal
			2.this name can be used for both single transistor or integrated circuit (multiple transistors)
		2.significant property of semiconductor:
			1.conductivity can be varied by doping (the introduction of impurity atoms)
				1.objective: increase the concentration of free electrons or holes, with no change in crystal property
					1.increase n(electron concentration): dope with valence 5 (phosporus, the electron donar)  => n-type
					2.increase p(hole concentration): dope with valence3 (boron, the electron acceptor)	=> p-type
				2.Result:
					1.n-type: more electrons than holes (n no more has temperature dependence)
					2.p-type: more holes than electrons (p no more has temperature dependence)
					3.silicon object: neutral, due to bound charge of impurity atoms
			2.two kinds of semiconductor:
				1.single-element semiconductors (silicon,group 4 in periodic table)
				2.compound semicondcutors (gallum-arsenide, group3+5 or group2+6)
					1.useful for ccts involve light(LEDs)
			3.silicon:
				1.4 valence electrons => share one with each of the 4 neighbours =>4 covalent bonds => regular lattice structure
				2.at absolute zero => covalent bonds intact => insulator
				3.at high temp => covalent bonds breaks => electron-hole pairs increases => increase in conductivity (the process is called thermal generation)
				4.recombination
					1.the reverse process to thermal generation
					2.n(concentrations of electrons)=p(concentration of holes), at equilibrium
				5.band gap energy (Eg)
					1.threshold enery to break covalent bond
					2.(1.12 eV) for silicon
		3.charge carriers:
			1.electrons
			2.holes
		4.mechanism for current flow:
			1.carrier drift
				1.drift velocity = mobility * Electric Field
				2.electon mobility > hole mobility (in silicon)		
			2.carrier diffusion
				1.pre-conditions: the semiconductor is non-uniform => carriers diffuse from high concentration to low concentration
				2.magnitude of current at any point is propotional to the slope of concentration profile (concentration gradient)
				3.Einstein relationship: Dn/Un = Dp/Up = thermal voltage (Dn is diffusion contant, Un is mobility)
		5.semiconductor structure:
			1.pn junction
				1.pn junction is essentially a diode
				2.basic element of BJT
				3.Important to FET
			2.pn junction with Open-Circuit Terminals (Equilibrium)
				1.pn junction is formed by creating regions of different doping in a single silicon crystal
				2.P is the Anode; N is the Cathode (these will be terminals of they are used as diode)
					1.The diffusion Current Id
						1.p side has higher concentration of holes => holes diffuse from p-side to n-side
						2.the same thing happens for n-side, but in reverse direction
						3.Id is same as  p-side direction
					2.The Drift Current Is
						1.formed by minority carriers swept accross the depletion region by E-field
						2.Strong dependence on temperature
						3.no dependence on barrier voltage
					3.The Depletion Region
						1.n-material close to the junction: delepleted of free electrons=> positively charged
						2.P-material close to the junction: delepleted of holes => negatively charged
						3.voltage barrier: Vo formed by the E-field forms a barrier to Id
					4.In equalibrium (no external source)
						1.Id=Is
						2. if Id>Is => the depletion region will widen , Vo will increase => Id decreases to form equilibrium
						3. if Id<Is => the depletion region will narrow, Vo will decrease => Id increases to form equilirbium
					5.The Junction Built-in Voltage
						1.this is essentially Vo
						2.0.6 V - 0.9 V for silicon
						3.conservation of energy (metal junction at the terminals)
					6.Width of charge stored in the Depletion Region
						1.depletion extends to the more lightly doped region
			3.The pn Junction with an Applied Voltage
				1.Properties with source
					1.p-side more positive => forward-bias voltage
					2.n-side more positive => reverse-bias voltage
					3.properties vastly different for different directions
				2.qualitative description
					1.Equilibrium
					2.Forward-biased
						1.Vo decreases
						2.I=Id-Is
						3.depletion region will narrow
					3.Reversed-biased
						1.Vo increases
						2.current is small and equal to Is
						3.depletion will widen
				3.The I_V Relationship of the junction
					1.to be understood
3.MOSFET Transistor:
	1.MOSFET Transistor
		1.Three-terminal devices
		2.Areas of applications:
			1.signal amplification
			2.digital logic
			3.memory
		3.Basic principle
			1.use the voltage between two terminals to control the current flowing in the third (can be use to realize a controlled source)
		4.Two types of three-terminal semiconductor devices:
			1.MOSFET
			2.BJT
		5.Importance: The most widely used electronic devices
		6.properties:
			1.small
			2.require little power
			3.can be used to build analog functions without resistors
	2.Device structure and physical Operation
		1.Device Structure
			1.A n-channel enhancement-type MOSFET
				1.p-type substrate (single-crystal silicon wafer)
					1.function: provides physical support
				2.two heavily dope p-region
				3.thin layer of SiO2 (insulator) between the source and drain
				4.metal on the the oxide layer
					1.function: form gate electrode (modern tech uses silicon gate)
				5.four terminals:
					1.gate terminal(G)
					2.soure terminal(S)
					3.drain terminal(D)
					4.body terminal(B)
				6.another name: IGFET
				7.operation: 
					1.always revere-biased (normal operation)
					2.drain always positive relative to the source
					3.can be cut-off by connecting the body terminal to the source
					4.direction of current: from D to S
					5.source and drain are physically the same (though different in opperation)
		2.Operation with zero gate voltage
			1.two back-to-back diodes exist
			2.no current flow even if Vds is applied	
		3.Creating a channel for current flow	
			1.Vg is applied => n-region created under the gate => conducting channel formed
			2.threshold voltage: the voltage of VGS at which suffcient number of electrons accumulate at channel to form conducting channel
			3.capacitor formed between the gate and the channel (oxide capacitance)=> E-field of the cap controls the amount of charge in the channel
										=> determines conductivity => determines the current if Vds is applied
				(the origin of the name, field-effect)
			4.if Vds=0, then voltage at every point along the channel is zero; voltage across the oxide is uniform and equal to Vgs
			5.Vov = Vgs - Vt
				1.larger the Vov, deeper the channel

		4. Applying a small Vds
			1.channel length is a characterization of fabrication technology (smaller the better)
			2.MOSFET behaves as a linear resistance rds, current is controlled by Vgs
		5.Operation as Vds is Increased
			1.the channel will be tapered
			2.propotional to Vov at the source (steepest)
			3.propotional to Vov - Vds at the drain (shallowest)
		6.Operation for  Vds >= Vov
			1.channel pinch-off if Vds=Vov
		7.The p-channel Mosfet
			1.The Structure is similar to NMOS
			2.substrate: n-type
			3.source and drain: p-type
			4.complementary to NMOS
			5.Vgs is negative
		8.CMOS
	2.I_V characteristics: 
		1.Two types of characteristics:
			1.static characteristics: dc or low frequency analysis
			2.dynamic characteristics: high frequency and high switching speed
		2.characteristics symbols
			1.arrowheads indicate current direction (it also indicates the type of the transistor), it's placed at the source terminal
			2.NMOS: current from drain to source
			3.PMOS: current from source to drain
			4.the drain is always positive relative to the source in an n-FET
		3.The Id-Vds characteristics
			1.conditions of usage:
				1.switch: the cutoff region, the triode region
				2.amplifier: the saturation region
			2.regions of operation:
				1.N-type:
					1.triode:Vgs>Vds+Vt; Vds<Vov
					2.saturation: Vd>VG-Vt; Vds>=Vov					
		4.The Id-Vgs characteristics
			1.For amplifiers, MOSFET work in saturation region
			2.MOSFET operates as contant-current source, the current is determined by Vgs
		5.Finite Output Resistance in Saturation
			1.channel length modulation
			2.the ouput resistance is inversely propotional to the current
			3.the modulation effect can be expressed as (1+r)
	3.MOSFET CCTs at DC
		1.assume no channel length modulation
	4.Applying MOSFET in Amplifier Design
		1.volage amplifier
			1.voltage-controlled current source be a tranconductance amplifier (input: voltage, output:current)
			2.add a resistor at the output current
		2.The voltage transfer characteristic (VTC)
			1.simply a plot of Vds vs Vgs 
	5.Small-signal Operation and Models
		1.linear amplification can be obtained by biasing the MOSFET to work in saturation region and keep the input signal small
			1.biased by Vgs(dc)
			2.input signal: Vgs (Vgs will be superimposed on Vgs)
			3.output signal: the drain Vds
		2.The DC bias point
			1.voltage at the drain, Vds=Vdd-Rd*Id
			2.ensure saturation-region operation: Vds>Vov
		3.The signal current in the Drain Terminal
			1.total drain current = dc current + signal current
		4.The voltage gain
			1.Av=Vds/Vgs=-gm*RD
		5.Separating the DC anaysis and the Signal Analysis
			1.signal analysis can be performed without dc quantities
		6.Small-signal Equivalent-circuit models
			1.input:Vgs(signal)
			2.output:gm*Vgs
			3.input resistance: infinite
			4.output resistance: infinite
			5.replace transistor with cct model,short dc voltage source, open dc current source
			6.shortcoming:it assumes the drain current in saturation is independent of the drain voltage
		7.The Transconductance Gm
		8.The T equivalent-circuit model
		9.summary
*		10.Analyzing MOSFET Amplifier CCTs
	12.Basic MOSFET Amplifiers
		1.Three Configurations
		2.characterizing amplifiers
		3.Biasing Transistor Amplifier CCT
4.Bipolar Junction Transistors:
	1.Structure and physical Operation
	2.BJT I_V characteristics
	3.BJT CCT at DC
	4.Small-signal Operation and Models
	5.Analyzing BJT Amplifier CCTS
5. Comparision of MOSFET and BJT
6.Body Effect

======================================================================================
ECE221 ELECTROMAGNETICS
======================================================================================
1.Electrostatic Source-Field Relationships:
	1.Maxwell's Equation (Static Electric Fields)
		1.Electrostatics:
			1.(divergence) of D-field = volume charge density
			2.(curl) of an E-field = 0;       =>(irrotational)
		2.Magnetostatics:
			1.(divergence) of B-field = 0;       =>(sourceless)
			2.(curl) of an H-field = J,current density per area
	2.Columb's Law
		1.Superposition of Electric Fields
			1.current density
				1.velocity * volume charge density
				2.vector
				3.current is the integral of current density over the cross-section 
			2.Electric flux density = permitivity * Electric intensity
			3.E-field (single point) = (constant) *charge / distance^2
		2.Multiple Point Charge Distributions
			1.summation of E-field(single point)
		3.Electric Fields due to Continuous Charge Distributions
				1.uniformly charged square plates
				2.infinite sheet of charge
				3.charged semicircle
				4.finite line charge
	3.Divergence(math)
	4.Point form of Gauss's Law
		1.(divergence) of D-field= volume charge density
		2.(surface integral)of the D-field 
				= total charge enclosed in an Gaussian surface
	5.E-field from Gauss's law
				1.sphererical charge distribution
				2.coaxial Cable

	6. Gradient, Curl, Stoke's Theorem(math)
	7. Electric potential
		1.equvalent to voltage
		2.differential voltage = (negative) electric field* differential length
	8. Electric potential difference
		1.potential difference form P1 to P2 =
			line integral of (negative) electric field* differential length
	9. Physical meaning of Electric Potential
		1.Propery of e-field: irrotational (means contour integral is 0)
	10.Potential of Point charges
		1.V-field (single point) = (constant) *charge / distance
	11.Equotential surfaces
	12.Potential of continuous charge distributions
	13.E-field from potential
		1.(divergence) of V-field = Electric Field
	14.Electric dipole
		1.equal magnititude opposite charge pairs
		2.dipole moment= charge magnitude * distance vector (from negative charge to positive charge)	
		3.voltage= (constant) * dipole moment / distance^2
	15.Poisson's and Laplace Equation
		1.Poisson's equation: laplacian of a V-field= (negative) charge density/ permitivity
		2.Laplace equation: if no charge is in the medium (0 density) => laplacian of a V-field= 0

2.Electric Properties of Material:
	1.Conductors
		1.electron mobility: effective distance particles can be accelerated  
		2.drift velocity = (negative)electron mobility *  E-field
		3.current density = charge density * drift velocity 
		4.current density = electrons' current density + hole's current density
		5.Result of 3 and 4:current density = conductance * E-field
			1.J=0 in perfect Dielectric
			2.E=0 in perfect Conductor 
	2.Joule's Law
		1.Power = (Volume Integral) of E vector field (dot) current density vector field
	3.Dielectric
	4.Polarization
		1.modification of D-field: D-field = permitivity * E-field + P(electric polarization field)
		2.Properties:
			1.Magnitude:  Linear:if P is directly propotional to D-field
			2.Direction:
				1.isotropic:E and P have the same direction
				2.anistopic:E and P have different directions
			3.homogeneous: if (permitivity, drift velocity and conductance are constant)
	5.Electric susceptibility
		1.suppose linear: P= permitivity * susceptibility * E-field
		2.physical meaning: susceptibility(Xe) is the ratio to the original D-field
	6.Relative Permitivity
		1.Er=1+Xe
	7.Dielectreic Strength
		2.Physical meaning: beyond the strength(Eds), the electrons will detach form molecules and form conduction current
			1.sparking will occur
			2.material structure damaged
	8.Electric Boudary Conditions: 
		1.tangential field equals between two boundary: Et1=Et2
		2.normal vecotr: always defined as away from the medium
		3.(D1n-D2n)=charge density at the boundary
		4.Boundary Conditions:
			1.Conductor-dielectric:D1= (normal)*charge density`
				1.density positive: E-field point away from conductor
				3.density negative: E-field point toward form conductor
			2.Conductor-Conductor:
				1.current density * (perimitivity1/conductance1-permitivity2/conductance2)=charge density
3.Application of the Electricstatic Field:
	1.Capacitance
		1.capacitance= permitivity* (surface integral over surface of positive condutor) of E-field (from positive to negative)
				/(negative)* (line integral from negative to positive conductor) of E-field
		2.resistance between conductors= (negative)* (line integral from negative to positive conductor) of E-field
				/conductance* (surface integral over surface of positive condutor) of E-field (from positive to negative)
		3.RC relationship: R*C= permitivity /conductance
		4.Property:
			1.capacitance only depends two properties
				1.capacitor geometry
				2.permitivity of insulating material
			2.value independent of E-field's magnitude

	2.Parallel Plate Capacitance: capacitance = charge/voltage = charge/(E*d) = (permitivity*Area)/d
	3.Coaxial Line Capacitance: capacitance = (2pi*permitivity*length)/(Ln(b/a))
	4.Electric Potential Energy
		1.We=(1/2)*Capcitance*Voltage^2=(1/2)*permitivity*(E-field^2)*volume
		2.Electrostatic Energy Density: We/volume=(1/2)*Capcitance*Voltage^2=(1/2)*permitivity*(E-field^2)
		3.For any dielectric within an E-field: Electric Potential Energy= (Volume Integral) of (Electric Potential Energy)(1/2)*permitivity*(E-field^2)
		4.Force Vector= (negative)* (gradient) of We
			1.parrel plate capacitor: (1/2)*permitivity*A*(E-field^2)
		5.physical meaning: energy provided by the source is stored in the dielectric as electric potential energy
4.Design using electric field:
	1.Poisson's and Laplace's Equations
	2.Uniqueness Theorem 
	3.One-dimensional Boundary Value Problems (BVPs) in cartesian, cylindrical and sphereical coordinates.	
5.Magnetostatic Source-Field Relationship:
	1.similarities between E-field and M-field
		1.Electrostatics:
			1.(divergence) of D-field = volume charge density
			2.(curl) of an E-field = 0;       =>(irrotational)
		2.Magnetostatics:
			1.(divergence) of B-field = 0;       =>(sourceless)   //also called Gauss's law for magnetism
			2.(curl) of an H-field = J,current density per area
	2.Differences between E-field and M-field
		1.Direction of the Force:
			1.E-field: Force in the same direction as E-field
			2.B-field: Force perpendicular to the B-field
		2.Condition of the Force:
			1.E-field: any state
			2.B-field: only when charges are moving
		3.Energy:
			1.E-field: expends energy when moving 
			2.B-field: force does no work to displace particles
	3.Magnetic Field:
		1.Magnetic Force(point charge)= charge * charge's moving velocty * B-field
				1.Postive charge direction: right-hand-rule
				2.Negative charge direction: opposite to right hand rule
		2.Magnetic Force on a Current-carrying Conductor
				1.Magnetic Force= current * (contour integral) differantial displacement vector * magnetic field
				2.Contour integral: if uniform B-field, net B-force is 0 
				3.Line integral: Magnetic Force= current * length vector (cross) B-field vecotr
		3.Magnetic Torque on a Current-carrying Loop
				1.General Principle: Torque (T) = distance vector from axis to force (d) (cross ) Force vector
					1.Torque direction: right-hand-rule
				2.Torque = magnetic moment vector (cross) B-field vector
	4.Lorentz Force Law
		1.Lorentz Force: Electromagnetic Force= Electric Force + Magnetic Force
	5.Biot-Savart Law
		1.H-field= (I/4pi)* (line integral) differential displacement vector * distance vector(from legnth to field)/ (distance ^2)
		2.Magnetic Field due to Surface and Volume Current Distributions
			1.H-field= (I/4pi)* (surface integral) current density vector (cross) distance vector(from legnth to field)
					*differential surface/ (distance ^2)
			2.H-field= (I/4pi)* (volume integral) current density vector (cross) distance vector(from legnth to field)
					*differential volume/ (distance ^2)
	6.Ampere's Law
		1.Differential Form: (curl) of an H-field = J,current density per area
		2.Integral Form: (contour integral) of an H-field = I enclosed
		3.Physical meaning: line integral of H around a closed path equals the current traversing through the surface
		4.Restriction: require sysmetry
	7.Magnetic Vector Potential
		1.A is the vector magnetic potential
			1.vector E-field = (negative) divergence of scalar potential
			2.vector B-field = curl of the vector magnetic potential
		2.Vector Poisson's Law:
			1.(laplacian) of A =(negative)permeability * current density
		3.magnetci flux links a surface S = surface integral of the magnetic flux density
6.Magnetic Properties of Materials:
	1. Magnetism
		1.Magnetic Moment vector
			1.the result of interactions between (magnetic dipole moments) and (external magnetic field)
		2.Nature of Behavior:
			1.crystalline structure
				1.classifications:
					1.diamagnetic
					2.paramagnetic
					3.ferromagnetic	
	2.Magnetic permeability
		1.Magnetic Moments (M)
			1.Physical meaning
				1.vector sum of magnetic dipole moments of an atom in an unit volume
			2.Relationships:
				1.D-field= (permitivity) * E-field (free space) => D-field= (permitivity) * E-field + M-field(dielectric)
				2.B-field= (permeability) * H-field (free space) => B-field= (permeability) * H-field +M-field(dielectric)
				3.Magnetic Susceptibility:
					1.P-field= Xp * E-field
					2.M-field= Xm * H-field					
	3.Magnetic Boundary Condition
	4.Self-inducatance:
		1.physical meaning:the ratio of magnetic flux linkage to the current I flowing through the conducting structure
7.Application of the Magenetostatic Field:
	1.Magnetic Energy
		1.magenetic energy stored in an inductor=(1/2)*(volume integral)of (permeability*square of magnetic intensity)
	2.Magnetic ccts (Flux mmf Reluctance)
	3.Magnetic Forces on current-carrying conductors
	4.Magnetic Torque
	5.DC Motors and Generators
8.Time-Varying Field:
	1.EMF
		1.EMF=Vtr(transformer emf) +Vm(motional emf)
		2.transformer emf: time-varing B-field linking stationary loop
		3.motional emf: static B-field linking a moving loop with a time-varying surface area relative (relative to the normal component of B) 
	2.Lenz's Law
		1.the polarity of Vtr(the direction of I) is always in a direction that opposes the change of magnetic flux that produces I
		2.Bind serves to oppose the change in Bt, but not necessary Bt itself
	3.The ideal transformer
		1.Voltage linearly propotional
		2.current inversely propotional
		3.Vm=(contour integral)of (velocity * B-field)
	4.displacement current		

======================================================================================
ECE216 Signal and System
======================================================================================
1.Introduction
	1.signals
	2.energy
	3.power
	4.periodic signals
	5.even/odd signals
2.Transformation of Independent Variable
3.Complex variables
4.Exponential Signals
5.Sinusodial Signals
6.Unit Impulse and Unit Step Functions
7.Continuos-time and Discrete-time Systems
8.Basic System properties
	1.memory
	2.inverse
	3.causality
	4.stability
9.Linear Time-invarient systems
10.Discrete-time convolution
11.Continous-time convolution
12.Properties of Linear Time-invarient system
13.LTI systems described by Differential and Difference Equations
14.Response of LTI systems to Complex Exponentials
15.Continous-Time Fourier Series
16.Properties of Continous-time fourier series
17.parseval's theorem
18.Fourier Series and LTI systems
19.Filtering
	1.Ideal low-pass filter
	2.RC filter
20.Continous-time filters Described by differential equations
21.Continous-time Fourier Transform
22.Fourier Transform of Periodic signals
23.Propertities of Continous-time Fourier Transform
24.convolution property of Fourier Transform
25.Multiplication property of Fourier Transform
26.Linear Constant Coefficient Differential Equations
27.Sampling
28.Nyquist Theorem
29.Reconstruction and Interpolation
30.Aliasing
31.Discrete-time Fourier Transform
32.Properties of Discrete-Time Fourier Transform
33.Linear Constant-Coefficient Difference Equations
34.Amplitude Modulation and demodulation
35.Frequency-Division Multiplexing


======================================================================================
ECE316 Communication System
======================================================================================
1.Introduction
	1. Communication System
		1.components and functions:
			1.Source: originates a message (human voice)
			2.Input Transducer: Transform the data into baseband signal/message signal
			3.Transmitter: Modify the signal for efficiency (subcomponents: A/D Convertor, encoder, modulator)
			4.Channel: Medium that conveys the output over a distance (copper wires, opticla fiber)
			5.Receiver: 
				1.reverse modification of Transimmiter
				2.revmove distortion at channel					
			6.Output Transducer: Transform message signal back to the natural form
		2.Channel Distortions:
			1.Linear Distortion: pass through frequency-selective channel
			2.Non-linear Distortion; attenuation that varies with signal amplitude
			3.Both can be compensenated by channel-dependent predistortions (Transmitter)	
		3.Noise: 
			1.External Noise:
				1.interference from nearby channel
				2.faulty-switch connection
				3.natural noise from lightning
			2.Internal Noise:
				1.thermal motion of charged particles in conductor
				2.diffusion, recombination of charged carriers
			3.Challenges:
				1.signal strength decrease during transmission,but noise remain at the same level
				2.amplify the signal => will also amplify the noise
	2. Analog and Digital System
		1.Why Digital kick Analog's ass?
			1.Digital is immune to noise (needs only to distinguish 1 or 0 when binary)
			2.Digital system can implement distortionless Regenerative Repeaters
				1.The repeater for Analog is simply amp and filter (not regenerative)
		2.A/D Conversion
			1.Sampling:sampling at a rate of twice the highest frequncy in the frequency spectrum
			2.Quantization: partition the amplitude range in to L intervals, each amplitude lies in the midpoint of each signal

		3.Pulse-coded Modulation -A Digital Representation
			1.every possible commmunication can be carry on with  a minimum of two symbols
	3.Channel Effect, Signal-to-Noise Ratio, Capacity
		1.Signal Bandwidth and Power
			1.Signals rich in content and change quickly have higher bandwidth
			2.channel bandwidth must exceed the signal bandwidth to be sent
			3.the number of pulses per second that can be transmitted is directly propotional to its bandwidth B
			4.the quality of analog and digital system varies with the SNR
			5.in fact, the power of signal and Bandwidth of channel are exchangable (we can trade Ps for B, vice versa)
				1.telephone: low bandwidth, high power
				2.space vehicle: high bandwidth, low power
		2.Channel Capacity and Data Rate
			1.shannon's capacity equation
				1.C=B*logbase2(1+SNR) bit/s
				2.These two parameters(B and SNR) represent the ultimate limitation on the rate of communication
	4.Modulation and Detection
		1.The baseband signal is used to modulate a carrier (a sinusoid with high frequency)
			1.AM (Amplitude Modulation): carreir's amplitude varies propotionally to basedband signal m(t)
			2.FM (Frequency Modualtion): carreir's frequency varies propotionally to basedband signal m(t)
			3.PM (Phase Modulation): carreir's phase varies propotionally to basedband signal m(t)
		2.Why modulating?
			1.Ease of Radiation
				1.modulating high-frequency carrier leads to smaller wavelength, this allows smaller antenna
			2.Simultaneous Transmission of Multiple Signals-Multiplexing
				1.frequency division multiplexing (FDM): spread over the bandwith
				2.time division multiplexing (TDM): suitable for pulse trains (need narrower pulses)
			3.Demodulation
				1.Isolate signal using filter
				2.A peak dector then recovers the basedband signal
	5. Digital Source Coding and Error Correction Coding
		1.Randomness, Redundancy and Source Coding
			1.Source coding: remove redundancy to shorten usage of bandwidth
			2.Error Correction: introduce redundancy intellegently to reduce error
		2.Error Correction Coding
			1.Source codigng: a message of probability P is assigned a word length of log (1/P)
			2.Error-Correction Coding: add pulses,use even or odd number of ploarities to locate and correct errors
	6.Historical Review
2.Signals and Signal Space
	1.Size of Signal
	2.Classification of Signals
	3.Some useful signal Operation
	4.Unit Impulse Signal
	5.Signals Versus Vectors
	6.Corelation of Signals
	7.Orthogonal Signal Sets
	8.Trignometric Fourier Series
	9.Exponential Fourier Series
3.Analysis and Transmission Signal
	1.Aperiodic Signal Representation by fourier integral	
	2.Transforms of some useful function
	3.Some properties of the fourier Transform
	4.Signal Transmission through a linear system
	5.Ideal VS practical filter
	6.Signal Distortion over a channel
	7.Signal Energy and Energy Special Density
	8.Signal Power and Power Special Density
	9.Numercial Computation Fourier Transform
4.Amplitude Modulation and Demodulation
	1.Baseband versus Carrier Communications
	2.Double-Sideband Amplitude Modulation
	3.Amplitude Modulation(AM)
	4.Bandwidth-efficient Amplitude Modulation
	5.Amplitude Modulation
	6.Local Carrier synchronization
	7.Frequency Division Multiplexing
	8.Phase locked loop and Applications
	9.NTSC Television Broadcasting system
5.Angle Modulation and Demodualtion
	1.Nonlinear Modualtion
	2.Bandwidth of Angle-Modulated Waves
	3.Generating FM waves
	4.Demodulation of FM signals
	5.Effects of nonlinear distortion and interference
	6.Superheterodyne Analog AM/FM Receivers
	7.FM Broadcasting System
6.Sampling and Analog-Digital Conversion
	1.Sampling Theory
	2.Pulse Code Modulation (PCM)
7.Principles of Digital Data transmission
8.Fundamentals of Probability theory
	1.Deterministic: compelete certainty about the value of signal at any instant t (no uncertainy, cannot convey information)
	2.Random Processes: uncertain message signal and noise signal (uncertainty exists, can convey information)
		1.experiment:roll a die
		2.sample space: sigma (includes all outcomes,define an experiment)
			1.events:subset of sample space (Aodd = (sai1,sai3,sai5))
				1.complement of an event:an event that contains everything not contained by the event (AuppercaseC = (sai2,sai4,sai6))
				2.union: logic or
				3.intersection: logic and
					1.mutually exulusive if nothing in common
			2.sample points:sai,element of sample space (sai1,sai2,sai3,sai3,sai5,sai6)
		3.Rules:
			1.unions of mutually exlusive events adds up
			2.intersaction of two events under conditional setting multiplies
			3.Baye's Rule:
				1.(probability of A, given B) = (probability of A)*(Probability of B, Given A)/(Probability of B)
		4.Bernoulli Trails



====================================================================================
ECE334 CMOS VLSI Design (p20)
====================================================================================

1.P-N junction (diode)
	1.N-junction:group 5 dopant, electron carrier,Cathode
	2.P-junction:group 3 dopant, hole carrier,Anode
	3.Forward-biased if P high; Reversed-biased if N high
2.CMOS Logic
	1.CMOS network= Pull-up(PMOS) + Pull-down(NMOS)
	2.Invertor:UP:1 PMOS; DOWN:1 NMOS
	3.NAND:UP:k PMOS,pararllel; DOWN:k NMOS,series
	4.NOR:UP:k PMOS,series;`DOWN:k NMOS,parrallel
	5.Compound Gates:UP:seperate the function into different inverting elements using DeMorgan's Law
			Down:Invert the function, and seperate it into non-inverting elements
	6.Transmission Gate(Pass Gate):pararllel combination of NMOS(strong 0) and PMOS(strong 1) to form a near perfect switch
	7.Tristate invertor:UP:2 PMOS, one of PMOS connect to EN; DOWN:2 NMOS,one of NMOS connect to ENNOT, in series,
	8.Tristate bufffer:invertor+tristate invertor
	9.Multiplexer:
		1.Non-storing structure:pararellel transimission gates with, gates connected to Select.
		2.Re-storing structure:
			1.Compound gates: derived from logic expression
			2.tristate invertor:tristate invertor in series, select as EN, signal connect to PMOS
3.Sequential Circuits
	1.Sequential:output depends on current and previous inputs
	2.Combinational:output depends only on inputs
	3.D-Latch:Multiplexer(CLK as select signal) + invertorX2 (Qnot store previous value)
	4.D-flipflop:neg-sensitive latch + pos-sensitive latch (rising-edge)
	5.Good Practice to put two invertors at the two ends
*4.CMOS Fabrication and Layout (Chap1.5 Pg19)
5.Devices
	1.Formation of the inversion layer
		1.negative gate:holes attracted to the gate
		2.positive gate:depletion region
		3.positive gate exceeding Vth: depletion region and inversion layer (conducting channel)
	2.Three Modes of Operation
		1.(OFF) Vgs < Vth: Ids=0
		2.(ON and Linear Resistive) Vds < Vov, Ids increases linearly with Vds: Ids= Beta x (Vov- Vds/2)x Vds
		3.(ON and Current Source) Vds > Vov, Ids increasess linearly with (1/2)x(Vov)^2, independent of Vds: Ids=(Beta/2)*(Vgt)^2
	3.Parameters of the device
		1.Cox (perimivity/ thcikness of oxide), capacitance per unit area
		2.k prime (mobility x Cox), purely geometric and technology dependent
		3.Beta (mobility x Cox x W/L), purely technology dependent
	4.Two Figures of Merit:
		1.Ion (Vgs=Vds=Vdd): Ion= (Beta/2) * (Vdd-Vth)
		2.Ioff (Vgs=0,Vds =Vdd): Ioff= 0
*6.C-V Characteristics (chap2.3 pg68)
7.Non-ideal I-V Effects
	1.Mobility Degradation and Velocity Saturation
		1.Mobility Degradation: high lateral field (Vds/L),carrier velocity ceases to increase linearly with field strength, results in lower Ids 
		2.Velocity Saturation: high vertical field (Vgs/L),carriers scatter of the oxide interface, slowing their progress, results in lower Ids
	2.Channel-Length Modulation: high Vds, larger depletion region around the drain shortens the channel length, result is the saturation current Ids increases somewhat with Vds
	3.Threshold Voltage Effect
		1.Body Effect: increase in the potential between source and body increases Vth
		2.Drain-induced barrrier lowering: increase in the drain voltage lowers the Vth
		3.Short-Channel Effect: increase in channel length increasesi the threshold
	4.Leakage
		1.Subthreshold Conduction:leakage resulted in current flow when transistor is nominally off
		2.Gate leakage: leakage into the gate
		3.Junction leakage: leakage into substrate
	5.Temperature Effect: increase in temperature degrades MOS characteristic
		1.decrease carrier mobility, decreas Ids
		2.decrease Vth, create leakage current

