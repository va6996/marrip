# Moving Average Re-Reference Interval Prediction

To execute the provided code, you will first have to install the ChampSim simulator on the required host. 
To do that, run the following commands: 
```
git clone https://github.com/ChampSim/ChampSim.git
cd scripts
./download_dpc3_traces.sh
```

Now copy the file marrip.llc_repl into the replacement folder inside the ChampSim folder.
Then execute the following command:
```
./build_champsim.sh bimodal no no no no marrip 1
./run_champsim.sh bimodal-no-no-no-no-marrip-1core 1 10 <trace>
```

Here, <trace> means one of the traces filed located in the dpc3_traces folder. 
This will generate a file in a results_10M folder. When you open the file  inside the folder, you will see some text such as:
```
CPU 0 cumulative IPC: 0.403119 instructions: 10000000 cycles: 24806577
L1D TOTAL     ACCESS:    3680311  HIT:    3290130  MISS:     390181
L1D LOAD      ACCESS:    2607451  HIT:    2254112  MISS:     353339
L1D RFO       ACCESS:    1072860  HIT:    1036018  MISS:      36842
L1D PREFETCH  ACCESS:          0  HIT:          0  MISS:          0
L1D WRITEBACK ACCESS:          0  HIT:          0  MISS:          0
L1D PREFETCH  REQUESTED:          0  ISSUED:          0  USEFUL:          0  USELESS:          0
L1D AVERAGE MISS LATENCY: 66.9087 cycles
L1I TOTAL     ACCESS:    1917812  HIT:    1917812  MISS:          0
L1I LOAD      ACCESS:    1917812  HIT:    1917812  MISS:          0
L1I RFO       ACCESS:          0  HIT:          0  MISS:          0
L1I PREFETCH  ACCESS:          0  HIT:          0  MISS:          0
L1I WRITEBACK ACCESS:          0  HIT:          0  MISS:          0
L1I PREFETCH  REQUESTED:          0  ISSUED:          0  USEFUL:          0  USELESS:          0
L1I AVERAGE MISS LATENCY: nan cycles
L2C TOTAL     ACCESS:     440883  HIT:     174088  MISS:     266795
L2C LOAD      ACCESS:     353337  HIT:     103553  MISS:     249784
L2C RFO       ACCESS:      36841  HIT:      19869  MISS:      16972
L2C PREFETCH  ACCESS:          0  HIT:          0  MISS:          0
L2C WRITEBACK ACCESS:      50705  HIT:      50666  MISS:         39
L2C PREFETCH  REQUESTED:          0  ISSUED:          0  USEFUL:          0  USELESS:          0
L2C AVERAGE MISS LATENCY: 75.3913 cycles
LLC TOTAL     ACCESS:     293577  HIT:     183488  MISS:     110089
LLC LOAD      ACCESS:     249784  HIT:     139863  MISS:     109921
LLC RFO       ACCESS:      16972  HIT:      16835  MISS:        137
LLC PREFETCH  ACCESS:          0  HIT:          0  MISS:          0
LLC WRITEBACK ACCESS:      26821  HIT:      26790  MISS:         31
LLC PREFETCH  REQUESTED:          0  ISSUED:          0  USEFUL:          0  USELESS:          0
LLC AVERAGE MISS LATENCY: 108.588 cycles
Major fault: 0 Minor fault: 3007
```
The lines with LLC* are of interest to us.

To run the benchmarks, you can simply execute the benchmarks.ipny file on Google Collab or any other Jupyter server.

In our file, we have included the results we got after running the traces for 10 of 20 traces that showed significant performance difference. 

The LLC TOTAL* line was grepped and pasted into the notebook, after which we processed the data to generate the benchmarks.