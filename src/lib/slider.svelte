<script>
    let { children } = $props();

    let container = $state();
    let carousel = $state();
    let grabbing = $state( false );
	let index = $state( 0 );

    const grabStart = ( e ) => {
        console.log( "grabbing!" );

        grabbing = true;
        index = -1;

        e.preventDefault();
    };

    const grabEnd = ( e ) => {
        console.log( "end grab..." );
        grabbing = false;

        if ( container !== undefined && carousel !== undefined ) {
            const scroll = container.scrollLeft;
            const mid = container.offsetWidth / 2;
    
            for ( let i = 0; i < carousel.children.length - 1; i++ ) {
                const el = carousel.children[ i ];
                const next_el = carousel.children[ i + 1 ];

                if ( next_el === undefined ) {
                    index = i;
                    return;
                };
    
                const right = el.offsetLeft + el.offsetWidth - scroll;

                if ( right >= 0 ) {
                    index = right > mid ? i : i + 1;
                    break;
                }
            }
        }

        e.preventDefault();
    };

    const handleDrag = ( e ) => {
        if ( !grabbing || container === undefined ) return;

        container.scrollLeft -= e.movementX;
    };


    $effect( () => {
        if ( carousel === undefined ) return;

        const i = index % carousel.children.length;
        const child = carousel.children[ i ];

        if ( typeof child !== "undefined" )
            child.scrollIntoView( { "behavior": "smooth" } );
    } );

    const scrollLeft = () => index--;
    const scrollRight = () => index++;
</script>

<div bind:this={container} class="w-full h-full min-h-[450px] rounded overflow-hidden bg-black/50">
    <div bind:this={carousel} onmousedown={ grabStart } onmouseup={ grabEnd } onmouseleave={ grabEnd } onmousemove={ handleDrag } class="w-full h-full flex flex-row transition-transform {grabbing ? "cursor-grabbing" : "cursor-grab"}" role="listbox" tabindex="0">
        {@render children?.()}
    </div>

    <button onclick={ scrollLeft } class="rounded-l absolute left-0 inset-y-0 w-8 text-4xl transition bg-black/25 hover:bg-black/50 cursor-pointer">&lsaquo;</button>
    <button onclick={ scrollRight } class="rounded-r absolute right-0 inset-y-0 w-8 text-4xl transition bg-black/25 hover:bg-black/50 cursor-pointer">&rsaquo;</button>

    <div class="absolute bottom-5 w-full text-center pointer-events-none">
        <div class="w-4 h-4 mx-1 inline-block rounded-full transition-colors"></div>
    </div>
</div>