# Week 4 — Postgres and RDS

aws rds create-db-instance \
  --db-instance-identifier cruddur-db-instance \
  --db-instance-class db.t3.micro \
  --engine postgres \
  --engine-version  14.6 \
  --master-username root \
  --master-user-password ***** \
  --allocated-storage 20 \
  --availability-zone us-east-1b \
  --backup-retention-period 0 \
  --port 5432 \
  --no-multi-az \
  --db-name cruddur \
  --storage-type gp2 \
  --publicly-accessible \
  --storage-encrypted \
  --enable-performance-insights \
  --performance-insights-retention-period 7 \
  --no-deletion-protection

  psql -Upostgres --host localhost
  CREATE database cruddur;
  psql cruddur < db/schema.sql -h localhost -U postgres

  export CONNECTION_URL="postgresql://postgres:password@localhost:5432/cruddur"
  gp env  CONNECTION_URL="postgresql://postgres:password@localhost:5432/cruddur"
  export PROD_CONNECTION_URL="postgresql://cruddurroot:Khadijah74@cruddur-db-instance.ci48gurczxnm.us-east-1.rds.amazonaws.com:5432/cruddur"
  gp env  PROD_CONNECTION_URL="postgresql://cruddurroot:Khadijah74@cruddur-db-instance.ci48gurczxnm.us-east-1.rds.amazonaws.com:5432/cruddur"