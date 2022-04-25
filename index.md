---
layout: page
title: Existentialism Quiz
menu_title: Quiz
menu_icon: house-door
---

<p>
    This is a quiz to evaluate which existential philosopher shares the same interests as you!
</p>


<div id="quiz"></div>
<br>
<button id="button">Submit</button>
<div id="result"></div>
    
<script>
    // modified code from: https://stackoverflow.com/questions/54635773/javascript-quiz-get-selected-radio-button-value-and-compare-to-correct-answer
    // overall website stolen from: https://github.com/Jean-Golding-Institute/hackathon-template
    var answers = ['Very much like me', 'Mostly like me', 'Somewhat like me', 'Not much like me', 'Not like me at all']
    
    const weights = new Map([['Very much like me', 1], ['Mostly like me',0.5], ['Somewhat like me', 0], ['Not much like me', -0.5], ['Not like me at all', -1]])
    var philScores = new Map([["beauvoir", 0], ["camus", 0], ["heidegger", 0], ["kierkegaard", 0], ["nietzsche", 0], ["sartre", 0]])
    
    var myQuestions = {
    q1: { // unique id for every question
        question: 'It comforts you to believe that God does not exist',
        agreePhil: ["nietzsche", "sartre"],
        disagreePhil: ["kierkegaard"],
    },
    q2: {
        question: 'You enjoy stories rather than complex theoretical pieces',
        agreePhil: ["camus", "beauvoir", "kierkegaard"],
        disagreePhil: ["heidegger", "nietzsche"],
    },
    q3: {
        question: 'You’d rather live an exciting, fast-paced life and die young than live comfortably to an old age.',
        agreePhil: ["Heidegger"],
        disagreePhil: ["kierkegaard", "camus"],
    },
    q4: {
        question: 'You believe that the world should function in a way that ensures just outcomes, whenever possible',
        agreePhil: ["beauvoir"],
        disagreePhil: ["nietzsche", "camus"],
    },
    q5: {
        question: 'You believe that we have a responsibility to freely act to protect the freedom of others',
        agreePhil: ["beauvoir", "camus", "sartre"],
        disagreePhil: ["nietzsche"],
    },
    q6: {
        question: 'You feel that, sometimes, ethical principles can be overruled by divine intervention',
        agreePhil: ["kierkegaard"],
        disagreePhil: ["beauvoir", "nietzsche", "sartre"],
    },
    q7: {
        question: 'You believe that humans have both consciousness and a self',
        agreePhil: ["camus", "sartre"],
        disagreePhil: ["heidegger", "kierkegaard"],
    },
    q8: {
        question: 'You\’re the life of the party',
        agreePhil: ["beauvoir", "camus"],
        disagreePhil: ["nietzsche", "sartre"],
    },
    q9: {
        question: 'You\’re willing to go to extreme lengths to see your goals accomplished',
        agreePhil: ["sartre"],
        disagreePhil: ["beauvoir", "camus"],
    },
    q10: {
        question: 'You believe that rules are important and should always be followed',
        agreePhil: ["kierkegaard"],
        disagreePhil: ["camus", "nietzsche"],
    },
    q11: {
        question: 'You are a person of principle: when you find a suitable guiding philosophy, you tend to do everything you can to live by it',
        agreePhil: ["kierkegaard"],
        disagreePhil: ["heidegger"],
    },
    q12: {
        question: 'Whenever possible, you try to make definite choices rather than \“go with the flow.\”',
        agreePhil: ["kierkegaard", "sartre"],
        disagreePhil: ["camus", "heidegger"],
    },
    q13: {
        question: 'You find that people give too much credence to arbitrary labels placed on them, either by themselves or by others',
        agreePhil: ["camus", "sartre"],
        disagreePhil: ["kierkegaard", "nietzsche"],
    },
    q14: {
        question: 'You value power, and, whenever possible, will go to great lengths to obtain it',
        agreePhil: ["camus", "nietzsche"],
        disagreePhil: [],
    },
    q15: {
        question: 'You don\’t think existence should be studied; it should be experienced',
        agreePhil: ["camus", "heidegger"],
        disagreePhil: ["kierkegaard", "sartre"],
    },
    q16: {
        question: 'You believe we still have a long way to go in achieving equality of the sexes',
        agreePhil: ["beauvoir", "sartre"],
        disagreePhil: ["heidegger", "nietzsche"],
    },
    q17: {
        question: 'You are attracted to other people and make new friends easily',
        agreePhil: ["beauvoir", "camus"],
        disagreePhil: ["kierkegaard", "nietzsche"],
    },
    q18: {
        question: 'Doing the right thing is your most important value',
        agreePhil: ["beauvoir", "kierkegaard"],
        disagreePhil: ["camus", "nietzsche"],
    },
    q19: {
        question: 'You find your purpose by putting faith in something larger than yourself, such as a God or some other spiritual principle',
        agreePhil: ["kierkegaard"],
        disagreePhil: ["camus", "sartre"],
    },
    q20: {
        question: 'You take stock of your life by looking at all that you can still accomplish, rather than all that your past achievements',
        agreePhil: ["nietzsche", "sartre"],
        disagreePhil: ["kierkegaard", "heidegger"],
    },
};

/*********************************************************************/

var quiz_id = document.getElementById('quiz');
var submitButton = document.getElementById('button');
var userAnswers = {}; // store the selected answers in this object, indexed by question id

/*********************************************************************/

var aQuestion;
Object.keys(myQuestions).forEach((questionId, arrayIndex) => {
    aQuestion = myQuestions[questionId];
    var questionContainer = document.createElement('div');
    var questionLabel = document.createElement('label');
    var optionContainer = document.createElement('section');
    
    answers.forEach((answer) => {
        var radioButton = generateRadioButton(questionId, answer);
        optionContainer.appendChild(radioButton);
    });

    questionLabel.innerText = `\n${arrayIndex + 1}. ${aQuestion.question}\n`;

    questionContainer.appendChild(questionLabel);
    questionContainer.appendChild(optionContainer);
    quiz_id.appendChild(questionContainer);
});

/*********************************************************************/

function getWeight(answer) {
    return weights.get(answer);
}

function showResults(params) {
    // Do your things
    // console.log(userAnswers);
    Object.keys(myQuestions).forEach((questionId, arrayIndex) => {
        aQuestion = myQuestions[questionId];
        aQuestion.agreePhil.forEach((phil) => {
            philScores.set(phil, philScores.get(phil) + getWeight(userAnswers[questionId]))
        });

        aQuestion.disagreePhil.forEach((phil) => {
            philScores.set(phil, philScores.get(phil) - getWeight(userAnswers[questionId]))
        });
    });

    // find max score
    var maxphil = "camus"
    philScores.forEach((score, phil) => {
        if (score > philScores.get(maxphil)) {
            maxphil = phil;
        }
        //var resultContainer = document.createElement('label');
        //resultContainer.innerText = `${phil}. ${score}\n`;
        //quiz_id.appendChild(resultContainer);
    });

    window.location.replace(maxphil);
}

/*********************************************************************/

submitButton.addEventListener('click', showResults);

/*********************************************************************/

function generateRadioButton(groupId, value) {
    var container = document.createElement('div');
    var label = document.createElement('label');
    var radioButton = document.createElement('input');

    radioButton.className = 'answers';
    radioButton.type = 'radio';
    radioButton.id = groupId;
    radioButton.value = value;
    radioButton.name = groupId;
    radioButton.addEventListener('input', (event) => {
        userAnswers[groupId] = event.currentTarget.value;
    });

    label.innerText = value;
    label.htmlFor = value;

    container.appendChild(radioButton);
    container.appendChild(label);

    return container;
}

</script>