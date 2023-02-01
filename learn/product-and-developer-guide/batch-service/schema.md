# Schema

**Cassandra Database**

**ER Diagram**

![Sunbird Courses](../../../.gitbook/assets/sunbird\_courses.png)

Following KeySpace and Tables were being used:

```
CREATE KEYSPACE sunbird_courses WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '1'}  AND durable_writes = true;

CREATE TYPE sunbird_courses.question (
    id text,
    assess_ts timestamp,
    max_score double,
    score double,
    type text,
    title text,
    resvalues list<frozen<map<text, text>>>,
    params list<frozen<map<text, text>>>,
    description text,
    duration decimal
);

CREATE TABLE sunbird_courses.content_consumption (
    userid text,
    contentid text,
    batchid text,
    courseid text,
    completedcount int,
    contentversion text,
    datetime timestamp,
    grade text,
    lastaccesstime text,
    lastcompletedtime text,
    lastupdatedtime text,
    progress int,
    result text,
    score text,
    status int,
    viewcount int,
    PRIMARY KEY (userid, contentid, batchid, courseid)
) WITH CLUSTERING ORDER BY (contentid ASC, batchid ASC, courseid ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';
CREATE INDEX inx_cc_status ON sunbird_courses.content_consumption (status);

CREATE TABLE sunbird_courses.user_activity_agg (
    activity_type text,
    activity_id text,
    user_id text,
    context_id text,
    agg map<text, int>,
    agg_details list<text>,
    agg_last_updated map<text, timestamp>,
    aggregates map<text, double>,
    PRIMARY KEY ((activity_type, activity_id, user_id), context_id)
) WITH CLUSTERING ORDER BY (context_id ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';

CREATE TABLE sunbird_courses.report_user_enrolments (
    userid text,
    courseid text,
    batchid text,
    "active" boolean,
    addedby text,
    certificates list<frozen<map<text, text>>>,
    certstatus int,
    completedon timestamp,
    completionpercentage int,
    contentstatus map<text, int>,
    datetime timestamp,
    enrolled_date timestamp,
    enrolleddate text,
    issued_certificates list<frozen<map<text, text>>>,
    lastreadcontentid text,
    lastreadcontentstatus int,
    progress int,
    status int,
    PRIMARY KEY (userid, courseid, batchid)
) WITH CLUSTERING ORDER BY (courseid ASC, batchid ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';

CREATE TABLE sunbird_courses.assessment_aggregator (
    user_id text,
    course_id text,
    batch_id text,
    content_id text,
    attempt_id text,
    created_on timestamp,
    grand_total text,
    last_attempted_on timestamp,
    question list<frozen<question>>,
    total_max_score double,
    total_score double,
    updated_on timestamp,
    PRIMARY KEY ((user_id, course_id), batch_id, content_id, attempt_id)
) WITH CLUSTERING ORDER BY (batch_id ASC, content_id ASC, attempt_id ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';
CREATE INDEX assessment_aggregator_attempted_on_idx ON sunbird_courses.assessment_aggregator (last_attempted_on);

CREATE TABLE sunbird_courses.course_batch (
    courseid text,
    batchid text,
    cert_templates map<text, frozen<map<text, text>>>,
    created_date timestamp,
    createdby text,
    createddate text,
    createdfor list<text>,
    description text,
    end_date timestamp,
    enddate text,
    enrollment_enddate timestamp,
    enrollmentenddate text,
    enrollmenttype text,
    mentors list<text>,
    name text,
    start_date timestamp,
    startdate text,
    status int,
    tandc boolean,
    updated_date timestamp,
    updateddate text,
    PRIMARY KEY (courseid, batchid)
) WITH CLUSTERING ORDER BY (batchid ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';
CREATE TRIGGER course_batch_trigger ON sunbird_courses.course_batch USING 'org.sunbird.cassandra.triggers.TransactionEventTrigger';

CREATE TABLE sunbird_courses.user_enrolments (
    userid text,
    courseid text,
    batchid text,
    "active" boolean,
    addedby text,
    certificates list<frozen<map<text, text>>>,
    certstatus int,
    completedon timestamp,
    completionpercentage int,
    contentstatus map<text, int>,
    datetime timestamp,
    enrolled_date timestamp,
    enrolleddate text,
    issued_certificates list<frozen<map<text, text>>>,
    lastreadcontentid text,
    lastreadcontentstatus int,
    progress int,
    status int,
    PRIMARY KEY (userid, courseid, batchid)
) WITH CLUSTERING ORDER BY (courseid ASC, batchid ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';

CREATE TABLE sunbird_courses.bulk_upload_process (
    id text PRIMARY KEY,
    data text,
    failureresult text,
    objecttype text,
    processendtime text,
    processstarttime text,
    status int,
    successresult text,
    uploadedby text,
    uploadeddate text
) WITH bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';
CREATE INDEX inx_bup_status ON sunbird_courses.bulk_upload_process (status);

CREATE TABLE sunbird_courses.user_content_consumption (
    userid text,
    courseid text,
    batchid text,
    contentid text,
    completedcount int,
    datetime timestamp,
    last_access_time timestamp,
    last_completed_time timestamp,
    last_updated_time timestamp,
    lastaccesstime text,
    lastcompletedtime text,
    lastupdatedtime text,
    progress int,
    status int,
    viewcount int,
    PRIMARY KEY (userid, courseid, batchid, contentid)
) WITH CLUSTERING ORDER BY (courseid ASC, batchid ASC, contentid ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';

CREATE TABLE sunbird_courses.assessment_aggregator_temp (
    course_id text,
    batch_id text,
    user_id text,
    content_id text,
    attempt_id text,
    created_on timestamp,
    grand_total text,
    last_attempted_on timestamp,
    question list<frozen<question>>,
    total_max_score double,
    total_score double,
    updated_on timestamp,
    PRIMARY KEY (course_id, batch_id, user_id, content_id, attempt_id)
) WITH CLUSTERING ORDER BY (batch_id ASC, user_id ASC, content_id ASC, attempt_id ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';

CREATE TABLE sunbird_courses.user_courses (
    batchid text,
    userid text,
    "active" boolean,
    addedby text,
    certificates list<frozen<map<text, text>>>,
    completedon timestamp,
    completionpercentage int,
    contentstatus map<text, int>,
    courseid text,
    datetime timestamp,
    delta text,
    enrolleddate text,
    grade text,
    lastreadcontentid text,
    lastreadcontentstatus int,
    progress int,
    status int,
    PRIMARY KEY (batchid, userid)
) WITH CLUSTERING ORDER BY (userid ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';
CREATE INDEX inx_ucs_status ON sunbird_courses.user_courses (status);
CREATE TRIGGER batch_enrollment_trigger ON sunbird_courses.user_courses USING 'org.sunbird.cassandra.triggers.TransactionEventTrigger';
```

**Elastic Search**

Following indexes were being used:

<details>

<summary>course-batch</summary>

```
{
    "settings": {
        "index": {
            "number_of_shards": "5",
            "number_of_replicas": "1",
            "analysis": {
                "filter": {
                    "mynGram": {
                        "token_chars": [
                            "letter",
                            "digit",
                            "whitespace",
                            "punctuation",
                            "symbol"
                        ],
                        "min_gram": "1",
                        "type": "ngram",
                        "max_gram": "20"
                    }
                },
                "analyzer": {
                    "cs_index_analyzer": {
                        "filter": [
                            "lowercase",
                            "mynGram"
                        ],
                        "type": "custom",
                        "tokenizer": "standard"
                    },
                    "keylower": {
                        "filter": "lowercase",
                        "type": "custom",
                        "tokenizer": "keyword"
                    },
                    "cs_search_analyzer": {
                        "filter": [
                            "lowercase",
                            "standard"
                        ],
                        "type": "custom",
                        "tokenizer": "standard"
                    }
                }
            }
        }
    }
}
```

</details>

<details>

<summary>course-batch-mapping</summary>

```
{
    "dynamic": false,
    "properties": {
        "all_fields": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower"
                }
            },
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer"
        },
        "batchId": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "courseId": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "createdBy": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "createdDate": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "createdFor": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "description": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "endDate": {
            "type": "date",
            "fields": {
                "raw": {
                    "type": "date"
                }
            }
        },
         "enrollmentEndDate": {
           "type": "date",
           "fields": {
              "raw":  {
                  "type": "date"
               }
           }
        },
        "enrollmentType": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "id": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "identifier": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "mentors": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "name": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "startDate": {
            "type": "date",
            "fields": {
                "raw": {
                    "type": "date"
                }
            }
        },
        "status": {
            "type": "long",
            "fields": {
                "raw": {
                    "type": "long"
                }
            }
        },
        "updatedDate": {
            "type": "text",
            "fields": {
                "raw": {
                    "type": "text",
                    "analyzer": "keylower",
                    "fielddata": true
                }
            },
            "copy_to": [
                "all_fields"
            ],
            "analyzer": "cs_index_analyzer",
            "search_analyzer": "cs_search_analyzer",
            "fielddata": true
        },
        "participantCount": {
            "type": "long",
            "fields": {
                "raw": {
                    "type": "long"
                }
            }
        },
        "completedCount": {
            "type": "long",
            "fields": {
                "raw": {
                    "type": "long"
                }
            }
        },
        "reportUpdatedOn": {
            "type": "date",
            "fields": {
                "raw": {
                    "type": "date"
                }
            }
        }
    }
}
```

</details>
