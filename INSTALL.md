Installing IELE
===============

In a nutshell, to install IELE on an Ubuntu 16.04 machine, run:

```

sudo apt-get update
sudo apt-get install make gcc maven openjdk-8-jdk flex opam pkg-config libmpfr-dev autoconf libtool pandoc libssl-devl build-essential libffi-dev
git submodule update --init # Initialize submodules
curl -sSL https://get.haskellstack.org/ | sh # Install stack
cd .build/secp256k1 && ./autogen.sh && ./configure --enable-module-recovery --enable-module-ecdh --enable-experimental && make && sudo make install # install secp256k1 from bitcoin-core
cd .build/pyethereum && sudo python setup.py install # install pyethereum to sign "ethereum" transactions
make deps # Build dependencies not installed by package manager
eval `opam config env` # add OCAML installation to path
make # Build project

```

To test against a fragment of the ethereum test suite, run `make test`
