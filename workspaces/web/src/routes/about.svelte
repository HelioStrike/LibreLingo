<script context="module">
  import MarkDownPage, { getMarkDownData } from "../components/MarkDownPage"
  import { _ } from "svelte-i18n"

  export async function preload(page, session) {
    return {
      readmeHTML: (
        await getMarkDownData(await import("../../../../README.md"))
      ).contents.split("<h2>Tech stack</h2>")[0],
    }
  }
</script>

<script>
  export let readmeHTML
</script>

<MarkDownPage {readmeHTML} title="About LibreLingo" description="{$_('about.meta.description')}" />
