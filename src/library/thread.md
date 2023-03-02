# `thread`
`thread` module provides a few functions related to threads and channels.

 - [`new`](#newf)
 - [`channel`](#channelcap)
 - [`send`](#sendch-msg)
 - [`receive`](#receivech)

## `new(f)`
`new` returns a function that when called, spawns a new thread.
```js
func do_something() {
    // do something
}
thread_do_something := new(do_something)
thread_do_something() // spawns a new thread
```

## `channel(cap)`
`channel` creates a new channel object of capacity that can hold at most `cap` messages at a time.
`cap` defaults to `:unbounded`.
```js
ch := channel(3) // creates a channel that can hold at most 3 messages at a time
```

## `send(ch, msg)`
`send` blocks the current thread until `msg` is sent.
If the channel is full, this call will block until the send operation can proceed.
```js
ch := channel(:unbounded)
send(ch, "Hello!")
```

## `receive(ch)`
`receive` attempts to receive a message from the channel without blocking.
It will either receive a message from the channel immediately or throw an error if the channel is empty.
```js
func do_something(ch) send(ch, "Hello")

ch := channel(:unbounded)
new(do_something)(ch)

println(receive(ch)) // "Hello"
```
