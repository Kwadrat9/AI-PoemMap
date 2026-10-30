# AI-PoemMap
Poem Map is a single-file, zero-dependency web app for categorizing poems on a visual 2D canvas. Everything runs locally in the browser — no backend, no build step, no installation. Drop index.html into Chrome and it works.

What it does

Poems are represented as colored rectangles on an SVG map. You can arrange them freely, group them into clusters, and connect related pieces with labeled lines. Each poem stores not just title and text, but its sensory fingerprint: music, feeling, smell, color, and an optional image. That's the core idea — treat a poem as a multi-sensory object and let the map reveal patterns across those dimensions.
Features

    Sidebar form — title, text, music, feeling, smell, color picker, image (URL or drag-and-drop file, 2 MB limit)

    Card list — all poems with color swatch, title, feeling; click to select and highlight on the map

    SVG map — draggable poem rectangles, semi-transparent cluster rectangles, connection lines with optional labels

    Clusters — create named groups with auto-assigned palette colors; drop a poem inside to snap it into a grid layout; clusters auto-expand as they fill

    Connections — "Connect" mode: click poem A, then poem B, add a label; click a line to delete

    Auto-link by tag — one click wires together all poems sharing the same feeling or smell, drawn as dashed cyan lines to distinguish them from manual links

    Pan & zoom — Ctrl+scroll to zoom at cursor, drag empty space to pan, +/- and reset buttons

    Context menus — right-click a poem (edit / remove from cluster / delete), a cluster (rename / delete), or a connection (delete)

    Persistence — auto-save to localStorage (debounced 300 ms), JSON export/import with structure validation and overwrite confirmation

    Dark theme with violet/cyan accent, responsive: sidebar collapses to a drawer below 900 px, toast notifications for all actions

Technical constraints

    One file: index.html — all CSS in <style>, all JS in <script>

    Vanilla ES2020+, no frameworks, no libraries, no build step

    SVG for the map (not canvas) — element-level events required

    Storage key poem-map-v1, version field reserved for future migrations

    Zero external requests (except user-supplied image URLs)

Design notes

    Poem and cluster x,y are top-left corners; consistent for both types

    Drag uses a 5 px threshold to separate click (select / connect) from move

    During drag only the moved element and its incident connections update — full re-render happens on drop

    Connection lines have a 14 px transparent hit area for easy clicking

    auto connections render dashed to distinguish from manual ones; auto-link deduplicates pairs and skips existing links

    Text color on poem cards auto-adjusts via luminance for readable contrast on any background

Use case

Built for a high-school student exploring poetry through sensory associations — but it works for anyone who wants to see relationships between creative works spatially rather than in a list. Export the JSON and you have a portable, human-readable snapshot of your entire map.

Fully made by Deepseek.
