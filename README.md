# gong-transcript
Bookmarklet page for drag and drop bookmarklet for copying a Gong transcript

Here's the raw JS code for the bookmarklet:

```javascript
const monologues = document.querySelectorAll(".monologue-inner")

const transcriptElements = []

monologues.forEach(monologue => {
    const speaker = monologue.querySelector("span.timestamp__speaker").innerText
    const dialogueElements = monologue.querySelectorAll("span.word-wrapper")
    const dialogue = []
    
    dialogueElements.forEach(element => {
        dialogue.push(element.innerText)
    })

    transcriptElements.push(`${speaker}: ${dialogue.join("")}`)
})

const transcript = transcriptElements.join("\n")
console.log(transcript)

try {
    await navigator.clipboard.writeText(transcript)
    window.alert("Transcript copied to clipboard!")
} catch (err) {
    window.alert(`Transcript could not be copied to clipboard, but is available in the browser console. Error: ${err}`)
}
```

And I used this page to minify and create the link code:
https://make-bookmarklets.com/
