Research Public API

1. GitHub (API)

Research the GitHub API for use in development projects.

- [GET] `/orgs/{org}/actions/variables `
- [POST] `/orgs/{org}/actions/variables*]`
- [GET] `/orgs/{org}/actions/variables/{name}*]`
- [PATCH] `/orgs/{org}/actions/variables/{name}*]`
- [DELETE] `/orgs/{org}/actions/variables/{name}]`

- [x]  Authentication
    
    For authentication, GitHub uses a requests header to get  access token 
    
    example:
    
    ```
    jobs:
      create_issue:
        runs-on: ubuntu-latest
        permissions:
          issues: write
        steps:
          - name: Create issue using REST API
            run: |
              curl --request POST \
              --url https://api.github.com/repos/${{ github.repository }}/issues \
              --header 'authorization: Bearer ${{ secrets.GITHUB_TOKEN }}' \
              --header 'content-type: application/json' \
              --data '{
                "title": "Automated issue for commit: ${{ github.sha }}",
                "body": "This issue was automatically created by the GitHub Action workflow **${{ github.workflow }}**. \n\n The commit hash was: _${{ github.sha }}_."
                }' \
              --fail
    ```
    

- [x]  HTTP methods usage
    
    For API design GitHub uses the same URL but according to the different operations
    
    they have defined different methods. 
    
- [x]  Naming Conventions
    
    For naming conventions especially root resources they kept the name in the plural (if there are multiple resources) and it is also a noun phrase. It does not matter if the user intended to get/post a single resource or a whole resource.
    
    but for a single resource in the (GET/PATCH) method, they just added dynamic parameters like /”root_resoucename/{singleresource_id}. 
    
- [x]  GitHub API versioning

`$ curl --header "X-GitHub-Api-Version:2022-11-28" https://api.github.com/zen`

To keep version control Github uses a header  named “x-api-version” where they mention version of the API 

- [x]  GitHub uses specific status codes
    
    Following status codes are used by GitHub In their API status code
    
     GET 200(success)
    
     POST 201(success)
    
     PATCH 204 (success)
    
     DELETE 204 (success)
    
1. Stripe(API)

 Research the Stripe API for use in development projects.

- [x]  Authentication
    
    Stripe uses an API key as auth token whenever any request comes to Stripe API it validate through
    
    that API key and it is a private key. which Stripe provide to their user to access their API and usually it looks to request headers for that access token 
    
- [x]  HTTP methods usage
    
    For API design Stripe follow uses the same URL but according to the different operations
    
    they have defined different methods. like (GET, POST, PUT, PATCH, etc).
    
- [x]  Naming Conventions
    
    Stripe uses the root resource name in the plural for both get and post requests and used a specific id that to get to a specific resource
    
    to get a single resource
    
    1. Create Payment Intent:
        - Request URL: **`POST https://api.stripe.com/v1/payment_intents`**
    2. Retrieve Payment Intent:
        - Request URL: **`GET https://api.stripe.com/v1/payment_intents/:id`**
- [x]  Stripe API versioning

To keep version control Stripe designs their API url such a way that users/clients can understand by seeing their URL. In URL, they mention their API version like “base_url”/v1”( here v for version).

curl https://api.stripe.com/v1/customers/cu_19YMK02eZvKYlo2Cvcb2J41W \
-u sk_test_4eC39HqLyjWDarjtT1zdp7dc: \
-H "Stripe-Account: acct_1032D82eZvKYlo2C" \
-G

- [x]  Stripe uses specific status codes
    
    Following status codes are used by Stripe In their API status code
    
    | 200 - OK | Everything worked as expected. |
    | --- | --- |
    | 400 - Bad Request | The request was unacceptable, often due to missing a required parameter. |
    | 401 - Unauthorized | No valid API key was provided. |
    | 402 - Request Failed | The parameters were valid but the request failed. |
    | 403 - Forbidden | The API key doesn't have permission to perform the request. |
    | 404 - Not Found | The requested resource doesn't exist. |
    | 409 - Conflict | The request conflicts with another request (perhaps due to using the same idempotent key). |
    | 429 - Too Many Requests | Too many requests hit the API too quickly. We recommend an exponential backoff of your requests. |
    | 500, 502, 503, 504 - Server Errors | Something went wrong on Stripe's end. (These are rare.) |