AWS:

    logs not getting generated for lambda:
        lambda function ni entha trigger chesina logs raavatle ante lambda don't have required permissions to create log group and log streams.

    403 while accesssing object in s3 while hosting:
        disable public access
        add bucket policy to have required permissions

        if you still face the 403 error then there must be account level block public access which basically overrides the bucket level permissions.

    requests blocks at load balancer level with waf rate limiting
        if you have cloudfront in place and it's re-directing requests to load balancer then alb waf will block the cloudfront requests after certain number of requests.

    layer for python dependencies
        we should add all dependecies inside python folder, otherwise it won't work
    
    ami not found error
        use $(aws ssm get-parameter) command to get the proper ami id

    s3 state backend fails with sso new profile
        https://github.com/hashicorp/terraform-provider-aws/issues/28263#issuecomment-1397004214

    ingress won't be created
        with wrong version
        if we don't specify ingressClass
    
    you can't create service account and attach it to pod until you enable OIDC -> eksctl utils associate-iam-oidc-provider --cluster ${CLUSTER_NAME} --approve
    
    something goes wrong with k8s object, always describe it.

    Error: Post "http://localhost/api/v1/namespaces/kube-system/serviceaccounts": dial tcp 127.0.0.1:80: connect: connection refused  -> You should have Kubernetes provider setup using host, certificate, token otherwise it will try to connect to localhost cluster and it will fail.

    failed to fetch VPC ID from instance metadata: EC2MetadataError: failed to make EC2Metadata request  ->  Ec2 instance metadata was disabled. make it enable to work properly.

    RDS blue green deployment:
        It needs too many permissions, even chatgpt didn't helped.
        It got green for few rds services and red for remaining even though we use same parameter group for both. It could be because of cluster settings.
    

Postgres Error Resolved:

    colima Stop
    brew services stop  postgresql@14
    sudo lsof -i:5432
    kill pid
    colima start
    docker rm postgresdb
    docker run command
    psql command 