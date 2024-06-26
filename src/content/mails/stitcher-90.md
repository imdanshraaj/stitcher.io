Hi ::subscriber.first_name::

This is massive: [property hooks](https://wiki.php.net/rfc/property-hooks) are coming! The vote is still ongoing, but there currently are 35 people voting yes, and only 1 voting no — an amazing result!

I definitely plan on writing an in-depth blog post about property hooks, I'll make two videos about them, _and_ I will have a live chat with Larry, the co-creator of the RFC next week, Tuesday, April 30th, at 8PM CEST. I'll make sure to send you a link at the start of next week! Meanwhile, you can [subscribe to PHP Annotated](https://www.youtube.com/@phpannotated) if you want to 😊

Ok, so, property hooks. I'm so excited about them. They allow programmers to write get and set hooks, so that you don't need to manually implement getters and setter anymore: 

```php
class User implements Named
{
    private bool $isModified = false;
 
    public function __construct(
        private string $first, 
        private string $last
    ) {}
 
    public string $fullName {
        get => $this->first . " " . $this->last;
 
        set { 
            [$this->first, $this->last] 
                = explode(' ', $value, 2);
                
            $this->isModified = true;
        }
    }
}
```

On top of that, the RFC allows interfaces to define property hook definitions:

```php
interface Named
{
    public string $fullName { get; }
}
```

And this is the big one for me: I plan to refactor all of Tempest's code to make use of property hooks in interfaces. It'll take some effort, but it'll be so worth it in the long run! In my eyes, this is a feature the same magnitude as typed properties, enums, and promoted properties. It's a huge step for modern PHP, and I'm so happy with it!

Speaking of Tempest, by the way, I just released a new video that I'm super proud of: [https://www.youtube.com/watch?v=CSNpmbUnN6Q](https://www.youtube.com/watch?v=CSNpmbUnN6Q). It's about how I'm creating `tempest/console`, and I'm super happy with how the video turned out. I definitely would appreciate you taking a look, and leaving a like and comment. Above all, I hope this video will inspire people to build great things 😊

Finally, if you happen to read this email immediately when it arrives, you could come and say hi in [the livestream](https://www.youtube.com/watch?v=RjjG6CBPhws) I'm doing this morning. I just wanna sit down, talk about the property hooks RFC, and do some coding on `tempest/console` — so if you've got the time, come check it out!

I hope to see you soon, wherever it might be!

Brent