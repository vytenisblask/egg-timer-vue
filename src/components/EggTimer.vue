<template>
    <div class="egg-container" @click="handleEggClick">
      <div class="egg" :class="{ 'ringing': isRinging }">
        <div class="egg-top" 
             :style="{ '--background-translation': `${backgroundTranslation}px`, '--rotation': `${rotation}deg` }"
             @pointerdown.prevent="startDrag">
             <div class="time-ruler-faces-container" :style="{ '--face-count': faceCount }">
                <div v-for="i in faceCount" :key="i" class="time-ruler-face-wrapper" :style="{ '--i': i }">
                <svg class="time-ruler-face" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1740 76" aria-hidden="true">
                <use href="#time-ruler"></use>
                </svg>
                </div>
            </div>
        </div>
        <div class="egg-center"></div>
        <div class="egg-bottom">
          <div class="time-arrow"></div>
          <div class="time-container">{{ formattedTime }}</div>
          <button class="timer-button" 
                  :class="{ 'stop': isTimerRunning }" 
                  @click="toggleTimer" 
                  :disabled="isButtonDisabled">{{ buttonText }}</button>
        </div>
      </div>
  
      <svg viewBox="0 0 1740 76" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" style="position: absolute; width: 0; height: 0;" class="time-ruler-faces-container">
        <defs>
            <symbol id="time-ruler">
        <path d="M-8 46H8v30H-8zm145 0h16v30h-16zM27 66h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zM172 66h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zM317 66h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zM462 66h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zM607 66h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zM752 66h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zM897 66h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zm-110 20h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zm-110 20h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zm-110 20h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zm-110 20h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm168-20h16v30h-16zm-110 20h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4zm29 0h4v10h-4z"/>
        <use href="#E" x="-118.3"/>
        <use href="#E" x="-408.3"/>
        <use href="#E" x="171.7"/>
        <use href="#B"/>
        <use href="#C"/>
        <use href="#D"/>
        <use href="#C" x="145"/>
        <use href="#E"/>
        <use href="#D" x="290"/>
        <use href="#E" x="145"/>
        <use href="#E" x="448.35"/>
        <use href="#F"/>
        <use href="#D" x="870"/>
        <use href="#F" x="145"/>
        <use href="#E" x="751.7"/>
        <use href="#G"/>
        <use href="#D" x="1160"/>
        <use href="#G" x="145"/>
        <use href="#E" x="1041.7"/>
        <use href="#B" x="1595"/>
        <use href="#D" x="566.653"/>
        <use href="#D" x="-290"/>
        <defs>
        <path id="B" d="M127.753 7.776c-.75 1-1.109 2.336-1.078 4.008h-6.234c.063-1.687.352-3.289.867-4.805.547-1.328 1.406-2.555 2.578-3.68.875-.797 1.914-1.406 3.117-1.828s2.68-.633 4.43-.633c3.25 0 5.871.84 7.863 2.52s2.988 3.934 2.988 6.762c0 2-.594 3.688-1.781 5.063-.75.859-1.531 1.445-2.344 1.758.609 0 1.484.523 2.625 1.57 1.703 1.578 2.555 3.734 2.555 6.469 0 2.875-.996 5.402-2.988 7.582s-4.941 3.27-8.848 3.27c-4.812 0-8.156-1.57-10.031-4.711-.984-1.672-1.531-3.859-1.641-6.562h6.563c0 1.359.219 2.484.656 3.375.813 1.641 2.289 2.461 4.43 2.461 1.313 0 2.457-.449 3.434-1.348s1.465-2.191 1.465-3.879c0-2.234-.906-3.727-2.719-4.477-1.031-.422-2.656-.633-4.875-.633v-4.781c2.172-.031 3.688-.242 4.547-.633 1.484-.656 2.227-1.984 2.227-3.984 0-1.297-.379-2.352-1.137-3.164s-1.824-1.219-3.199-1.219c-1.578 0-2.734.5-3.469 1.5z"/>
        <path id="C" d="M288.667 22.448v5.227h-3.844v7.312h-6.539v-7.312h-13.453v-5.836l12.492-20.625h7.5v21.234h3.844zm-18.891 0h8.508V7.776l-8.508 14.672z"/>
        <path id="D" d="M303.48 35.831c-4.328 0-7.363-1.516-9.105-4.547s-2.613-7.352-2.613-12.961.871-9.937 2.613-12.984 4.777-4.57 9.105-4.57 7.367 1.523 9.117 4.57c1.734 3.047 2.602 7.375 2.602 12.984s-.871 9.93-2.613 12.961-4.777 4.547-9.105 4.547zm3.914-8.555c.609-2.062.914-5.047.914-8.953 0-4.094-.309-7.125-.926-9.094s-1.918-2.953-3.902-2.953-3.297.984-3.937 2.953-.961 5-.961 9.094c0 3.906.32 6.895.961 8.965s1.953 3.105 3.938 3.105 3.289-1.039 3.914-3.117z"/>
        <path id="E" d="M566.363 18.112c-.812 0-1.516.102-2.109.305-1.047.375-1.836 1.07-2.367 2.086l-6-.281 2.391-18.773h18.727V7.12h-13.898l-1.219 7.43c1.031-.672 1.836-1.117 2.414-1.336.969-.359 2.148-.539 3.539-.539 2.813 0 5.266.945 7.359 2.836s3.141 4.641 3.141 8.25c0 3.141-1.008 5.945-3.023 8.414s-5.031 3.703-9.047 3.703c-3.234 0-5.891-.867-7.969-2.602s-3.234-4.195-3.469-7.383h6.656c.266 1.453.773 2.574 1.523 3.363s1.844 1.184 3.281 1.184c1.656 0 2.918-.582 3.785-1.746s1.301-2.629 1.301-4.395c0-1.734-.406-3.199-1.219-4.395s-2.078-1.793-3.797-1.793z"/>
        <path id="F" d="M1151.73 34.987h-6.844V11.55h-7.992V7.003c2.109-.094 3.586-.234 4.43-.422 1.344-.297 2.438-.891 3.281-1.781.578-.609 1.016-1.422 1.313-2.437.172-.609.258-1.062.258-1.359h5.555v33.984z"/>
        <path id="G" d="M1440.254 7.917c-.797-.953-1.937-1.43-3.422-1.43-2.031 0-3.414.758-4.148 2.273-.422.875-.672 2.266-.75 4.172h-6.492c.109-2.891.633-5.227 1.57-7.008 1.781-3.391 4.945-5.086 9.492-5.086 3.594 0 6.453.996 8.578 2.988s3.188 4.629 3.188 7.91c0 2.516-.75 4.75-2.25 6.703-.984 1.297-2.602 2.742-4.852 4.336l-2.672 1.898c-1.672 1.188-2.816 2.047-3.434 2.578s-1.137 1.148-1.559 1.852h14.836v5.883h-23.273c.063-2.437.586-4.664 1.57-6.68.953-2.266 3.203-4.664 6.75-7.195 3.078-2.203 5.07-3.781 5.977-4.734 1.391-1.484 2.086-3.109 2.086-4.875 0-1.437-.398-2.633-1.195-3.586z"/>
        </defs>
        </symbol>
        </defs>
      </svg>
    </div>

</template>

<script>
export default {
  data() {
    return {
      timerInterval: null,
      timeRemaining: 0,  // in seconds
      isRinging: false,
      backgroundTranslation: 0,
      rotation: 0,
      lastRotation: 0,
      minuteDegreeInterval: 1.5,
      secondDegreeInterval: 1.5 / 15,
      timerWindingSound: new Audio('/audio/timer-winding.wav'),
      timerAlarmSound: new Audio('/audio/timer-alarm.wav'),
      timerTickingSound: new Audio('/audio/timer-ticking.wav'),
      faceCount: 48
    };
  },
  mounted() {
    this.timerTickingSound.loop = true;
  },
  computed: {
    formattedTime() {
      const totalSeconds = this.timeRemaining;
      const hours = Math.floor(totalSeconds / 3600);
      const minutes = Math.floor((totalSeconds % 3600) / 60);
      const seconds = Math.floor(totalSeconds % 60);
      const formattedMinutes = String(minutes).padStart(2, '0');
      const formattedSeconds = String(seconds).padStart(2, '0');
      return hours ? `${hours}:${formattedMinutes}:${formattedSeconds}` : `${minutes}:${formattedSeconds}`;
    },
    buttonText() {
      return this.timerInterval ? 'Stop' : 'Start';
    },
    isButtonDisabled() {
      return this.timeRemaining <= 0;
    },
    isTimerRunning() {
      return !!this.timerInterval;
    }
  },
  methods: {
    handleEggClick() {
      if (this.isTimerOpen() || this.isAlarmPlaying()) return;
      this.$el.classList.add('active');
      document.addEventListener('pointerdown', this.handleClickOutside);
    },
    isTimerOpen() {
      return this.$el.classList.contains('active');
    },
    isAlarmPlaying() {
      return !this.timerAlarmSound.paused && !this.timerAlarmSound.ended;
    },
    handleClickOutside(e) {
      if (!e.target.closest('.egg, .timer-button') && !this.isAlarmPlaying()) {
        document.addEventListener('pointerup', this.closeTimer, { once: true });
      }
    },
    closeTimer() {
      this.$el.classList.remove('active');
      document.removeEventListener('pointerdown', this.handleClickOutside);
    },
    toggleTimer() {
      if (this.timerInterval) {
        this.pauseTimer();
        this.timerInterval = null;
      } else {
        this.startTimer();
      }
    },
    startTimer() {
      this.timerTickingSound.play();
      this.timerInterval = setInterval(() => {
        if (this.timeRemaining > 0) {
          this.timeRemaining--;
        } else {
          this.stopTimer();
          this.isRinging = true;
          this.timerAlarmSound.play();
        }
      }, 1000);
    },
    pauseTimer() {
      this.timerTickingSound.pause();
      clearInterval(this.timerInterval);
    },
    stopTimer() {
      clearInterval(this.timerInterval);
      this.timerInterval = null;
      this.timerTickingSound.pause();
      this.isRinging = true;
    },
    startDrag(e) {
      if (!this.isTimerOpen() || this.isAlarmPlaying()) return;
      const startX = e.clientX;
      const startAngle = this.rotation;

      this.$el.querySelector('.egg-top').classList.add('dragged');
      if (this.isTimerRunning) this.pauseTimer();

      const pointerMoveHandler = (e) => {
        const deltaX = e.clientX - startX;
        const angleChange = deltaX / 2;

        this.rotation = Math.max(startAngle + angleChange, 0);
        const minutesSet = Math.max(this.rotation % 360 / 6, 0);
        this.timeRemaining = Math.max(minutesSet * 60, 0);

        if (!this.isTimerRunning && this.rotation >= 0) {
          this.timerButtonDisabled = true;
        }

        if (Math.abs(this.rotation - this.lastRotation) >= 1) {
          this.timerWindingSound.play();
          this.lastRotation = this.rotation;
        }
        console.log('Rotation:', this.rotation);
      };

      const pointerUpHandler = () => {
        this.$el.querySelector('.egg-top').classList.remove('dragged');

        document.removeEventListener('pointermove', pointerMoveHandler);
        document.removeEventListener('pointerup', pointerUpHandler);
      };

      document.addEventListener('pointermove', pointerMoveHandler);
      document.addEventListener('pointerup', pointerUpHandler);
    },
  },
};

</script>
  
  
<style>
  /* Styles in main app file */
</style>