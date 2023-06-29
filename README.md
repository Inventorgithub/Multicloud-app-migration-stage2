# Stage 2 of strategic Multicloud data/app migration!

# Luxxy COVID Testing System

This repository contains code for the Luxxy COVID Testing System, which is a web application built with Python. It allows users to manage COVID testing records and generate PDF reports.

## Deployment

The application is deployed using Docker and Kubernetes. It consists of a backend server written in Python and a MySQL database for storing the testing records.

### Prerequisites

- Docker
- Kubernetes cluster

### Deployment Steps

1. Build the Docker image:

```bash
docker build -t luxxy-covid-testing-system .
```

2. Deploy the application to Kubernetes:

```bash
kubectl apply -f deployment.yaml
```

3. Expose the service:

```bash
kubectl apply -f service.yaml
```

### Environment Variables

The Luxxy COVID Testing System requires the following environment variables to be set:

- `AWS_BUCKET`: The name of the AWS S3 bucket used for storing PDF reports.
- `S3_ACCESS_KEY`: AWS access key for accessing the S3 bucket.
- `S3_SECRET_ACCESS_KEY`: AWS secret access key for accessing the S3 bucket.
- `DB_HOST_NAME`: The hostname or IP address of the MySQL database.
- `DB_USER`: The username for the MySQL database.
- `DB_PASSWORD`: The password for the MySQL database.
- `DB_NAME`: The name of the MySQL database.
- `DB_PORT`: The port number for the MySQL database.

Make sure to set these environment variables before deploying the application.

### Database Setup

The Luxxy COVID Testing System requires a MySQL database with the following table:

```sql
CREATE TABLE `records` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `guest_name` varchar(200) NOT NULL,
  `home_country` varchar(200) DEFAULT NULL,
  `testing_type` varchar(200) DEFAULT NULL,
  `testing_result` varchar(200) DEFAULT NULL,
  `pdf` varchar(200) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=latin1;
```

Please ensure that the database is set up with this table before deploying the application.

## Usage

Once the Luxxy COVID Testing System is deployed and running, you can access it using the assigned IP or domain.

1. Open a web browser and enter the application URL.
2. Use the provided features to manage COVID testing records, including adding new records, updating existing records, and generating PDF reports.

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvement, please feel free to open an issue or submit a pull request.
