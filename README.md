# Timetrack

- Timetrack is a simple commandline program for analysing your own calendar data.
- The idea for this project was inspired by Devi Parikh's calendar-based time management technique (I highly recommend reading her blog post: https://blog.usejournal.com/calendar-in-stead-of-to-do-lists-9ada86a512dd).
- After experimenting with Devi's method for a while, I made some adaptations and developed Timetrack as part of my time management and productivity workflow (see [slides](https://github.com/wuningxi/Talks/blob/main/2020_How_to_be_organised_and_productive_during_your_PhD.pdf) from my productivity talk).
- If you are only interested in how to install and use Timetrack, feel free to skip to [Setup](#setup) and [Usage](#usage).

![Analysing calendar data with Timetrack](data/screenshots/overview.jpg?raw=true "Analysing calendar data with Timetrack")

## Motivation

### Calendar-based time management

In her excellent blog post, Devi Parikh proposed to use a calender-based approach for time management instead of commonly used to-do lists (https://blog.usejournal.com/calendar-in-stead-of-to-do-lists-9ada86a512dd).
The key idea is to schedule every task in your calendar (like you would do with a meeting) instead of keeping it on an ever-growing to-do list. This has the advantage of making the required time visible and making you think about how to best allocate it to certain tasks. I tried Devi's calendar-based time management system and really liked it. Its simple and effective. It requires you to break down large problems into more manageable chunks and encourages focusing on a single well-defined task at hand without getting distracted.

### My adjustments

After trying this system for a couple of weeks, I made the following adjustments:

1.  Keep separate calendars (and don’t move tasks to the ‘done’ calendar)
2.  Record your productivity levels
3.  Review what is/isn’t working
4.  Analyse your calendar and productivity data with Timetrack

#### 1.  Keep separate calendars (and don’t move tasks to done calendar)

In her blog post, Devi recommends using three calendars: ‘meetings’, ‘to-do’ and ‘done’ (there is also the ‘block’ calendar to reserve time for eating/sleeping/etc.). The idea is simple: place all new tasks in the ‘to-do’ calendar and then move them to the ‘done’ calendar once you’re finished. However, this doesn’t take into account that **tasks differ in importance and difficulty**.

I therefore keep separate calendars for major vs. minor work-related tasks. Major tasks are tasks which will get you closer to your current professional goal. For example, if your main goal is to successfully complete your PhD, this could include tasks such as writing a paper, analysing data or writing code. Major tasks naturally tend to be relatively difficult and require high energy and focus. In contrast, minor tasks do not immediately contribute to your main goal, but still need to get done. These could include writing emails, planning your schedule for next week or reading a reading group paper unrelated to your own research.
In contrast to major tasks, minor tasks tend to require lower energy levels. **By placing major and minor tasks in different calendars, one look on your weekly schedule makes it immediately clear how important your tasks are and how long they will probably take.** This is useful information when it comes to optimally scheduling your tasks. For example, if you are more productive in the morning, this prime time should be reserved for working on your major tasks, while minor tasks can be deferred to after lunch when concentration levels and productivity tend to be lower.
Although the feeling of moving a task from the ‘to-do’ to ‘done’ calendar can be rewarding, this action deletes valuable information regarding the task’s importance when analysing past calendar data (see point 3). Therefore, each task should be kept in its respective calendar after it’s done (see point 2 for what you should do instead after finishing a task). Tasks which are not work-related (e.g. working on a side project, eating, sleeping) go in the ‘life’ calendar, so they can be easily omitted during calendar analysis. You can also create additional calendars based on your personal needs (e.g. for travel or health/wellbeing).

![Example week in calendar](data/screenshots/calendar.png?raw=true "Example calendar")
(Calendars: blue=major, yellow=minor, pink=meeting, light green=life, dark green=health, grey=travel)


#### 2.  Record your productivity levels

If you follow the instructions above for a couple of days, your calendar will soon contain a lot of interesting data, including how much time you spent on what kind of tasks and when. However, it doesn’t provide any insight into your productivity levels while working on different tasks. **After completing a task, assign a score between 1 -unproductive- and 5 -highly productive/flow state like- to the accomplished task** (You can store the productivity score in the ‘location’ section of the calendar entry which is not ideal, but has the benefit of making it show up in the weekly calendar view). Over time, rating your own productivity will help you to get to know your own working rhythm. It might also help to think about questions such as: Are you most productive in the morning or evening? What would be the best task to match your current energy level? Do you need a short walk after a stressful meeting to recover your energy level? Use this insight into your productivity patterns when scheduling your tasks.

#### 3.  Review what is/isn’t working

At the end of the week, schedule a short weekly review task for Friday afternoon. The idea is to have a **look at your calendar at the end of the week and think about the following questions: What went well? What didn’t? What could I improve next week?**. Write down the answer to these questions in your calendar to keep yourself accountable and learn from your experience.

![Weekly review](data/screenshots/weekly_review.png?raw=true "Weekly review")


#### 4.  Analyse your calendar and productivity data with Timetrack

By following this technique, your calendar will accumulate a large amount of valuable information over time. **Initially, you can simply look at your weekly calendar view to observe your working patterns, but as time progresses it becomes difficult to identify trends. That's why I wrote Timetrack.** Timetrack is a simple tool for analysing your calendar data. Its commandline interface allows you to adjust several settings, including which time periods and calendars to analyse (e.g. only major, minor and meetings). In the basic setting, the program reads your calendar data and summarises how much time you spent on which kind of task over a certain period of time to help you track your own progress.

 ![Timetrack summary for two week period](data/screenshots/two-week_summary.png?raw=true "Timetrack summary for two week period")

However, without taking productivity into account, the summary is only quantitative and may encourage you to maximise working hours rather than productivity. Therefore, **you can use Timetrack's `--prod_score` flag to visualise your average daily productivity alongside quantitative information, allowing you to focus on increasing your productivity rather than working time.**

 ![Timetrack summary for two week period with productivity scores](data/screenshots/two-week_summary_prod.png?raw=true "Timetrack summary for two week period with productivity scores")


## Setup

### 1. Download Timetrack

```
git clone https://github.com/wuningxi/Timetrack.git
cd Timetrack
```

### 1. Install the required Python packages

Make sure you have Python 3 installed on your system and install the required Python packages:
```
python --version
pip install -r requirements.txt
```

### 2. Export your calendar data

Export the calendars you want to analyse as .ics files to `data/calendars/`. How to export the .ics files depends on your calendar client, but here is an example for exporting calendars with the Mac calendar programme.

![How to export a calendar from Mac calendar app](data/screenshots/export_calendar.png?raw=true "Export calendar")


### 3. Add the Timetrack folder to the system path (on Mac)

Edit `timetrack.sh` in a text editor, so that `TIMETRACKDIR` points to the location of your timetrack folder (e.g. /Users/nicole/code/Timetrack). Then, add the following line to your `~/.bash_profile` (replacing `/path/to/Timetrack/timetrack.sh` with the appropriate path, e.g. `/Users/nicole/code/Timetrack/timetrack.sh`): 
```
source /path/to/Timetrack/timetrack.sh
```
This will give you access to `timetrack_multi_cal` and `timetrack_single_cal` from anywhere in the command line. Now, reload `~/.bash_profile`:
```
source ~/.bash_profile
```

### 3. Add the Timetrack folder to the system path (on Linux)

Edit `timetrack.sh` in a text editor, so that `TIMETRACKDIR` points to the location of your timetrack folder (e.g. /Users/nicole/code/Timetrack). Then, add the following line to your `~/.bashrc` (replacing `/path/to/Timetrack/timetrack.sh` with the appropriate path, e.g. `/Users/nicole/code/Timetrack/timetrack.sh`): 
```
source /path/to/Timetrack/timetrack.sh
```
This will give you access to `timetrack_multi_cal` and `timetrack_single_cal` from anywhere in the command line. Now, reload `~/.bashrc`:
```
source ~/.bashrc
```

### 3. Add the Timetrack folder to the system path (on Windows)

Change 'TIMETRACKDIR' to the location of your timetrack folder (e.g. C:\Users\nicole\Code\Timetrack) in both `timetrack_multi_cal.bat` and `timetrack_single_cal.bat`.

Then, add the timetrack folder to the system path environment variables. This allows the use of `timetrack_multi_cal` and `timetrack_single_cal` from anywhere in the command line. On Windows 10, this is done via `Control Panel > System and Security > System > Advanced System Settings > Environment Variables`. Then double click on `Path` in System Variables then the `Browse...` button.

(Many thanks to [Tom271](https://github.com/Tom271) for writing the Windows `.bat` files.)

## Usage

Now you can directly call `timetrack_multi_cal` or `timetrack_single_cal` from the commandline. As the name suggest, `timetrack_single_cal` analyses data from a single calendar, while `timetrack_multi_cal` provides a summary for multiple calendars. Calendars and time interval are adjustable through commandline arguments (see [Options](#options)). You can check if everything is working by running:
```
timetrack_multi_cal -calendars MajorTest.ics,MinorTest.ics -start 2020-10-29 -end 2020-11-01 --prod_score --remove_grid
```
This should produce the following output:
```
==>spent 0 days 13 hours 0 minutes on tasks from 2020-10-29 to 2020-11-01
   - MajorTest.ics tasks: 0 days 6 hours 45 minutes (avg. productivity: 4.8)
   - MinorTest.ics tasks: 0 days 6 hours 15 minutes (avg. productivity: 3.0)
```
![Example plot produced by timetrack_multi_cal](data/screenshots/example.png?raw=true "Example plot produced by multi_cal")


## Options

Options for `timetrack_single_cal`:
```
usage: single_calendar.py [-h] [--today] [--this_week] [--this_month]
                          [-start START] [-end END] [-calendar CALENDAR_NAME]

optional arguments:
  -h, --help            show this help message and exit
  --today               Only display today's data
  --this_week           Only display this week's data
  --this_month          Only display this month's data
  -start START          Start date as yyy-mm-dd
  -end END              End date as yyy-mm-dd
  -calendar CALENDAR_NAME
                        calendar name, e.g. Major.ics, Minor.ics or
                        Meeting.ics
```
Options for `timetrack_multi_cal`:
```
timetrack_multi_cal -h
usage: multi_calendar.py [-h] [--today] [--this_week] [--this_month]
                         [-start START] [-end END] [-calendars [CALENDARS]]
                         [--prod_score] [--all_days] [--print_details]
                         [--remove_grid]

optional arguments:
  -h, --help            show this help message and exit
  --today               Only display today's data
  --this_week           Only display this week's data
  --this_month          Only display this month's data
  -start START          Start date as yyy-mm-dd
  -end END              End date as yyy-mm-dd
  -calendars [CALENDARS]
                        Names of calendars to load separated by comma, e.g.:
                        Major.ics,Minor.ics,Meeting.ics
  --prod_score          Plot productivity scores.
  --all_days            Plot all days, even those without tasks.
  --print_details       Print time spent per calendar category per day.
  --remove_grid         Remove horizontal gridlines from plot.

```
