<script lang="ts">
    // import type { PageData } from './$types';
    import { Button } from "$lib/components/ui/button";
    import * as Dialog from "$lib/components/ui/dialog";

    let rejectorContainer: HTMLDivElement

    function plusOrMinus() {
        return Math.round(Math.random()) ? 1 : -1
    }

    function randomMovement() {
        let topPosition = (Math.ceil(Math.random() * 150) + 100) * plusOrMinus()
        let leftPosition = (Math.ceil(Math.random() * 150) + 100) * plusOrMinus()
        rejectorContainer.style.top = `${topPosition}px`
        rejectorContainer.style.left = `${leftPosition}px`
    }

    function returnRejectButton() {
        rejectorContainer.style.top = `0px`
        rejectorContainer.style.left = `0px`
    }
    
    // export let data: PageData;
</script>

<div class="grid grid-cols-1 text-center h-[80vh]">
    <div class=" self-center">
        <h1 class="text-4xl font-bold mb-4">Will You Be My Valentine?</h1>
        <div class="grid grid-cols-2 px-64 gap-32">
            <Dialog.Root>
                <Dialog.Trigger class="w-full">
                    <Button class="w-full" on:click={returnRejectButton}> Yes </Button>
                </Dialog.Trigger>
                <Dialog.Content>
                    <Dialog.Header>
                        <Dialog.Title>"Key" Date Obtained!</Dialog.Title>
                        <Dialog.Description>
                            It seems your valentine has a mysterious activity in mind next valentine's day.
                            Keep your wits and eyes sharp!
                        </Dialog.Description>
                    </Dialog.Header>
                    <img src="/key.png" class="p-24" alt="A Mysterious Key">
                </Dialog.Content>
            </Dialog.Root>
            <div class="relative">
                <div class="w-full absolute" bind:this={rejectorContainer} on:pointerenter={randomMovement}>
                    <Button variant='destructive' class="w-full" on:click={randomMovement}> No </Button>
                </div>
            </div>
        </div>
    </div>
</div>