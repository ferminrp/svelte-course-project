<script>
    import Header from "./UI/Header.svelte";
    import MeetupGrid from "./Meetups/MeetupGrid.svelte";
    import TextInput from "./UI/TextInput.svelte";
    import Button from "./UI/Button.svelte";

    let title = "";
    let subtitle = "";
    let address = "";
    let description = "";
    let imageUrl = "";
    let email = "";

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
        },
    ];

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
</script>

<Header />

<main>
    <form on:submit|preventDefault={addMeetup}>
        <TextInput
            id="title"
            label="Title"
            type="text"
            value="{title}"
            on:input={(event) => (title = event.target.value)}
        />
        <TextInput
            id="subtitle"
            type="text"
            label="Subtitle"
            value="{subtitle}"
            on:input={(event) => (subtitle = event.target.value)}
        />
        <TextInput
            type="text"
            id="address"
            label="Address"
            value="{address}"
            on:input={(event) => (address = event.target.value)}
        />
        <TextInput
            type="text"
            id="imageUrl"
            label="Image Url"
            value="{imageUrl}"
            on:input={(event) => (imageUrl = event.target.value)}
        />
        <TextInput
            type="email"
            id="email"
            label="Email"
            value="{email}"
            on:input={(event) => (email = event.target.value)}
        />
        <TextInput
            controlType="textarea"
            id="description"
            label="Descriptionl"
            value="{description}"
            on:input={(event) => (description = event.target.value)}
        />
        <Button type="submit" caption="Save" />
    </form>
    <MeetupGrid {meetups} />
</main>

<style>
    main {
        margin-top: 5rem;
    }
    form {
        width: 30rem;
        max-width: 90%;
        margin: auto;
    }
</style>
