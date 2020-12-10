# Given-a-function-f-and-N-return-a-debounced-f-of-N-milliseconds.
Given a function f, and N return a debounced f of N milliseconds.  That is, as long as the debounced f continues to be invoked, f itself will not be called for N milliseconds.

function debounce(callback, waitingTime, immediate) {
    var timeout;           

    return function() {
        var context = this;
        var args = arguments;

        var shouldCallNow = immediate && !timeout;

        // Resets the callback timer
        clearTimeout(timeout);

        // Schedules the callback to run on the next N ms
        timeout = setTimeout(function() {
            timeout = null;
            if (!immediate) {
                callback.apply(context, args);
            }
        }, waitingTime);

        if (shouldCallNow) {
            callback.apply(context, args);
        } 
     };
};
