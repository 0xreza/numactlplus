# numactl+

The paper below proposes a bandwidth-aware page placement approach for NUMA architectures. As a part of that work, we implemented a new page allocation policy in the Linux kernel, called "weighted interleave" which enables weighted allocation of pages on specified NUMA nodes for the specified applications.

The modified linux kernel is available [here](https://github.com/0xreza/SNAKE-4.17.12).

Example) to allocate the pages for [target_program] on the nodes 0 and 2 with the 1:3 proportions:

```
./numactl --weights=1,3 --interleave=0,2 [target_program]
```

__D. Gureya, J. Neto, P. Romano, R. Rodrigues, V. Quema, P. Bhatotia, R. Karimi, V. Vlassov, J. Barreto,
“BWAP: Bandwidth-Aware Page Placement for NUMA Architectures” [in submission]__

Please send an email to "paper[at]0xreza[dot]com", to recieve the pre-print version of the paper.


# numactl

[![Build Status](https://travis-ci.org/numactl/numactl.svg?branch=master)](https://travis-ci.org/numactl/numactl)

Simple NUMA policy support. It consists of a numactl program to run other
programs with a specific NUMA policy and a libnuma shared library ("NUMA API")
to set NUMA policy in applications.

The libnuma binary interface is supposed to stay binary compatible.

Incompatible changes will use new symbol version numbers.

In addition there are various test and utility programs, like `numastat` to
display NUMA allocation statistics and `memhog`.

In `test/` there is a small regression test suite.

Note that `regress` assumes a unloaded machine with memory free on each node.
Otherwise you will get spurious failures in the non-strict policies (prefered,
interleave.)

See the manpages [`numactl.8`](https://linux.die.net/man/8/numactl) and
[`numa.3`](https://linux.die.net/man/3/numa) for details.

# License, Copyrights, Acknowledgements

`numactl` and the demo programs are under the GNU General Public License, v.2.

`libnuma` is under the GNU Lesser General Public License, v2.1.

The manpages are under the same license as the Linux manpages (see the files.)

`numademo` links with a library derived from the C version of STREAM by John D.
McCalpin and Joe R. Zagar for one sub benchmark. See `stream_lib.c` for the
license. In particular when you publish `numademo` output you might need to pay
attention there or filter out the STREAM results.

It also uses a public domain Mersenne Twister implementation from Michael
Brundage.

Version 2.0.10-rc2: (C)2014 SGI

Author:
Andi Kleen, SUSE Labs

Version 2.0.0 by Cliff Wickman (`cpw@sgi.com`), Christoph Lameter
(`clameter@sgi.com`) and Lee Schermerhorn (`lee.schermerhorn@hp.com`).

