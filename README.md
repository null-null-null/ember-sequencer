[![npm version](https://badge.fury.io/js/ember-sequencer.svg)](https://badge.fury.io/js/ember-sequencer)
[![Build Status](https://travis-ci.org/null-null-null/ember-sequencer.svg?branch=master)](https://travis-ci.org/null-null-null/ember-sequencer)

# ember-sequencer

A simple Ember.js sequencer, allowing you to string together a series of frames defined directly within your template.

## installation

```bash
ember install ember-sequencer
```

## usage

```hbs
{{#ember-sequencer
  animationAdapter="velocity"
  animationIn=(hash duration=1000 effect=(hash translateX=(array 0 '100%') opacity=(array 1 0)))
  animationOut=(hash duration=1000 effect=(hash opacity=0))
  as |sequencer|}}
  {{#sequencer.frame}}
    <div>Frame 1</div>
  {{/sequencer.frame}}
  {{#sequencer.frame}}
    <img src="my-image.png">
  {{/sequencer.frame}}
  {{#sequencer.frame as |frame|}}
    <h1>Sub-Sequencer</h1>
    {{#if frame.isVisible}}
      {{#ember-sequencer
        animationAdapter="velocity"
        animationIn=(hash duration=1000 effect=(hash translateY=(array 0 '-100%') opacity=(array 1 0)))
        animationOut=(hash duration=1000 effect=(hash opacity=0))
        as |sub-sequencer|}}
        {{#sub-sequencer.frame}}
          <div>Frame 1</div>
        {{/sub-sequencer.frame}}
        {{#sub-sequencer.frame}}
          <div>Frame 2</div>
        {{/sub-sequencer.frame}}
        {{#sub-sequencer.frame}}
          <div>Frame 3</div>
        {{/sub-sequencer.frame}}
      {{/ember-sequencer}}
    {{/if}}
  {{/sequencer.frame}}
{{/ember-sequencer}}

```
