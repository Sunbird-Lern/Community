# Functional Configurations

```
sunbird_username_num_digits=4
download_link_expiry_timeout=300
sunbird_default_country_code=+91
sunbird_encryption_key=SunBird
sunbird_encryption=ON
sunbird_otp_allowed_attempt=2
```

### Bulk Upload Config

```
#size of bulk upload data is 1001 including header in csv file
sunbird_user_bulk_upload_size=1001
bulk_upload_org_data_size=300
# Bulk upload file max size in MB
file_upload_max_size=10
```

### Batch Service Config

```
# Batch size for cassandra batch operation
cassandra_write_batch_size=100
```

### OTP Config

```
sunbird_otp_expiration=1800
sunbird_otp_length=6
sunbird_otp_hour_rate_limit=5
sunbird_otp_day_rate_limit=20
```

### Other Config

```
managed_user_limit=30
sunbird_api_request_lower_case_fields=source,externalId,userName,provider,loginId,email,prevUsedEmail
sunbird_rate_limit_enabled=true
sunbird_health_check_enable=true
sunbird_sync_read_wait_time=1500
sunbird_gzip_size_threshold=262144
sunbird_fuzzy_search_threshold=0.5
ekstep_authorization=
```
