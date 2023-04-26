
<template>
  <!-- // Static -->
  <HelloWorld msg="Hello World!" />
  <input type="text" v-model="who" class="m-2 p-2 bg-gray-100 border border-gray-500">
  <Greeting greeting="Hi" :who="who" />

  <!-- // Reactive -->
  <HelloWorld :msg="appWho" />
  <button class="m-2 px-5 py-2.5 rounded-lg bg-gray-400 text-white" @click="setWho('JavaScript')">JavaScript</button>
  <button class="m-2 px-5 py-2.5 rounded-lg bg-gray-400 text-white" @click="setWho('Everyone')">Everyone</button>

  <div class="container">
    <Repeat :times="count" content="55" />
    <button class="m-2 px-5 py-2.5 rounded-lg bg-gray-400 text-white" @click="increment()">Repeat</button>
  </div>

  <div class="container">
    <CustomSelect :selected="selected" :options="options" />
  </div>

  <div class="container">
    <!-- <PaginatedList :items="snacks" /> -->
    <PaginatedList :items="snacks" :limit=3 :offset=1 />
  </div>

  <div class="container">
    <Repeat1 :config="{ times: 3, content: `Repeat me.` }" />
  </div>

  <div class="container">
    <!-- without template content -->
    <Box></Box>
    <!-- with template content -->
    <Box>
      <h3>This whole h3 is rendered in the slot with parent count {{ count1 }}</h3>
    </Box>
    <button class="px-5 py-2.5 bg-gray-400 text-white rounded" @click="count1++">Increment</button>
  </div>

  <div class="container">
    <Article>
      <template v-slot:title>
        <h3>My Article Title</h3>
      </template>
      <!-- <template v-slot:excerpt>
        <p>First paragraph of content</p>
        <p>Second paragraph of content</p>
      </template> -->
      <template #excerpt>
        <p>Shorthand syntanx for slot</p>
      </template>
      <template #default>Hello</template>
    </Article>
  </div>

  <div class="container">
    <PaginatedList :items="snacks">
      <template #default="{ item }">
        {{ item.content }}
      </template>
    </PaginatedList>
  </div>

  <div class="container">
    <Card>
      <template #image>
        <img src="https://picsum.photos/id/1015/300" alt="landscape">
      </template>
      <template #title>
        <h2>My Holiday picture</h2>
      </template>
      <template #description>
        <p>Here I can describe the contents of the picture.</p>
        <p>For example what we can see in the photo is a nice landscape</p>
      </template>
    </Card>
  </div>

  <div class="container">
    <input type="text" ref="theInput" class="p-2 rounded bg-gray-50 border border-gray-500">
    <button class="px-5 py-2.5 bg-gray-400 rounded text-white" @click="focus()">Focus Input</button>
  </div>

  <div class="container">
    <Countable></Countable>
  </div>

  <div class="container">
    <p>Message: {{ parentMessage }}</p>
    <ChildtoParent @send="updateParentMessage" />
    <button class="text-white bg-gray-400 px-5 py-2.5" @click="parentMessage = ``">Reset</button>
  </div>

  <div class="container">
    <h1>script setup emits</h1>
    <p>Message: {{ parentMessage1 }}</p>
    <MessageEditor @send="updateParentMessage1" />
    <button class="text-white bg-gray-400 px-5 py-2.5" @click="parentMessage1 = ``">Reset setup</button>
  </div>

  <div class="container">
    <h1 class="text-2xl font-semibold my-2">Chat Interface</h1>
    <MessageFeed :message="chatMessage" />
    <ChatInterface @send="showMessage" />
  </div>
</template>

<script lang="ts">
import Box from './components/Box.vue';
import CustomSelect from './components/CustomSelect.vue';
import Greeting from './components/Greeting.vue';
import HelloWorld from './components/HelloWorld.vue';
import PaginatedList from './components/PaginatedList.vue';
import Repeat from './components/Repeat.vue';
import Repeat1 from './components/Repeat1.vue';
import Article from './components/Article.vue';
import Card from './components/Card.vue';
import Countable from './components/Countable.vue';
import ChildtoParent from './components/ChildtoParent.vue';
import MessageEditor from './components/MessageEditor.vue';
import ChatInterface from './components/ChatInterface.vue';
import MessageFeed from './components/MessageFeed.vue';

export default {
  components: {
    HelloWorld,
    Greeting,
    Repeat,
    CustomSelect,
    PaginatedList,
    Repeat1,
    Box,
    Article,
    Card,
    Countable,
    ChildtoParent,
    MessageEditor,
    ChatInterface,
    MessageFeed
  },
  data() {
    return {
      appWho: "Vue.js",
      greeting: "Hello",
      who: "Vue.js",
      count: 1,
      // selected: "",
      selected: "salt-vinegar",
      options: [
        {
          value: "ready-salted",
          label: "Ready Salted",
        },
        {
          value: "cheese-onion",
          // label: "",
          label: "Cheese & Onion",
        },
        {
          value: "salt-vinegar",
          label: "Salt & Vinegar",
        }
      ],
      snacks: [
        {
          id: "ready-salted",
          content: "Ready Salted"
        },
        {
          id: "cheese-onion",
          content: "Cheese & Onion"
        },
        {
          id: "salt-vinegar",
          content: "Salt & Vinegar"
        }
      ],
      count1: 0,
      parentMessage: "",
      parentMessage1: "",
      chatMessage: [""],
    }
  },
  methods: {
    setWho(newWho: string) {
      this.appWho = newWho
    },
    increment() {
      this.count += 1
    },
    focus() {
      (this.$refs.theInput as any).focus()
    },
    updateParentMessage(newMessage: string) {
      this.parentMessage = newMessage
    },
    updateParentMessage1(newMessage: string) {
      this.parentMessage1 = newMessage
    },
    showMessage(msg: string) {
      this.chatMessage = [...this.chatMessage, msg]
    },
  }
}
</script>