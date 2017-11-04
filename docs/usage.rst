Usage
=====

The C++ and CUDA C code has been written as an extended module of Python. We can use the functions of GALAMOST by loading and calling its modules through a Python script.
With the prepared script, you should now be able to try running GALAMOST as:

   Examples::
   
      ./yourscript.gala --gpu=0 >a.log&
	  
Where you may specify the GPU id with the ``--gpu=`` option and output the screen information into ``a.log`` file. If the script file has no executive permission, the command of ``chmod +x yourscript.gala`` should be executed before running above command.
Here is an example of script for DPD simulation. The head of GALAMOST script usually is:

   Examples::
   
      #!/usr/bin/python
      import sys
      sys.path.append('/opt/galamost3/lib')
      import galamost
      
      global _options
      parser = OptionParser()
      parser.add_option('--gpu', dest='gpu',help='GPU on which to execute')
      (_options, args) = parser.parse_args()
	  
where the first paragraph sets the path of the installed library of GALAMOST ``galamost.so`` for loading the Python extensible modules of GALAMOST. The second paragraph is used for parsing GPU id from the executive command. 
Then, by reading the configuration from a prepared XML file, a system with necessary information can be built up by

   Examples::
   
      filename = 'A.xml'
      build_method = galamost.XmlReader(filename)
      perform_config = galamost.PerformConfig(_options.gpu)
      all_info = galamost.AllInfo(build_method,perform_config)
	  
After that, we need to build up an application which will call following defined and added objects by:

   Examples::
   
      dt = 0.01
      app = galamost.Application(all_info, dt)

Further, we should define the needed objects by the classes of GALAMOST and pass them to the application, such as the following example: non-bonded DPD force, NVT thermostat with GWVV algorithm, and information analysis methods:
      
   Examples::
  	  
      neighbor_list = galamost.NeighborList(all_info, 1.0 ,0.05) # (,rcut,rbuffer)
      dpd=galamost.DpdForce(all_info,neighbor_list,1.0, 12345) # (,,rcut,seed)
      dpd.setParams('A', 'A', 25.0, 3.0) # (,,alpha,sigma)
      dpd.setParams('A', 'B', 40.0, 3.0) # ( ,,alpha,sigma)
      dpd.setParams('B', 'B', 25.0, 3.0) # ( ,,alpha,sigma)
      app.add(dpd)

      group = galamost.ParticleSet(all_info,"all" )
      comp_info = galamost.ComputeInfo(all_info, group)
      Gwvv = galamost.DpdGwvv(all_info, group)
      app.add(Gwvv)
      
      dinfo = galamost.DumpInfo(all_info, comp_info, 'data.log')
      dinfo.setPeriod(200)
      app.add(dinfo)
	  
The tail of script usually sets the number of time steps to run, and the function of analysis of neighbor list etc.
      
   Examples::
  	  
      app.run( 10000)
      neighbor_list.printStats()

