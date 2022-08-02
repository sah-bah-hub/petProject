<!DOCTYPE html>
<html lang="en">
  <head>
    <script src="https://kit.fontawesome.com/ed7a96ce4d.js" crossorigin="anonymous"></script>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width">
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
    <style type="text/css">
      ::-webkit-scrollbar {
        width: 7px;
        background-color: rgba(0,0,0,100);
      }

      ::-webkit-scrollbar-thumb {
        border-radius: 10px;
        background: #1c1c1c;
      }

      ::-webkit-scrollbar-track {
        -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.2);
        border-radius: 10px;
        background-color: rgba(0,0,0,100);
      }
      *{
        padding: 0px;
        margin: 0px;
      }
      p{
      }
      .backgraund{
        width:  100%;
        height: 100%;
        background-color: grey;
        color: white;
      }
      .sliderContainer{
        height: 90%;
        overflow-x: scroll;
        overflow-y: hidden;
      }
      .sliderContainer::-webkit-scrollbar {
        display: none;
      }
      .slider{
        height: 100%;
        position: relative;
        right: 0px;
        transition: all 0.3s ease 0s;
        display: inline-flex;
      }
      .slider > div{
        width: 300px;
        scroll-snap-align: center;
      }
      #container{
        background-color: #080404;
        border-radius: 10px;
        width: 300px;
        /*max-width: 300px;*/
        height: 550px;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        box-shadow: black 1px 3px 5px;
        overflow: hidden;
        font-family: cursive;

      }
      .tabSelectorBtn{
        padding: 0em 2em;
        height: 10%;
        display: inline-flex;
        justify-content: space-around;
      }
      .tabSelectorBtn button{
        padding: 1em;
        /* margin: 1em; */
        background-color: rgba(0 0 0 / 0.3);
        color: gray;
        font-size: larger;
        transition: 0.1s;
        border-radius: 50%;
        border: none;
        cursor: pointer;
      }
      .tabSelectorBtn button:hover{
        background-color: rgba(50 50 50 / 0.5);
      }
      .tabSelectorBtn button:active{
        background-color: rgba(50 50 50 / 0.4);
      }
      .selected{
        color: #2460a8 !important;
        transition: 0.3s;
      }
      .btn > div{
        height: 100%;
      }
      .btn > div > div{
        position: relative;
        left: 50%;
        top: 50%;
        width: fit-content;
        transform: translate(-50%, -50%);
      }
      #curTime {
        padding-left: 1.5em;
        font-family: system-ui;
        color: gray;
        font-size: 0.9em;
        margin-top: -0.5em;
      }

      .btn button{
        padding: 15px;
        border-radius: 50%;
        border: 0;  
        margin: 10px;
        background-color: #242424;
        color: #2460a8;
        cursor: pointer;
      }
      .btn button:hover{
        background-color: #272727;
      }
      .btn button:active{
        background-color: #303030;
      }
      .hide{
        display: none !important;
      }
      .hideSlide{
        transition: 0.5s;
        opacity: 0;
      }
      .show{
        transition: 0.5s;
        opacity: 1;
      }
      #log{
        height: 45%;
        overflow-y: auto;
      }

      .btn{
        height: 20%;
      }
      .flagString{
        float: left;
        width: -webkit-fill-available;
        padding: 0px 10px;
        font-family: cursive;
        transition: 0.3s;
        opacity: 1;
        height: 2.5em;
      }
      .newflagString{
        opacity: 0;
        height: 0;
        transition: 0.3s;
      }
      .flagString div{
        float:  left;
        padding: 10px;
      }
      .flagString div:not(.gap){
        color: grey;
      }
      .flagString .gap{
        float: right;
      }

      /*styles after creating first flag*/
      .flagWasCreated #StopWatchString{
        transition: 0.5s;
        padding: 0em 0em 0em 0.5em ;
        font-size: 2.5em;
      }
      .flagWasCreated #curTime{
        opacity: 1;
        transition: 0.5s;
      }
      .flagWasCreated .time{
        transition: 0.5s;
        height: 15%;
        width: 300px;
      }
      .flagWasCreated #log{
        transition: 0.5s;
        height: 65%;
      }

      /*styles befor creating first flag*/
      .flagWasntCreated #StopWatchString{
        transition: 0.5s;
        padding: 1em;
        font-size: -webkit-xxx-large;
      }
      .flagWasntCreated #curTime{
        opacity: 0;
      }
      .flagWasntCreated .time{
        height: 35%;
        width: 300px;
      }
      .flagWasntCreated #log{
        height: 45%;
        transition: 0.5s;
      }


      .snap{
        scroll-snap-type: y mandatory;
      }
      .hSnap{
        scroll-snap-type: x mandatory;
      }
      .timePicker > div > div{
        padding: 0.2em 0.3em;
        scroll-snap-align: center;
        color: #303030;
        font-size: 0.8em;
      }
      .timePicker > div{
        overflow-y: scroll;
        user-select: none;
        height: 60%;
        width: 25%;
      }
      .timePicker > div:not(.line){
        cursor: grab;
      }
      .timePicker > div:not(.line):active{
        cursor: grabbing;
      }
      
      .timePicker{
        display: inline-flex;
        height: 80%;
        margin: 2em 0em -2em 0em;
        justify-content: space-evenly;
        width: 300px;
        text-align: center;
      }
      .selectedTimerTime{
        color: white !important;
        font-size: 1.3em !important;
      }
      .timePicker > div::-webkit-scrollbar {
        display: none;
      }
      .timerView{
        width: 300px;
        height: 80%;
      }
      .Timer{
        font-size: 2em;
        scroll-snap-align: center;
      }
      .clouseSelect{
        color: gray !important;
        font-size: 1em !important;
      }
      .TimerString{
        padding: 4em 1em 0em;
        text-align: center;
        font-size: 1.1em;
      }
      .currentTime {
        text-align: center;
        font-size: 0.5em;
      }
      .circle-dash {
        stroke-dasharray: 4 2;
        stroke: black;
        mix-blend-mode: unset;
      }
      .progress{
        stroke: #2460a8;
        transform: rotate(270deg);
        transform-origin: center;
      }
      .stopTimer{
        stroke: darkgray;
      }
      .regress{
        stroke: gray;
        transform: rotateY(180deg) rotate(270deg);
        transform-origin: center;
      }
      .progressbar {
        position: absolute;
        margin: 0.5em 0em;
      }
      .line {
        width: 0em !important;
        border: solid 0.01em;
        border-radius: 50%;
        border-color: rgba(50 50 50 / 0.1);
      }
      .TimerEnd{
        width: inherit;
        height: 100%;
      }
      .TimerEnd .DateContainer{
        margin: auto;
        padding: 0em;
        font-size: 1.5em;
        width: max-content;
      }
      .TimerEnd .date{
        font-size: 0.3em;
        text-align: center;
      }
      .TimerEnd .ico{
        font-size: 1.3em;
        margin: auto;
        width: fit-content;
        padding: 1.5em;
        color: gray;
      }
      .TimerEnd .timerInfo{
        margin: auto;
        width: fit-content;
        font-size: 0.4em;
        text-align: center;
        padding: 3em;
      }
      .TimerEnd .btnContainer{
        margin: auto;
        width: fit-content;
        padding: 1em;
      }
      .TimerEnd .btnContainer button{
        padding: 0.5em 5em;
        margin: auto;
        background-color: rgba(50 50 50 / 0.3);
        color: white;
        border: gray;
        border-radius: 1em;
        cursor: pointer;
      }
      .TimerEnd .btnContainer button:hover {
        background-color: rgba(50 50 50 / 0.5);
      }
      .TimerEnd .btnContainer button:active {
        background-color: rgba(50 50 50 / 0.4);
      }

      .Clock > div{
        width: inherit;
        text-align: center;
        padding: 3em 0em;
      }
      .Clock .time{
        font-size: 3em;
      }
      .Clock .date{
        color: gray; 
      }

      .Alarm .btn{
        margin: auto; 
        width: fit-content;
        padding: 1em;
        margin-top: -1.5em;
      }
      .alarmContainer {
        height: 85%;
        width: -webkit-fill-available;
        overflow: auto;
      }
      .alarmContainer::-webkit-scrollbar {
        display: none;
      }
      .popupSadow{
        height: -webkit-fill-available;
        width: -webkit-fill-available;
        position: fixed;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        z-index: 2;
        background-color: rgba(0,0,0,0.3);
        display: flex;
        backdrop-filter: blur(0.2em);
      }
      .popup {
        width: 90%;
        height: 55%;
        margin: auto;
        border-radius: 0.5em;
        background-color: black;
      }
      .AlarmTimePicker{
        width: 100%;
        justify-content: space-evenly;
        display: inline-flex;
        font-size: 2em;
        height: 78%;
        margin: 0.5em 0em -0.5em 0em;
        text-align: center;
      }
      button.cancel {
          color: #6e1212;
      }
      button.save {
          color: #124503;
      }
      .AlarmTimePicker > div > div{
        padding: 0.2em 0.3em;
        scroll-snap-align: center;
        color: #303030;
        font-size: 0.8em;
      }
      .AlarmTimePicker > div{
        overflow-y: scroll;
        user-select: none;
        width: 25%;
      }
      .AlarmTimePicker > div:not(.line){
        cursor: grab;
      }
      .AlarmTimePicker > div:not(.line):active{
        cursor: grabbing;
      }
      
      .popup .btn{
        padding: 1.5em;
      }
      .AlarmTimePicker > div::-webkit-scrollbar {
        display: none;
      }

      .switch {
        position: relative;
        display: inline-grid;
        width: 45px;
        height: 25px;
      }
      .switch input {
        opacity: 0;
        width: 0;
        height: 0;
      }
      .toggleSlider {
        position: absolute;
        cursor: pointer;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: #ccc;
        -webkit-transition: .4s;
        transition: .4s;
      }
      .toggleSlider:before {
        position: absolute;
        content: "";
        height: 19px;
        width: 19px;
        left: 3px;
        bottom: 3px;
        background-color: white;
        -webkit-transition: .4s;
        transition: .4s;
      }
      input:checked + .toggleSlider {
        background-color: #2196F3;
      }
      input:focus + .toggleSlider {
        box-shadow: 0 0 1px #2196F3;
      }
      input:checked + .toggleSlider:before {
        -webkit-transform: translateX(20px);
        -ms-transform: translateX(20px);
        transform: translateX(20px);
      }
      .toggleSlider.round {
        border-radius: 34px;
      }
      .toggleSlider.round:before {
        border-radius: 50%;
      }
      .AlarmElement{
        display: inline-flex;
        width: -webkit-fill-available;
        padding: 1em;
        justify-content: space-between;
        cursor: pointer;
      }
      .AlarmElement:hover{
        background-color: rgba(50 50 50 / 0.1);
      }
      .AlarmElement:active{
        background-color: rgba(50 50 50 / 0.2);
      }
      .AlarmElement .time{
        font-size: 2em;
        transition: 0.5s;
      }
      .idle{
        color: gray;
      }
      .AlarmElement .timeLeft{
        color: gray;
        font-size: 0.8em;
      }
      .Alarm .TimerEnd{
        font-size: 2em;

      }
      .canHorizontalDraging{
        cursor: grab;
      }
      .canHorizontalDraging:active{
        cursor: grabbing !important;
      }
    </style>
  </head>
  <body class="backgraund">
    <div id="container">
      <div class="tabSelectorBtn">
        <button @click="selectTab('Alarm',0)" class="Alarm selected">
          <i class="fa fa-bell"></i>
        </button>
        <button @click="selectTab('Clock',1)" class="Clock">
          <i class="fa fa-clock"></i>
        </button>
        <button @click="selectTab('StopWatch',2)" class="StopWatch">
          <i class="fa fa-stopwatch"></i>
        </button>
        <button @click="selectTab('Timer',3)" class="Timer">
          <i class="fa fa-hourglass"></i>
        </button>
      </div>
      <div class="sliderContainer canHorizontalDraging">
        <div class="slider">
          <div is="Alarm"></div>
          <div is="Clock"></div>
          <div is="StopWatch"></div>
          <div is="Timer"></div>
        </div>
      </div>
    </div>
    <script type="text/javascript">
      var ClockVueApp = new Vue({
        el: "#container",
        data: {
          tabArray: ["Alarm","Clock","StopWatch","Timer"],
          particleArray: [],
          lastEvent: null,
        },
        mounted(){
          this.scrollListner();
          this.careateTachnes();
        },
        methods:{
          careateTachnes(){
            var verticalElements = document.querySelectorAll(".canVerticalDraging");
            verticalElements.forEach(x => this.verticalDragScroller(x)) 
            var horizontalElements = document.querySelectorAll(".canHorizontalDraging");
            horizontalElements.forEach(x => {
              this.horizontalDragScroller(x);
            })
          },
          horizontalDragScroller(el){
            const scollElement = el;

            function Particle( elem ) {
              this.element = elem;
              this.positionX = elem.scrollLeft * -1;
              this.dragPositionX = elem.scrollLeft * -1;
              this.velocityX = 0;
              this.friction = 0.90;
              this.accelX = 0;
              this.isDragging = false;
              this.lastPosition = 0;
            }

            Particle.prototype.render = function() {
              if (canMove) {
                if (this.positionX *-1 <=0) { 
                  this.positionX = 0;
                }
                if (this.positionX * -1 > this.element.scrollWidth) { 
                  this.positionX = this.element.scrollWidth*-1;
                }
                this.element.scrollLeft = (this.positionX * -1).toFixed(0);
              }
            };

            Particle.prototype.update = function() {
              this.applyDragForce();
              this.integrate();
            };

            Particle.prototype.integrate = function() {
              this.velocityX += this.accelX;
              this.velocityX *= this.friction;
              this.positionX += this.velocityX;
              this.accelX = 0;
            };

            Particle.prototype.applyForce = function( force ) {
              this.accelX += force * 0.5;
            };

            Particle.prototype.applyDragForce = function() {
              if ( !this.isDragging ) {
                return;
              }
              var dragVelocity = this.dragPositionX - this.positionX;
              var dragForce = dragVelocity - this.velocityX;
              this.applyForce( dragForce );
            };

            var it = this;
            var particle;

            document.addEventListener( 'DOMContentLoaded', init(), false );

            function init() {
              particle = new Particle( scollElement );
              it.particleArray.push({"particle":particle, "name":scollElement.parentNode.className});
              scollElement.addEventListener( 'mousedown', onMousedown, false );
            }

            var dragForce = 0;

            function animate() {
              if (scollElement.classList.item("hSnap")) {scollElement.classList.remove("hSnap")};
              particle.update();
              particle.render();
              var AnimationFrame = requestAnimationFrame( animate );
              if (isDragging && !particle.isDragging && particle.positionX != 0 && particle.lastPosition == particle.positionX.toFixed(0)) {
                cancelAnimationFrame( AnimationFrame );                      
                isDragging = false ;
                scollElement.classList.add("hSnap");
                particle.positionX = scollElement.scrollLeft *-1;
                particle.dragPositionX = scollElement.scrollLeft *-1; 
              } 
              particle.lastPosition = particle.positionX.toFixed(0);
            }

            var dragStartX;
            var dragStartY;
            var canMove;
            var particleDragStartX;
            var isDragging = false;

            function onMousedown( event ) {
              it.lastEvent = event;
              if([... event.target.classList].find(x => x == "hour" || x == "minut" || x == "second") != null){
                return
              }
              if (!isDragging) {
                animate()
              }
              event.preventDefault();
              dragStartX = event.pageX;
              dragStartY = event.pageY;
              particleDragStartX = particle.positionX;
              particle.isDragging = true;
              isDragging = true;
              setDragPositionX( event );
              window.addEventListener( 'mousemove', onMousemove, false );
              window.addEventListener( 'mouseup', onMouseup, false );
            }

            function onMousemove( event ) {
              setDragPositionX( event );
              canMove = Math.abs(event.pageY - dragStartY)<Math.abs(event.pageX - dragStartX);
            }

            function setDragPositionX( event ) {
              var moveX = event.pageX - dragStartX;
              particle.dragPositionX = particleDragStartX + moveX;
            }

            function onMouseup() {
              it.lastEvent = event;
              particle.isDragging = false;
              window.removeEventListener( 'mousemove', onMousemove, false );
              window.removeEventListener( 'mouseup', onMouseup, false );
            }
          },
          verticalDragScroller(el){
            const scollElement = el;

            function Particle( elem ) {
              this.element = elem;
              this.positionY = elem.scrollTop * -1;
              this.dragPositionY = elem.scrollTop * -1;
              this.velocityY = 0;
              this.friction = 0.97;
              this.accelY = 0;
              this.isDragging = false;
              this.lastPosition = 0;
            }

            Particle.prototype.render = function() {
              if([...scollElement.classList].filter(x => x == "hours" || x == "minutes" || x == "seconds").length != 0){
                if (this.positionY > 0) { 
                  this.positionY -= this.element.scrollHeight
                  this.dragPositionY = this.positionY
                }
                if (this.positionY * -1 > this.element.scrollHeight) { 
                  this.positionY += this.element.scrollHeight
                  this.dragPositionY = this.positionY
                }
              } else {
                if (this.positionY *-1 <=0) { 
                  this.positionY = 0;
                  return
                }
                if (this.positionY * -1 > this.element.scrollHeight) { 
                  this.positionY = this.element.scrollWidth*-1;
                  return
                }
              }
              this.element.scrollTop = (this.positionY * -1).toFixed(1);
            };

            Particle.prototype.update = function() {
              this.applyDragForce();
              this.integrate();
            };

            Particle.prototype.integrate = function() {
              this.velocityY += this.accelY;
              this.velocityY *= this.friction;
              this.positionY += this.velocityY;
              this.accelY = 0;
            };

            Particle.prototype.applyForce = function( force ) {
              this.accelY += force;
            };

            Particle.prototype.applyDragForce = function() {
              if ( !this.isDragging ) {
                return;
              }
              var dragVelocity = this.dragPositionY - this.positionY;
              var dragForce = dragVelocity - this.velocityY;
              this.applyForce( dragForce );
            };


            var particle;

            document.addEventListener( 'DOMContentLoaded', init(this), false );

            function init(it) {
              particle = new Particle( scollElement );
              it.particleArray.push({"particle":particle, "name":scollElement.parentNode.className});
              scollElement.addEventListener( 'mousedown', onMousedown, false );
            }

            var dragForce = 0;

            function animate() {
              particle.update();
              particle.render();
              var AnimationFrame = requestAnimationFrame( animate );
              if (isDragging && !particle.isDragging && particle.positionY != 0 && particle.lastPosition == particle.positionY.toFixed(1)) {
                cancelAnimationFrame( AnimationFrame );                      
                isDragging = false 
              } 
              particle.lastPosition = particle.positionY.toFixed(1);
            }

            var dragStartY;
            var dragStartX;
            var particleDragStartY;
            var isDragging = false;

            function onMousedown( event ) {
              if (!isDragging) {
                animate()
              }
              event.preventDefault();
              dragStartY = event.pageY;
              dragStartX = event.pageX;
              particleDragStartY = particle.positionY;
              particle.isDragging = true;
              isDragging = true;
              setDragPositionX( event );
              window.addEventListener( 'mousemove', onMousemove, false );
              window.addEventListener( 'mouseup', onMouseup, false );
            }

            function onMousemove( event ) {
              setDragPositionX( event );

            }

            function setDragPositionX( event ) {
              var moveY = event.pageY - dragStartY;
              particle.dragPositionY = particleDragStartY + moveY;
            }

            function onMouseup() {
              particle.isDragging = false;
              window.removeEventListener( 'mousemove', onMousemove, false );
              window.removeEventListener( 'mouseup', onMouseup, false );
            }
          },
          scrollListner(){
            document.querySelector(".sliderContainer").addEventListener("scroll",(el) =>{
              var lastSelected = document.querySelector(".selected");
              lastSelected.classList.remove("selected");

              var newSelected = document.querySelector(".tabSelectorBtn ."+this.tabArray[Math.floor(el.target.scrollLeft / 300)]);
              newSelected.classList.add("selected");
            });
          },
          selectTab(className,number){
            let position = (document.querySelector(".slider").scrollWidth / document.querySelector(".slider").children.length) * number;
            let element  = this.particleArray.filter(x => x.name == "").map(x => x.particle)[0]
            element.positionX = position *-1;
            element.dragPositionX = position *-1;
            document.querySelector(".slider ."+className).scrollIntoView({behavior: "smooth"});
          },
        },
        components:{
          "Alarm":{
            data: function(){
              return{
                popupShow: false,
                alarmWork: false,
                AlarmArray: [],
                editAlarm: null,
                TimeNow: "",
                DateNow: "",
                currentTime: "",
              }
            },
            methods:{
              openPopup(object){
                this.popupShow = true;
                let particleArray = ClockVueApp.particleArray.filter(x => x.name == "AlarmTimePicker").map(x => x.particle);
                if (object != null){
                  this.editAlarm = object;
                  Vue.nextTick(() => {
                    let position = document.querySelector(".AlarmTimePicker .hours  ").children[0].offsetHeight * ((object.Time.getHours() < 12 ? object.Time.getHours() + 24 : object.Time.getHours()) -1);
                    document.querySelector(".AlarmTimePicker .hours  ").scrollTop = position;
                    particleArray[0].positionY = position *-1;
                    particleArray[0].dragPositionY = position *-1;
                    Vue.nextTick(() => {
                      position = document.querySelector(".AlarmTimePicker .minutes").children[0].offsetHeight * ((object.Time.getMinutes() < 30 ? object.Time.getMinutes() + 60 : object.Time.getMinutes()) -1);
                      document.querySelector(".AlarmTimePicker .minutes").scrollTop = position;
                      particleArray[1].positionY = position *-1;
                      particleArray[1].dragPositionY = position *-1;
                    });
                  });
                  return
                }
                var now = new Date();
                Vue.nextTick(() => {
                  let position = document.querySelector(".AlarmTimePicker .hours  ").children[0].offsetHeight * ((now.getHours() < 12 ? now.getHours() + 24 : now.getHours()) -1);
                  document.querySelector(".AlarmTimePicker .hours  ").scrollTop = position;
                  particleArray[0].positionY = position *-1;
                  particleArray[0].dragPositionY = position *-1;
                  Vue.nextTick(() => {
                    position = document.querySelector(".AlarmTimePicker .minutes").children[0].offsetHeight * ((now.getMinutes() < 30 ? now.getMinutes() + 60 : now.getMinutes()) -1);
                    document.querySelector(".AlarmTimePicker .minutes").scrollTop = position;
                    particleArray[1].positionY = position *-1;
                    particleArray[1].dragPositionY = position *-1;
                  });
                });
              },
              createAlarm(){
                var selected = document.querySelectorAll(".AlarmTimePicker .selectedTimerTime");
                var now = new Date();
                now.setHours(selected[0].innerText)
                now.setMinutes(selected[1].innerText)
                now.setSeconds(0)
                let timeString = now.getHours() +":"+ this.zeroPad(now.getMinutes(),2);
                if (this.AlarmArray.find(x => x.timeString == timeString) != null){
                  this.closePopup();
                  return
                }
                if (this.editAlarm != null) {
                  this.editAlarm.Time = now;
                  this.editAlarm.timeString = timeString;
                  this.editAlarm.active = true;
                  this.editAlarm.difference = "";
                  this.closePopup();
                  return
                }
                this.AlarmArray.push({
                  Time: now,
                  timeString: timeString,
                  active: true,
                  difference: ""
                })
                this.closePopup();
              },
              closePopup(){
                this.editAlarm = null;
                this.popupShow = false;
              },
              deleteAlarm(){
                this.AlarmArray.splice(this.AlarmArray.indexOf(this.editAlarm), 1);
                this.closePopup()
              },
              update(){
                var now = new Date();
                this.AlarmArray.forEach(x => {
                  this.TimeNow = this.zeroPad(now.getHours(),2) + ":" + this.zeroPad(now.getMinutes(),2);
                  this.DateNow = now.toLocaleString('default', { day: 'numeric'  }) + " " + now.toLocaleString('default', { month: 'long', weekday: 'long' });
                  this.currentTime = x.timeString;
                  if (!x.active) {
                    x.difference = ""
                    return
                  }
                  var obj = x
                  let time = x.Time
                  if (Math.floor(time / 1000) == Math.floor(now / 1000)) {
                    this.alarmWork = true;
                  }
                  if(time < now){
                    time.setDate(time.getDate() + 1)
                  }
                  let difference =  now - time;
                  let timeString = "Alarm in ";
                  var curArray = [[Math.floor(difference / 1000 / 60 / 60) % 60 *-1-1,"h"],[Math.floor(difference / 1000 / 60) % 60 *-1,"m"]];
                  curArray.forEach(el => {
                    if (el[0] != 0) {
                      timeString += el[0] + " " +el[1]+ " ";
                    }
                  })
                  obj.difference = timeString
                  Object.assign(obj,x)
                })
              },
              zeroPad(num, places) {
                return String(num).padStart(places, '0')
              },
              clouseAlarm(){
                this.alarmWork = false;
              }
            },
            mounted(){
              setInterval(this.update,100);
              var now = new Date();
              now.setHours(8)
              now.setMinutes(0)
              now.setSeconds(0)
              this.AlarmArray.push({
                Time: now,
                timeString: now.getHours() +":"+ this.zeroPad(now.getMinutes(),2),
                active: true,
                difference: ""
              })
            },
            components:{
              "Popup":{
                props: ['obj'],
                data: function(){
                  return{
                    infoArray: [[".hours","hour",23],[".minutes","minut",59]],
                  }
                },
                mounted(){
                  this.createTime();
                  this.createTime();
                  this.addScrollSnap();
                },
                methods:{
                  createTime(){
                    this.infoArray.forEach(el => {
                      var container = document.querySelector(".AlarmTimePicker " + el[0]);
                      for (var i = el[2]; i >= 0; i--) {
                        let element = document.createElement("div");
                        element.innerText = this.zeroPad(i,2);
                        element.classList.add(el[1]);
                        container.prepend(element);
                      }
                    })
                  },                  addScrollSnap(){
                    this.infoArray.forEach(el => {
                      let hours = document.querySelector(".AlarmTimePicker " +el[0]);
                      var timer = null;

                      hours.addEventListener('scroll', () => {
                        if (hours.classList.length != 1){
                          hours.classList.remove("snap")

                        }
                        clearTimeout(timer);
                          var index = Math.ceil(document.querySelector(".AlarmTimePicker "+el[0]).scrollTop / document.querySelectorAll(".AlarmTimePicker ."+el[1])[0].offsetHeight) +1;

                          var preSelected  =     document.querySelectorAll(".AlarmTimePicker ."+el[1])[ index - 1 ];
                          var selected     =     document.querySelectorAll(".AlarmTimePicker ."+el[1])[index];
                          var postSelected =     document.querySelectorAll(".AlarmTimePicker ."+el[1])[index + 1];

                          document.querySelectorAll(".AlarmTimePicker ."+el[1]).forEach((element) => {
                            if(element != preSelected && element != postSelected){
                              element.classList.remove("clouseSelect");
                            }
                            if(element != selected){
                              element.classList.remove("selectedTimerTime")                          
                            }
                          })
                          preSelected.classList.add("clouseSelect");
                          postSelected.classList.add("clouseSelect");
                          selected.classList.add("selectedTimerTime")

                          timer = setTimeout(function() {

                            hours.classList.add("snap")
                            
                          }, 250);
                      })
                    })
                  },
                  zeroPad(num, places) {
                    return String(num).padStart(places, '0')
                  },
                },
                template:`
                  <div class="popupSadow">
                    <div class="popup">
                      <div class="AlarmTimePicker">
                        <div class="hours canVerticalDraging"></div>
                        <div class="line"></div>
                        <div class="minutes canVerticalDraging"></div>
                      </div>
                      <div class="btn">
                        <button class="save" title="save" @click="$emit('addAlarm')">
                          <i class="fa fa-check"></i>
                        </button>
                        <button v-if="obj != null" class="delete" title="delete" @click="$emit('delete')">
                          <i class="fa fa-trash"></i>
                        </button>
                        <button class="cancel" title="cancel" @click="$emit('closePopup')">
                          <i class="fa fa-plus" style="transform: rotate(45deg);"></i>
                        </button>
                      </div>
                    </div>
                  </div>
                `
              },
              "AlarmElement":{
                props: ['obj'],
                data: function(){
                  return{
                  }
                },
                mounted(){
                },
                methods:{
                },
                template:`
                  <div class="AlarmElement" @click="$emit('edit')">
                    <div :class="obj.active ? '': 'idle'">
                      <p class="time">{{obj.timeString}}</p>
                      <p class="timeLeft">{{obj.difference}}</p>
                    </div>

                    <div class="switcher">
                      <label class="switch">
                        <input type="checkbox" v-model="obj.active">
                        <span class="toggleSlider round"></span>
                      </label>
                    </div>
                  </div>
                `
              }
            },
            template:`
              <div class="Alarm">
                <div v-show="!alarmWork" class="AlarmChild" style="height:100%">
                  <div class="alarmContainer canVerticalDraging">
                    <div v-for="el,idx in AlarmArray" is="AlarmElement" :obj="el" :key="idx" @edit="openPopup(el)"></div>
                  </div>
                  <div class="btn">
                    <button title="Create" @click="openPopup()">
                      <i class="fa fa-plus"></i>
                    </button>
                  </div>
                  <div v-show="popupShow">
                    <div is="Popup" :obj="editAlarm" @closePopup="closePopup()" @addAlarm="createAlarm()" @delete="deleteAlarm()"></div>
                  </div>
                </div>
                <div v-show="alarmWork">
                  <div class="TimerEnd">
                    <div class="DateContainer">
                      <p>{{TimeNow}}</p>
                      <p class="date">{{DateNow}}</p>
                    </div>
                    <div class="ico">
                      <i class="fa fa-bell"></i>
                    </div>
                    <div class="timerInfo">
                      <p>time is over!</p>
                      <p>{{currentTime}}</p>
                    </div>
                    <div class="btnContainer">
                      <button @click="clouseAlarm()">ok</button>
                    </div>
                  </div>
                </div>
              </div>
            `
          },
          "Clock":{
            data: function(){
              return{
                curTime: "",
                curDate: ""
              }
            },
            methods:{
              update(){
                var now = new Date();
                this.curTime = this.zeroPad(now.getHours(),2) + ":" + this.zeroPad(now.getMinutes(),2) + ":" + this.zeroPad(now.getSeconds(),2);
                this.curDate = this.zeroPad(now.getDate(),2) + "." + this.zeroPad(now.getMonth(),2)  + "." + now.getFullYear();

              },
              zeroPad(num, places) {
                return String(num).padStart(places, '0')
              },
            },
            mounted(){
              setInterval(this.update,100);
            },
            template:`
              <div class="Clock">
                <div>
                  <p class="time">{{curTime}}</p>
                  <p class="date">{{curDate}}</p>
                </div>
              </div>
            `
          },
          "StopWatch":{
            data: function(){
              return{
                interval: null,
                timeStart: null,
                timePause: null,
                counter: 0,
                timeLastflag: null,
                StopWatchString: "00:00.00",
              }
            },
            methods:{
              startStopWatch() {
                this.timeStart = new Date();
                this.interval = setInterval(this.updateTime,10);

                var startBtn = document.querySelector("#startBtn");
                startBtn.classList.add("hide");

                var runingBtn = document.querySelector("#runingBtn");
                runingBtn.classList.remove("hide");
              },
              createFlag() {
                this.counter += 1;
                var now = new Date();
                let gap = now - this.timeStart;
                var loggerElement = document.querySelector("#log");
                var flagString = document.createElement("div");
                flagString.classList.add("newflagString");

                var icoCcontainer = this.createDiv("" , "ico")
                var flagIco = document.createElement("i");
                flagIco.classList.add("fa","fa-flag");
                icoCcontainer.append(flagIco);


                if (loggerElement.children.length == 0) {
                  var StopWatch = document.querySelector(".slider .StopWatch");
                  StopWatch.classList.add("flagWasCreated")
                  StopWatch.classList.remove("flagWasntCreated")
                  difference = gap;
                } else{
                  difference = now - this.timeLastflag;
                }
                flagString.append(icoCcontainer, this.createDiv(this.zeroPad(this.counter,2), "counter") ,  this.createDiv("+ " + this.timeFormat(difference), "difference") , this.createDiv(this.timeFormat(gap), "gap"))

                loggerElement.prepend(flagString)
                setTimeout(() => {
                  flagString.classList.add("flagString");
                  flagString.classList.remove("newflagString");
                }, 0)
                
                this.timeLastflag = now;
              },
              pauseStopWatch() {
                clearInterval(this.interval);
                var runingBtn = document.querySelector("#runingBtn");
                runingBtn.classList.add("hide");


                var stopBtn = document.querySelector("#stopBtn");
                stopBtn.classList.remove("hide");
                this.timePause = new Date() - this.timeStart 
              },
              stopStopWatch() {
                clearInterval(this.interval);
                this.counter = null;
                this.timeLastflag = null;
                this.timePause = null;
                this.timeStart = null

                var loggerElement = document.querySelector("#log").children;
                for (var i = loggerElement.length - 1; i >= 0; i--) {
                  loggerElement[i].remove()
                }

                this.StopWatchString = '00:00.00';

                var stopBtn = document.querySelector("#stopBtn");
                stopBtn.classList.add("hide");

                var runingBtn = document.querySelector("#startBtn");
                runingBtn.classList.remove("hide");


                var StopWatch = document.querySelector(".slider .StopWatch");
                StopWatch.classList.add("flagWasntCreated")
                StopWatch.classList.remove("flagWasCreated")
              },
              playStopWatch() {
                this.timeStart = new Date() - this.timePause ;
                this.interval = setInterval(this.updateTime,10);

                var stopBtn = document.querySelector("#stopBtn");
                stopBtn.classList.add("hide");

                var runingBtn = document.querySelector("#runingBtn");
                runingBtn.classList.remove("hide");
              },
              createDiv(text, className) {
                var div = document.createElement("div");
                div.innerText = text;
                div.classList.add(className);
                return div
              },
              timeFormat(gap) {
                let minets =  Math.floor(gap / 1000 / 60) % 60;
                let seconds =  Math.floor(gap / 1000) % 60;
                let milesecond = Math.floor(gap / 10) % 100;
                return this.zeroPad(minets,2) + ":" + this.zeroPad(seconds,2) + "." + this.zeroPad(milesecond,2)
              },
              updateTime() {
                var now = new Date();
                let gap = now - this.timeStart;

                let minets =  Math.floor(gap / 1000 / 60) % 60;
                let seconds =  Math.floor(gap / 1000) % 60;
                let milesecond = Math.floor(gap / 10) % 100;

                this.StopWatchString = this.zeroPad(minets,2) + ":" + this.zeroPad(seconds,2) + "." + this.zeroPad(milesecond,2);
              },
              zeroPad(num, places) {
                return String(num).padStart(places, '0')
              }
            },
            template:`
              <div class="StopWatch flagWasntCreated">
                <div class="time show">
                  <p id="StopWatchString">{{StopWatchString}}</p>
                  <p id="curTime">Current time</p>
                </div>
                <div id="log" class="canVerticalDraging">     
                </div>
                <div class="btn">
                  <div id="startBtn">
                    <div>
                      <button title="play" @click="startStopWatch()" ><i class="fa fa-play"></i></button>
                    </div>
                  </div>
                  <div id="runingBtn" class="hide">
                    <div>
                      <button title="flag"  @click="createFlag()"><i class="fa fa-flag"></i></button>
                      <button title="pause" @click="pauseStopWatch()"><i class="fa fa-pause"></i></button>
                    </div>
                  </div>
                  <div id="stopBtn" class="hide">
                    <div>
                      <button title="stop" @click="stopStopWatch()"><i class="fa fa-stop"></i></button>
                      <button title="play" @click="playStopWatch()"><i class="fa fa-play"></i></button>
                    </div>
                  </div>
                </div>
              </div>
            `,
          },
          "Timer":{
            data: function(){
              return{
                infoArray: [[".hours","hour",23],[".minutes","minut",59],[".seconds","second",59]],
                TimerString: "00:00:00",
                TimeNow: "00:00:00",
                DateNow: "",
                currentTime: "",
                timeStart: null,
                timeEnd: null,
                timePause: null,
                interval: null,
                totalTime: null,
              }
            },
            mounted(){
              this.createTime();
              this.createTime();
              document.querySelector(".timePicker .hours").scrollTop = document.querySelector(".timePicker .hours").scrollHeight * 0.46;
              document.querySelector(".timePicker .minutes").scrollTop = document.querySelector(".timePicker .minutes").scrollHeight * 0.485;
              document.querySelector(".timePicker .seconds").scrollTop = document.querySelector(".timePicker .seconds").scrollHeight * 0.485;
              this.addScrollSnap();
            },
            methods:{
              addScrollSnap(){
                this.infoArray.forEach(el => {
                  let hours = document.querySelector(".timePicker " +el[0]);
                  var timer = null;

                  hours.addEventListener('scroll', () => {
                    if (hours.classList.length != 1){
                      hours.classList.remove("snap")

                    }
                    clearTimeout(timer);
                      var index = Math.ceil(document.querySelector(".timePicker "+el[0]).scrollTop / document.querySelectorAll(".timePicker ."+el[1])[0].offsetHeight) +1;

                      var preSelected  =     document.querySelectorAll(".timePicker ."+el[1])[ index - 1 ];
                      var selected     =     document.querySelectorAll(".timePicker ."+el[1])[index];
                      var postSelected =     document.querySelectorAll(".timePicker ."+el[1])[index + 1];

                      document.querySelectorAll(".timePicker ."+el[1]).forEach((element) => {
                        if(element != preSelected && element != postSelected){
                          element.classList.remove("clouseSelect");
                        }
                        if(element != selected){
                          element.classList.remove("selectedTimerTime")                          
                        }
                      })
                      preSelected.classList.add("clouseSelect");
                      postSelected.classList.add("clouseSelect");
                      selected.classList.add("selectedTimerTime")

                    timer = setTimeout(function() {

                      hours.classList.add("snap")
                      
                    }, 250);
                  })
                })
              },
              createTime(){
                this.infoArray.forEach(el => {
                  var container = document.querySelector(".timePicker " + el[0]);
                  for (var i = el[2]; i >= 0; i--) {
                    let element = document.createElement("div");
                    element.innerText = this.zeroPad(i,2);
                    element.classList.add(el[1]);
                    container.prepend(element);
                  }
                })
              },
              startTimer(){
                var selected = document.querySelectorAll(".timePicker .selectedTimerTime");

                var curArray = ["h","m","s"];
                this.currentTime = "Total ";
                curArray.forEach((el,i) => {
                  if (parseInt(selected[i].innerText) != 0) {
                    this.currentTime += parseInt(selected[i].innerText) + " " +el+ " ";
                  } 
                })
                if(this.currentTime == "Total "){
                  return
                }

                var timePicker = document.querySelector(".Timer .timePicker");
                timePicker.classList.add("hide");

                var timerView = document.querySelector(".Timer .timerView");
                timerView.classList.remove("hide");


                var startBtn = document.querySelector(".Timer .btn #startBtn");
                startBtn.classList.add("hide");

                var stopBtn = document.querySelector(".Timer .btn #runingBtn");
                stopBtn.classList.remove("hide");

                this.timeStart = new Date();

                this.timeEnd = new Date();

                this.timeEnd.setHours(this.timeEnd.getHours()     + parseInt(selected[0].innerText));
                this.timeEnd.setMinutes(this.timeEnd.getMinutes() + parseInt(selected[1].innerText));
                this.timeEnd.setSeconds(this.timeEnd.getSeconds() + parseInt(selected[2].innerText));

                this.totalTime = this.timeEnd - new Date();

                this.interval = setInterval(this.updateTime,10);
              },
              pauseTimer(){
                clearInterval(this.interval);
                this.timePause = new Date() - this.timeStart 
                var runingBtn = document.querySelector(".Timer .btn #runingBtn");
                runingBtn.classList.add("hide");

                var stopBtn = document.querySelector(".Timer .btn #stopBtn");
                stopBtn.classList.remove("hide");
                
                var progress = document.querySelector(".Timer .progress");
                progress.classList.add("stopTimer");
              },
              stopTimer(){
                clearInterval(this.interval);
                var timePicker = document.querySelector(".Timer .timePicker");
                timePicker.classList.remove("hide");

                var timerView = document.querySelector(".Timer .timerView");
                timerView.classList.add("hide");


                var stopBtn = document.querySelector(".Timer .btn #stopBtn");
                stopBtn.classList.add("hide");

                var runingBtn = document.querySelector(".Timer .btn #startBtn");
                runingBtn.classList.remove("hide");
                this.currentTime = "";
              },
              playTimer(){
                this.timeEnd.setHours(  new Date().getHours()   + parseInt(this.TimerString.slice(0,2)))
                this.timeEnd.setMinutes(new Date().getMinutes() + parseInt(this.TimerString.slice(3,5)))
                this.timeEnd.setSeconds(new Date().getSeconds() + parseInt(this.TimerString.slice(6,8)))

                this.interval = setInterval(this.updateTime,10);

                var stopBtn = document.querySelector(".Timer .btn #stopBtn");
                stopBtn.classList.add("hide");

                var runingBtn = document.querySelector(".Timer .btn #runingBtn");
                runingBtn.classList.remove("hide");
                
                var progress = document.querySelector(".Timer .progress");
                progress.classList.remove("stopTimer");
              },
              updateTime() {
                var now = new Date();
                let gap = this.timeEnd - now;

                let hours =  Math.floor(gap / 1000 / 60 / 60) % 60;
                let minets =  Math.floor(gap / 1000 / 60) % 60;
                let seconds =  Math.floor(gap / 1000) % 60;
                let milesecond = Math.floor(gap);

                this.TimerString = this.zeroPad(hours,2) + ":" + this.zeroPad(minets,2) + ":" + this.zeroPad(seconds,2);

                if (gap < 0 ) {
                  this.TimerIsOver();
                }
                this.updateProgressBar((gap / this.totalTime * 100) * -1 + 100);

                this.TimeNow = this.zeroPad(now.getHours(),2) + ":" + this.zeroPad(now.getMinutes(),2);
              },
              updateProgressBar(procent){
                var el =  document.querySelector(".Timer .progress");
                var radius = el.r.baseVal.value;
                var range = 2 * Math.PI * radius;
                el.style.strokeDasharray = `${range} ${range}`;
                el.style.strokeDashoffset = procent / 100 * range;
              },
              zeroPad(num, places) {
                return String(num).padStart(places, '0')
              },
              TimerIsOver(){
                var now = new Date();
                this.DateNow = now.toLocaleString('default', { day: 'numeric'  }) + " " + now.toLocaleString('default', { month: 'long', weekday: 'long' })
                var TimerEnd = document.querySelector(".Timer .TimerEnd");
                TimerEnd.classList.remove("hide");

                var timerView = document.querySelector(".Timer .timerView");
                timerView.classList.add("hide");


                var stopBtn = document.querySelector(".Timer .btn #stopBtn");
                stopBtn.classList.add("hide");

                var runingBtn = document.querySelector(".Timer .btn #startBtn");
                runingBtn.classList.remove("hide");
              },
              clouseTimer(){
                clearInterval(this.interval);
                var timePicker = document.querySelector(".Timer .timePicker");
                timePicker.classList.remove("hide");

                var TimerEnd = document.querySelector(".Timer .TimerEnd");
                TimerEnd.classList.add("hide");
              }
            },
            template:`
              <div class="Timer">
                <div class="timePicker">
                  <div class="hours canVerticalDraging"></div>
                  <div class="line"></div>
                  <div class="minutes canVerticalDraging"></div>
                  <div class="line"></div>
                  <div class="seconds canVerticalDraging"></div>
                </div>
                <div class="timerView hide">
                  <svg class="progressbar" width="300" height="300">
                    <circle class="regress" stroke-width="15" cx="150" cy="150" r="130" fill="transparent"></circle>
                    <circle class="progress" stroke-width="15" cx="150" cy="150" r="130" fill="transparent"></circle>
                    <circle class="circle-dash" stroke-width="15" cx="150" cy="150" r="130" fill="transparent"></circle>
                  </svg>
                  <p class="TimerString">{{TimerString}}</p>
                  <p class="currentTime">{{currentTime}}</p>
                </div>
                <div class="TimerEnd hide">
                  <div class="DateContainer">
                    <p>{{TimeNow}}</p>
                    <p class="date">{{DateNow}}</p>
                  </div>
                  <div class="ico">
                    <i class="fa fa-bell"></i>
                  </div>
                  <div class="timerInfo">
                    <p>time is over!</p>
                    <p>{{currentTime}}</p>
                  </div>
                  <div class="btnContainer">
                    <button @click="clouseTimer">ok</button>
                  </div>
                </div>
                <div class="btn">
                  <div id="startBtn">
                    <div>
                      <button title="play" @click="startTimer"><i class="fa fa-play"></i></button>
                    </div>
                  </div>
                  <div id="runingBtn" class="hide">
                    <div>
                      <button title="stop" @click="stopTimer()"><i class="fa fa-stop"></i></button>
                      <button title="pause" @click="pauseTimer()"><i class="fa fa-pause"></i></button>
                    </div>
                  </div>
                  <div id="stopBtn" class="hide">
                    <div>
                      <button title="stop" @click="stopTimer()"><i class="fa fa-stop"></i></button>
                      <button title="play" @click="playTimer"><i class="fa fa-play"></i></button>
                    </div>
                  </div>
                </div>
              </div>
            `,
          }
        },
      });
    </script>
  </body>
</html>
