
<script>
	let sentence = '';
	const nospchar = /[^A-Za-z\s]+/g;
	const dashes = /-/g;
	const spaces = /\s\s+/g;
	import {bible} from './wordlist.json';
	
	let slength = 0;
	let words_in_bible = 0;
	let fsentence = null;
	
	function a(){
		words_in_bible = 0;
		fsentence = sentence.trim().toLowerCase().replace(dashes, ' ').replace(nospchar, '').replace(spaces, ' ').split(' ');
		slength = fsentence.length;
		for(let i = 0; i < fsentence.length; i++){
			if(fsentence[i] == ""){
				//fsentence.splice(i,1);
				//i--;
				slength--;
				continue;
			}
			if(bible.includes(fsentence[i])){
				words_in_bible++;
			}
		}
	}
	
</script>
<svelte:head>
<!-- HTML Meta Tags -->
<title>Are those words in the Bible?</title>
<meta name="description" content="None of those words are in the Bible; or are they?">

<!-- Google / Search Engine Tags -->
<meta itemprop="name" content="Are those words in the Bible?">
<meta itemprop="description" content="None of those words are in the Bible; or are they?">

<!-- Facebook Meta Tags -->
<meta property="og:url" content="https://rattus.tech">
<meta property="og:type" content="website">
<meta property="og:title" content="Are those words in the Bible?">
<meta property="og:description" content="None of those words are in the Bible; or are they?">

<!-- Twitter Meta Tags -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Are those words in the Bible?">
<meta name="twitter:description" content="None of those words are in the Bible; or are they?">

</svelte:head>

<center><h1>"None of those words are in the Bible."</h1></center>

<center><textarea bind:value={sentence} on:input={e => a()}></textarea></center>
<br>
<center>Your sentence has {slength} {slength == 1 ? "word" : "words"}. {words_in_bible == 0 ? "None" : words_in_bible} of them {words_in_bible == 1 ? "is" : "are"} in the Bible.</center>
<center>Your sentence is {slength == 0 ? "???" : words_in_bible/slength*100}% holy.</center>
<br>
<br>
<br>
<center>Made with &#128514; by Jeremy Mausman</center>
