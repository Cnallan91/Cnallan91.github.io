var allHands = [
  ["AA", "AKs", "AQs", "AJs", "ATs", "A9s", "A8s", "A7s", "A6s", "A5s", "A4s", "A3s", "A2s"],
  ["AKo", "KK", "KQs", "KJs", "KTs", "K9s", "K8s", "K7s", "K6s", "K5s", "K4s", "K3s", "K2s"],
  ["AQo", "KQo", "QQ", "QJs", "QTs", "Q9s", "Q8s", "Q7s", "Q6s", "Q5s", "Q4s", "Q3s", "Q2s"],
  ["AJo", "KJo", "QJo", "JJ", "JTs", "J9s", "J8s", "J7s", "J6s", "J5s", "J4s", "J3s", "J2s"],
  ["ATo", "KTo", "QTo", "JTo", "TT", "T9s", "T8s", "T7s", "T6s", "T5s", "T4s", "T3s", "T2s"],
  ["A9o", "K9o", "Q9o", "J9o", "T9o", "99", "98s", "97s", "96s", "95s", "94s", "93s", "92s"],
  ["A8o", "K8o", "Q8o", "J8o", "T8o", "98o", "88", "87s", "86s", "85s", "84s", "83s", "82s"],
  ["A7o", "K7o", "Q7o", "J7o", "T7o", "97o", "87o", "77", "76s", "75s", "74s", "73s", "72s"],
  ["A6o", "K6o", "Q6o", "J6o", "T6o", "96o", "86o", "76o", "66", "65s", "64s", "63s", "62s"],
  ["A5o", "K5o", "Q5o", "J5o", "T5o", "95o", "85o", "75o", "65o", "55", "54s", "53s", "52s"],
  ["A4o", "K4o", "Q4o", "J4o", "T4o", "94o", "84o", "74o", "64o", "54o", "44", "43s", "42s"],
  ["A3o", "K3o", "Q3o", "J3o", "T3o", "93o", "83o", "73o", "63o", "53o", "43o", "33", "32s"],
  ["A2o", "K2o", "Q2o", "J2o", "T2o", "92o", "82o", "72o", "62o", "52o", "42o", "32o", "22"]
];

var userHands = [];
var randomHand;
var card1Image = "";
var card2Image = "";
var suits = ["_of_clubs", "_of_diamonds", "_of_hearts", "_of_spades"];
var offsuits = [];
var tableCells = document.getElementsByTagName("td");

// Review Page Variables

var handsPlayedCount = 0;
var wrongHandCount = 0;
var correctHandCount = 0;
var wrongHands = [];

$( document ).ready(function() {
  $('.ranges-grid').append(handsTable);
});

// Picks A random hand

function cardPicker () {
  handsPlayed();
  $('#cardHolder').empty();
  var randomNumber1 = Math.floor(Math.random() * 12);
  var randomNumber2 = Math.floor(Math.random() * 12);
  randomHand = allHands[randomNumber1][randomNumber2];
  card1Image += ("<img src=images/cards/") + (randomHand[0]);
  card2Image += ("<img src=images/cards/") + (randomHand[1]);  

  var randomSuitNumber = Math.floor(Math.random() * suits.length); 
  var card1Suit = suits[randomSuitNumber];
  card1Image += (card1Suit);

  if (randomHand[2] == "s") {
    card2Image += (card1Suit);
  } else {
    suits.splice(randomSuitNumber,1);
    var randomOffsuitNumber = Math.floor(Math.random() * offsuits.length); 
    var card2Suit = suits[randomOffsuitNumber];
    card2Image += (card2Suit);
    suits.splice(randomSuitNumber,0, card1Suit);
  }

  card1Image += (".svg>");
  card2Image += (".svg>");
  $('#cardHolder').append(card1Image, card2Image);
  card1Image = "";
  card2Image = "";
}

// Quiz Button

$('#raiseButton').on('click', function(event) {
  event.preventDefault();
  if (userHands.indexOf(randomHand) > -1) {
    $(".quizArea").css("background-color", "#2b4c2f");
    correctHandCount++;
  } else {
    $(".quizArea").css("background-color", "#3d0d0d");
    wrongHandCount++;
    wrongHands.push(randomHand);
  }
  handsPlayedCount++;
  cardPicker();
});

$('#foldButton').on('click', function(event) {
  event.preventDefault();
  if (userHands.indexOf(randomHand) > -1) {
    $(".quizArea").css("background-color", "#3d0d0d");
    wrongHandCount++;
    wrongHands.push(randomHand);
  } else {
    $(".quizArea").css("background-color", "#2b4c2f");
    correctHandCount++;
  }
  handsPlayedCount++;
  cardPicker();
});

// Populate Table

var handsTable = function () {

  "use strict";

  var table = $('<table oncontextmenu="return false;" id="table1" />'),
      rows = [],
      row,
      i,
      j;

  for (i = 0; i < allHands.length; i = i + 1) {
    row = $('<tr />');
    for (j = 0; j < allHands[i].length; j = j + 1) {
      row.append($('<td />').html(allHands[i][j]));
    }
    rows.push(row);
  }


  for (i = 0; i < rows.length; i = i + 1) {
    table.append(rows[i]);
  }

  return table;
};

// Count Functions

function handsPlayed() {
  $(".handCount").html('<h4 class="handCount">Hands played : ' + handsPlayedCount + '</h4>');
}

function correctHandsPlayed() {
  $(".correctHands").html('<h4 class="handCount">Correct hands : ' + correctHandCount + '</h4>');
}

function wrongHandsPlayed() {
  $(".wrongHands").html('<h4 class="handCount">Wrong hands : ' + wrongHandCount + '</h4>');
}

// Buttons

$(function () {

  // Grid Highlight and Buttons

  var broadwayCards = $(".startPageWrapper .ranges-grid td").filter(function () {
    return this.innerHTML.match(/[A-Z]{2}/); 
  });

  // Highlight features

  var isMouseDown = false;
  $(".startPageWrapper .ranges-grid td")
    .mousedown(function () {
    isMouseDown = true;
    $(this).toggleClass("highlighted");
    return false;
  })
    .mouseover(function () {
    if (isMouseDown) {
      $(this).toggleClass("highlighted");
    }
  });

  $(document)
    .mouseup(function () {
    isMouseDown = false;
  });

  // Highlight buttons

  $('#pairsButton').on('click', function(event) {
    event.preventDefault();
    for (i = 0; i < 13; i++) {
      $("td").eq(i * 14).addClass("highlighted")
    }   
  });

  $('#broadwayButton').on('click', function(event) {
    event.preventDefault();
    broadwayCards.addClass("highlighted");
  });

  $('#scButton').on('click', function(event) {
    event.preventDefault();
    for (i = 0; i < 12; i++) { 
      $("td").eq(i * 14 + 1).addClass("highlighted");
    }
  });

  $('#clearButton').on('click', function(event) {
    event.preventDefault();
    if ($("td").hasClass("highlighted")) {
      $("td").removeClass("highlighted");
    }
  });

  // Start Stop & Menu buttons

  $('#startButton').on('click', function(event) {
    event.preventDefault();
    $('.startPageWrapper .highlighted').each(function() {
      userHands.push($(this).text());
    });
    $( ".startPageWrapper" ).addClass("hidden");
    $(".quizArea").removeClass("hidden");
    cardPicker();
  });

  $('#stopButton').on('click', function(event) {
    event.preventDefault();
    ($(".quizArea").addClass("hidden"));
    ($(".reviewPageWrapper").removeClass("hidden"));
    correctHandsPlayed();
    wrongHandsPlayed();
    $('.reviewGrid').append(handsTable);
    $.each(userHands, function() {
      $('.reviewPageWrapper .ranges-grid td:contains("' + this + '")').addClass("highlighted");
    });
    $.each(wrongHands, function() {
      $('.reviewPageWrapper .ranges-grid td:contains("' + this + '")').addClass("highlightedWrong");
    });
  }); 

});