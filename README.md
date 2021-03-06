# PPtoPPWWjets
This version is tested in CMSSW_10_6_12, for the workflow:
     - Starting from CMSSW 94X AOD (data+MC)
     - Rerunning the PPS proton reconstruction with the Ultra-Legacy + re-MiniAOD settings on data 
     - Running the proton direct simulation + reconstruction on signal MC

Step-by-step instructions to setup a working environment, including the proton direct simulation for signal MC

	cmsrel CMSSW_10_6_17
	cd CMSSW_10_6_17/src/
	cmsenv

	git cms-init
	git cms-addpkg IOMC/EventVertexGenerators RecoCTPPS Validation/CTPPS CalibPPS/ESProducers
	cd CalibPPS/ESProducers
	git clone https://github.com/cms-data/CalibPPS-ESProducers.git data
	cd ../..
	git clone https://github.com/jjhollar/PPtoPPWWjets.git
	cd PPtoPPWWjets/
	git checkout HTCondorCutsAndFixedStructure 
	cd ..
	git clone git@github.com:cms-jet/JetToolbox.git JMEAnalysis/JetToolbox -b jetToolbox_102X_v3
	cp /afs/cern.ch/work/k/kshcheli/public/jonathan/toolboxstuff JMEAnalysis/JetToolbox/python/jetToolbox_cff.py
	git clone git@github.com:AndreaBellora/protonPreMix.git
	scram b -j8

	cd PPtoPPWWjets/PPtoPPWWjets/python

    cmsRun ConfFileLegacyReRecoPrelim_cfg.py
	 (for data)
	cmsRun ConfFileLegacyReRecoPrelimMCAllInOne_cfg.py 
	 (for signal MC with proton direct sim)

References:
	https://twiki.cern.ch/twiki/bin/viewauth/CMS/JetToolbox#How_to_run_the_jetToolbox
	https://twiki.cern.ch/twiki/bin/viewauth/CMS/TaggedProtonsDirectSimulation#Full_step_by_step_recipe_to_setu
