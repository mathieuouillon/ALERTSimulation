# ALERTSimulation

How to run simulation for ALERT detector : 

Inside the good docker.

Clone this repository with the submodules : 
```console
git clone --recurse-submodules https://github.com/mathieuouillon/ALERTSimulation
```

Build clas12-offline-software in `alert-geometry` folder : 
```console
./build-coatjava.sh
```

Generate the ALERT geometry files in `alert` folder. 
- Start with the AHDC geometry in `alert/AHDC_geom` folder :
  Fisrt the `rga_fall2018` variation.
  ```console
  ./../../alert-geometry/coatjava/bin/run-groovy factory_ahdc.groovy --variation rga_fall2018 --runnumber 11
  ```
  Then the `default` variation.
  ```console
  ./../../alert-geometry/coatjava/bin/run-groovy factory_ahdc.groovy --variation default --runnumber 11
  ```

  Then generate other files with `./ahdc.pl` : 
  ```console
  ./ahdc.pl config.dat 
  ```

- Now, the ATOF geometry in `alert/ATOF_geom` folder :
  Fisrt the `rga_fall2018` variation.
  ```console
  ./../../alert-geometry/coatjava/bin/run-groovy factory_atof.groovy --variation rga_fall2018 --runnumber 11
  ```
  Then the `default` variation.
  ```console
  ./../../alert-geometry/coatjava/bin/run-groovy factory_atof.groovy --variation default --runnumber 11
  ```

  Then generate other files with `./ahdc.pl` : 
  ```console
  ./atof.pl config.dat 
  ```
  
  - Now, the ALERT target geometry in `alert/ALERT_target` folder :
    ```console
  ./targets.pl config.dat 
  ```
  
- Now, the ALERT external shell geometry in `alert/external_shell_nonActif` folder :
    ```console
  ./alertshell.pl config.dat 
  ```
- Now, the Helium Bag geometry in `alert/He_bag` folder :
    ```console
  ./hebag.pl config.dat 
  ```
  
  
  ## Build GEMC
  build gemc in `gemc_source` folder : 
  ```console
  scons -j4 OPT=1 
  ```
