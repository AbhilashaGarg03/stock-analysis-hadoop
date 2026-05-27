# Stock Analysis Using Hadoop Framework

## Project Overview

A distributed big data analytics project analyzing global stock market data using the Apache Hadoop framework. This project demonstrates practical implementation of MapReduce, Hive, and HDFS for processing and analyzing large-scale stock datasets.

## Business Objective

Analyze stock performance across multiple countries and industries to:
- Identify top-performing stocks by sector
- Analyze average high prices by country
- Generate market insights and trends
- Demonstrate scalability of big data processing

## Technology Stack

- **Distributed Framework**: Apache Hadoop
- **Distributed Storage**: HDFS (Hadoop Distributed File System)
- **Query Language**: Hive
- **Data Processing**: MapReduce
- **Visualization**: Hive queries with result export

## Project Structure

```
stock-analysis-hadoop/
├── README.md
├── Abstract.docx
├── project_report.docx
├── configuration/         # Hadoop configuration files
│   ├── core-site.xml
│   ├── hdfs-site.xml
│   ├── yarn-site.xml
│   └── hive-site.xml
├── mapreduce/            # MapReduce code
│   ├── mapper.JPG
│   ├── reducer.JPG
│   └── driver_code.JPG
├── hive/                 # Hive queries
│   ├── stock_analysis.sql
│   └── results/
└── visualizations/       # Analysis results
    ├── dashboards/
    ├── charts/
    └── reports/
```

## Dataset

Stock market data from multiple countries including:
- **Asia**: Hong Kong, India
- **Europe**: Germany
- **Metrics**: Open, High, Low, Close prices, Volume

## Key Analyses

### 1. Stock Performance by Region
   - Asian market trends
   - European market comparison
   - Healthcare vs Manufacturing sectors

### 2. Average High Prices
   - Country-wise comparisons
   - Sector analysis
   - Temporal trends

### 3. Top Gainers
   - Best performing stocks
   - Performance rankings
   - Market leaders

### 4. Market Segment Analysis
   - Healthcare industry stocks
   - Manufacturing sector stocks
   - Growth indicators

## Installation & Setup

### Prerequisites

- Java 8+
- Hadoop 2.7+ or 3.x
- Hive 2.3+
- Linux/Unix environment

### Hadoop Installation

```bash
# Download and install Hadoop
wget https://archive.apache.org/dist/hadoop/common/hadoop-3.2.1/hadoop-3.2.1.tar.gz
tar -xzf hadoop-3.2.1.tar.gz
mv hadoop-3.2.1 /usr/local/hadoop

# Set environment variables
echo "export HADOOP_HOME=/usr/local/hadoop" >> ~/.bashrc
echo "export PATH=$PATH:$HADOOP_HOME/bin" >> ~/.bashrc
source ~/.bashrc

# Format HDFS namenode
$HADOOP_HOME/bin/hdfs namenode -format
```

### Configuration

Update Hadoop configuration files (see `/configuration` directory):
- `core-site.xml` - FS settings
- `hdfs-site.xml` - HDFS configuration
- `yarn-site.xml` - YARN resource management
- `hive-site.xml` - Hive metastore settings

### Start Hadoop Cluster

```bash
# Start HDFS
$HADOOP_HOME/sbin/start-dfs.sh

# Start YARN
$HADOOP_HOME/sbin/start-yarn.sh

# Verify (access http://localhost:8088 for YARN UI)
```

## Running Analyses

### MapReduce Jobs

```bash
# Compile MapReduce code
javac -cp $HADOOP_HOME/share/hadoop/common/* *.java

# Create JAR
jar cf StockAnalysis.jar *.class

# Submit job
hadoop jar StockAnalysis.jar StockAnalysisDriver input/ output/

# View results
hadoop fs -cat output/part-r-00000
```

### Hive Queries

```bash
# Start Hive CLI
hive

# Load data into Hive table
LOAD DATA INPATH 'hdfs:///stock_data/' INTO TABLE stock_table;

# Run analysis queries
SELECT country, AVG(high) as avg_high_price FROM stock_table GROUP BY country;

# Export results
INSERT OVERWRITE LOCAL DIRECTORY '/home/results' SELECT * FROM query_results;
```

## Key Findings

- **Top Gainers**: [Stock symbols and performance]
- **Regional Performance**: [Country-wise analysis]
- **Sector Leaders**: [Healthcare/Manufacturing leaders]
- **Market Trends**: [Key insights]

## Visualizations

The project includes multiple visualizations:
- Market dashboards
- Performance charts
- Regional comparisons
- Sector analysis

See `/visualizations` directory for detailed charts.

## Performance Metrics

- Data Processing Time: [X minutes for Y GB of data]
- Scalability: Linear scaling across nodes
- Query Response Time: [X seconds for complex queries]

## Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Data imbalance across regions | Partitioning strategy in Hive |
| HDFS storage management | Compression and partitioning |
| Query performance | Indexing and sampling strategies |

## Future Enhancements

- Spark integration for faster processing
- Real-time streaming analysis
- Predictive analytics models
- Machine learning pipeline integration

## Files & Documentation

- `project_report.docx` - Detailed project report
- `Abstract.docx` - Executive summary
- Configuration files in `/configuration`
- MapReduce implementation images
- Query results and dashboards

## Author

Abhilasha Garg

## License

[License Information]

## References

- Apache Hadoop Official Documentation
- Hive LanguageManual
- MapReduce Tutorial
