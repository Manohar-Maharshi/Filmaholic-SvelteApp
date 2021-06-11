<script>
	export let title = "";
</script>


<!-- <h1 class="glitch" data-text="Movie Wiki">{title}</h1> -->
<h1 class="glitch heading heading--stroke" data-text="Movie Wiki">{title}</h1>
<style>
	.heading--stroke {
	  -webkit-text-stroke-width: 1px;
	  -moz-text-stroke-width: 2px;
	  -webkit-text-stroke-color: #efeff1;
	  -moz-text-stroke-color: #772ce8;
	}
	.glitch {
	  text-transform: uppercase;
	  color: #efeff1;
	  font-size: 1.3rem;
	  text-shadow: -1px -1px 5px #772ce8, 2px 2px 5px #772ce8;
	  animation: glitch-skew 5s infinite linear alternate-reverse;
	}
	.glitch::before {
	  content: attr(data-text);
	  position: absolute;
	  top: 0;
	  left: 0;
	  width: 100%;
	  height: 100%;
	  left: 2px;
	  text-shadow: -1px -1px 1px #772ce8, 2px 2px 5px #772ce8;
	  clip: rect(44px, 450px, 56px, 0);
	  animation: glitch-anim 5s infinite linear alternate-reverse;
	}
	.glitch::after {
	  content: attr(data-text);
	  position: absolute;
	  top: 0;
	  left: 0;
	  width: 100%;
	  height: 100%;
	  left: -2px;
	  text-shadow: -1px -1px 1px #772ce8, 2px 2px 1px #772ce8;
	  animation: glitch-anim2 5s infinite linear alternate-reverse;
	}

	@keyframes glitch-anim {
	  0% {
	    clip: rect(42px, 9999px, 33px, 0);
	    transform: skew(0.56deg);
	  }
	  5% {
	    clip: rect(88px, 9999px, 31px, 0);
	    transform: skew(0.56deg);
	  }
	  10% {
	    clip: rect(26px, 9999px, 85px, 0);
	    transform: skew(0.08deg);
	  }
	  15% {
	    clip: rect(85px, 9999px, 40px, 0);
	    transform: skew(0.88deg);
	  }
	  20% {
	    clip: rect(31px, 9999px, 93px, 0);
	    transform: skew(0.15deg);
	  }
	  25% {
	    clip: rect(77px, 9999px, 71px, 0);
	    transform: skew(0.03deg);
	  }
	  30% {
	    clip: rect(88px, 9999px, 62px, 0);
	    transform: skew(0.66deg);
	  }
	  35% {
	    clip: rect(5px, 9999px, 8px, 0);
	    transform: skew(0.06deg);
	  }
	  40% {
	    clip: rect(30px, 9999px, 99px, 0);
	    transform: skew(0.53deg);
	  }
	  45% {
	    clip: rect(23px, 9999px, 100px, 0);
	    transform: skew(0.02deg);
	  }
	  50% {
	    clip: rect(10px, 9999px, 91px, 0);
	    transform: skew(0.03deg);
	  }
	  55% {
	    clip: rect(8px, 9999px, 66px, 0);
	    transform: skew(0.82deg);
	  }
	  60% {
	    clip: rect(21px, 9999px, 66px, 0);
	    transform: skew(0.72deg);
	  }
	  65% {
	    clip: rect(7px, 9999px, 46px, 0);
	    transform: skew(0.39deg);
	  }
	  70% {
	    clip: rect(38px, 9999px, 99px, 0);
	    transform: skew(0.5deg);
	  }
	  75% {
	    clip: rect(63px, 9999px, 71px, 0);
	    transform: skew(0.34deg);
	  }
	  80% {
	    clip: rect(98px, 9999px, 78px, 0);
	    transform: skew(0.69deg);
	  }
	  85% {
	    clip: rect(79px, 9999px, 29px, 0);
	    transform: skew(0.8deg);
	  }
	  90% {
	    clip: rect(27px, 9999px, 76px, 0);
	    transform: skew(0.45deg);
	  }
	  95% {
	    clip: rect(33px, 9999px, 67px, 0);
	    transform: skew(0.67deg);
	  }
	  100% {
	    clip: rect(29px, 9999px, 72px, 0);
	    transform: skew(0.53deg);
	  }
	}
	@keyframes glitch-anim2 {
	  0% {
	    clip: rect(49px, 9999px, 57px, 0);
	    transform: skew(0.68deg);
	  }
	  5% {
	    clip: rect(19px, 9999px, 71px, 0);
	    transform: skew(0.34deg);
	  }
	  10% {
	    clip: rect(34px, 9999px, 85px, 0);
	    transform: skew(0.1deg);
	  }
	  15% {
	    clip: rect(7px, 9999px, 91px, 0);
	    transform: skew(0.87deg);
	  }
	  20% {
	    clip: rect(62px, 9999px, 84px, 0);
	    transform: skew(0.88deg);
	  }
	  25% {
	    clip: rect(77px, 9999px, 53px, 0);
	    transform: skew(0.62deg);
	  }
	  30% {
	    clip: rect(87px, 9999px, 63px, 0);
	    transform: skew(0.11deg);
	  }
	  35% {
	    clip: rect(87px, 9999px, 54px, 0);
	    transform: skew(0.56deg);
	  }
	  40% {
	    clip: rect(68px, 9999px, 51px, 0);
	    transform: skew(0.94deg);
	  }
	  45% {
	    clip: rect(82px, 9999px, 19px, 0);
	    transform: skew(0.02deg);
	  }
	  50% {
	    clip: rect(93px, 9999px, 4px, 0);
	    transform: skew(0.34deg);
	  }
	  55% {
	    clip: rect(6px, 9999px, 79px, 0);
	    transform: skew(0.3deg);
	  }
	  60% {
	    clip: rect(27px, 9999px, 85px, 0);
	    transform: skew(1deg);
	  }
	  65% {
	    clip: rect(68px, 9999px, 18px, 0);
	    transform: skew(0.42deg);
	  }
	  70% {
	    clip: rect(84px, 9999px, 44px, 0);
	    transform: skew(0.62deg);
	  }
	  75% {
	    clip: rect(10px, 9999px, 41px, 0);
	    transform: skew(0.06deg);
	  }
	  80% {
	    clip: rect(62px, 9999px, 58px, 0);
	    transform: skew(0.16deg);
	  }
	  85% {
	    clip: rect(51px, 9999px, 86px, 0);
	    transform: skew(0.97deg);
	  }
	  90% {
	    clip: rect(5px, 9999px, 89px, 0);
	    transform: skew(0.76deg);
	  }
	  95% {
	    clip: rect(60px, 9999px, 90px, 0);
	    transform: skew(0.99deg);
	  }
	  100% {
	    clip: rect(59px, 9999px, 63px, 0);
	    transform: skew(0.06deg);
	  }
	}
	@keyframes glitch-skew {
	  0% {
	    transform: skew(5deg);
	  }
	  10% {
	    transform: skew(0deg);
	  }
	  20% {
	    transform: skew(-4deg);
	  }
	  30% {
	    transform: skew(3deg);
	  }
	  40% {
	    transform: skew(-1deg);
	  }
	  50% {
	    transform: skew(-4deg);
	  }
	  60% {
	    transform: skew(2deg);
	  }
	  70% {
	    transform: skew(-1deg);
	  }
	  80% {
	    transform: skew(-2deg);
	  }
	  90% {
	    transform: skew(3deg);
	  }
	  100% {
	    transform: skew(-2deg);
	  }
	}
</style>