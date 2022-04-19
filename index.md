---
layout: page
title: Philosophy quiz
menu_title: Quiz
menu_icon: house-door
---

## PHILOSOPHY

<p>Question 1: I like chocolate.</p>

<input type="radio" name="q1" value="5">Very much like me
<input type="radio" name="q1" value="4">Mostly like me
<input type="radio" name="q1" value="3">Somewhat like me
<input type="radio" name="q1" value="2">Not much like me
<input type="radio" name="q1" value="1">Not like me at all

    
<button type="button" onclick="displayRadioValue()">
    Submit
</button>
    
    
<div id="result"></div>
    
<script>
    const weights = new Map([["5", 1], ["4",0.5], ["3", 0], ["2", -0.5], ["1", -1]])
    const philScores = new Map([["beauvoir", 0], ["camus", 0], ["heidegger", 0], ["kierkegaard", 0], ["sarte", 0]])
    // for loop to iterate through question numbers (append q + #) to create radio buttons
    // mapping of question to philosophers
    // questions should associate themselves in a map with philsophers - pos neg values means that different portions of the array are applied
    // {Question : [[left group] [right group]]} - can be inversed, we add the value to the right group, we subtract the value from the left group
    // function call should be made to make these additions/subtractions O(1) time
    function displayRadioValue() {
        var ele = document.getElementsByName('q1');
            
        for(i = 0; i < ele.length; i++) {
            if(ele[i].checked)
            document.getElementById("result").innerHTML
                    = "Question 1: "+weights.get(ele[i].value);
        }
    }
</script>

<br>

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ultrices gravida dictum fusce ut placerat orci nulla pellentesque. Adipiscing commodo elit at imperdiet dui accumsan. Imperdiet sed euismod nisi porta lorem mollis aliquam. Consequat id porta nibh venenatis cras. Arcu risus quis varius quam quisque. Magna eget est lorem ipsum dolor. Mollis nunc sed id semper risus. Leo vel orci porta non pulvinar. Metus dictum at tempor commodo ullamcorper a lacus. Aliquam sem fringilla ut morbi tincidunt augue interdum velit euismod. Urna molestie at elementum eu facilisis.

Facilisis volutpat est velit egestas dui. Urna molestie at elementum eu facilisis. Et ultrices neque ornare aenean. Dapibus ultrices in iaculis nunc sed. Egestas sed sed risus pretium quam vulputate dignissim suspendisse in. Tortor vitae purus faucibus ornare suspendisse sed. Elit scelerisque mauris pellentesque pulvinar pellentesque. Consequat nisl vel pretium lectus quam id. Felis eget nunc lobortis mattis. Mattis aliquam faucibus purus in massa. Fermentum leo vel orci porta non pulvinar. Imperdiet dui accumsan sit amet. A diam maecenas sed enim ut sem viverra. Dictumst vestibulum rhoncus est pellentesque elit ullamcorper dignissim.

Eu mi bibendum neque egestas congue quisque. Et netus et malesuada fames ac turpis egestas integer. Varius sit amet mattis vulputate enim nulla aliquet porttitor lacus. Vestibulum morbi blandit cursus risus at. Nibh tortor id aliquet lectus proin nibh nisl condimentum id. Et malesuada fames ac turpis. Sed adipiscing diam donec adipiscing tristique risus nec feugiat in. Et malesuada fames ac turpis egestas integer eget aliquet nibh. Et tortor at risus viverra adipiscing at in tellus. Sit amet justo donec enim.

Vitae aliquet nec ullamcorper sit amet. Morbi tristique senectus et netus et malesuada fames. Nec nam aliquam sem et tortor consequat id porta. Tristique magna sit amet purus gravida. Quis commodo odio aenean sed adipiscing diam. Id velit ut tortor pretium viverra suspendisse. Sapien et ligula ullamcorper malesuada proin. Est placerat in egestas erat imperdiet sed euismod. Vitae congue eu consequat ac felis donec et odio. Feugiat pretium nibh ipsum consequat nisl vel pretium lectus. Consequat id porta nibh venenatis cras sed felis.

Sed viverra ipsum nunc aliquet bibendum. Lorem ipsum dolor sit amet consectetur adipiscing elit. Vel eros donec ac odio tempor orci dapibus. Lorem ipsum dolor sit amet consectetur adipiscing elit. Interdum velit laoreet id donec ultrices tincidunt arcu non. Porttitor leo a diam sollicitudin tempor id eu nisl. Nunc mattis enim ut tellus. Congue mauris rhoncus aenean vel elit scelerisque. Curabitur gravida arcu ac tortor dignissim convallis. Interdum consectetur libero id faucibus nisl.
