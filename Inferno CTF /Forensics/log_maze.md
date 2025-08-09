---

## Challenge Description "log_maze"

The volcano research station’s logs were rotated and compressed quickly before a disaster. Among these noisy logs, a secret flag is hidden — encoded in base64 inside a rotated compressed log file. Beware of fake encoded strings scattered to mislead you.

Your task: find, decode, and extract the real flag.

Files provided: zipped folder of rotated and compressed logs.

---

## Solver Writeup — Step-by-step

1. Unzip the provided archive:

   ```bash
   unzip log_maze.zip
   cd log_maze
   ```

2. List files:

   ```bash
   ls -l
   ```

   Notice regular logs (`system.log`), rotated compressed logs (`system.log.1.gz`), and some fake logs (`fake1.log`, `fake2.log`).

3. Search for base64 strings in the rotated compressed log:

   ```bash
   zcat system.log.1.gz | grep TRACE
   ```

   You’ll get a line with a base64-encoded string.

4. Decode the base64 string to reveal the flag:

   ```bash
   echo 'BASE64_STRING_HERE' | base64 -d
   ```

   It will output something like:

   ```
   flag{volcano_logs_unraveled_9a7b}
   ```

5. Ignore fake logs that contain random base64-like strings that decode to garbage.
