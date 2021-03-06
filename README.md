# ECS Container Definition

This module make it easier to create and standardize Container Definitions for your ECS Services.
Official documentation for the Task's Container Definitions can be found [here](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html#standard_container_definition_params).

##### Example

      provider aws {
        region = "us-east-1"
      }

      module task_def {
        source = "ecs-container-definition"

        name = "api-gateway"

        image         = "nginx"
        image_version = "lastest"

        command = ["foo"]
        entrypoint = ["bar"]

        cpu    = 128
        memory = 512

        environment_variables = [{
          name  = "SERVER_PORT",
          value = 8181
        }]

        port_mappings = [
          { container_port = 8181, host_port = 8181 }
        ]

        cloudwatch_log_group = "my-example-log-group"
      }
