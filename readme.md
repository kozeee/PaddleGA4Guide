# For the full guide, see the main branch

---

## What is this?
This branch is a specific implementation in which the user requires the ability to redirect their buyers after successful checkout

## Why do we need this?
Currently paddle offers the ability to redirect buyers (this can be set through paddle.js, or in the dashboard). This redirect currently races our events and cant prevent information from being properly pushed to tag manager/analytics

## How are we fixing it?
Instead of pushing the datalayer from checkout, we can push it from the thank you page, thus avoiding the race condition.

There may be more elegant solutions, but something simple and easy to implement would be localstorage which is what this example uses.

All we do is save the dataLayer to localstorage on the checkout page, allow the buyer to be redirected, and then read that data from localstorage and push it to tag manager via dataLayer.push(). Then we can just delete the data from localstorage.

Obviously this implementation only works if the buyer is being redirected to another part of the vendor's website, but I believe that is the case a majority of the time.
