# mec incourse 1
1. define noise, distortion and bandwidth
2. explain pcm technique 
3. short note on am, fm, and pm
4. draw osi model. function of transport layer
5. ask vs fsk vs psk vs qam
6. bandwidth 2 Mhz, data rate=? if in nrz-l coding scheme
7. calculate periods from the frequency
	1. 40hz
	2. 20Mhz
	3. 200Khz
8. calculate bit rate for 4000 baud baud rate and modulation type: fsk, ask, bpsk, and 16-qam
# mec incourse 2
1. define multiplexing. basic principle of tdm
2. block code technique in error detection
3. how stop-and-wait arq protocol works for noisy channels
4. humming code technique for error correction
5. functions of hdlc frame formats
# niter incourse 1
1. differentiate between data and telecommunication
2. distinguish between the topologies
	1. bus vs star
	2. mesh vs hybrid
3. draw three sine waves with different amplitude, frequency and phase
4. justify the statement based on fourier analysis - "a digital signal is a composite analog signal"
5. a signal has a bandwidth of 20hz and highest frequency is 60hz, determine lowest frequency and draw the spectrum if the signal contains all integral frequencies of the same amplitude
6. determine bandwidth of a periodic signal that is cecomposed into 4 sine waves with frequencies of 100, 300, 500, and 900 hz. draw the spectrum assuming all components have a mazimum amplitude of 10v.
7. if the peak voltage of a signal is 20 times the peak voltage of the noise, what is snr and and $snr_(db)$ 
8. calculate the channel capacity for a channel with spectrum 1Mhz to 2Mhz and a signal to noise ratio of 15dB
9. how are iso and osi related to each other? match the following to one or more layers of the osi model
	1. reliable process to process message delivery
	2. error correction and retransmission
	3. define frames
	4. user service (email, file ransfer)
	5. transmission of bit stream
10. suppose you are asked to communicate between host A(clien) and host B(https web server), where there is an intermediate device (S). now using the mentioned application and addressing draw all the steps involved in a tcp/ip communication

| device type      | client A          | server B          | switch S |
| ---------------- | ----------------- | ----------------- | -------- |
| application type | ftp request       | ftp data          | n/a      |
| ip address       | 102.168.10.10     | 192.168.10.20     | n/a      |
| mac adress       | a1:a2:a3:a4:a5:a6 | b1:b2:b3:b4:b5:b6 | n/a      |
your answer should include all the basic and appropriate header contents of transport layer. network layer and data-link layer of tcp/ip protocol
# niter incourse 2
1. a network with a bandwidth of 10 mbps can pass only an average of 12000 frames/minute, with each frame carrying an average value of 10000 bits. find the throughput of this network and determine how much bandwidth will remain unused.
2. explain how block coding improved the performance of line coding. with a neat block diagram, discuss the process of 8b/10b encoding technique of block coding
3. the capacity of this channel is zero regardless of the bw if the noise is so strong that the signal is faint. justify it mathematically
4. a digital communication system transmits data at a rate of 100 kbps each signal element carries 1 bit of data. the case factor c varies between 0 and 1. answer the following
	1. determine the range of minimum bandwidth
	2. find the number of signal levels used in this system
	3. if the system designer wants to reduce bandwidth, should the increase or decrease the number of signal levels? justify mathematically
5. why use the scrambling technique? convert the given sequence 111_000_0000_0000 using the following scrambling technique. assume last non-zero signal as positive
	1. b8zs
	2. hdb3
6. draw the nrz-l, nrz-i, manchester, and differntial manchester scheme signals for the following data. assume last non zero signal as positive
	1. 0000_0000
	2. 1111_1111
	3. 0101_0101
	4. 1010_1010
7. to guarantee the detection of up to s errors in all cases, the minimum hamming distance in a block code must be dmin=s+1; true of false? justify with an example
8. a simple parity check code can detect an odd number of errors through the syndrome- prove it
# fec incourse 1
1. write the key differences between analog and digital signals with diagram. a periodic signal has a bandwidth of 2hz. the highest frequency is 60 hz. what is the lowest frequency? draw the spectrum if the signal contains all frequencies of the same amplitude
2. what information dhcp provides? a bank has mutiple branches across a country. which network topology should be used and why
3. discuss the three main types of transmission impaisments with examples. what is the propagation time if de distance (atlantic ocean) between the two points is 16,000km? assume propagation speed to be $2.4xx10^8$ m/s in cable
4. why are nyquist and shannon formulas important in data communication? suppose, we need to send 265 kbps over a noiseless channel with a bandwidth of 20khz. how many signal levels do we need?
