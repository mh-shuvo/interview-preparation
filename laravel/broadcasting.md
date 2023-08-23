# Broadcasting

Broadcasting in Laravel provides a seamless way to achieve real-time communication between the server and clients, enabling interactive and dynamic applications.

If you want build a real time communication in your application then you need to work with more stuffs of laravel along with Broadcast.
Like:

- Event Listener
- Channel

Now I want to talk about data flow of real time communication in a laravel application.

- `Event:` It means something happen in the application. It as class which is implement `Illuminate\Contracts\Broadcasting\ShouldBroadCast`. It's just prepared data which is necessary for Event BroadCasting.
- `Event BroadCasting:` When fire and event it actually dispatched. when dispatched of an event it push the event data into the broadcasting system.
 - `Broadcasting System:` It actually build the communication between server and client using Pusher, Redis and more on. After build the communication it broadcast the message with ShouldBroadCast.
 - `Channel:` It is defiend the receiver of the event.
 - `Listeners(Clients):` Listener actually wait for listening the event by subscribing the channel. when and event fire the listener listen it by the channel and execute the code as per on it and changes the user interface.