<script>
    import Header from './UI/Header.svelte';
    import MeetupGrid from './Meetups/MeetupGrid.svelte';

    const meetups = [
        {
            id: 'm1',
            title: 'Codign Bootcamp',
            subtitle: 'Learn to code in 2 hours',
            description: 'Some experts will teach you how to code',
            imageUrl: 'https://images.unsplash.com/photo-1531482615713-2afd69097998?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80',
            address: '27th Nerd Road, 32523 New York',
            contactEmail: 'code@Text.com'
        },
        {
            id: 'm2',
            title: 'Swim Together',
            subtitle: 'Let\'s go for some swimming',
            description: 'We will swim a lot',
            imageUrl: 'https://images.unsplash.com/photo-1560090995-01632a28895b?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1049&q=80',
            address: '12th Pool Road, 32523 New York',
            contactEmail: 'swim@Text.com'
        }
    ]
</script>

<style>
</style>


<Header />

<MeetupGrid {meetups}/>

