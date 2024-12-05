# NTIA Software Tester UE

Penetration Testing Tool for Software Defined Radio

## Overview

This project is a security testing tool based on srsRAN Project's User
Equipment, used to test 5G and open radio access networks (RANs) via the Uu air
interface between the UE and the network. While this enables different types of
testing, the focus of the software is on RAN security testing. This soft T-UE is
fully software-defined and compatible with widely available, commercial
off-the-shelf software radio hardware. Standardized 3GPP or O-RAN tests as well
as custom test procedures can then be implemented and executed at minimal cost
and at different stages of RAN development and integration. This system allows
for testing many commercial and open source random access networks with minimal
technical overhead. Many attacks on the RAN can be run automatically by the
system.

- [UE Documentation](https://github.com/oran-testing/soft-t-ue/blob/main/docs/UE.md)
- [gNB Documentation](https://github.com/oran-testing/soft-t-ue/blob/main/docs/gNB.md)
- [Attack Documentation](https://github.com/oran-testing/soft-t-ue/blob/main/docs/attacks)

**NOTE: This system is designed to run on ubuntu and is tested on ubuntu 24.04**

## Installation

Testing can be done with one machine (ZMQ) or two. Each command should be run in a seperate terminal.

Before installing, clone the soft-t-ue repo and the srsRAN_Project repo.

To install the UE, run (Machine A):

```bash
sudo ./soft-t-ue/scripts/install-ue.sh
```

To install the 5gs, run (Machine B):

```bash
sudo ./soft-t-ue/scripts/install-open5gs.sh
```

To install the gNB run (Machine B):

```bash
sudo ./soft-t-ue/scripts/install-gnb.sh
```

When configuring the iperf3, choose yes:

![Soft-T-UE-System.png](docs/images/configuring_iperf3_yes.png)

## Running

**To run the UE, run (Machine A):**

```bash
cd soft-t-ue/docker
sudo docker compose up srsue
```

**To run the 5gs, run (Machine B):**

```bash
cd srsRAN_Project/docker
sudo docker compose up 5gc
```
\
**<span style="color: #e03e2d;">!!!</span>
gNB should run last
<span style="color: #e03e2d;">!!!</span>** \
Otherwise, gnB will not work.

**To run the gNB run (Machine B):**

```bash
sudo gnb -c ./soft-t-ue/configs/zmq/gnb_zmq.yaml
```

## System Architecture

![Soft-T-UE-System.png](docs/images/Soft-T-UE-System.png)
