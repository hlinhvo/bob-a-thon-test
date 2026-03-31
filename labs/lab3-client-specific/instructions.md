# Lab 3: RealDataTeam Stream Processing Use Cases

**Duration:** 90 minutes  
**Difficulty:** Advanced  
**Prerequisites:** Completed Labs 1 and 2, Python/Kafka/Spark knowledge

## 🎯 Objectives

By the end of this lab, you will be able to:
- Apply Bob to RealDataTeam's real-time data processing challenges
- Build and optimize Kafka-based stream processing pipelines
- Implement data quality validation for streaming data
- Create real-time analytics with Spark
- Optimize performance for high-throughput systems
- Demonstrate tangible value and ROI with Bob

## 📋 Setup

Before starting, ensure you have:
- [ ] Completed Labs 1 and 2
- [ ] Access to the sample stream processing project
- [ ] Python 3.9+ with Kafka and Spark libraries installed
- [ ] Kafka cluster accessible (local or remote)
- [ ] Spark environment configured
- [ ] Understanding of RealDataTeam's data platform architecture

## 🎯 RealDataTeam Use Cases

This lab focuses on four critical use cases for RealDataTeam's real-time data processing system:

1. **Stream Processing Pipelines** (45 min) - High Priority
2. **Data Quality Validation** (30 min) - High Priority
3. **Real-time Analytics** (30 min) - Medium Priority
4. **Performance Optimization** (30 min) - Medium Priority

---

## Use Case 1: Stream Processing Pipelines (45 minutes)

**Priority:** High  
**Business Value:** Reliable, scalable stream processing with proper error handling and monitoring

### Scenario

RealDataTeam needs to build a robust Kafka-based stream processing pipeline that consumes events from multiple topics, transforms the data, and produces enriched events to downstream systems. The pipeline must handle high volumes (10,000+ events/second), include proper error handling, and provide monitoring capabilities.

### Tasks

1. **Create a Kafka Consumer with Error Handling**
   - Set up consumer with proper configuration
   - Implement retry logic for transient failures
   - Add dead letter queue for failed messages
   - Include offset management

2. **Build Stream Transformation Logic**
   - Parse and validate incoming JSON messages
   - Transform data structure for downstream consumers
   - Add timestamp and metadata enrichment
   - Handle schema evolution

3. **Implement Kafka Producer**
   - Configure producer for reliability
   - Add batching for performance
   - Implement idempotent writes
   - Include monitoring metrics

4. **Add Monitoring and Logging**
   - Track processing metrics (throughput, latency)
   - Log errors with context
   - Add health check endpoints
   - Create alerting thresholds

### Bob Workflow

```
Step 1: Understand existing patterns
"Read the existing Kafka consumer in src/streaming/base_consumer.py and show me the configuration patterns for reliability and error handling."

Step 2: Create robust consumer
"Create a new Kafka consumer in src/streaming/event_consumer.py that:
1. Consumes from 'raw-events' topic
2. Includes retry logic with exponential backoff
3. Sends failed messages to 'dlq-events' topic
4. Commits offsets only after successful processing
5. Includes proper logging and metrics

Use the patterns from base_consumer.py but add enhanced error handling."

Step 3: Add transformation logic
"In src/streaming/transformers.py, create a transform_event function that:
1. Validates JSON schema
2. Adds processing_timestamp field
3. Enriches with source_system metadata
4. Handles missing or malformed fields gracefully
5. Returns transformed event or raises ValidationError

Include comprehensive docstrings and type hints."

Step 4: Implement producer
"Create a Kafka producer in src/streaming/event_producer.py that:
1. Produces to 'enriched-events' topic
2. Uses idempotent writes (enable.idempotence=true)
3. Batches messages for performance
4. Includes retry configuration
5. Tracks success/failure metrics

Add tests in tests/streaming/test_producer.py."

Step 5: Add monitoring
"Update src/monitoring/metrics.py to track:
1. Events processed per second
2. Processing latency (p50, p95, p99)
3. Error rate
4. Consumer lag
5. Dead letter queue size

Use Prometheus metrics format."
```

### Success Criteria

- [ ] Consumer handles 10,000+ events/second
- [ ] Error handling with retry and DLQ implemented
- [ ] All messages processed exactly once (no duplicates)
- [ ] Monitoring metrics available
- [ ] Tests cover happy path and error scenarios
- [ ] Processing latency < 100ms at p95

### 💰 Business Impact

**Time Savings:** Building this pipeline manually takes 8-12 hours. With Bob: 2-3 hours (70% reduction)

**Quality Improvements:**
- Proper error handling prevents data loss
- Monitoring enables proactive issue detection
- Tests ensure reliability

**Estimated Value:** 6-9 hours saved per pipeline × 4 pipelines/month = 24-36 hours/month

---

## Use Case 2: Data Quality Validation (30 minutes)

**Priority:** High  
**Business Value:** Ensure data integrity, prevent downstream issues, maintain trust in analytics

### Scenario

RealDataTeam processes millions of events daily. Bad data causes downstream failures and incorrect analytics. You need to implement comprehensive data quality checks that validate schema, detect anomalies, and profile data quality metrics in real-time.

### Tasks

1. **Schema Validation**
   - Define expected schema for events
   - Validate required fields
   - Check data types
   - Enforce value constraints

2. **Data Profiling**
   - Track null rates per field
   - Monitor value distributions
   - Detect outliers
   - Calculate completeness metrics

3. **Anomaly Detection**
   - Identify unusual patterns
   - Flag suspicious values
   - Alert on quality degradation
   - Track quality trends

4. **Quality Reporting**
   - Generate quality metrics
   - Create quality dashboard data
   - Alert on threshold violations
   - Maintain quality history

### Bob Workflow

```
Step 1: Define schema
"Create a Pydantic model in src/schemas/event_schema.py for our streaming events with:
- event_id (UUID, required)
- timestamp (datetime, required)
- event_type (enum: 'click', 'view', 'purchase', required)
- user_id (string, required)
- amount (float, optional, must be >= 0)
- metadata (dict, optional)

Include validation rules and helpful error messages."

Step 2: Implement validation
"Create src/quality/validator.py with a DataValidator class that:
1. Validates events against the schema
2. Returns validation results with specific errors
3. Tracks validation metrics (pass rate, error types)
4. Handles batch validation efficiently

Include comprehensive tests."

Step 3: Add data profiling
"Create src/quality/profiler.py with a DataProfiler class that:
1. Calculates null rates for each field
2. Tracks value distributions (min, max, mean, median)
3. Detects outliers using IQR method
4. Computes completeness scores
5. Generates profiling reports

Use Spark for efficient processing of large datasets."

Step 4: Implement anomaly detection
"Add anomaly detection to src/quality/anomaly_detector.py:
1. Use statistical methods (z-score, IQR)
2. Detect sudden changes in event rates
3. Flag unusual value patterns
4. Generate anomaly alerts with context

Include configurable thresholds."

Step 5: Create quality dashboard
"Update src/monitoring/quality_metrics.py to expose:
1. Real-time validation pass rate
2. Field-level null rates
3. Anomaly counts by type
4. Quality score (0-100)
5. Trend indicators

Format for Grafana dashboard."
```

### Success Criteria

- [ ] Schema validation catches 100% of malformed events
- [ ] Data profiling runs in real-time (< 1 second lag)
- [ ] Anomaly detection identifies issues within 5 minutes
- [ ] Quality metrics available in dashboard
- [ ] Alerts trigger on quality degradation
- [ ] Tests cover all validation rules

### 💰 Business Impact

**Quality Improvements:**
- Prevents bad data from reaching analytics (saves 4-6 hours/week debugging)
- Early detection of data issues (reduces incident response time by 80%)
- Maintains data trust and reliability

**Cost Savings:**
- Prevents downstream pipeline failures
- Reduces manual data investigation time
- Avoids incorrect business decisions from bad data

**Estimated Value:** 4-6 hours/week saved = 16-24 hours/month

---

## Use Case 3: Real-time Analytics (30 minutes)

**Priority:** Medium  
**Business Value:** Immediate insights, faster decision-making, competitive advantage

### Scenario

RealDataTeam needs real-time analytics on streaming data to provide immediate insights to business users. This includes aggregations, windowing operations, and streaming joins to calculate metrics like events per minute, user activity patterns, and revenue trends.

### Tasks

1. **Windowed Aggregations**
   - Implement tumbling windows (5-minute intervals)
   - Calculate event counts by type
   - Compute average values
   - Track unique users

2. **Streaming Joins**
   - Join events with user profiles
   - Enrich with reference data
   - Handle late-arriving data
   - Manage state efficiently

3. **Real-time Metrics**
   - Events per second by type
   - Revenue per minute
   - Active users (5-minute window)
   - Conversion rates

4. **Output to Dashboard**
   - Write results to Kafka topic
   - Update Redis cache
   - Trigger alerts on thresholds
   - Maintain metric history

### Bob Workflow

```
Step 1: Set up Spark Structured Streaming
"Create src/analytics/stream_analytics.py with Spark Structured Streaming setup:
1. Read from Kafka 'enriched-events' topic
2. Parse JSON messages
3. Define watermark for late data (10 minutes)
4. Configure checkpointing

Include proper error handling and logging."

Step 2: Implement windowed aggregations
"Add windowed aggregation functions:
1. Tumbling window (5 minutes)
2. Count events by event_type
3. Sum amounts for 'purchase' events
4. Count distinct user_ids
5. Calculate average amount per purchase

Use Spark window functions efficiently."

Step 3: Add streaming joins
"Implement streaming join in src/analytics/enrichment.py:
1. Join events stream with user_profiles (from Kafka)
2. Add user segment and tier information
3. Handle null values gracefully
4. Optimize join performance with broadcast hints

Include tests with sample data."

Step 4: Create output writers
"Add output writers in src/analytics/writers.py:
1. Write to 'analytics-results' Kafka topic
2. Update Redis with latest metrics (TTL: 1 hour)
3. Trigger alerts if thresholds exceeded
4. Log metrics for historical analysis

Include retry logic and error handling."

Step 5: Add monitoring
"Update monitoring to track:
1. Processing lag (event time vs processing time)
2. Throughput (events/second)
3. State size
4. Checkpoint duration
5. Output latency

Add alerts for degraded performance."
```

### Success Criteria

- [ ] Real-time metrics updated within 30 seconds
- [ ] Handles 5,000+ events/second
- [ ] Late data handled correctly (up to 10 minutes)
- [ ] Streaming joins perform efficiently
- [ ] Metrics available in dashboard
- [ ] Tests verify calculation accuracy

### 💰 Business Impact

**Business Value:**
- Immediate insights enable faster decisions
- Real-time monitoring detects issues quickly
- Competitive advantage from timely data

**Time Savings:**
- Eliminates batch processing delays (hours → seconds)
- Reduces manual metric calculation
- Faster incident detection and response

**Estimated Value:** Real-time insights worth 10-15 hours/week in faster decision-making

---

## Use Case 4: Performance Optimization (30 minutes)

**Priority:** Medium  
**Business Value:** Reduced infrastructure costs, improved scalability, better user experience

### Scenario

RealDataTeam's stream processing pipelines are experiencing performance issues: high latency, resource exhaustion, and scaling challenges. You need to optimize the pipelines for better throughput and lower latency while reducing infrastructure costs.

### Tasks

1. **Identify Bottlenecks**
   - Profile current performance
   - Analyze resource usage
   - Identify slow operations
   - Review configuration

2. **Optimize Kafka Configuration**
   - Tune consumer settings
   - Optimize producer batching
   - Adjust partition strategy
   - Configure compression

3. **Optimize Spark Processing**
   - Reduce shuffles
   - Optimize window operations
   - Tune memory settings
   - Improve partitioning

4. **Implement Caching**
   - Cache reference data
   - Use broadcast variables
   - Implement result caching
   - Optimize state management

### Bob Workflow

```
Step 1: Profile current performance
"Analyze src/streaming/consumer.py and identify performance bottlenecks:
1. Review Kafka consumer configuration
2. Check for inefficient operations
3. Identify resource-intensive code
4. Suggest optimization opportunities

Provide specific recommendations with expected impact."

Step 2: Optimize Kafka settings
"Update Kafka configuration in src/config/kafka_config.py:
1. Increase fetch.min.bytes to 1MB for better batching
2. Set max.poll.records to 500 for optimal throughput
3. Enable compression (compression.type=snappy)
4. Tune linger.ms for producer batching
5. Optimize partition assignment strategy

Explain the rationale for each change."

Step 3: Optimize Spark operations
"Refactor src/analytics/stream_analytics.py to improve performance:
1. Reduce shuffles by using coalesce instead of repartition
2. Optimize window operations with proper watermarking
3. Use broadcast joins for small reference data
4. Tune spark.sql.shuffle.partitions based on data volume
5. Implement incremental aggregations

Add performance tests to measure improvement."

Step 4: Implement caching
"Add caching in src/streaming/cache_manager.py:
1. Cache user profiles in Redis (TTL: 1 hour)
2. Use Spark broadcast variables for reference data
3. Implement result caching for expensive computations
4. Add cache invalidation logic

Include cache hit rate monitoring."

Step 5: Measure improvements
"Create performance benchmarks in tests/performance/:
1. Measure throughput (events/second)
2. Track latency (p50, p95, p99)
3. Monitor resource usage (CPU, memory)
4. Calculate cost per million events
5. Compare before/after metrics

Generate performance report."
```

### Success Criteria

- [ ] Throughput increased by 50%+
- [ ] Latency reduced by 40%+
- [ ] Resource usage optimized (30% reduction)
- [ ] Infrastructure costs reduced
- [ ] Performance tests validate improvements
- [ ] Documentation updated with tuning guide

### 💰 Business Impact

**Cost Savings:**
- 30% reduction in infrastructure costs = significant monthly savings
- Better resource utilization
- Reduced need for scaling

**Performance Improvements:**
- 50% higher throughput enables business growth
- 40% lower latency improves user experience
- Better scalability for future needs

**Estimated Value:** Infrastructure cost reduction + improved capacity = substantial ROI

---

## 🎓 Key Learnings

### Bob's Value for Stream Processing

1. **Rapid Development**
   - Build complex pipelines 70% faster
   - Generate boilerplate code instantly
   - Implement best practices automatically

2. **Quality Assurance**
   - Comprehensive error handling
   - Proper testing coverage
   - Production-ready code

3. **Performance Optimization**
   - Identify bottlenecks quickly
   - Apply proven optimization patterns
   - Measure improvements accurately

4. **Knowledge Transfer**
   - Learn Kafka/Spark best practices
   - Understand complex patterns
   - Build team expertise

### Real-World Application

**Daily Development:**
- Use Bob for new pipeline development
- Optimize existing pipelines
- Debug production issues
- Generate monitoring code

**Code Reviews:**
- Validate error handling
- Check performance patterns
- Ensure best practices
- Verify test coverage

**Troubleshooting:**
- Analyze performance issues
- Debug data quality problems
- Investigate pipeline failures
- Optimize resource usage

---

## 📊 Measuring Success

### Immediate Metrics
- [ ] Completed at least 2 use cases
- [ ] All tests passing
- [ ] Code follows Python/Kafka/Spark best practices
- [ ] Monitoring implemented

### Quality Metrics
- [ ] Proper error handling in all pipelines
- [ ] Comprehensive test coverage (>80%)
- [ ] Performance meets requirements
- [ ] Documentation complete

### Value Metrics
- [ ] Solved real data platform challenges
- [ ] Measurable time savings
- [ ] Improved pipeline reliability
- [ ] Enhanced performance

---

## 💡 Tips for Success

### 1. Start with Understanding
- Read existing pipeline code first
- Understand data flow and patterns
- Ask Bob to explain complex Spark operations
- Review Kafka configuration

### 2. Plan Your Approach
- Use todo lists for complex pipelines
- Break down into testable components
- Identify dependencies early
- Plan for error scenarios

### 3. Work Incrementally
- Build one component at a time
- Test each piece independently
- Verify with sample data
- Integrate gradually

### 4. Focus on Reliability
- Add comprehensive error handling
- Implement retry logic
- Include monitoring from the start
- Test failure scenarios

### 5. Optimize Wisely
- Profile before optimizing
- Measure improvements
- Document tuning decisions
- Balance performance and maintainability

---

## ✅ Completion Checklist

- [ ] Completed at least 2 RealDataTeam use cases
- [ ] Built or optimized stream processing pipelines
- [ ] Implemented data quality validation
- [ ] All code tested and working
- [ ] Monitoring and logging in place
- [ ] Documentation updated
- [ ] Demonstrated measurable value
- [ ] Comfortable using Bob for data platform work

---

## 🚀 Next Steps

### Immediate Actions
1. Commit your work to version control
2. Share learnings with the data engineering team
3. Identify next pipelines to build/optimize
4. Schedule follow-up sessions

### Ongoing Development
1. Use Bob daily for pipeline development
2. Apply patterns learned to other use cases
3. Share tips with team members
4. Build team best practices

### Continuous Improvement
1. Track time saved on pipeline development
2. Measure quality improvements
3. Monitor performance gains
4. Gather team feedback on Bob adoption

---

## 📚 Resources

- **RealDataTeam Documentation**: Internal wiki
- **Kafka Best Practices**: Apache Kafka documentation
- **Spark Optimization**: Spark performance tuning guide
- **Bob Resources**: See `resources/` directory
- **Support**: Data platform team channel

---

## 🎉 Congratulations!

You've completed the RealDataTeam bobathon! You now have the skills to:
- Build robust Kafka-based stream processing pipelines
- Implement comprehensive data quality validation
- Create real-time analytics with Spark
- Optimize performance for high-throughput systems
- Use Bob effectively for data platform development

**Remember:** The best way to master Bob for stream processing is to use it on real pipelines. Start with smaller optimizations, build confidence, and gradually tackle more complex use cases.

---

## 🌟 Bob Differentiators for Data Platforms

Throughout this lab, you experienced Bob's unique capabilities for data engineering:

### 1. **Literate Coding for Complex Pipelines**
Bob explained Kafka consumer patterns, Spark transformations, and streaming joins in plain language, accelerating your understanding of complex data flows.

### 2. **Multi-Mode Intelligence**
- **Ask Mode**: Understood Kafka/Spark concepts and best practices
- **Plan Mode**: Broke down complex pipeline development into steps
- **Code Mode**: Implemented production-ready streaming code

### 3. **Bob Findings for Data Quality**
Proactive analysis identified potential issues in stream processing code: missing error handling, inefficient Spark operations, and data validation gaps.

### 4. **Context Optimization**
Bob efficiently handled large pipeline codebases, understanding relationships between consumers, processors, and producers without hitting token limits.

### 5. **Intelligent Model Selection**
Bob automatically used faster models for simple config changes and more powerful models for complex Spark optimization—you didn't need to configure this.

### 6. **Enterprise Modernization**
While this lab focused on Python/Kafka/Spark, Bob excels at modernizing legacy data platforms, including Java-based systems and batch-to-streaming migrations.

---

**Questions?** Reach out to your facilitator or the data platform team!

**Feedback:** Please share your experience to help improve future bobathons for data engineering teams.
