<script>
    import { _ } from '../../i18n.js'

    export let retro = {
        items: [],
        actionItems: [],
    }

    $: workedItems =
        retro.items &&
        retro.items.reduce((prev, item) => {
            if (item.type === 'worked') {
                prev.push(item)
            }
            return prev
        }, [])
    $: improveItems =
        retro.items &&
        retro.items.reduce((prev, item) => {
            if (item.type === 'improve') {
                prev.push(item)
            }
            return prev
        }, [])
    $: questionItems =
        retro.items &&
        retro.items.reduce((prev, item) => {
            if (item.type === 'question') {
                prev.push(item)
            }
            return prev
        }, [])
</script>

<div class="flex flex-grow p-4 dark:text-white">
    <div class="px-4">
        <div class="mb-4">
            <h2 class="text-3xl font-rajdhani">{$_('works')}</h2>
                {#each workedItems as item (item.id)}
                * {item.content} <br/> 
                {/each}
        </div>
        <br/>
        <div class="mb-4">
            <h2 class="text-3xl font-rajdhani">{$_('needsImprovement')}</h2>
                {#each improveItems as item (item.id)}
                * {item.content} <br/> 
                {/each}
        </div>
        <br/>
        <div class="mb-4">
            <h2 class="text-3xl font-rajdhani">{$_('questions')}</h2>
                {#each questionItems as item (item.id)}
                * {item.content} <br/> 
                {/each}
        </div>
        <br/>
        <div class="mb-4">
            <h2 class="text-3xl font-rajdhani">{$_('actionItems_markdown')}</h2>
                {#each retro.actionItems as item (item.id)}
                * {item.content} <br/> 
                {/each}
        </div>
    </div>
</div>
