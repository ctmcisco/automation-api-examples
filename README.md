# automation-api-examples

This repo provides full end to end examples and walkthroughs for the Pulumi Automation API. The Automation API is available in preview for `Go` and `Node.js` with support for [`C#`](https://github.com/pulumi/pulumi/compare/auto/dotnet) and [`Python`](https://github.com/pulumi/pulumi/compare/auto/python) under active development. 

Full docs for can be found here:
- [Go](https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/x/auto?tab=doc)
- [Node.js](https://www.pulumi.com/docs/reference/pkg/nodejs/pulumi/pulumi/x/automation/)
## Content

Take a look at our examples grouped by language.

### Go Examples

Example   | Description |
--------- | --------- |
[Git Repo](go/git_repo_program) | Use Automation API with a Pulumi program from a git repo. In this case a static S3 website from the [Pulumi examples repo](https://github.com/pulumi/examples/tree/master/aws-go-s3-folder).
[Inline Program](go/inline_program) | Use Automation API with an `inline` Pulumi program. Inline programs are self contained in a single `main.go` and support full debugging capabilities. In this demo we deploy the same static S3 website adapted from the [Pulumi examples repo](https://github.com/pulumi/examples/tree/master/aws-go-s3-folder).
[Local Program](go/local_program) | This example shows how to use Automation API with an existing traditional CLI-driven Pulumi program. We add an Automation API deployment program to our Fargate program that deploys a web service via a Fargate task behind a load balancer.
[Inline/Local Hybrid Program](go/inline_local_hybrid) | This example shows how to refactor your infrastructure to get the best of both worlds, a debuggable `inline` program that can still be driven by the Pulumi CLI for convenience (one off deployments, inspecting the stack, retrieving outputs, etc). In this example we deploy an S3 stacic website. The `automation/main.go` is fully debuggable, including the shared deployment function. The stack can also be managed via the CLI program in `cli/main.go`.
[Multi-Stack Orchestration](go/multi_stack_orchestration) | This example shows how to use Automation API to tame the complexity of multiple stacks with dependent stack outputs. We decompose our S3 static website into two stacks, one that manages the bucket, and another that manages the `index.html` file. Both of these are defined as inline programs, and are deployed and destroyed together via a single `main.go`
[Pulumi Over HTTP - Infra as RESTFUL resources](go/pulumi_over_http) | This application demonstrates how to run Automation API in an HTTP server to expose infrastructure as RESTful resources. In our case, we've defined and exposed a static website `site` that exposes all of the `CRUD` operations plus list. Users can hit our REST endpoint and create custom static websites by specifying the `content` field in the `POST` body. All of our infrastructure is defined in `inline` programs that are constructed and altered on the fly based on input parsed from user specified `POST` bodies. 
[Database Migration](go/database_migration) | This example provisions an AWS Aurora SQL database and executes a database "migration" using the resulting connection info. This migration creates a table, inserts a few rows of data, and reads the data back to verify the setup. This is all done in a single program using an `inline` Pulumi program. With Automation API you can orchestrate complex workflows that go beyond infrastructure provisioning and into application management, database setup, etc.

### Node.js Examples

Example  | Toolchain | Description |
--------- | --------- | --------- |
[Inline Program](nodejs/inlineProgram-tsnode) | Typescript + ts-node | Use Automation API with an `inline` Pulumi program. Inline programs are self contained in a single `index.ts` and support full debugging capabilities. In this demo we deploy the same static S3 website adapted from the [Pulumi examples repo](https://github.com/pulumi/examples/tree/master/aws-ts-s3-folder). This example uses `typescript` with `ts-node` as an execution environment.
[Inline Program](nodejs/inlineProgram-ts) | Typescript (tsc) + node | Use Automation API with an `inline` Pulumi program. Inline programs are self contained in a single `index.ts` and support full debugging capabilities. In this demo we deploy the same static S3 website adapted from the [Pulumi examples repo](https://github.com/pulumi/examples/tree/master/aws-ts-s3-folder). This example uses `typescript` compiled into `javascript` via `tsc` and executed via `node`.
[Inline Program](nodejs/inlineProgram-js) | Javascript + node | Use Automation API with an `inline` Pulumi program. Inline programs are self contained in a single `index.js` and support full debugging capabilities. In this demo we deploy the same static S3 website adapted from the [Pulumi examples repo](https://github.com/pulumi/examples/tree/master/aws-js-s3-folder). This example uses plain `javascript` executed via `node`.
[Local Program](nodejs/localProgram-tsnode) | Typescript + ts-node | This example shows how to use Automation API with an existing traditional CLI-driven Pulumi program. We add an Automation API deployment program to our existing CLI-driven S3 website program. This example uses `typescript` with `ts-node` as an execution environment.
[Cross-Language Program](nodejs/crossLanguage-tsnode) | Typescript + ts-node | This example shows how to use Automation API in `typescript` with an existing traditional CLI-driven Pulumi program written in a __different__ language, in this case `go`. We add an Automation API deployment program to our Fargate program that deploys a web service via a Fargate task behind a load balancer. This automation program uses `typescript` with `ts-node` as an execution environment.
[Database Migration](nodejs/databaseMigration-ts) | Typescript (tsc) + node | This example provisions an AWS Aurora SQL database and executes a database "migration" using the resulting connection info. This migration creates a table, inserts a few rows of data, and reads the data back to verify the setup. This is all done in a single program using an `inline` Pulumi program. With Automation API you can orchestrate complex workflows that go beyond infrastructure provisioning and into application management, database setup, etc.