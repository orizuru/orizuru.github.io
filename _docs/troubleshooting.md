---
---

# orizuru deploy

## orizuru deploy failed and asked me to verify my account with a credit card
> Command failed: heroku addons:create cloudamqp:lemur -a morning-waters-96022<br>
> Creating cloudamqp:lemur on morning-waters-96022... !<br>
> ▸    Please verify your account to install this add-on plan (please enter a<br>
> ▸    credit card) For more information, see<br>
> ▸    https://devcenter.heroku.com/categories/billing Verify now at<br>
> ▸    https://heroku.com/verify

The Orizuru template apps use Heroku Add-ons. Heroku only allows add-ons to be added programmatically to Heroku apps in verified accounts, i.e. those that have completed their billing details.

This is the case *even when installing add-ons under a free plan.*
