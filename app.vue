<script setup lang="tsx">
const isCardRed = ref(true);

function updateStyle() {
    isCardRed.value = !isCardRed.value;
}

const CardDescription = (props: { name: string; title: string }) => (
    <>
        <h3 class="mt-6 text-base font-semibold leading-7 tracking-tight text-white">{props.name}</h3>
        <p class="text-sm leading-6 text-yellow-400">{props.title}</p>
    </>
);

const CardButton = (props: { action: () => any }, components: { slots: any }) => (
    <div class="mt-6 flex justify-center gap-x-6">
        <button
            onClick={props.action}
            type="submit"
            class="flex-none rounded-md bg-yellow-500 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-yellow-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-yellow-500"
        >
            {components.slots.default()}
        </button>
    </div>
);

const Card = (props: { toggleColour: boolean }, components: { slots: any }) => (
    <>
        <div class={"rounded-2xl px-8 py-10 w-80 " + `${props.toggleColour ? "bg-red-800" : "bg-yellow-800"}`}>
            {components.slots.default()}
        </div>
    </>
);
</script>

<template>
    <div class="flex justify-center p-4">
        <Card :toggleColour="isCardRed">
            <CardImage
                src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA9&auto=format&fit=facearea&facepad=8&w=1024&h=1024&q=80"
            />
            <CardDescription name="Lopez Simba" title="Human Resources" />
            <CardButton :action="updateStyle">Switch Colour</CardButton>
        </Card>
    </div>
</template>
