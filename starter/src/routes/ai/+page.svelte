<script>
    let text="";
    /**
	 * @type {string | import("axios").AxiosResponse<import("openai").CreateCompletionResponse, any> | undefined}
	 */
    let output;
	import { Card, Label,Input, P, Button } from 'flowbite-svelte';
    import { Configuration, OpenAIApi } from 'openai';

    const configuration = new Configuration({
        apiKey: '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'
    });
    const openai = new OpenAIApi(configuration);
    const serve = async () => {
        output = await openai.createCompletion({
            model: 'text-davinci-002',
            prompt: text,
            max_tokens: 2000,
            temperature: 0.6
        });
        output = output.data.choices[0].text;
        text=""
    };
</script>

<div class="grid md:grid-cols-2">
    <Card>
        <Label>
        <Label>
            Enter Your Query:
            <Input bind:value={text} id="large-input" size="lg" placeholder="Query?" />
        </Label>
        <Label>
            <Button on:click={serve}>Submit</Button>
        </Label>
    </Label>
    </Card>
    {#if output}
    <Card>
        <Label>
            <P>
                {output}
            </P>
        </Label>
    </Card>
    {/if}
</div>

