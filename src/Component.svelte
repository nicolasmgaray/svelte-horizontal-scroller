<style>
    .HorizontalScroll {
        width: var(--horizontal-scroller-width, auto);
        cursor: grab;
        scroll-snap-type: x mandatory;
        -webkit-overflow-scrolling: touch;
        scroll-behavior: smooth;
        overflow-x: auto;
        padding: var(--horizontal-scroller-padding, 1em);
        display: flex;
        gap: var(--horizontal-scroller-gap, 1em);
    }

    .HorizontalScroll::-webkit-scrollbar {
        display: none;
    }

    .HorizontalScroll > :global(*) {
        flex-grow: 0;
        flex-shrink: 0;
    }
</style>

<script>
    let horizontalScroll;
    let pos = { left: 0, x: 0 };

    function mouseDownHandler(e) {
        // Set initial scroll and mouse position
        pos = {
            left: horizontalScroll.scrollLeft,
            x: e.clientX,
        };
        // Remove CSS styles
        horizontalScroll.style.scrollBehavior = 'auto';
        horizontalScroll.style.cursor = 'grabbing';
        horizontalScroll.style.userSelect = 'none';
        horizontalScroll.style.scrollSnapType = 'none';
        // Add handlers
        document.addEventListener('mousemove', mouseMoveHandler);
        document.addEventListener('mouseup', mouseUpHandler);
    };

    function mouseUpHandler() {
        // Remove listeners
        document.removeEventListener('mousemove', mouseMoveHandler);
        document.removeEventListener('mouseup', mouseUpHandler);
        // Restore css
        horizontalScroll.style.scrollSnapType = 'x mandatory';
        horizontalScroll.style.cursor = 'grab';
        horizontalScroll.style.removeProperty('user-select');
        horizontalScroll.style.scrollBehavior = 'smooth';
    };

    function mouseMoveHandler(e) {
        // Update scroll based on mouse movement
        const dx = e.clientX - pos.x;
        horizontalScroll.scrollLeft = pos.left - dx;
    };
</script>

<div class="HorizontalScroll"
     on:mousedown={mouseDownHandler}
     bind:this={horizontalScroll}>
    <slot/>
</div>