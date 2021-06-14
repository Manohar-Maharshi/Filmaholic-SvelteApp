


<buttom class="favorites" data-tooltip="Favorites" data-tooltip-location="bottom">
	<span>Favorites</span>
	<svg type="color-fill-current" width="20px" height="20px" version="1.1" viewBox="0 0 20 20" x="0px" y="0px" class="ScSvg-sc-1j5mt50-1 BNeRR"><g><path fill-rule="evenodd" d="M9.171 4.171A4 4 0 006.343 3H6a4 4 0 00-4 4v.343a4 4 0 001.172 2.829L10 17l6.828-6.828A4 4 0 0018 7.343V7a4 4 0 00-4-4h-.343a4 4 0 00-2.829 1.172L10 5l-.829-.829z" clip-rule="evenodd"></path></g></svg>
</buttom>


<style>
	.favorites{
		display: flex;
		align-items: center;
		padding:0.3rem 0.5rem;
		border-radius: 0.2rem;
		margin-left: 0.2rem;
		color: #efeff1;
		background-color: transparent;
		border: none;
		outline:none;
		font-family: inherit;
		font-weight: 600;
		font-size: inherit;
		color: #ffff;
		cursor: pointer;
	}
	.favorites{
		color: #ffff;
		background-color: #9147ff;
	}
	.favorites svg{
		margin-left: 0.5rem;
		width: 1rem;
		height: 1rem;
		text-align: center;
		fill: #ffff;
	}
	:global([data-tooltip]) {
	  position: relative;
	  z-index: 100;
	}

	/* Positioning and visibility settings of the tooltip */
	:global([data-tooltip]:before),
	:global([data-tooltip]:after) {
	  position: absolute;
	  visibility: hidden;
	  opacity: 0;
	  left: 50%;
	  bottom: calc(100% + 5px); /* 5px is the size of the arrow */
	  pointer-events: none;
	  transition: 0.1s;
	  will-change: transform;
	}

	/* The actual tooltip with a dynamic width */
	:global([data-tooltip]:before) {
	  content: attr(data-tooltip);
	  padding: 2px 5px;
	  width: max-content;
	  white-space: pre-wrap;
	  border-radius: 3px;
	  font-size: 14px;
	  background-color: #fff;
	  color: #000;
	  text-align: center;
	  box-shadow: 0px 0px 24px rgba(0, 0, 0, 0.2);
	  transform: translate(-50%, -5px) scale(0.5);
	}

	/* Tooltip arrow */
	:global([data-tooltip]:after) {
	  content: '';
	  border-style: solid;
	  border-width: 5px 5px 0px 5px;
	  border-color: #fff;
	  color: #ffff;
	  transition-duration: 0s; 
	  transform-origin: top; 
	  transform: translateX(-50%) scaleY(0);
	}

	/* Tooltip becomes visible at hover */
	:global([data-tooltip]:hover:before),
	:global([data-tooltip]:hover:after) {
	  visibility: visible;
	  opacity: 1;
	}
	/* Scales from 0.5 to 1 -> grow effect */
	:global([data-tooltip]:hover:before) {
	  transition-delay: 0.1s;
	  transform: translate(-50%, -5px) scale(1);
	}
	/* 
	  Arrow slide down effect only on mouseenter (NOT on mouseleave)
	*/
	:global([data-tooltip]:hover:after) {
	  transition-delay: 0.1s;
	  transition-duration: 0.1s;
	  transform: translateX(-50%) scaleY(1);
	}
	/* RIGHT */
	:global([data-tooltip-location="right"]:before),
	:global([data-tooltip-location="right"]:after) {
	  left: calc(100% + 5px);
	  bottom: 50%;
	}

	:global([data-tooltip-location="right"]:before) {
	  transform: translate(5px, 50%) scale(0.5);
	}
	:global([data-tooltip-location="right"]:hover:before) {
	  transform: translate(5px, 50%) scale(1);
	}

	:global([data-tooltip-location="right"]:after) {
	  border-width: 5px 5px 5px 0px;
	  border-color: transparent rgba(55, 64, 70, 0.9) transparent transparent;
	  transform-origin: right;
	  transform: translateY(50%) scaleX(0);
	}
	:global([data-tooltip-location="right"]:hover:after) {
	  transform: translateY(50%) scaleX(1);
	}



	/* BOTTOM */
	:global([data-tooltip-location="bottom"]:before),
	:global([data-tooltip-location="bottom"]:after) {
	  top: calc(100% + 5px);
	  bottom: auto;
	}

	:global([data-tooltip-location="bottom"]:before) {
	  transform: translate(-50%, 5px) scale(0.5);
	}
	:global([data-tooltip-location="bottom"]:hover:before) {
	  transform: translate(-50%, 5px) scale(1);
	}

	:global([data-tooltip-location="bottom"]:after) {
	  border-width: 0px 5px 5px 5px;
	  border-color: transparent transparent rgba(55, 64, 70, 0.9) transparent;
	  transform-origin: bottom;
	}

</style>