
# Hadoop in Docker with MapReduce Programs

This repository demonstrates setting up a Hadoop system using Docker and developing Hadoop MapReduce programs for tasks like n-gram frequency analysis and log analysis.

## Project Overview

- **Hadoop in Docker**  
  The project includes setting up Hadoop inside a Docker container. A `Dockerfile` is provided to automate the setup process, along with necessary configuration files for HDFS and YARN. The Hadoop setup operates in a single-node mode, allowing local execution of Hadoop jobs.

- **n-gram Frequency Analysis**  
  This MapReduce program calculates the frequency of n-grams in a given input text. You can specify the size of the n-gram (e.g., unigram, bigram, trigram), and the program outputs the frequency of each n-gram in the text.

- **Log File Analysis**  
  This part involves analyzing a real-world log file using Hadoop MapReduce to answer various questions, such as counting the number of hits, identifying popular website paths, and determining the amount of data transferred. The log file is in Common Log Format (CLF).

## Setup Instructions

### Prerequisites

- [Docker](https://www.docker.com/) installed on your machine.
- Familiarity with running basic Docker and Hadoop commands.

### Step 1: Building and Running the Docker Hadoop Image

1. Clone the repository:
   ```bash
   git clone https://github.com/YourUsername/hadoop-docker-project.git
   cd hadoop-docker-project
   ```

2. Build the Docker image:
   ```bash
   docker build -t hadoop-docker .
   ```

3. Run the Docker container:
   ```bash
   docker run -it hadoop-docker
   ```

4. Inside the container, you can verify the Hadoop setup by running a sample Hadoop job, like Wordcount.

### Step 2: Running the n-gram Frequency Program

1. Place your input text file inside the container.

2. Execute the n-gram MapReduce job:
   ```bash
   hadoop jar ngram.jar NgramDriver input_file output_directory n
   ```

3. After execution, the output directory will contain the results showing the frequency of each n-gram.

### Step 3: Log Analysis with MapReduce

1. Place the log file (`access_log`) in the container's HDFS.

2. Execute the log analysis MapReduce programs to answer specific questions, such as:
   ```bash
   hadoop jar loganalysis.jar LogAnalysisDriver input_log_file output_directory
   ```

3. The results will be saved in the output directory, answering the questions such as "Which IP address accessed the website the most?" or "How many requests returned a 404 status code?"

## Example Use Cases

- **n-gram Analysis**: Useful for analyzing the frequency of character sequences in large text datasets, which has applications in natural language processing.
- **Log Analysis**: Helpful in identifying web traffic patterns, frequently accessed resources, and potential bottlenecks in web applications.

## File Structure

- `Dockerfile`: Used to build the Hadoop Docker image.
- `hdfs-site.xml`, `yarn-site.xml`: Configuration files for Hadoop's HDFS and YARN.
- `ngram.jar`: The compiled MapReduce program for n-gram frequency analysis.
- `loganalysis.jar`: The compiled MapReduce program for analyzing log files.
- `bootstrap.sh`: A script to start the Hadoop services inside the Docker container.
- `access_log`: Sample log file used for log analysis.

