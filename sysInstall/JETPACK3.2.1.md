1.Install JETPACK 32.1
sudo apt-get install bzip2
sudo apt-get install lbzip2
tar -vxjf JAX-TX2-Jetson_Linux_R32.1.0_aarch64.tbz2
cd Linux_for_Tegra/rootfs
sudo tar -jxpf ../../JAX-TX2-Tegra_Linux_Sample-Root-Filesystem_R32.1.0_aarch64.tbz2
cd ..
sudo ./apply_binaries.sh
tar -xvf Realtimes_L4T_321_V1.1.tar
cd Realtimes_L4T_321_V1.1/
cd ..
Set TX2 to recovery mode.
sudo ./flash.sh rtso-9003 mmcblk0p1

Success!
