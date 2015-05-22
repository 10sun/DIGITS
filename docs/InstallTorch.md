# Torch Installation

Follow these instructions to install Torch on Mac OS X and Ubuntu 12+:

http://torch.ch/docs/getting-started.html

## Luarocks dependencies

To use Torch in DIGITS, you need to install a few extra dependencies.

    % luarocks install image
    % luarocks install inn
    % luarocks install "https://raw.github.com/Sravan2j/lua-pb/master/lua-pb-scm-0.rockspec"
    % luarocks install ccn2

## LMDB and lightningmdb

For now, Torch reads datasets that were created for Caffe. This requires installation of LMDB for Torch, which as you can see below is a bit of a hassle. In the future, we plan to remove this dependency and go with a different data storage format.

#### LMDB

If LMDB wasn’t already installed, install it using the command below:

* On Ubuntu: `sudo apt-get install liblmdb-dev`
* On Mac OS X: `brew install lmdb`

#### Lua Wrapper for LMDB (lightningmdb)

During installation, lightningmdb requires the LMDB header and libraries, so luarocks needs to know the following locations:

* `LMDB_INCDIR`
  * Contains `lmdb.h`
  * e.g. `/usr/include`
* `LMDB_LIBDIR`
  * Contains `liblmdb.so` and `liblmdb.a`
  * e.g. `/usr/lib/x86_64-linux-gnu`

Install lightningmdb (you may need to edit the paths at the end for your specific LMDB installation):

    % luarocks install lightningmdb LMDB_INCDIR=/usr/include LMDB_LIBDIR=/usr/lib/x86_64-linux-gnu

