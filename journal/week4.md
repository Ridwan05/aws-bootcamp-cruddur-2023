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
  export PROD_CONNECTION_URL="postgresql://root:Khadijah74@cruddur-db-instance.ci48gurczxnm.us-east-1.rds.amazonaws.com:5432/cruddur"
  gp env  PROD_CONNECTION_URL="postgresql://rroot:Khadijah74@cruddur-db-instance.ci48gurczxnm.us-east-1.rds.amazonaws.com:5432/cruddur"

  chmod u+x bin/db-connect
  chmod u+x bin/db-create
  chmod u+x bin/db-drop
  chmod u+x bin/db-schema-load
  chmod u+x bin/db-seed
  chmod u+x bin/db-sessions
  chmod u+x bin/db-setup
  chmod u+x bin/rds-update-sg-rule

  pip install -r requirements.txt

  GITPOD_IP=$(curl ifconfig.me)

export DB_SG_ID="sg-06bd0d82272a02c12"
gp env DB_SG_ID="sg-06bd0d82272a02c12"
export DB_SG_RULE_ID="sgr-082495c1abe52e9d7"
gp env DB_SG_RULE_ID="sgr-082495c1abe52e9d7"


arn:aws:lambda:us-east-1:898466741470:layer:psycopg2-py38:2