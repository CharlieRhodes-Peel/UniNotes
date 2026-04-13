# Analog to Digital Converter

### Flash Converter:
- Fastest option (still has a delay at the nanosecond level)
- Most expensive option in terms of money and space
- It's just a bunch of comparators (yes minecraft)
	- Each comparator = an extra step in the digital converter
### MCP3008 (the one used in the labs)
- 10 bit resolution
- 200 kHz max sample rate
- +- 1.5 LSB offset error and +- 1 LSB gain error
- It's much slower than the flash converter as it does the conversion in chunks

# Sample Rate:
- Sample rate should always be 2x the highest frequency allowed, after that (mathematically) the conversions will be wrong and produce lower sounds than it should.
	- Should filter out signals above /2 the highest freq.
- Is similar with image compression

## IDK WHERE TO PUT THIS YET:
### PWM:
Brightness with LED's
![[Pasted image 20231020130322.png]]
- Top one is 75% brightness
- 50%
- 20%
You can't tell if it's flickering fast enough because it's too fast for the human eye to [[register]]