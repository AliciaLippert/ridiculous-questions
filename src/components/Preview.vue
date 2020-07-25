<template>
  <div class="h-screen flex flex-col">

    <section class="w-full flex items-center justify-center">
        <!-- <img src="@/assets/icons/gopher.jpg"> -->
<!--         <p class="text-center py-3 text-sm">Let's happy hour y'all</p>
 -->    </section>

    <section class="w-full flex items-center justify-center question">
      <div class="relative">
       <!--  <p class="smaller">This is a question for {{chosenTeam}}</p><br /> -->
        <p>{{chosenQuestion}}</p>
      </div>
    </section>

    <section class="w-full flex items-center justify-center flex-grow">
      <div class="relative">
        <a href="#" class="rainbow-button" v-on:click="picker();">Question!</a>
      </div>
    </section>




    <p class="text-center py-3 text-sm">
      Made with ❤️ 
    </p>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

import generateTriangleCss from '@/utils/triangle-styles'
import generateTooltipCss from '@/utils/tooltip-styles'

import CssCode from '@/components/CSSCode'
import HtmlCode from '@/components/HTMLCode'

//import states from "../assets/data.json"


export default {
  components: {
    CssCode,
    HtmlCode
  },




  data: () => ({

  list: [
    "Have you ever seen a ghost?",
    "What do you think it’s like being Ellen Degeneres?",
    "Would you rather have a hand made out of ham or an armpit that dispenses sunscreen?",
    "As you lay dying, which celebrity would you want to stroke your hair?",
    "If you were given the powers of King Midas, what would you choose to turn everything that you touch into?",
    "What’s the best kind of cheese?",
    "Isn’t silver actually better than gold?",
    "Who is your favorite historical character?",
    "Would you rather be a cow or a badger?",
    "Have you ever had a near death experience?",
    "What’s the worst experience you’ve ever had in a hotel?",
    "What’s the best advice you’ve ever received and ignored?",
    "If you had to go on a month-long vacation with a celebrity, who would you choose?",
    "What’s the best museum you’ve ever been to?",
    "If you could have a part of the human body named after you, what would it be and why?",
    "What do you consider your median achievement?",
    "Would you rather have a tongue that could taste impending danger or a free iPhone?",
    "Would you rather do a Freaky Friday with Kim Kardashian or Kanye West?",
    "What do you consider to be the most mediocre chocolate bar?",
    "Would you rather have no ears or no dignity?",
    "If you had to, would you rather give up chocolate or cheese?",
    "What modern-day item do you think will seem ridiculously archaic in ten years’ time?",
    "Did any future celebrities go to your school?",
    "If you had a silo, what would you store in it?",
    "What’s the most pretentious book you’ve ever bought but not read?",
    "What’s the most impulsive thing you’ve ever done?",
    "What’s the most unusual restaurant you’ve ever been to?",
    "What thing that seemingly everyone loves do you not like that much?",
    "Do you have something that you should regret, but you don’t?",
    "When people find out about what you do for a living, what’s the most annoying thing they say?",
    "What is your biggest weakness?",
    "What’s your favorite store?",
    "What would be the worst place you can imagine to go on a first date?",
    "Do you prefer things to be planned or spontaneous?",
    "What’s the most unusual thing you’ve ever collected?",
    "Who is your most eccentric relative and what is the most eccentric thing you’ve ever done?",
    "What is your most interesting quirk?",
    "What convention of our society do you wish no longer existed?",
    "What have you recently done for the first time?",
    "What is the opposite of a koala?",
    "What do you consider a wasted life?",
    "What’s fine in small numbers but terrifying in large numbers?",
    "What do you wish you knew more about?",
    "Is there a line between art and not art?",
    "What would the trailer to a movie about your life be like?",
    "What’s the weirdest thing that has happened to you while working at your job?",
    "What is the funniest corporate / business screw up you have heard of?",
    "What is the funniest doomsday device a super villain could threaten the world with?",
    "If you found a briefcase filled with 1 million in 100$ bills in front of your door, what would you do with it?",
    "What are some things you want to accomplish before you die?",
    "What book has influenced you the most?",
    "What’s the most food you've ever eaten for breakfast?",
    "How long do you think it would take to fill a bath with your tears?",
    "How do you decide when it’s time to retire a pair of pants?",
    "What’s the quickest you’ve broken a new Year’s resolution?",
    "What's the worst gift you've ever received?",
    "Who will play the lead in the movie about this pandemic and why?",
    "What is the worst animal?",
    "Why do you think everyone stopped wearing hats?",
    "How would you improve apples?",
    "What’s the worst thing that a cow has done to you?",
    "Have you ever come up with a brilliant idea for an app?",
    "What’s the most pretentious thing that you have ever done?",
    "Have you ever made up with your nemesis and become friends?",
    "What was the last thing that struck you?",
    "What’s the scariest thing that has ever happened to you in an AirBnB?",
    "Who is your favourite Steve?",
    "Would you rather be able to see through walls or get an all expenses paid first-class trip to Madagascar?",
    "What's the most lamented thing you've ever had stolen from you?",
    "What is your least favourite colour?",
    "Where or what are you an hour from right now?",
    "What's the worst leak you've ever experienced?",
    "What was the best birthday you ever had?",
    "What are your tactics for winning at Monopoly?",
    "What do you think Tom Cruise is doing right now?",
    "Who is your favourite octogenarian?",
    "What was the most inconvenient/annoying occasion that your phone battery ran out?",
    "Have you ever had an epiphany?",
    "Would you rather have no ears or no dignity?",
    "Where is the strangest place that you've ever slept (or tried to sleep)?",
    "If you didn't live where you live now, where would you live?",
    "How would you break out of prison?",
    "If you could time travel and say only five words to your younger self, what would those words be?",
    "Where is the fanciest place you've ever been?",
    "Is cereal soup?",
    "What secret conspiracy would you like to start?",
    "What are the unwritten MongoDB rules?",
    "What is something that everyone looks stupid doing?",
    "What part of a kid’s movie completely scarred you?", 
    "What inanimate object do you wish you could eliminate from existence (excluding the ones that kill people)?",
    "If peanut butter wasn’t called peanut butter, what would it be called?",
    "What movie would be greatly improved if it was made into a musical?",
    "What sport would be the funniest to add a mandatory amount of alcohol to?",
    "What would be the coolest animal to scale up to the size of a horse?",
    "What would the world be like if it was filled with male and female copies of you?",
    "If you were arrested with no explanation, what would your friends and family assume you had done?",
    "If someone asked to be your apprentice and learn all that you know, what would you teach them?",
    "If all the States in the USA were represented by one food, what state would you want to live in based on that food?",
    "Do you have a preferred ear?", 
    "Chickens or Moscow?",
    "Would you rather wear a hat made out of beef or shoes made out of yogurt?",
    "Do you have a favorite plate?", 
    "To be or not to be?", 
    "If you could have a dream dinner party with any person living or dead, who would you employ to do the dishes?",
    "What do you think fish are thinking about?",
    "Have you ever stolen a golf cart?",
    "What's the most expensive thing you've had eaten by a pet?",
    "Do you have a favorite unsolved crime?",
    "What's the most amazing thing you've ever witnessed but not participated in?",
    "What would surprise your school's career counselor about the job you have now as an adult?",
    "What's the furthest you've ever burrowed?",
    "Do you think you've already had the best day of your life?",
    "What useless phrase are you able to say in a foreign language?",
    "What is your favorite flat thing?",
    "What is the dumbest thing you once believed, but now you no longer believe?",
    "Do you take it personally that you've never been abducted by aliens?",
    "Have you ever annoyed a mailman?",
    "What one legal thing would you make illegal?",
    "What one illegal thing would you make legal?",
    "What's the most boring thing you can order from a coffee shop?",
    "Can ghosts change clothes or do they stay in the clothes they died in forever?",
    "Is it better to have loved and lost than to have to eat nothing but Pop Tarts for three months?",
    "Where did your family go on vacation when you were a kid?",
    "Would it be better to never be able to say 'yes' or never be able to say 'no'?",
    "Do you buy yourself birthday presents?",
    "Do you sleep with socks on?"

  ],

  team: [
    "Sarah", "Alicia", "Lars", "Shiva", "Alissa"

  ],



    chosenQuestion: '', 
    chosenTeam: ''
  }),

  

  computed: {
    ...mapGetters([
      'getSettings'
    ]),
    stylesTriangle () {
      return generateTriangleCss(this.getSettings)
    },
    stylesTooltip () {
      return generateTooltipCss(this.getSettings)
    },
    // questions() {
    //   return states.bigList.map(item => {
    //     return item.question;
    //   });
    // }
  },

  methods: {
     picker: function(){
        var chosenNumber = Math.floor(Math.random() * this.list.length);
        this.chosenQuestion = this.list[chosenNumber];
    }, 

    person: function(){
        var chosenPerson = Math.floor(Math.random() * this.team.length);
        this.chosenTeam = this.team[chosenPerson];
    }
  }
}
</script>
