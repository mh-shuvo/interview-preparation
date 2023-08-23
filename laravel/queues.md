# Queues
Queue is a mechanism to perform the long running task asynchronously and in the background without break the normal flow of application. 

If you want to implement queue in your application you need to sevaral components along with its:

- `Job:` It is a class which is actually implement the `Illuminate\Contracts\Queue\ShouldQueue` interface. It's a unit of work together called task. In the Job class you need to define what should done.
- `Queue Configuration:` Laravel support multiple queue driver like database, redis, amazon sqs etc. You can choose anyone from those driver based on your application.
- `Job worker:` The worker always monitoring the queue for pending job and process them. 

- `Job Processing:` When start the processing of the job in that time worker actually call the `handle()` method of the job. After completing process the job marked as completed.

- `Retry mechanism`: If the job is fail then laravel allow to retry it in certain number time. If the job is finally failed after multiple retry then it's store into the failed job.