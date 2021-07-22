<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    import TextInput from "../UI/TextInput.svelte";
    import Button from "../UI/Button.svelte";
    import Modal from "../UI/Modal.svelte";
    import { isEmpty, isValidEmail } from "../helpers/validation";

    let title = "";
    let subtitle = "";
    let address = "";
    let description = "";
    let imageUrl = "";
    let email = "";

    $: titleValid = !isEmpty(title);
    $: subtitleValid = !isEmpty(subtitle);
    $: addressValid = !isEmpty(address);
    $: descriptionValid = !isEmpty(description);
    $: imageValid = !isEmpty(imageUrl);
    $: emailValid = isValidEmail(email);
    $: formIsValid =
        titleValid &&
        subtitleValid &&
        addressValid &&
        descriptionValid &&
        imageValid &&
        emailValid;

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

    function cancel() {
        dispatch("cancel");
    }
</script>

<Modal title="Edit Meetup Data" on:cancel>
    <form on:submit|preventDefault={submitForm}>
        <TextInput
            id="title"
            label="Title"
            valid={titleValid}
            validityMessage="Pease enter a valid title"
            value={title}
            on:input={(event) => (title = event.target.value)}
        />
        <TextInput
            id="subtitle"
            label="Subtitle"
            validityMessage="Pease enter a valid subtitle"
            valid={subtitleValid}
            value={subtitle}
            on:input={(event) => (subtitle = event.target.value)}
        />
        <TextInput
            id="address"
            label="Address"
            validityMessage="Pease enter a valid address"
            valid={addressValid}
            value={address}
            on:input={(event) => (address = event.target.value)}
        />
        <TextInput
            id="imageUrl"
            label="Image Url"
            validityMessage="Pease enter a valid image url"
            valid={imageValid}
            value={imageUrl}
            on:input={(event) => (imageUrl = event.target.value)}
        />
        <TextInput
            type="email"
            id="email"
            label="Email"
            valid={emailValid}
            validityMessage="Pease enter a valid email"
            value={email}
            on:input={(event) => (email = event.target.value)}
        />
        <TextInput
            controlType="textarea"
            id="description"
            label="Description"
            valid={descriptionValid}
            validityMessage="Pease enter a valid description"
            bind:value="{description}"
            on:input={(event) => (description = event.target.value)}
        />
    </form>
    <div slot="footer">
        <Button type="button" mode="outline" on:click={cancel}>Cancel</Button>
        <Button type="button" on:click={submitForm} disabled={!formIsValid}>Save</Button>
    </div>
</Modal>

<style>
    form {
        width: 100%;
    }
</style>
