<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    import TextInput from "../UI/TextInput.svelte";
    import Button from "../UI/Button.svelte";

    let title = "";
    let subtitle = "";
    let address = "";
    let description = "";
    let imageUrl = "";
    let email = "";

    function submitForm() {
        dispatch("save", {
            title: title,
            subtitle: subtitle,
            address: address,
            description: description,
            email: email,
            imageUrl: imageUrl,
        });
    }
</script>

<form on:submit|preventDefault={submitForm}>
    <TextInput
        id="title"
        label="Title"
        value={title}
        on:input={(event) => (title = event.target.value)}
    />
    <TextInput
        id="subtitle"
        label="Subtitle"
        value={subtitle}
        on:input={(event) => (subtitle = event.target.value)}
    />
    <TextInput
        id="address"
        label="Address"
        value={address}
        on:input={(event) => (address = event.target.value)}
    />
    <TextInput
        id="imageUrl"
        label="Image Url"
        value={imageUrl}
        on:input={(event) => (imageUrl = event.target.value)}
    />
    <TextInput
        type="email"
        id="email"
        label="Email"
        value={email}
        on:input={(event) => (email = event.target.value)}
    />
    <TextInput
        controlType="textarea"
        id="description"
        label="Descriptionl"
        value={description}
        on:input={(event) => (description = event.target.value)}
    />
    <Button type="submit">Save</Button>
</form>

<style>
    form {
        width: 30rem;
        max-width: 90%;
        margin: auto;
    }
</style>
