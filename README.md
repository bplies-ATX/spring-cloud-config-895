# spring-cloud-config-895
Demo of #895 https://github.com/spring-cloud/spring-cloud-config/issues/895

This demo makes use of the existing unit test resource files.

Adjust `src/main/resources/application.yml` to point to a local copy of spring-cloud-config's test encrypt-repo.  
Otherwise you can use a different JKS with some other repo.

Execute `./gradlew bootRun`

In a terminal invoke: `curl http://user:test@localhost:8888/foo/encrypt`

Notice the secret was not decrypted
```"config.foo":"AQCohs2V6P8/UiG6a4TF/CZTCBdt5Q7wvNvcyf6vs2ByK2ZYSM77Nu0sOAduxUpMbVwJ/syecmkIXR+hU3EfT2uqPieA7/v5n33ppqIQ9JAt5JggdYIGe+wX25zU3DTXOOJdAAMzNX+zjOVyCh0QtmJf/kFslg6NqQq0E+kSg3zBi3AnkKj5BLnLIxkjxzKA4mnDXpSm7ekLZZP2iQSYSW/82AC7UOLLzTqwInMI3tJLW1e9Ne+LDsjmSxA+nkK9zhidtXPwb/SPaNF74cJCEf9mgzzKYwJlwqChLzJt8UQ1jHwRc8B6FufmizUHSp27nxdtVB4HMqh3nNsMCy137Ces58T09ZS/y/cYNRxcFbp78MHFHUqAgbC0B/p5t6h4XbQ="
```

CTRL+C to kill the process

Adjust `build.gradle` and swap commented out blocks for `cloudVersion` and to use `Camden.SR2` instead of `Dalston.SR5`

Execute `./gradlew bootRun`

In a terminal invoke: `curl http://user:test@localhost:8888/foo/encrypt`

Notice the secret used to be decrypted
```"config.foo":"foo"```
