# Run ECS task

Run a given ECS task, wait for result and exits accordingly to the task result. The original motivation to create this script was to run tasks on ECS during Continuous integration pipelines.

## Installation

- Install and configure [AWS CLI version 2.0 or higher.](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- Install the script:
```bash
curl https://raw.githubusercontent.com/fretadao/run-ecs-task/master/run-ecs-task -o ./run-ecs-task
chmod +x run-ecs-task
```

## Usage
```bash
Script for running ECS tasks, wait for result and exits accordingly to the task result.

Required arguments:
    -c | --cluster             Name of ECS cluster
    -d | --task-definition     Name of task definition to run
    -m | --command             Command to execute on the task deploy(overrides image CMD). Command args must be separated by comma, eg.:  "sh,echo,\$FOO"
    -n | --container-name      Container name defined by the task
    -r | --region              Cluster region
    -l | --launch-type         Task launch type, supported values: "EC2", "FARGATE"
    --capacity-provider        Capacity provider strategy in the format: '[{"capacityProvider": "Name", "weight": value, "base": value}, ...]'. When capacity provider is specified,
                               launch-type must be empty

Optional arguments:
    --subnets                  Subnets IDS for the task execution, supported only if the task network mode is "awsvpc". IDS must be separated by comma, eg.: "subnet-id1,subnet-id2"
    --security-groups          Security groups IDS for the task execution, supported only if the task network mode is "awsvpc". IDS must be separated by comma, eg.: "sg-id1,sg-id2"
    -v | --version             Display script version
```
