# Wellspent back-end assessment

Thank you for applying! This assessment will help us understand how you reason, how you communicate and your ability to translate requirements into working code.

## Guidelines

1. *This assessment should take no longer than 3 hours*. We'd like to respect your time, so submit whatever you can accomplish within this timeframe.
2. *Submissions will only be accepted as zipped source code, or a github repository*. Please include everything in a single zip file, and email it to kieran@wellspent.co when you are done the assessment.
3. *Incomplete submissions are fine*. Though the assessment is designed to be completable within the timeframe, it is also intended to be challenging.
4. *Where there is ambiguity in the requirements, make a decision with the business in mind and focus on speedy delivery*.
5. *Be prepared to justify your decisions*. If we decide to bring you in for a technical interview, we will expect you to explain aspects of your implementation and thought process.

## Requirements

*Summary*: Your back-end system requires the capacity to process event-driven jobs outside of the HTTP request lifecycle, and you need a reusable pattern to emit events and declare how to process them. You have chosen to build a queue backed by a _redis cluster_, with queue logic handled by the library [Bull](https://github.com/OptimalBits/bull).

*Evaluation*: We must be able to execute your solution, so you should include a sample event queue that uses your queue interface. Demonstrate your working solution in whatever way is easiest. A full nodejs webserver is not expected for this assignment, but might make testing easier.

* Story: As a developer building a new type of event-driven job,
    * I should be able to use a single interface to declare new events
    * I should be able to use that same interface to:
        * Specify how an event is processed
        * Set event processing concurrency
        * Specify how the event should be sanitized for logging purposes
        * Begin processing events from the queue
        * Gracefully stop processing events in preparation to shut down
        * Automatically log all queue-level and redis-level errors in one consistent manner
        * Automatically remove completed jobs from the underlying redis database
        * Automatically generate a UUID for this event, logging the beginning and ending of processing with this UUID, and making it available to the processing function

* Bonus story: As a developer creating a scheduled piece of work,
    * I should be able to leverage the same event queue interface to create events on a repeating, cron-like schedule

## Suggestions

1. Consider using [Docker](https://docs.docker.com/) and this [redis cluster image](https://github.com/Grokzen/docker-redis-cluster) to simplify getting the queue working




