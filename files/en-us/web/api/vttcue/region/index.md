---
title: "VTTCue: region property"
short-title: region
slug: Web/API/VTTCue/region
page-type: web-api-instance-property
browser-compat: api.VTTCue.region
---

{{APIRef("WebVTT")}}

The **`region`** property of the {{domxref("VTTCue")}} interface returns and sets the {{domxref("VTTRegion")}} that this cue belongs to.

## Value

A {{domxref("VTTRegion")}} object.

## Examples

In the following example a new {{domxref("VTTCue")}} is created, then the value of `region` is printed to the console.

```js
let video = document.querySelector("video");
let track = video.addTextTrack("captions", "Captions", "en");
track.mode = "showing";

let cue = new VTTCue(0, 0.9, "Hildy!");
console.log(cue.region);

track.addCue(cue);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
