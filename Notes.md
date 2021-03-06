# Streak-er

## User Story

As a user I should be able to call streaker globally, because I work in many different environments.

I should be able to start a streak with an initial count

I should be able to view active streaks

I should be able to log work for multiple streaks at once

I should be able to see stats on a streak

I should be able to see comments associated with streak dates

CLI arguments should mimic git API where applicable for ease of use

## Data Structure

### TABLES:

    CREATE TABLE streak (
        id INTEGER PRIMARY KEY NOT NULL,
        name TEXT NOT NULL,
        description TEXT,
        init_date DATE NOT NULL,
        start_date DATE NOT NULL,
        init_count INTEGER DEFAULT 1,
        current_streak INTEGER DEFAULT 1,
        current_streak_start_date DATE NOT NULL,
        longest_streak INTEGER DEFAULT 1,
        longest_streak_start_date DATE NOT NULL,
        longest_streak_end_date DATE
    )

    CREATE TABLE entry (
        id INTEGER PRIMARY KEY NOT NULL,
        datetime DATE NOT NULL,
        comment TEXT,
        streak_id INT NOT NULL,
        FOREIGN KEY(streak_id) REFERENCES streak(id)
    )

#### METHODS/FUNCTIONS:

    __init_streak__(name, streak_init_count=1, longest_streak=1, comment):
        ## to do:
            ## verify longest_streak >= streak_init_count
            ## insert description variable

        streak_init_date = Datetime.now()
        current_streak = streak_init_count

        if streak_init_count == 1:
            streak_start_date = streak_init_date
        else:
            streak_start_date = streak_init_date - streak_init_count

        db.serialize(

            db.run(f'
            INSERT INTO streak (name, init_date, start_date, init_count, current_streak, longest_streak)
            VALUES ({name}, {streak_init_date}, {streak_start_date}, {streak_init_count}, {current_streak}, {longest_streak})
            ')

            db.run(f'
            INSERT INTO entry (datetime, comment, streak id)
            VALUES ({streak_init_date}, {comment}, {self.lastID})
            ')
        )

        print(f'
        Congratulations! You started a new streak named "{name}"!
        This streak has been going for {streak_init_count} day(s)!
        ')


