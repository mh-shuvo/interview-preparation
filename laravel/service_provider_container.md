# Service Container
Service Container is a container which is used to manage the instantiation of object and resolve dependency of the class. It servs as a central repository in the entire application to provide instantiation and dependency resolation. Laravel Service Container provides lot's of facility to manage the class dependencies. 

- You can create singleton class object or create new one whenever you needed. 
- Automatically resolve dependencies by using PHP Reflection Class API in behind. 
- You can also bind concreate implementation of interface or abstract class.

# Service Provider

Service Provider is the classes which is registering the services, binding other component into the Service Container. It's like a bridge between application and Service Container. 

Actually in `register()` method of Service Provider used to registering the service or binding or configuring other stuffs into container if you want to available your service from the booting the application.

- You can register services and their implementation withine the container. And the service can be class, interface etc.
- Every Service Provider have `boot()` method that allows you to perform tasks after all other providers have been registered.

# Real Life Example to understand it


Here's a simple example to illustrate the difference:

Suppose we have an interface `SendNotification` and two different implementations: `SmsNotification` and `SlackNotification`.

### Service Container:

The Service Container is responsible for managing instances and injecting dependencies. It will automatically resolve the appropriate SendNotification implementation based on the context:


    
    // Binding implementations in the Service Container
    app()->bind(SendNotification::class, SmsNotification::class); // Using Laravel's global helper function

    // In a controller or another class
    class NotificationController {
        public function sendNotification(SendNotification $notification) {
            // The container will automatically inject the appropriate implementation
            $notification->send();
        }
    }

### Service Providers:

The Service Provider defines how services should be registered in the Service Container. It encapsulates the binding logic:



    class NotificationServiceProvider extends ServiceProvider {
        public function register() {
            $this->app->bind(SendNotification::class, SmsNotification::class);
        }
    }


By defining the binding in the NotificationServiceProvider, you centralize the registration process. This allows you to swap the implementation easily by changing the binding, without modifying the code that relies on the SendNotification interface.

In summary, the Service Container handles dependency injection and the resolution of dependencies, while Service Providers manage the registration of services and their configurations within the container.