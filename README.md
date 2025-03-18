1. Build project
   `yarn build`
2. CREATE A NEW BUCKET FOR BRANCH (if not on dev)
   `aws s3api create-bucket --bucket {{BUCKET}} --region {{REGION}}`
3. CD TO DIST
   `cd dist`
4. ZIP BUILD DIRECTORY
   `zip -r dist.zip .`
5. SYNC DIST DIRECTORY WITH S3 BUCKET
   `aws s3 cp dist.zip s3://{{BUCKET}}/latest/dist.zip`
6. TRIGGER A DEPLOYMENT
   `aws amplify start-deployment --app-id {{APP ID}} --branch-name staging --source-url s3://{{BUCKET}}/latest/dist.zip`
