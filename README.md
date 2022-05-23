# scrape-panos
Methods for scraping panoramic/virtual/360 tours. Eventually I aim to include a collection of useful scripts for example, to generate a list of URLs to scrape for a particular panorama format, or based on a particular pattern, to extract URL lists from WACZ/WARC files, to scrape XML files for patterns/files and so on.

For now I will use it to start documenting methods.

# General strategy
To scrape a web-hosted panorama, a general strategy (which can be accomplished through a range of different methods) is to:

1. Work out the tile URL pattern. Tile URLs point to a large number (often thousands) of image files, which are used by the panorama viewer to render the scene(s). URLs generally follow a pattern, using numbers and/or letters to denote the tile's spatial location/extent.
2. Generate a list of all tile URLs.
3. Generate a list of all other files required for the tour. This will include at least one HTML page, but often multiple JavaScript files, MP3s for tour narration, non-tile image files for hotspots and UI elements, and so on.
4. Use these two lists to create and test an archived version of the site. Sometimes the testing process will highlight missing files, which should then be added, and further testing cycles run until the archive appears complete.

Each step can use one or more approaches. These are detailed below, although this is not exhaustive. Sometimes you will need to develop a new approach to suit the scenario.

# 1. Work out the tile URL pattern
There are several ways to do this. The first two options should be tried first, as they involve checking for shortcuts. After this, it is up to you, although you may choose depending on preference/experience/your analysis of the specific tour and suitability. Options 3+ are to be detailed in their own subsections. Sometimes a combination of methods 3+ may be appropriate.

1. Check if the tile URLs are in open web folders. Rarely the case, but if it is, it will save a lot of time.
2. Check what JavaScript library the tour uses, and whether you or anyone you know are familiar with it. A library will generally follow the same URL pattern when used on different sites (although library configuration can impact on this), so you may save some time here by reusing someone else's code, or at least getting advice from them.
3. Examine the source code and data files used by the webpage, for example `.js` and `.xml`/`.json` files and `<script>` tags, to figure out the tour's tile pattern. This method when combined with experience/step 2, can be very quick - but may be more tricky for unfamiliar tour libraries.
4. Run network analysis while viewing the live tour to generate a list of files downloaded, exploring a scene in enough depth to figure out the general pattern, then exploring all scenes superficially to figure out the scene URLs/slugs
5. Run manual webrecorder while viewing the live tour, then scrape `.wacz`/`.warc` files (e.g. using `grep`/`sed`/`awk` etc.) to generate a list of URLs, and then as in step 4, figure out the pattern and apply it to all scenes.

## 1.1 Checking for open web folders
TODO

## 1.2 Checking the JS library
TODO

## 1.3 Examining the source code and data files
TODO

## 1.4 Network analysis
TODO

## 1.5 Manual webrecorder
TODO

# 2. Generate a list of all tile URLs
Once you know the pattern, it is up to you how you generate a list of URLs. Some options are:

1. Use a scripting language such as JS(/Node), Python or R (but any will do) to follow a pattern, e.g. using loops/functional methods. Some examples will be added below.
2. Use a pattern generation tool such as reverse RegEx, or Tracery, to generate URLs based on a given pattern. TODO examples
3. Use a spreadsheet/database to set up the variables and join them into a pattern to generate a list.
4. Use an advanced text editor to generate each stage of the pattern, using copy/paste and find/replace (or regex find/replace) to change the relevant sections.

## TODO examples for the above

# 3. Generate a list of all other files
TODO approaches... similar to 1, in general.

# 4. Create and test and archive version
For testing purposes, it is generally advised to create a local archive version. Once this is confirmed complete and working, it can optionally (depending on the project) be saved/distributed elsewhere.

Types of archive version:
1. Filesystem mirror of folder/file structure. Can be tested by running a local webserver. Can be shared as a compressed archive file such as zip.
2. Web archive file e.g. warc/wacz. Can be tested using tools such as replayweb.page. Can be shared as a wacz file.
3. Web archive mirror of folder/file structure. Cannot be used for initial testing, but can be created from the results of #1 or 2 above. Once this itself has been tested, it can serve as a long-term archive.

TODO detail the above
