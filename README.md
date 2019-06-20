## ccminer

This is a fork of https://github.com/tpruvot/ccminer.git with additions for mining LBRY. It is a CUDA miner. It requires nVidia hardware. 
Early editions of ccminer included support for LBRY through the old getwork interface that is still in use by many pools. This fork also includes support for direct use of getblocktemplate (GBT).


### Solo mining direct: 
```
# start a lbrycrd daemon on testnet:
./lbrycrdd -server -txindex -rpcuser=ruser -rpcpassword=rpswd -testnet

# in a separate console, run ccminer:
./ccminer -a lbry -o 127.0.0.1:19245 -u ruser -p rpswd -D

```
This requires support for coinbasetxn in lbrycrd's getblocktemplate implementation, which is fairly new. 

### Compilation:
```
./autogen.sh
./configure --with-cuda=/usr/lib/cuda-10.1/targets/x86_64-linux CXXFLAGS="-Og -march=native -g -Wfatal-errors -L/usr/lib/cuda-10.1/targets/x86_64-linux/lib" CFLAGS="-Og -march=native -g"
make -j5
```
