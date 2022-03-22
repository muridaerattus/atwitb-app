
<script>
	let sentence = '';
	const nospchar = /[^A-Za-z\s]+/;
	const dashes = /-/;
	import {bible} from './wordlist.json';
	
	let slength = 0;
	let words_in_bible = 0;
	let fsentence = null;
	
	function a(){
		words_in_bible = 0;
		fsentence = sentence.toLowerCase().replace(dashes, ' ').replace(nospchar, '').split(' ');
		slength = fsentence.length;
		for(let i = 0; i < slength; i++){
			if(bible.includes(fsentence[i])){
				words_in_bible++;
			}
		}
	}
	
</script>

<center><h1>"None of those words are in the Bible."</h1></center>

<center><textarea bind:value={sentence} on:input={e => a()}></textarea></center>
<br>
<center>Your sentence has {slength} {slength == 1 ? "word" : "words"}. {words_in_bible == 0 ? "None" : words_in_bible} of them {words_in_bible == 1 ? "is" : "are"} in the Bible.</center>
<center>Your sentence is {slength == 0 ? "???" : words_in_bible/slength*100}% holy.</center>
<br>
<br>
<br>
<center>Made with &#128405; by Jeremy Mausman</center>
