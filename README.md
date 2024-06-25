# Wordpress Helm Chart

Before using the chart the custom Docker images need to be built and uploaded to a registry.

The wordpress image should be configuired to accept environment variables into wp-config.php.

# Usage

replace values in values.yaml with correct image values and other required secrets and then use helm install command.