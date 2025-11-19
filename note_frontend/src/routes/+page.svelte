<script lang="ts">
  import Sidebar from '$lib/components/Sidebar.svelte';
  import Editor from '$lib/components/Editor.svelte';
  import EmptyState from '$lib/components/EmptyState.svelte';
  import {
    initNotes,
    notesStore,
    activeNoteId,
    activeNote,
    createNote
  } from '$lib/stores/notes';

  // Initialize notes on mount (client only)
  $effect(() => {
    if (typeof window !== 'undefined') {
      initNotes();
    }
  });

  // Keyboard shortcuts: Ctrl/Cmd+N for new, Ctrl/Cmd+S is handled in Editor
  function onGlobalKeydown(e: KeyboardEvent) {
    const isNew = (e.metaKey || e.ctrlKey) && e.key.toLowerCase() === 'n';
    if (isNew) {
      e.preventDefault();
      createNote();
    }
  }
</script>

<svelte:head>
  <title>Simple Notes</title>
  <meta name="description" content="Create, view, edit and delete notes. Markdown supported." />
</svelte:head>

<svelte:window onkeydown={onGlobalKeydown} />

<div class="page">
  <Sidebar notes={$notesStore} currentId={$activeNoteId} />
  {#if $activeNote}
    <Editor note={$activeNote} />
  {:else}
    <EmptyState onCreate={createNote} />
  {/if}
</div>

<style>
  .page {
    display: contents; /* layout grid is defined by +layout.svelte main */
  }
</style>
