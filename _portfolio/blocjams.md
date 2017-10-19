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

Throughout each challenge new concepts where introduced, I had to learn and assimilate them into my pages.  We also had to refactor our vanilla JavaScript into JQuery to reduce the number of lines of code on the page.  I also had an issue where the player bar wasn't able to play or pause songs, nor could it move to the previous or next song or even change the volume of the song.  

## Solution

To fix the problem of not being able to use the player bar to play or pause songs or be able to seek through a song and adjust its volume we use the code blocks below. The clickHandler function checks to see if the selected song is stopped(no song playing), paused or playing (At #1) as well as manages which icon appears based on which state the song is in playing or paused (At #2).  This block of code also fires off additional functions that keep seek bars synced with the progress of the current song being played (At #3).

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
       var $volumeFill = $('.volume .fill');
       var $volumeThumb = $('.volume .thumb');
       $volumeFill.width(currentVolume + '%');
       $volumeThumb.css({left: currentVolume + '%'});

     } else if (currentlyPlayingSongNumber === songNumber) {
             // #1
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

This bloc is responsible for all of the data passed into the seek bars, duration, current location in the song, etc.  It makes sure it's data for the currently playing song as well as filters that data to be more readable to humans instead of just outputting a song duration in raw seconds this converts the duration into a readable minutes:seconds format.

{% highlight javascript %}
var setCurrentTimeInPlayerBar = function (currentTime) {
    //set text of element with .current-time class to current time in the song
    $('.current-time').text(filterTimeCode(currentTime));
  }

  var setTotalTimeInPlayerBar = function (totalTime){
    //set text of element with .total-time class to the length of the song
    $('.total-time').text(filterTimeCode(totalTime));
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
