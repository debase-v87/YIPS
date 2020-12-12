---
yip: 1
title: Composing with S-pool 1
status: WIP
author: anon18382, @jusTaPunkk (@PunkUnknown)
discussions-to: https://debaseonomics.medium.com/debase-v88-new-dawn-e6bc213796a3
created: 12-11-2020
---
## Simple Summary
We propose S-pool 1, which will stabilize Debase to target during positive rebase cycles.

## Abstract
This stabilizer will use a randomized threshold of positive rebases, to inflate part of the supply to the LPs and stabilize prize of Debase during positive rebase cycles.

## Motivation
DEBASE is supposed to stabilize towards the target range. In line with the vision of Debaseonomics to use s-pools to stabilize DEBASE price, s-pool 1 will do so in expansion cycles (periods of high number of positive rebases, consecutively or otherwise).  

## Technical specification
The s-pool will take in DAI/DEBASE LPs and provide rewards in DEBASE. 
The rewards are given out after k positive rebases over a period of n rebase cycles, where k is sampled from a normal distribution with a known mean and standard deviation. 
The randomness incentivizes continous liquidity, as otherwise the rewards system can be manipulated if the blocktime of the rewards were known beforehand.
Furthermore, we use Chainlink VRF as a source of randomness given that on-chain randomness can be manipulated by miners.

### Configurable parameters

* Integer: Rewards requested by the the stabilizers
* Integer: Duration over which rewards will be distributed
* Boolean: Count positive rebases in sequence
* Boolean: Revoke further rewards in case of non-positive rebase
* Integer: Duration of rewards that will be revoked
* Boolean: Award rewards before previous rewards have been distributed
* Boolean: Pool is enabled for staking/withdrawal
* Normal distribution parameters
  * Integer[100]: Array filled with the numbers from Normal Distribution
  * Integer: Expected Value of the Normal Distribution (mean)
  * Integer: Stanard deviation of the Normal Distribution
