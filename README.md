<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<style>
body {margin:0;}
* {outline:none;box-sizing:border-box;}
#hand {position:absolute;top:100px;left:25px;right:25px;height:450px;overflow:auto;border:2px solid black;}
#discard {position:absolute;top:600px;left:25px;right:25px;height:450px;overflow:auto;border:2px solid black;}
</style>
</head>
<body>
<h1>Card Games Program ♠♣♥♦</h1>
<div id="hand"></div>
<div id="discard"></div>
<button onclick="draw()">Draw</button>
<button onclick="shuffle()">Shuffle</button>
<button onclick="discardDraw()">Discard Draw</button>
<input id="discardCardInput"><button onclick="discardCard(document.getElementById('discardCardInput').value.toLowerCase())">Discard Card</button>
<input id="placeCardDiscard"><button onclick="placeCardDiscard(document.getElementById('placeCardDiscard').value.toLowerCase())">Place A Card In The Discard Pile</button>
<input id="removeDiscardCard"><button onclick="removeDiscardCard(document.getElementById('removeDiscardCard').value.toLowerCase())">Remove A Card From The Discard Pile</button>
<a href="https://www.roblox.com/games/5012201557/Tower-Wars-Hacker-pistol-Roblux-TNT">Play tower wars on roblox!</a>
<script>
//Publish so it is available for free, but with OWN ADS
//♠♣♥♦
//Use buttons to do different actions to allow most types of card games
var cards = [
"ace of spades","ace of clubs","ace of hearts","ace of diamonds",
"2 of spades","2 of clubs","2 of hearts","2 of diamonds",
"3 of spades","3 of clubs","3 of hearts","3 of diamonds",
"4 of spades","4 of clubs","4 of hearts","4 of diamonds",
"5 of spades","5 of clubs","5 of hearts","5 of diamonds",
"6 of spades","6 of clubs","6 of hearts","6 of diamonds",
"7 of spades","7 of clubs","7 of hearts","7 of diamonds",
"8 of spades","8 of clubs","8 of hearts","8 of diamonds",
"9 of spades","9 of clubs","9 of hearts","9 of diamonds",
"10 of spades","10 of clubs","10 of hearts","10 of diamonds",
"jack of spades","jack of clubs","jack of hearts","jack of diamonds",
"queen of spades","queen of clubs","queen of hearts","queen of diamonds",
"king of spades","king of clubs","king of hearts","king of diamonds"
]
var unshuffledDeck = []
unshuffledDeck = unshuffledDeck.concat(cards)
var discard = []
var hand = []
function shuffle() {
deck = []
unshuffledDeck = []
unshuffledDeck = unshuffledDeck.concat(cards)
var i = 0
var c = ""
var n = 52
while(i < 52) {
c = unshuffledDeck[Math.floor(Math.random()*n)]
unshuffledDeck.splice(unshuffledDeck.indexOf(c),1)
//https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice
n = n - 1
deck.push(c)
i = i + 1
}
hand = []
document.getElementById("hand").innerHTML = "Hand: " + createCards(hand)
discard = []
document.getElementById("discard").innerHTML = "Discard: " + createCards(discard)
}

function draw() {
//https://www.w3schools.com/js/js_array_methods.asp
var l = deck.length
if(l != 0) {
hand.unshift(deck.shift())
document.getElementById("hand").innerHTML = "Hand: " + createCards(hand)
}
else {
return("empty")
}
}

function discardCard(card) {
if(hand.indexOf(card) != -1) {
hand.splice(hand.indexOf(card),1)
discard.unshift(card)
document.getElementById("discard").innerHTML = "Discard: " + createCards(discard)
document.getElementById("hand").innerHTML = "Hand: " + createCards(hand)
}
else {
return("empty")
}
}

function discardDraw() {
if(discard.length != 0) {
hand.unshift(discard.shift(discard[0]))
document.getElementById("discard").innerHTML = "Discard: " + createCards(discard)
document.getElementById("hand").innerHTML = "Hand: " + createCards(hand)
}
else {
return("empty")
}
}

function createCards(cards) {
//♠♣♥♦
var l = cards.length
var i = 0
var cards2 = ""
var suit = ""
var suitName = ""
var card = ""
var card1 = ""
while(i < l) {
if(cards[i].indexOf("clubs") != -1) {
suit = "♣"
suitName = "clubs"
}
else if(cards[i].indexOf("spades") != -1) {
suit = "♠"
suitName = "spades"
}
else if(cards[i].indexOf("diamonds") != -1) {
suit = "♦"
suitName = "diamonds"
}
else {
suit = "♥"
suitName = "hearts"
}
card = cards[i]
card = card.split("Of " + suitName)
card = card[0]
card1 = card[0]
if(card[1] != "a" && card[1] != "u" && card[1] != "i" && card[1] != "c") {card1 = card1 + card[1];}
cards2 += "<div style='border:1px solid black;height:300px;width:200px;font-family:arial;position:absolute;left:"+String((i*225)%1125)+"px;top:"+String(50+Math.floor(i/5)*325)+"px;'><p style='font-size:50px;margin-top:0px;'>"+suit+"</p><p style='text-align:center;font-size:80px;margin-top:0px;'>"+card1.toUpperCase()+"</p><br><p style='text-align:right;font-size:50px;margin-top:-60px;'>"+suit+"</p></div>"
i = i + 1
}
return(cards2)
}
	

function placeCardDiscard(card) {
discard.unshift(card)
document.getElementById("discard").innerHTML = "Discard: " + createCards(discard)
}


function removeDiscardCard(card) {
if(discard.indexOf(card) != -1) {
discard.splice(discard.indexOf(card),1)
document.getElementById("discard").innerHTML = "Discard: " + createCards(discard)
}
else {
return("empty")
}
}


shuffle()
document.getElementById("hand").innerHTML = "Hand: " + createCards(hand)
document.getElementById("discard").innerHTML = "Discard: " + createCards(discard)
</script>
</body>
</html>
