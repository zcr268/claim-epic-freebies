# Claim Epic Freebies

EpicGames Weekly Giveaways Auto Claimer
1

This is a supplementary repository for [Revadike/epicgames-freebies-claimer](https://github.com/Revadike/epicgames-freebies-claimer)

Please leave a star [:star:](https://github.com/xuac/claim-epic-freebies#:~:text=star) if you find this helpful.

## Setup

All you need to set this up, is to follow through this guide.

1. Click [this link](https://github.com/xuac/claim-epic-freebies/fork) to fork the repo or use the button.

   <p align="center">
     <img src="https://i.imgur.com/WRxfXmg.png">
   </p>

2. Go to [Actions tab](../../actions) and click on the big green button that says "I understand my workflows, go ahead and run them"

   <p align="center">
     <img src="https://i.imgur.com/gAsnfRv.png">
   </p>

3. Go to the [secrets menu in settings tab](../../settings/secrets)

   <p align="center">
     <img src="https://i.imgur.com/k21dFyM.png">
   </p>

4. Create 3 new secrets with the name `USERNAME`, `PASSWORD` and `SECRETKEY` (all uppercase) and update the secrets with the corresponding values

   - `USERNAME` - Your EpicGames email address
   - `PASSWORD` - Your EpicGames password
   - `SECRETKEY` - Your Authenticator Key for 2FA *

    \* You can skip or delete `SECRETKEY` if 2FA is disabled. The two-step verification secret will be displayed when you enable enable two-step verification using the "Authenticator" app. If you have already enabled it, you can see it by turning it off and then on again.


   <p align="center">
     <img src="https://i.imgur.com/4q9GyOk.png">
   </p>


Yep, that's it. This will run as scheduled and automatically claim free games available.

## Advanced configurations

You can change the behavior of this workflow by editing the [claim.yml](.github/workflows/claim.yml) file.

#### Schedule

You can change the trigger schedule using cron expressions. You can use [crontab guru](https://crontab.guru/) if you don't know how cron expressions work.

```yml
schedule:
  - cron: "0 0 * * *" # Everyday at 00:00 UTC
```

**Note:** _The scheduler of GitHub Actions is a bit inaccurate, so there may be a delay of about 5 to 10 minutes._

#### Multiple Accounts

If you want to set this up for multiple accounts, You need to create more secrets and jobs. You can label them accordingly for easy identification. You also need to create more jobs in order to do this.

```yml
jobs:
  claim:
```

By default, there is only one job. You can create multiple jobs by duplicating the jobs

```yml
jobs:
  claim1:
  ...

  claim2:
  ...
```

#### Timeout limit

This is setup because sometimes the script fails to login and asks for manual login, which you can't do. So, it would just wait forever.

```yml
timeout-minutes: 5 # Automatically stop after 5 minutes
```

#### Manual trigger

You can trigger the action manually by starring the repository.

To enable this feature, uncomment the following lines. (remove the `#` sign from the starting)

```yml
#    watch:
#        types: [started] # When repo owner stars this repo
```

**Note** _This feature is not limited to you. Anyone who stars your fork can trigger the action._
