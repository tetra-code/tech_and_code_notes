# AWS S3

## IAM policies
identy based policies. Can specify what actions are allowed on waht AWS resources. These are attached to IAM users, groups, or roles. Written in JSON using AWS access policy language. The *principal* element is not required in the JSON. 

it is used for S3 policy rather than bucket policy

Use this if you need control access to AWS services other than S3, numerous S3 buckets with different permission requirements, or prefer to keep the access control policies in the IAM layer

## S3 Bucket policy
resouce based policies, also use AWS access policy langauge (also JSON). Attached directly to S3 bucket. This requires a *principal* element that specifies the specific user we wnat to assign this to. also *resource* element which speicifes which bucket and *action* element that specfies what to do with the hbucket

Use this if you want a simple way to grant *cross-account* access to your S3 environment wihtout IAM roels, prefer to keep the access control policies in the S3 layer


## Access Control List or ACL
Legacy access control mechanisms that precedes IAM. AWS doesn't recommend this, so use either IAM or S3 bucket policy. But if you do use this, it can be attached to a bucket or to object level. Limited options for grantees and permissions. Doesn't use AWS access policy langauge


1. decision starts at deny
2. evaluate all policies
3. if explicit deny final deny
4. otherwise check allow
5. if explicit allow, final decision is allow.
6. Otherwise final deny


To allow bucket access
1. unblock public access. IF you have this blocked and try to open the object URL, you'll get access denied message

Once enabled, you get edit the access control list. Check whether tghe ACL is on bucket level or object level. IF you want to check only a single object, no need to enable on the bucket level. Go  to the object level ACL 