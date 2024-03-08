# Echostr

Echostr is a webbased micro-application doing just one thing as good as possible. It will echo (advertise) your relay preferences to your social graph on Nostr. It means that it's trying to tell the clients of your followers which relay they should read to get the events you're posting. 

[https://github.com/nostr-protocol/nips/blob/master/65.md](https://github.com/nostr-protocol/nips/blob/master/65.md)

> 💡 The purpose of this NIP is to help clients find the events of the people they follow, to help tagged events get to the people tagged, and to help nostr scale better.

NIP-65 is submitted by Mike Dilger who is the author of the client Gossip.  
To learn more about Mike, Gossip and NIP-65 you should listen to this [Nostrovia podcast episode](https://fountain.fm/episode/13389100721).

> Gossip follows people at the relays they profess to post to. That means it has to discover which relays those are and make smart relay selection choices based on things like which relays cover the most people you follow.

[Video about the Gossip relay model](https://mikedilger.com/gossip-relay-model.mp4)

*Notes from the author @Sebastian* 
* I started this project because I'm **scratching my own itch**. I'm loosing my list of relays and followed contacts because the use of different clients. 
* **I’m an advocate of more Nostr clients need to adopt NIP-65 for this reason. With Echostr I’m trying to proof that purpose in practice.**
* I'm not familiar (yet) with all the NIPs from Nostr. I'm learning among the way by doing.
* This is one of my first pieces of software I'm developing for Nostr.

### Other relevant resources

- https://github.com/nostr-protocol/nips/pull/349
- https://github.com/nostr-protocol/nips/pull/230
- https://github.com/nostr-protocol/nips/pull/218
- https://bountsr.org/design/2023/01/26/relay-based-design.html
- https://overcast.fm/+_cNZFP9sg/48:30 Nostr Talks with Hodlbod (developer of the client Coracle) about relay discovery and gossiping 

## Application flow

- [ ] Authenticate with your Nostr profile
- [ ] Get your social graph
  - [ ] Contact list 
      - [ ] List of followers
      - [ ] List of following
      - [ ] Search for relays where your npub1 lives [inspired by Coracle.social](https://github.com/staab/coracle/blob/1e0b032d0384f389deb5ac458e8146b17ff3c13b/src/agent/cmd.ts#L13)
        - [ ] Use [nostr.watch](http://nostr.watch) as a source for validating relays
      - [ ] Get relay list of each followed person
        - [ ] Check their relays on their NIP-05 internet identifier
        - [ ] Find events with kind 10002 which contains relay list metadata
        - [ ] Find most recent event with kind 0 which contains a relay list metadata 
        - [ ] Check relay hints (tags) of own notes
- [ ] Get an overview of the relays where your events live
- [ ] Get an overview with a diff between your contact metadata relay list (kind 0), relay list metadata (kind 10002) and relays of your internet identifier (NIP-05)
- [ ] Push / delegate selected list of relays to your social graph with event kind `10002`
  - [ ] Push it as a kind 0
  - [ ] Push it as a kind 10002
- [ ] Store your selected relays as a backup (JSON file)
  - [ ] On your personal relay
  - [ ] On your device
- [ ] Get list of relay recommendations based on your social graph
  - [ ] Relays where to read from
  - [ ] Relays where to post to
- [ ] Ask your followers to do the same by publishing a note to build even a better relay graph with this tool.

## NIP implementations

- [ ] NIP-02 - Contact List and Petnames
- [ ] NIP-05 - Mapping Nostr keys to DNS-based internet identifiers
- [ ] NIP-07 - `window.nostr` capability for web browsers for login
- [ ] NIP-11 - Relay Information Document
- [ ] NIP-20 - Command Results
- [ ] NIP-42 - Authentication of clients to relays
- [ ] NIP-65 - Relay List Metadata
- [ ] NIP-78 - Arbitrary custom app data

## Features + roadmap 

- [x] Init Vue project  
- [x] Add README.me  
- [x] Push project to Github
- [ ] Make a scheme of the application flow with Excalidraw
- [ ] Make a design 
- [ ] Build a proof-of-concept
- [ ] Ask for feedback on the concept and PoC 
- [ ] Fund the project with sats (zaps, fundraiser, donations)
- [ ] Build & ship it

## Requirements

* Node
* NPM

## Tech stack / dependencies

* Vue 3 with Vite
* NDK (Nostr Dev Kit)
* SASS
* TailwindCSS

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

## How to contribute

1. Create an issue
2. Create a pull request from your forked repo
3. Just send me a message

## About the author

Sebastian Hagens is a self-employed creative technologist working as a Drupal & fullstack webdeveloper and tech consultant.

**Follow Sebastian on Nostr**  
Pubkey: `npub1qe3e5wrvnsgpggtkytxteaqfprz0rgxr8c3l34kk3a9t7e2l3acslezefe`      
Handle: `sebastian@sebastix.dev`

## License
`GPL-2.0` GNU General Public License v2.0

## Donations / funding

Between my fiat mining work as a developer I spend time building this application.

You are free to send some sats:
* bitcoin: `bc1p3p6jq2sxsf650lgllv57st9h97xj37fflg5t8d265saz6yqzcdyqd7pzun`
* lightning address: `sebastian@lnd.sebastix.com`  
* Nostr: `npub1qe3e5wrvnsgpggtkytxteaqfprz0rgxr8c3l34kk3a9t7e2l3acslezefe` / `sebastian@sebastix.dev`