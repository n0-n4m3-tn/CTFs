## Challenge Description "log maze"

The volcano research station’s logs were rotated and compressed quickly before a disaster. Among these noisy logs, a secret is hidden


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

   Notice regular logs (`system.log`), rotated compressed logs (`system.log.1.gz`), and some fake logs (`log1.log`, `log2.log`).

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

<img width="1491" height="112" alt="image" src="https://github.com/user-attachments/assets/824e76d9-fe55-4894-b6e1-887ce076891c" />

