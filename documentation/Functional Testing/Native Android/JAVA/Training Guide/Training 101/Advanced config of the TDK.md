Make sure you have read the [option list](https://github.com/TestArmada/flank#configure-flank) about Flank configurations.

Then, in the `config.properties` in your root directory, customize your own properties.

- The essential part of the config is `device`, will combine with device name, version, orientation and locale, e.g.:

    ```bash
    devices=model:Nexus5X;version:23;orientation:portrait;locale:en,\
            model:Nexus6P;version:24,\
            model:NexusLowRes;version:26
    ```

- Another important feature is shard, the TDK help you shard proper tests to VMs, three options are recommended to be set
    ```
    shard-timeout: Timeout in minutes for each shard. 5 minutes by default.
    shard-duration: Duration in seconds for each shard

    numShards: Number of shards to split the tests across. Unused by default.
    ```

    learn more at [Configure Flank](https://github.com/TestArmada/flank#configure-flank).

- If you need more logs when debugging, set `debug-prints=true` default is `false`.


