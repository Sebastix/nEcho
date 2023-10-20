# Echostr

Echostr is a micro-application on the web doing just one thing as good as possible. It will echo (advertise) your relay preferences to your social graph on nostr. It means that it's trying to tell the clients of your followers which relay they should read to get the events you're posting. 

[https://github.com/nostr-protocol/nips/blob/master/65.md](https://github.com/nostr-protocol/nips/blob/master/65.md)

> 💡 The purpose of this NIP is to help clients find the events of the people they follow, to help tagged events get to the people tagged, and to help nostr scale better.

NIP-65 is submitted by Mike Dilger who is the author of Gossip.  
To learn more about Mike, Gossip and NIP-65 you should listen to this [Nostrovia podcast episode](https://fountain.fm/episode/13389100721).

> Gossip follows people at the relays they profess to post to. That means it has to discover which relays those are and make smart relay selection choices based on things like which relays cover the most people you follow.

[Video about the Gossip relay model](https://mikedilger.com/gossip-relay-model.mp4)

*Notes from the author @Sebastian* 
* I started this project because I'm **scratching my own itch**. I'm loosing my list of relays and followed contacts because the use of different clients. 
* **I’m an advocate of more Nostr clients need to adopt NIP-65 for this reason. With Echostr I’m trying to proof that purpose in practice.**
* I'm not familiar (yet) with all the NIPs from Nostr and I'm learning among the way by doing.
* This is one of my first pieces of software I'm developing for Nostr.

### Other relevant resources

- https://github.com/nostr-protocol/nips/pull/349
- https://github.com/nostr-protocol/nips/pull/230
- https://github.com/nostr-protocol/nips/pull/218
- https://bountsr.org/design/2023/01/26/relay-based-design.html
- https://overcast.fm/+_cNZFP9sg/48:30 Nostr Talks with Hodlbod about relay discovery and gossiping 

## Application flow

- [ ] Authenticate with your Nostr profile
- [ ] Get your social graph
  - [ ] Contact list 
      - [ ] List of followers
      - [ ] List of following
      - [ ] Search for relays where your npub1 lives [inspired by Coracle.social](https://github.com/staab/coracle/blob/1e0b032d0384f389deb5ac458e8146b17ff3c13b/src/agent/cmd.ts#L13)
        - [ ] Use [nostr.watch](http://nostr.watch) as a source
      - [ ] Get relay list of each followed person
        - [ ] Check their relays on their NIP-05 internet identifier
        - [ ] Find events with kind 10002 which contains relay list metadata
        - [ ] Check relay hints (tags) of notes
- [ ] Get an overview of the relays where your events live
- [ ] Push / delegate selected list of relays to your social graph with event kind `10002`
- [ ] Store your selected relays as a backup (JSON file)
  - [ ] On your personal relay
  - [ ] On your device
- [ ] Get list of relay recommendations based on your social graph
  - [ ] Relays where to read from
  - [ ] Relays where to post to
- [ ] Ask your followers to do the same by posting a note to build even a better relay graph with this tool. Ask the client authors to implement NIP-65 for this.

## NIP implementations

- [ ] NIP-02 - Contact List and Petnames
- [ ] NIP-05 - Mapping Nostr keys to DNS-based internet identifiers
- [ ] NIP-07 - `window.nostr` capability for web browsers
- [ ] NIP-11 - Relay Information Document
- [ ] NIP-20 - Command Results
- [ ] NIP-42 - Authentication of clients to relays
- [ ] NIP-65 - Relay List Metadata
- [ ] NIP-78 - Arbitrary custom app data

## TODOs

- [x] Init Vue project  
- [x] Add README.me  
- [x] Push project to Github
- [ ] Make a scheme of the application flow
- [ ] Ask for feedback on the concept 
- [ ] Build

## Requirements

* Node
* NPM

Possible dependencies to use

* https://github.com/nbd-wtf/nostr-tools

## Tech stack

* Vue 3 with Vite

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Used dependencies

See `package.json`

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```bash
npm run dev
```

### Type-Check, Compile and Minify for Production

```bash
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```bash
npm run lint
```

## How to contribute

1. Create an issue
2. Create a pull request from your forked repo
3. Just send me a message

## About the author

Sebastian Hagens is a self-employed creative technologist working as a fullstack webdeveloper and tech consultant.  
Follow Sebastian on Nostr:  
Pubkey `npub1qe3e5wrvnsgpggtkytxteaqfprz0rgxr8c3l34kk3a9t7e2l3acslezefe`  
NIP-05 id `sebastian@sebastix.dev`