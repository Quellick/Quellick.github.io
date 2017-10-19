---
layout: post
title: BlocJams
thumbnail-path: "img/blocjams.png"
short-description: BlocJams is a Spotify replica for finding the best music and listening to it online.

---

{:.center}
![]({{ site.baseurl }}/img/blocjams.png)

## Summary

This is a project to reconstruct a replica of Spotify to get familiar with HTML and CSS as well as animating with JavaScript and JQuery.

## Explanation

I set up each page as instructed and was given a code challenge for each section to work through on my own.

## Problem

Throughout each challenge new concepts where introduced, I had to learn and assimilate them into my pages.  We also had to refactor our vanilla JavaScript into JQuery to reduce the number of lines of code on the page.  I also had an issue where the player bar wasn't able to play or pause songs, nor could it move to the previous or next song.  The code below handles any clicks when people select the song they wish to hear.  It checks that the song isn't already currently playing (At #1) as well as manages which icon appears based on which state the song is in (At #2).  This block of code also helps keep the seek bars synced with the progress of the current song being played as well as allowing the user to adjust the volume. (At #3 and #4)

{% highlight javascript %}
var clickHandler = function(){
       var songNumber = parseInt($(this).attr('data-song-number'));
       // #1
       if (currentlyPlayingSongNumber !== null) {
       var currentlyPlayingCell = getSongNumberCell(currentlyPlayingSongNumber);
       currentlyPlayingCell.html(currentlyPlayingSongNumber);
     }
       if (currentlyPlayingSongNumber !== songNumber) {
       // #2
       $(this).html(pauseButtonTemplate);
       setSong(songNumber);
       currentSoundFile.play();
       // #3
       updateSeekBarWhileSongPlays()
       // #3
       updatePlayerBarSong();
       // #4
       var $volumeFill = $('.volume .fill');
       var $volumeThumb = $('.volume .thumb');
       $volumeFill.width(currentVolume + '%');
       $volumeThumb.css({left: currentVolume + '%'});

     } else if (currentlyPlayingSongNumber === songNumber) {
             if (currentSoundFile.isPaused()) {
                // #2
                $(this).html(pauseButtonTemplate);
                $('.main-controls .play-pause').html(playerBarPauseButton);
                currentSoundFile.play();
                // #3
                updateSeekBarWhileSongPlays()
            } else {
                // #2
                $(this).html(playButtonTemplate);
                $('.main-controls .play-pause').html(playerBarPlayButton);
                currentSoundFile.pause();
             }
     }
    };
    {% endhighlight %}

## Solution

I learned new concepts from JavaScript and JQuery and applied them to refactoring the vanilla JavaScript into JQuery.  
We also generated the code and logic needed to update the player seek bar when a new song is selected as well as the ability to move through the song by clicking on the seek bar.

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
    //divide timeInSeconds by 60 to get whole minutes
    var wholeMinutes = Math.floor(value / 60);
    //return the time formatted as X:XX
    return (wholeMinutes + ":" + (wholeSeconds < 10 ? '0' + wholeSeconds : wholeSeconds));
  }
  {% endhighlight %}

## Results

I ended up with a site able to store a vast amount of album collections as well as display those albums on a page of their own complete with song lists and information about each song, such as duration and title.

## Conclusion

This is still a work in progress, but I have learned a lot about JavaScript and JQuery, more specifically while JQuery may make things easier in some respects it is no longer considered best practice.  
The reason is that the latest versions of HTML/CSS offer much the same functionality as JQuery, as well as new Symantec HTML that JQuery can't make use of.
