# MVF Developer Tests
## S3 API

Thanks for your interest in a developer role at MVF.

We have a simple project which we would like you to take a look at in your own time.

You can spend as much or as little time on it as you wish, but if we have asked you to take a look at this, we would usually expect to receive a response in a 3-4 days.

The task is to build a restful API based on data we have in our AWS S3 bucket. You can attempt this in any language you are familiar with - see it as a opportunity to showcase the skills you have which are relevant for the role you want.

How would you implement this? Fork our repo and let us see your ideas!

### Challenge
Build an API to expose the data in our S3 bucket.

We have a public S3 bucket set up at: https://mvf-devtest-s3api.s3-eu-west-1.amazonaws.com/

This contains a number of json files named with the pattern "<guid>.json", e.g.:
    9f9131f0-4267-4293-8970-bb41a91c20c4.json

Each guid (globally unique identifier) represents a customer with access to the API and the data listed within the file represent the accounts they have access to, each of these accounts also being identified by a guid.

Please build a Restful API to expose the data according to the following rules:

  1. Users with knowledge of a customer guid may search the json file named with the guid and may have access to all it's contents.
  2. Users with knowledge of an account guid may have access to any of the data for that account, but not anything else within the same file.
  3. The request should include an Authentication HTTP header in the format: "Authentication: custom-digest <unixtime>:<digest>"

    > <unixtime> is the unix timestamp of the current time in UTC, within the last 15 minutes, e.g. 1499793194
    >
    > <digest> is generated by calculating the SHA256 hash of "<unixtime><http verb><uri path><secret key>"
    >
    > <http verb> being GET, PUT, POST, DELETE, PATCH as appropriate
    >
    > <uri path> is for example /api/v1/customer/<customer guid>/list
    >
    > <secret> is the API secret key, in this case: "8acfab26-1efb-4d3f-9701-bb4743d62d71"


### Deliverables

Please build at least the first 3 endpoints and then attempt the authentication sub-task.

We recognise that all of these items may not be possible in the time allotted, so
please document which of these is delivered in your submission.

1. Customer Accounts
    /api/v1/customer/<customer guid>/accounts
        List the account ids (guid) of all accounts for the customer

2. Account
    /api/v1/account/<account guid>
        Return all the details of the account specified

3. Account Field
    /api/v1/account/<account guid>/<field>
        Return the field requested for the account specified

4. Authentication
    Please add authentication at this stage

5. Additional Ideas
    If you have ideas for endpoints not specified, feel free to implement and describe in your submission

    /api/v1/customer/<customer guid>/accounts/?lastname=Smith
    >   Return the account ids for all accounts for the customer with a last name of "Smith"

    /api/v1/customer/<customer guid>/accounts/?<design the query required>
    >   Return the account ids for all accounts for the customer with an email ending @domain.com

    /api/v1/customer/<customer guid>/accounts/?<design the query required>
    >   Return the account ids for all accounts for the customer with a negative balance

    /api/v1/customer/<customer guid>/accounts/?<design the query required>
    >   Return the account ids for all accounts for the customer with a balance between <minimum> and <maximum>.

    /api/v1/customer/<customer guid>/accounts/?<design the query required>
    >   Return the account ids for the smallest set of accounts with a total combined balance bewteen <minimum> and <maximum>.

    /api/v1/customer/<customer guid>/accounts/?<any query>&<sort by>
    >   Design a sorting option and implement across appropriate endpoints

---
### MVF
Do you want to work with the Smartest Tech and the Sharpest Minds? Apply at: http://www.mvfglobal.com/vacancies