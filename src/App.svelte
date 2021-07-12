<script>
    import Header from "./UI/Header.svelte";
    import MeetupGrid from "./Meetups/MeetupGrid.svelte";
    import TextInput from "./UI/TextInput.svelte";
    import Button from "./UI/Button.svelte";
    import EditMeetup from "./Meetups/EditMeetup.svelte";

    let meetups = [
        {
            id: "m1",
            title: "Codign Bootcamp",
            subtitle: "Learn to code in 2 hours",
            description: "Some experts will teach you how to code",
            imageUrl:
                "https://images.unsplash.com/photo-1531482615713-2afd69097998?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80",
            address: "27th Nerd Road, 32523 New York",
            contactEmail: "code@Text.com",
            isFavorite: false,
        },
        {
            id: "m2",
            title: "Swim Together",
            subtitle: "Let's go for some swimming",
            description: "We will swim a lot",
            imageUrl:
                "https://images.unsplash.com/photo-1560090995-01632a28895b?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1049&q=80",
            address: "12th Pool Road, 32523 New York",
            contactEmail: "swim@Text.com",
            isFavorite: false,
        },
    ];

    let editMode;

    function addMeetup() {
        const newMeetup = {
            id: Math.random().toString(),
            title: title,
            description: description,
            subtitle: subtitle,
            imageUrl: imageUrl,
            contactEmail: email,
            address: address,
        };

        meetups = [newMeetup, ...meetups];
    }

    function toggleFavorite(event) {
        // Tomo del event el detail que contiene el id del meetup
        const id = event.detail;
        // Traigo la info del meetup cuyo id coincide con el que disparo el evento
        const updatedMeetup = { ...meetups.find((m) => m.id === id) };
        // el nuevo valor para isfavorite es el opuesto al que habia antes
        updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
        const meetupIndex = meetups.findIndex((m) => m.id === id);
        const updatedMeetups = [...meetups];
        updatedMeetups[meetupIndex] = updatedMeetup;
        meetups = updatedMeetups;
    }
</script>

<Header />

<main>
    <Button caption="New Meetup" on:click={() => editMode = "add"} />
    {#if editMode == "add"}
        <EditMeetup />
    {/if}
    <MeetupGrid {meetups} on:togglefavorite={toggleFavorite} />
</main>

<style>
    main {
        margin-top: 5rem;
    }
</style>
