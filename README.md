# Streak-er

## Introduction
Streak-er is a simple motivational tool designed to help keep track of user-defined "streaks". A streak can be anything you do (or want to do) every day. All you have to do to keep a streak alive is log an entry at least once a day by typing in a single bash command with an optional comment:

    $ streak code -m "worked on streak-er docs"
    > Entry logged for streak "code"!
    > Congratulations! You've kept this streak alive for 14 days!

Once installed Streak-er is available globally by default, so it can be called from any directory at any time. There are no strict rules or systems to enforce them, streaks are based on the honor system; if you choose to cheat it you're only lying to yourself.

## Installation and Getting Started

### 1. Download and setup
Installation instructions will go here.

    $ curl | some url maybe
some text

    $ python streaker.py init
    > Streaker successfully initialized!

make sure streak command is available globally

    $ streak --version
    > Streaker version 0.0.1

and you're good to go!


### 2. Create your first streak

Check current status of database

    $ streak --status
    > No streaks in database.

When you create your first streak it automatically counts that day as your first day of the streak. You can change this behavior by setting the initial count to something other than 1.

    $ streak --new_streak code --description "Write at least one line of code" --init_count 10

See some other part of docs for all available parameters during streak creation.

### 3. Continuing your streak

Streaks by default are kept alive by making at least one entry a day. Maybe future versions will have the ability to filter by x number of days per week, or a manual entry of pass/fail arguments (like did a batter get a hit this game or not), but not in version one.

Streaks should be able to be kept alive with just a two word command

    $ streak code
    > Entry logged for streak "code"!
    > Congratulations! You've kept this streak alive for 11 days!

Comments on entries are optional, but encouraged.

    $ streak code -m "cleaned up Streaker init module"
    > Entry logged for streak "code"!
    > Congratulations! You've kept this streak alive for 11 days!

You are welcome to add as many entries per day as you would like, but the streak count only climbs once a day at midnight (system time).

### 4. Checking streak stats

Checked earlier, nothing. Check again

        $ streak --status
        > 2 entries for 1 Streak

Aight

Check streak stats

        $ streak code --stats
        > ---------------------------------
        > Streak name:
        >   code
        > Description:
        >   Write at least one line of code
        > Entries:
        >   3
        > Current streak length:
        >   13
        > Longest streak length:
        >   13

