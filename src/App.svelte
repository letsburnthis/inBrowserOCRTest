<script>
    /* eslint-disable */
	import  Tesseract  from 'tesseract.js';
    
    
   
    let imgText = '';

    function recognize(){
        console.log('function started');
        const img = document.getElementById('input').files[0];
        console.log('got selected file');
        Tesseract.recognize(
        img,
        'eng',
        { logger: m => imgText=m.status+" "+Math.floor(m.progress*100)+"% complete." }
        ).then(({ data: { text } }) => {
            console.log(text);
            imgText=text;
        })
        



    }



    





</script>




<div id="app">
    <p>Choose an image file on your computer to run inbrowser OCR on. Nothing ever leaves your computer.</p>
    
    <!--allows you to select a file on local computer, this file path is then accessed through pure javascript as "input"-->
    <!--could use a v-on:change to automatically run ocr but keeping them seperate just to show both steps-->
    <input type="file" id="input">
    <button on:click={recognize}>recognize</button>

   {#if imgText != ''}
    <p>{imgText}</p>
   {/if} 
</div>