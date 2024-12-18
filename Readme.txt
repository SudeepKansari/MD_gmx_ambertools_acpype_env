Steps to install gromacs in linux terminal with cuda compatibility:

########################################################### CUDA TOOLKIT INSTALLATION: ###################################################### 
#	https://developer.nvidia.com/cuda-downloads			                                                                    #
#	#Follow the steps and copy the commands in terminal according to distro. 							    #
#																	    #
#	Then in .bashrc, provide this line at the end and save:										    #
#	export PATH=/usr/local/cuda-12.6/bin:$PATH											    #
#	export LD_LIBRARY_PATH=/usr/local/cuda-12.6/lib64:$LD_LIBRARY_PATH							            #
#																	    #
#	To check the current installation, use the following commands in terminal:							    #
#	nvcc --version                      												    #
#	nvidia-smi															    #
#																	    #
#	These commands will show the latest cuda-12.6 compiler and cuda version 12.6 respectively.                                          #
#								                                                                            #
########################################################## GROMACS INSTALLATION STEPS: ######################################################
#       sudo apt update                                                                                                                     #
#       sudo apt install build-essential                                                                                                    #
#       sudo apt install cmake (CMake version 3.18.4 or later)                                                                              #
#       https://manual.gromacs.org/current/download.html  (Latest Gromacs version 2024.4)                                                   #
#	tar xfz gromacs-2024.4.tar.gz					                                                                    #
#	cd gromacs-2024.4						                                                                    #
#	mkdir build						                                                                            #
#	cd build							                                                                    #
#	cmake .. -DCUDA_TOOLKIT_ROOT_DIR=/usr/local/cuda-12.6 -DCMAKE_CUDA_COMPILER=/usr/local/cuda-12.6/bin/nvcc -DGMX_GPU=CUDA            #
#	make							                                                                            #
#	make check						                                                                            #
#	sudo make install						                                                                    #
#	source /usr/local/gromacs/bin/GMXRC	                                                                                            #
#############################################################################################################################################

To ensure that GROMACS can be executed from any folder without having to source the GMXRC file each time, you can add the source command to 
your shell’s startup script. Here’s how you can do it:
1. Open your shell’s startup script with a text editor. If you’re using Bash, the file will be .bashrc or .bash_profile in your home directory.
   You can open it with:
        
        nano ~/.bashrc

2. Add the following line to the end of the file:

       source /usr/local/gromacs/bin/GMXRC

3. Save and close the file. For nano, you can do this by pressing Ctrl + X, then Y to confirm, and Enter to save.
4. Restart or enter source ~/.bashrc
