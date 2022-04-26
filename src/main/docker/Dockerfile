FROM public.ecr.aws/lambda/java:latest

# Copy function code and runtime dependencies from Maven layout
COPY classes ${LAMBDA_TASK_ROOT}
COPY *.jar ${LAMBDA_TASK_ROOT}/lib/

# Set the CMD to your handler (could also be done as a parameter override outside of the Dockerfile)
CMD [ "org.playground.lambda.Handler::handleRequest" ]
