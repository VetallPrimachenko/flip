<template>

    <div
            class="container-fluid p-0 intro"
            :style="{backgroundImage: 'url(src/assets/images/home/home-slide-1.jpg)'}">
        <!--:style="{backgroundImage: 'url(/images/home/home_1.jpg)'}"-->
        <div class="flip d-flex flex-column flip_background-1 pos-absolute"
             ref="flipParent">
            <div class="flip__item d-flex"
                 v-for="(item, key) in flipAnimation.columnElements"
                 ref="flipChild"
                 :key="key">
                <div class="flip__item__elem d-flex "
                     v-for="(elem, keyChild) in item"
                     v-if="flipAnimation.resElementHeight"
                     :class="[
                     	elem.rotateX ? ('rotate-x-' + flipAnimation.rotateCounter) : '',
                        elem.rotateY ? ('rotate-y-' + flipAnimation.rotateCounter) : '',
                        'changeBgItem-' + elem.activeFlip,
                        (keyChild == 0 || keyChild == 1) ? 'change-small-bg-' + elem.activeFlip : '',
                        ((flipAnimation.columnElements[3][0].activeFlip || flipAnimation.columnElements[3][1].activeFlip) == 1 ? false : (key == 3 && (keyChild == 0 || keyChild == 1)) ? 'change-small-bg-color' : '')
                     ]"
                     :key="keyChild"
                     :style="{'background-position-y' : '-' + (key * flipAnimation.resElementHeight) + 'px',
                                'background-position-x' : '-' + (keyChild * flipAnimation.resElementWidth) + 'px'}">
                </div>
            </div>
        </div>
        <!--intro-filter-->
        <div class="info">
            <div class="container-fluid p-0">
                <div class="row no-gutters">
                    <div class="col-sm-4 col-md-4 col-lg-3 hidden-xs-down h-100vh d-flex flex-column">
                        <div class="w-100 background-image info_left-image">
                            <!--<img class="w-100 of-c" :src="imgLeft" alt="">  :style="{'background-image': 'url(' + imgLeft + ')'}"-->
                            <div class=""></div>
                            <!--info-filter__dark-->
                        </div>
                        <div class="animation-button-relative">
                            <transition name="slide-left">
                                <div class="button-info m-auto d-flex" v-if="(flipAnimation.columnElements[flipAnimation.columnElements.length - 1][0].activeFlip ||
                                 flipAnimation.columnElements[flipAnimation.columnElements.length - 1][1].activeFlip) == 1 ? false : true && flipAnimation.activeAnimationText">
                                    <!--v-if="flipAnimation.columnElements[0][0].activeFlip != 1"-->
                                    <a href="#" class="button button_line button_link-small m-auto">
                                        About
                                    </a>
                                </div>
                            </transition>
                        </div>
                    </div>
                    <div class="col-sm-8 col-md-8 col-lg-9 background-image h-100vh d-flex flex-column">
                        <!-- deleted h-100vh :style="{'background-image': 'url(' + imgRight + ')'}"-->
                        <div class="row  no-gutters f-1 align-items-center">
                            <!--info-filter-->
                            <div class="animation-text-relative">
                                <transition name="slide-top">
                                    <div class="col-10 offset-1 col-lg-5 offset-lg-4 flip-animation-text"
                                         v-for="(item, index) in arrayObject"
                                         :key="index"
                                         v-if="(index + 1) == flipAnimation.columnElements[0][0].activeFlip && flipAnimation.activeAnimationText">
                                        <!--     <h5 class="up-title text-uppercase font-weight-bold color_dark-white"
                                                 v-if="item.description[0].description"
                                             >{{item.description[0].description}}</h5>-->
                                        <h2 class="block-title color_white mb-30"
                                            v-if="item.description[0].description"
                                            v-html="item.description[0].description">

                                        </h2>
                                        <!--<p class="color_white"
                                           v-if="item.description[2].description"
                                        >{{item.description[2].description}}</p>-->  <!--<p class="color_white"
                                           v-if="item.description[2].description"
                                        >{{item.description[2].description}}</p>-->
                                    </div>
                                </transition>
                            </div>
                        </div>
                        <div class="h-80 d-flex bgc-onyx hidden-sm-up">
                            <div class="button-info m-auto ">
                                <a href="/about3" class="button button_line button_link-small">
                                about
                            </a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>


	export default {
		props: {
			arrayObject: ''
		},
		data () {
			return {
				flipElement: '',
				flipAnimation: {
					resElementHeight: 0,
					resElementWidth: 0,
					activityFlip: false,
					rotateCounter: 0,
					backgroundsItem: 1,
					activeAnimationText: true,
					activeAnimationButton: false,
					columnElements: [
						[
							{rotateX: false, rotateY: false, id: 1, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 2, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 3, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 4, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 5, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 6, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 7, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 8, activeFlip: 1}
						],
						[
							{rotateX: false, rotateY: false, id: 9, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 10, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 11, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 12, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 13, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 14, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 15, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 16, activeFlip: 1}
						],
						[
							{rotateX: false, rotateY: false, id: 17, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 18, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 19, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 20, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 21, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 22, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 23, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 24, activeFlip: 1}
						],
						[
							{rotateX: false, rotateY: false, id: 25, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 26, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 27, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 28, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 29, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 30, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 31, activeFlip: 1},
							{rotateX: false, rotateY: false, id: 32, activeFlip: 1}
						]
					]
				}
			}
		},
		methods: {
			isActivityFlip () {
				let rotateDeg = 180
				let maxRotateDeg = 720
				setInterval(() => {
					this.activeFlipFun()
					this.flipAnimation.rotateCounter += rotateDeg
					if (this.flipAnimation.rotateCounter > maxRotateDeg) {
						//	clearInterval(setIntervalFun)
						this.flipAnimation.rotateCounter = 180
					}
				}, 6000)
			},
			flip () {
				return {
					flipElementWidth () {
						let maxRowElements = this.flipAnimation.columnElements[0].length
						this.flipAnimation.resElementWidth = this.$refs.flipChild[0].clientWidth / maxRowElements
						return this.flipAnimation.resElementWidth
					},
					flipElementHeight () {
						let maxColumnElements = this.flipAnimation.columnElements.length
						this.flipAnimation.resElementHeight = this.$refs.flipParent.offsetHeight / maxColumnElements
						return this.flipAnimation.resElementHeight
					}
				}
			},
			windowResize () {
				window.addEventListener('resize', () => {
					this.flip().flipElementWidth.call(this)
					this.flip().flipElementHeight.call(this)
				}, false)
			},
			activeFlipFun () {
				let newCounter = 100
				let maxElements = 5
				this.flipAnimation.activeAnimationText = false
				this.flipAnimation.activeAnimationButton = true
				this.allElements().forEach((item, key) => {
					let counter = newCounter * key
					item.rotateX = false
					item.rotateY = false
					setTimeout(() => {
						if (key % 2 === 0) {
							item.rotateX = true
							item.activeFlip++
							if (item.activeFlip === maxElements) {
								item.activeFlip = 1
							}
						} else {
							item.rotateY = true
							item.activeFlip++
							if (item.activeFlip === maxElements) {
								item.activeFlip = 1
							}
							if (counter === 3100) {
								this.flipAnimation.activeAnimationText = true
							}
						}
					}, (counter - 500))
				})
			},
			shuffle (array) {
				let counter = array.length
				while (counter > 0) {
					let index = Math.floor(Math.random() * counter)
					counter--
					let temp = array[counter]
					array[counter] = array[index]
					array[index] = temp
				}
				return array
			},
			allElements () {
				let allElements = []
				this.flipAnimation.columnElements.forEach(function (item) {
					item.forEach(function (itemChild) {
						allElements.push(itemChild)
					})
				})
				return this.shuffle(allElements)
			}
		},
		mounted () {
			this.flip().flipElementWidth.call(this)
			this.flip().flipElementHeight.call(this)
			this.windowResize()
			this.isActivityFlip()
		}
	}

</script>

<style lang="sass">
    *
        margin: 0
        padding: 0
    .intro
        width: 100%
        height: 100vh
    .flip
        position: absolute;
        width: 100%;
        height: 100%;
        left: 0;
        top: 0;
        display: flex
        flex-direction: column
        &_background-1
            .flip__item__elem
                background-repeat: no-repeat
            .changeBgItem-1
                background-image: url('assets/images/home/home-slide-1.jpg')
            .changeBgItem-2
                background-image: url('assets/images/home/home-slide-2.jpg')
            .changeBgItem-3
                background-image: url('assets/images/home/home-slide-3.jpg')
            .changeBgItem-4
                background-image: url('assets/images/home/home-slide-4.jpg')
            .change-small-bg-1
                background-image: url('assets/images/home/home-slide-1.jpg')
            .change-small-bg-2
                background-image: url('assets/images/home/home-slide-small-1.jpg')
            .change-small-bg-3
                background-image: url('assets/images/home/home-slide-small-2.jpg')
            .change-small-bg-4
                background-image: url('assets/images/home/home-slide-small-3.jpg')
            .change-small-bg-color
                background: none
                background-color: #111413
            .rotate-x-180
                animation: flip-x-180 .4s linear
                transition: all .4s linear
            .rotate-y-180
                animation: flip-y-180 .4s linear
                transition: all .4s linear
            .rotate-x-360
                animation: flip-x-360 .4s linear
                transition: all .4s linear
            .rotate-y-360
                animation: flip-y-360 .4s linear
                transition: all .4s linear
            .rotate-x-540
                animation: flip-x-360 .4s linear
                transition: all .4s linear
            .rotate-y-540
                animation: flip-y-360 .4s linear
                transition: all .4s linear
            .rotate-x-720
                animation: flip-x-360 .4s linear
                transition: all .4s linear
            .rotate-y-720
                animation: flip-y-360 .4s linear
                transition: all .4s linear
        &__item
            width: 100%
            height: 33.33%
            display: flex
        &__item__elem
            width: 12.5%
            height: 100%


    .animation-text
        animation: fade-in-text .4s linear
        transition: all .1s linear

    @keyframes fade-in-text
        0%
            filter: opacity(0) grayscale(0)
        50%
            filter: opacity(0.1) grayscale(100%)
        100%
            filter: opacity(1) grayscale(0)

    @keyframes flip-x-180
        0%
            transform: rotateX(0) scale(1)
            filter: opacity(1) grayscale(0)
        50%
            transform: rotateX(90deg) scale(1.1)
            filter: opacity(0.3) grayscale(100%)

        100%
            transform: rotateX(180deg) scale(1)
            filter: opacity(1) grayscale(0)

    .text-uppercase
        //width: 50%
        span
            display: block

    @keyframes flip-y-180
        0%
            transform: rotateY(0) scale(1)
            filter: opacity(1) grayscale(0)

        50%
            transform: rotateY(90deg) scale(0.8)
            filter: opacity(0.3) grayscale(100%)

        100%
            transform: rotateY(180deg) scale(1)
            filter: opacity(1) grayscale(0)

    @keyframes flip-x-360
        0%
            transform: rotateX(180deg) scale(1)
            filter: opacity(1) grayscale(0)
        50%
            transform: rotateX(90deg) scale(1.1)
            filter: opacity(0.3) grayscale(100%)

        100%
            transform: rotateX(0deg) scale(1)
            filter: opacity(1) grayscale(0)

    @keyframes flip-y-360
        0%
            transform: rotateY(180deg) scale(1)
            filter: opacity(1) grayscale(0)

        50%
            transform: rotateY(90deg) scale(0.8)
            filter: opacity(0.3) grayscale(100%)

        100%
            transform: rotateY(0deg) scale(1)
            filter: opacity(1) grayscale(0)

    @keyframes flip-x-540
        0%
            transform: rotateX(360deg) scale(1)
            filter: opacity(1) grayscale(0)
        50%
            transform: rotateX(450deg) scale(1.1)
            filter: opacity(0.3) grayscale(100%)

        100%
            transform: rotateX(540deg) scale(1)
            filter: opacity(1) grayscale(0)

    @keyframes flip-y-360
        0%
            transform: rotateY(360deg) scale(1)
            filter: opacity(1) grayscale(0)

        50%
            transform: rotateY(450deg) scale(0.8)
            filter: opacity(0.3) grayscale(100%)

        100%
            transform: rotateY(540deg) scale(1)
            filter: opacity(1) grayscale(0)
</style>