<script>
    import Panel from '$lib/Panel.svelte';
    import  "../../node_modules/commonmark/dist/commonmark.js"
    import { onMount } from 'svelte';
    var reader = new commonmark.Parser();
	var writer = new commonmark.HtmlRenderer();
	var parsed = reader.parse("Hello *world*"); // parsed is a 'Node' tree
	// transform parsed if you like...
    var result = writer.render(parsed); // result is a String
    
    var textarea
    var handleClick
    onMount(() => {
        textarea = document.getElementById("eidtor")

        handleClick = ()=>{
            var parsed = reader.parse(textarea.value); // parsed is a 'Node' tree
            // transform parsed if you like... 
            result = writer.render(parsed); // result is a String
            // writer.render(textarea.value)
            console.log(result)

        }
        
	});
	// commonmark.Parser
</script>

<div >
    <Panel>
        <!-- <button on:click={handleClick}>
            eval
        </button> -->
        &nbsp;
        <div class="mb-3">
            <div style="width:50%; float:left">
                <label for="title" class="form-label">Post Title</label>
                <input type="email" class="form-control" id="title" > 
            </div>
            <div style="width:50%; float:left">
                <label for="author" class="form-label">Author Name</label>
                <input type="email" class="form-control" id="author" > 
            </div>
            
          </div>
          <div class="mb-3">
            <label for="eidtor" class="form-label">Post Content</label>
            <textarea on:change={handleClick} class="form-control" id="eidtor" rows="20"></textarea>
          </div>
        <!-- <textarea style="width:100%;height:30vw" on:change={handleClick} id="eidtor"></textarea> -->
        <h1>Post Preview</h1>
        <hr style="border: 2px solid black;">
        {@html result}
    </Panel>
    

</div>