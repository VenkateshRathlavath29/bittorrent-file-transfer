# BitTorrent Mechanism

For a given input CSV file containing the URLs and the number of parallel TCP connections for each URL, the program downloads different chunks of the file from different peers, combines them, and saves the final file locally.

The purpose of this assignment is to understand the mechanism of BitTorrent. BitTorrent obtains a torrent file containing a list of peers hosting the file and downloads different chunks of the file from different peers.

## Input

A CSV file with the following structure:

```text
[URL-1 for the object],[Number of parallel TCP connections to this URL]
[URL-2 for the object],[Number of parallel TCP connections to this URL]
..
..
```

## Output

1. Downloaded file, saved in the local directory.
2. A graph showing the progress of all threads.

## Example

### Input File

`input.csv`

```csv
vayu.iitd.ac.in/big.txt,6
norvig.com/big.txt,4
```

It indicates that a total of **10 threads** will run:

- 6 threads will download chunks from the `vayu.iitd.ac.in` server.
- 4 threads will download chunks from the `norvig.com` server.

### Commands to Run

**Python Version:** `3.6.12`

```bash
python main.py input.csv output.txt <total_bytes_of_the_file_to_download>
```

## Specifications of the Model

### 1. File Chunking

The whole file is divided into chunks of **10 KB**.

### 2. HTTP Range Requests

The program uses the HTTP `GET` command to download a particular range of bytes using the `Range` header in HTTP.

The HTTP request looks as follows:

```http
GET /big.txt HTTP/1.1
Host: vayu.iitd.ac.in
Connection: keep-alive
Range: bytes=0-99
```

### 3. HTTP Header and Data Separation

The HTTP header and data are separated by the following four characters:

```text
\r\n\r\n
```

### 4. Handling Network Interruptions

The implementation is designed to remain unaffected by irregular interruptions in the Internet connection.