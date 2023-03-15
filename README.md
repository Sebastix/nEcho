# Echostr

Echostr is a micro-application doing just one thing as good as possible. It will echo (advertise) your relay preferences to your social graph on nostr.

[https://github.com/nostr-protocol/nips/blob/master/65.md](https://github.com/nostr-protocol/nips/blob/master/65.md)


> 💡 The purpose of this NIP is to help clients find the events of the people they follow, to help tagged events get to the people tagged, and to help nostr scale better.

*Notes from the author @Sebastix* 
* I started this project because I'm **scratching my own itch**. I'm loosing my list of relays and followed contacts because the use of different clients. 
* **I’m an advocate of more nostr clients need to adopt NIP-65 for this reason. With Echostr I’m trying to proof that purpose in practice.**
* I'm not familiar (yet) with all the NIPs from nostr and I'm learning among the way by doing.

## Application flow

- [ ] Authenticate with your nostr ID
- [ ] Get your social graph
    - [ ] List of followers
    - [ ] List of followed
    - [ ] Search for relays where your npub lives (inspired by Coracle.social)
      - [ ] Use [nostr.watch](http://nostr.watch) as a source
    - [ ] Get relay list of each followed person
      - [ ] Check their relays on their NIP-05 identifier
- [ ] Get an overview of the relay where your events live
- [ ] Push / delegate selected list of relays to your social graph with event kind `10002`
- [ ] Store your selected relays as a backup (JSON file)
  - [ ] On your personal relay
  - [ ] On your device
- [ ] Get list of relay recommendations based on your social graph
- [ ] Ask your followers to do the same with a note to build even a better relay graph with this tool

## NIPs implementation

- [ ] NIP-02
- [ ] NIP-11
- [ ] NIP-20
- [ ] NIP-42
- [ ] NIP-65

## TODOs

- [x] Init Vue project  
- [ ] Add README.me  
- [ ] Push project to Github
- [ ] Make a scheme of the application flow 

## Requirements

* Node
* NPM

## Tech stack

* Vue 3 with Vite
* TypeScript support

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Used dependencies

See `package.json`

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

## How to contribute

1. Create an issue
2. Create a pull request from your forked repo
3. Just send me a message

## About the author

Sebastian Hagens is a self-employed creative technologist as a webdeveloper and tech consultant.  
Follow Sebastian on Nostr with pubkey `npub1qe3e5wrvnsgpggtkytxteaqfprz0rgxr8c3l34kk3a9t7e2l3acslezefe` or NIP-05 ID: `sebastian@sebastix.dev`