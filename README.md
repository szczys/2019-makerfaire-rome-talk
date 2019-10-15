# The World is Hiring Hackers: Why a Personal Journey of Discovery Has a Place on the Modern Engineer's Resume
## A talk presented by Mike Szczys at 2019 Maker Faire Rome

These slides can be view at:
https://szczys.github.io/2019-makerfaire-rome-talk/#/

Slide are based on the reveal.js platform found here:
https://github.com/hakimel/reveal.js

## Installation

The **basic setup** is for authoring presentations only. The **full setup** gives you access to all reveal.js features and plugins such as speaker notes as well as the development tasks needed to make changes to the source.

### Basic setup

The core of reveal.js is very easy to install. You'll simply need to download a copy of this repository and open the index.html file directly in your browser.

1. Download the latest version of reveal.js from <https://github.com/hakimel/reveal.js/releases>
2. Unzip and replace the example contents in index.html with your own
3. Open index.html in a browser to view it

### Full setup

Some reveal.js features, like external Markdown and speaker notes, require that presentations run from a local web server. The following instructions will set up such a server as well as all of the development tasks needed to make edits to the reveal.js source code.

1. Install [Node.js](http://nodejs.org/) (4.0.0 or later)

1. Clone the reveal.js repository
   ```sh
   $ git clone https://github.com/hakimel/reveal.js.git
   ```

1. Navigate to the reveal.js folder
   ```sh
   $ cd reveal.js
   ```

1. Install dependencies
   ```sh
   $ npm install
   ```

1. Serve the presentation and monitor source files for changes
   ```sh
   $ npm start
   ```

1. Open <http://localhost:8000> to view your presentation

   You can change the port by using `npm start -- --port=8001`.

# Exporting to PDF

It's always nice to have a PDF when all else fails and you just need to show the presentation on someone else's machine. Reveal.js has options for PDF export but when making the style for this deck I didn't make changes to the PDF print styling so things like the background image is missing.

The alternative solution to this is to use Decktape to export the slides. This works great, except for the embedded videos which don't get exported at all (not even a thumbnail image). My solution was to export the deck as screenshots using Decktape, then take my own screenshots of the slides that have videos, then roll them all into a PDF. Hacky, but it'll work in a pinch.

* Install Deck tape in same directory as the reveal.js presentation: `npm install decktape`
* Make a directory to hold screenshots: `mkdir screenshots`
* Run Decktap: ````npm bin`/decktape --screenshots reveal -s 1920x1080 http://192.168.1.105:8000/ 2019-rome-maker-faire-talk-Szczys.pdf```
* Turn off controls and progress to take screenshots of the video slides:
  * `controls: false,`
  * `progress: false,`
* Take screenshots the same sizes as captured by Decktape and replace the appropriate slides in the screenshots directory
* `cd screenshots`
* convert "*.png" -quality 100 2019-rome-maker-faire-talk_Szczys-Mike.pdf
