<script lang="ts">
    import {marked} from "marked";
    import DOMPurify from "dompurify";
    const Prism : any = Window["Prism"];
    import {
    tick,
    onDestroy,
    onMount,
    createEventDispatcher,
    afterUpdate,
  } from 'svelte'
  export let value: string = '# Hello World\n```css\n.hello{\ntop:10px;\n}\n```';

  let markdownBody: HTMLElement;
  // We are not generic, so we can have a bit of liberty setting up markdown like github does.
  marked.setOptions({
    gfm: true,
    tables: true,
    breaks: true,
    pedantic: false,
    smartLists: true,
    smartypants: false,
    sanitizer: DOMPurify.sanitize,
  });

  var htmlOut = marked.parse(value);
  console.log(htmlOut);

  $: html = `${htmlOut}<!--${0}-->`
</script>
<svelte:head>
    <link href="https://unpkg.com/prismjs@1.27.0/themes/prism.min.css" rel="stylesheet"/>
	<link href="https://unpkg.com/prismjs@1.27.0/themes/prism-twilight.min.css" rel="stylesheet"/>
	<link href="https://unpkg.com/prismjs@1.27.0/plugins/line-numbers/prism-line-numbers.min.css" rel="stylesheet"/>
	<link href="https://unpkg.com/prismjs@1.27.0/plugins/toolbar/prism-toolbar.min.css" rel="stylesheet"/>
	<link href="https://unpkg.com/prismjs@1.27.0/plugins/command-line/prism-command-line.min.css" rel="stylesheet"/>
    
    <script src="https://unpkg.com/prismjs@1.27.0/components/prism-core.min.js" ></script>
	<script src="https://unpkg.com/prismjs@1.27.0/plugins/autoloader/prism-autoloader.min.js" ></script>
	<script src="https://unpkg.com/prismjs@1.27.0/plugins/highlight-keywords/prism-highlight-keywords.min.js" ></script>
	<script src="https://unpkg.com/prismjs@1.27.0/plugins/line-numbers/prism-line-numbers.min.js" ></script>
	<script src="https://unpkg.com/prismjs@1.27.0/plugins/toolbar/prism-toolbar.min.js" ></script>
	<script src="https://unpkg.com/prismjs@1.27.0/plugins/command-line/prism-command-line.min.js" ></script>
</svelte:head>
<div bind:this={markdownBody} class="markdown-body">
  {@html html}
</div>


