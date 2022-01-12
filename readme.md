# Coding challenge II: Save our deploy train

## Problematic
The engineering team is shipping features and improvements many times per day, all those deployments need to be well orchestrated.

Each developer can ship his changes to a test environment before going to prod, to ensure all is working as expected.

Imagine a case where two developers end two different features at the same, one of them will wait until the other mate ends testing his deployed code then he can pursue deploying his feature, this can lead to train traffic jam sometimes.

## Expected solution
Using ansible and docker-compose, pop-up 2 containers distributed as following:

One nginx container (this will hosts your 3envs vhosts files)
One php container
Example

test1.testycan.shop
test2.testycan.shop
test3.testycan.shop

## Solution explanation 

By integrating CI / CD into their day-to-day work, developers can achieve two important goals: first, the ability to run test suites on a server other than the production computer so that the engineer can continue to develop new functionality without distractions, and second, the ability to send builds to your customer or QA engineer to demonstrate / test / analyze a new feature, even if they cannot build and run the project on their own computers.

I used two external services to do this. One is GitHub for CI (using Actions) and source control, and the second is Docker Hub for hosting our Docker images. I also used Ansible for configuring the remote host.

