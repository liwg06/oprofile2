
# for compile:
(1) if get source by git , run
```
 apt-get install automake
 apt-get install libtool
```
(2) deps
```
 apt-get install libpopt-dev
 apt-get install binutils-dev
 apt-get install libiberty-dev
```
(3) config & make & install
```
 ./configure --prefix=/usr/local/optools
 time make
 make install
```
# support other cpus
(1) deal with:  "Your kernel's Performance Events Subsystem does not support your processor type."
  
  common contents between '{ }' which in operf's main func and replace it with `rc = 0;` :
  ``` 
  else if (rc == ENOENT) {
      ...
  } 
  ```
(2) deal with: "Unable to obtain cpu_type"

  modify ` __get_cpu_type ` or 
  
  ` _get_arm_cpu_type ` , specifically,  in "switch cpuid" cases

# visualized callgraphs
## deps:
(1) dot (graphviz), http://www.graphviz.org

  apt-get install graphviz

(2) gprof2dot, https://github.com/jrfonseca/gprof2dot

## steps:
(1) ./opreport -cg > callgraph.data

(2) cat callgraph.data | ./gprof2dot.py -f oprofile | dot -Tpng -o callgraph.png




