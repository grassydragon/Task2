# Task2

The `godot/.gitlab-ci.yml` configuration file can be used to build, test and zip the linux binary from the `master` branch of the Godot repository.

The maximum artifact size in GitLab should be increased because the size of the linux binary is close to 1 Gb.

The runner can be registered with the command `sudo docker exec -i task2_runner_1 gitlab-runner register`. It is important to check in GitLab that the runner is able to run pipelines without tags.

To allow executors inside the runner to be able to communicate with GitLab the `network_mode = "gitlab-network"` parameter should be added in the `gitlab-runner/config.toml` file. This can be done in three ways:
- by adding the `network_mode = "gitlab-network"` parameter after the runner is registered,
- by supplying the `--docker-network-mode gitlab-network` parameter to the register command,
- by supplying the `--template-config template-config.toml` parameter to the register command and adding the `network_mode = "gitlab-network"` parameter in the `template-config.toml` file.

In the result the `gitlab-runner/config.toml` file should have the following structure:
```
...
[[runners]]
  ...
  [runners.docker]
    ...
    network_mode = "gitlab-network"
```
