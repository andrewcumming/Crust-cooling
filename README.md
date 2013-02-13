This code follows the thermal evolution of a neutron star crust. It is designed to model observations of accreting neutron stars in quiescence and the decline of magnetar outbursts.

To compile, `make` should compile the cooling code `crustcool`. You will need to create the directory `o` for the object files, as well as directories `gon_out` and `out` which are used for output during the runs.

The file `init.dat` sets up the run. The parameters are

	Tt		temperature at the top of the crust during accretion
	Tc		core temperature
	Qimp	impurity parameter
	Qinner 	(optional) a different impurity parameter for the inner crust
	Qrho	the density at which the Q changes from Qimp to Qinner (default 1e12)

	Edep	energy deposited
	Einner	(optional) a different value of energy deposited for the inner crust
	rhot	lowest density to be heated
	rhob	highest density to be heated
	mass	neutron star mass in solar masses
	radius	neutron star radius in km

	Bfield  magnetic field strength in the crust in G

	mdot	accretion rate in Eddington units (1.0 == 8.8e4 g/cm^2/s)

	precalc	force a precalc (1) or instead load in previously saved precalc (0)
	ngrid	number of grid points
	SFgap	neutron superfluid gap (0=normal neutrons)
	kncrit	neutrons are normal for kn<kncrit (to use this set SFgap=4)
	sph		whether to inlcude SF phonons (0=no 1=yes)

	piecewise	if =1 then the initial temperature is specified in a piecewise
				format in the lines beginning with > in this file
	timetorun	time to run in days
	neutrinos	include neutrino cooling (1=yes 0=no)
	instant		heat "instantly" if =1, otherwise model the outburst

	toutburst	accretion outburst duration in years
	accreted	crust composition  1=accreted crust   2=equilibrium crust
	
You can include comments (`#`) in the `init.dat` file, blank lines are ignored, and lines beginning with `>` are (optionally) to specify the piecewise initial temperature profile.

If you give an argument, e.g.

	crustcool source

then the code will look for the file `init/init.dat.source` instead of `init.dat`. This is useful to keep different setups for modelling different data sets for example.
