
<style>
    #content{
        position: relative;
        left:10vw;
        width:80vw;
    }
</style>

<script>
    import { getStores, navigating, page, session } from '$app/stores';
    import {onMount} from "svelte"
    import  "../../../node_modules/commonmark/dist/commonmark.js"

    var reader = new commonmark.Parser();
	var writer = new commonmark.HtmlRenderer();
    var getStoresResult = getStores()
    var title
    page.subscribe((value)=>{
        title = value.params.title
        console.log(value.params.title)
    })
    var result = "<p>Loading...</p>"
    onMount(()=>{
        fetch("http://localhost:1337/posts?slug="+title)
        .then(response => response.json())
        .then(data =>{
            console.log(data)
            var parsed = reader.parse(data[0].postContent); // parsed is a 'Node' tree
            // transform parsed if you like... 
            result = writer.render(parsed); // result is a String
        });
       
    })
    
</script>



<div id="content">
    {@html result}
</div>