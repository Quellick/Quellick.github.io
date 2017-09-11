---
layout: post
title: BlocJams
thumbnail-path: "img/blocflix.png"
short-description: BlocJams is a Spotify replica for finding the best music and listening to it online.

---

{:.center}
![]({{ site.baseurl }}/img/blocflix.png)

## Summary

This is a project to reconstruct a replica of Spotify to get familiar with html and css as well as animating with JavaScript and JQuery.

## Explanation

I set up each page as instructed and was given a code challenge for each section to work through on my own.

## Problem

Throughout each challenge new concepts where introduced I had to learn and assimilate them into my pages.  We also had to refactor our vanilla JavaScript into JQuery to reduce the amount of lines of code on the page.  
I also had an issue where the player bar wasn't able to play or pause songs, nor could it move to the previous or next song.  

## Solution

I learned new concepts from JavaScript and JQuery and applied them to refactoring the vanilla JavaScript into JQuery.  
We also generated the code and logic needed to get the player bar to play/pause a song as well as move to the next/previous songs in the album list.

{% highlight javascript %}
var setCurrentTimeInPlayerBar = function (currentTime) {
    //set text of element with .current-time class to current time in the song
    $('.current-time').text(filterTimeCode(currentTime));
    //add method so current time updates with the song playback
  }

  var setTotalTimeInPlayerBar = function (totalTime){
    //set text of element with .total-time class to the length of the song
    $('.total-time').text(filterTimeCode(totalTime));
    //add method so the total time is set when a song first plays.
  }

  var filterTimeCode = function(timeInSeconds){
    //Use parseFloat method to get the seconds in number form
    var value = parseFloat(timeInSeconds);
    //store variable for the whole seconds and whole minutes
    var wholeSeconds = Math.floor(value % 60, 10);
    //divide timeInSeconds by 60 to get whole minutes?
    var wholeMinutes = Math.floor(value / 60);
    //return the time formatted as X:XX
    return (wholeMinutes + ":" + (wholeSeconds < 10 ? '0' + wholeSeconds : wholeSeconds));
  }
  {% endhighlight %}

## Results

I ended up with a site able to store a vast amount of album collections as well as display those albums on a page of their own complete with song lists and information about each song, such as duration and title.

## Conclusion

This is still a work in progress, but I have learned a lot about JavaScript and JQuery, more specifically while JQuery may make things easier in some respects it is no longer considered best practice.  
The reason is that the latest versions of HTML/CSS offer much the same functionality as JQuery, as well as new Symantec html that JQuery can't make use of.
