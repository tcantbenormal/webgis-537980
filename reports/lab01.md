

<!-- Start of picture text -->
3~ OF Reto<br>ae ly ><br>: a<br>e<br>Ray)<br>sa<br>rex’<br><!-- End of picture text -->

**Web GIS Lab 01: Your First Web Map** 

**Name:** Muhammad Taimoor Ashfaq Malik **Reg No:** 537980 **Course:** Web GIS **Instructor:** Dr. Shahid Nawaz Khan 

# **Part 1: Set Up Your Tools** 

Git, Python and the project folder were verified from PowerShell. The local web server was started from the project folder and answered HTTP/1.0 200 OK for index.html. 

git --version                          # git version 2.55.0.windows.5 



<!-- Start of picture text -->
BE Windows PowerShell x PP - oo xX<br>PS C:\Users\hp> git<br>git version 2.55.0.windows.5<br><!-- End of picture text -->

git config --global core.autocrlf      # false 



<!-- Start of picture text -->
BE Windows PowerShell x + » - ag x<br>PS C:\Users\hp> git<br>git version 2.55.0.windows.5<br>PS C:\Users\hp> git config core.autocrlf<br>False<br>PS C:\Users\hp><br><!-- End of picture text -->

git config --global user.name          # (already set) git config --global user.email         # (already set, same as GitHub account) 



<!-- Start of picture text -->
BB Windows Powershell x + © - ag x<br>PS C:\Users\hp> git<br>git version 2.55.0.windows.5<br>PS C:\Users\hp> git config core.autocrlf<br>false<br>PS C:\Users\hp> git config user. nam<br>tcantbenornal<br>PS C:\Users\hp> git config user. email<br>mnalik.ms25igis@student .nust .edu. pk<br>PS C:\Users\hp><br><!-- End of picture text -->

## **Checkpoint 1** 

I used Antigravity IDE for the lab which is based on VS Code itself. 



<!-- Start of picture text -->
Islamabad ©0279 pig Bdatwcte Nomen - SL @<br>bi GIS, NUS' wedons + nip *<br>ba<br>\ Bm Picewes Cover<br>= ice bueCOssSHBOre er aom ws<br><!-- End of picture text -->

_Figure 2. Checkpoint 1: project folder_ 

# **Part 2: Your First Web Page** 

index.html was created with the lines from the handout: 

<!DOCTYPE html> <html lang="en"> <head> <meta charset="utf-8"> <title>My First Web GIS</title> </head> <body> <h1>Islamabad</h1> <p>My first web page for the Web GIS course at IGIS, NUST.</p> </body> </html> 

The page was opened at http://127.0.0.1:3001/index.html. Developer Tools were opened with F12. 

## **Checkpoint 2** 

Elements tab showing the HTML as the browser parsed it, with the address bar showing 127.0.0.1. 



<!-- Start of picture text -->
€ > 6 @ M Owon esvon e:<br>IR CB _tlements Console Sources Network > @1 Many @@ i x<br>Islamabad eee ee ee<br>[atone inust, *Siienenn<br>Sofer Computed Luynt Ennis DOM ests Ropers 3<br>‘> Geena |<br>OR HE 0 sean eupeecnaeu Ae eam2S<br><!-- End of picture text -->

_Figure 3. Checkpoint 2: Elements tab_ 

The Network tab after a reload shows exactly **one request** , for index.html. The other one is of the live preview from antigravity (it shows vscode since the IDE is based on VS Code and so does the livepreview extension) 



<!-- Start of picture text -->
€ > 6 @ M Oowom esvon e:<br>TR LB Blements Console Sources _Network_ >> Many<br>Islamabad ©D 1A Creepin Gounwace nome ~ SLL@ GB i Ox<br>My Fst wb pgs for WIS couse a GI, UST. sO) 1) fy) tS)<br>OR HE 0 sean eupeecneu Ae eam2<br><!-- End of picture text -->

_Figure 5. Network tab, one request_ 

# **Part 3: Styling with CSS** 

A <style> block was added inside <head>, and the body was replaced with a heading, a subtitle paragraph with class="subtitle", and an empty <div id="map"></div>. 

body      { font-family: system-ui, sans-serif; margin: 0; padding: 24px; background: #f4f6f8; color: #13293d; } h1        { margin: 0 0 4px; color: #0b2545; } .subtitle { color: #5a6b7b; margin-top: 0; } #map      { height: 480px; width: 100%; border-radius: 8px; } 

After saving, the styled heading and subtitle appear and nothing else. The div is there, 480 px tall, empty and invisible, which is correct at this stage. 



<!-- Start of picture text -->
Islamabad preiienenvCeren<br>OF ce beecneéa a6 omAone<br><!-- End of picture text -->

_Figure 6. Styled page with empty map div_ 

## **Checkpoint 3** 

The map div selected in the Elements panel. The Styles pane shows the #map rule with height: 580px, width: 100% and border-radius: 8px. 



<!-- Start of picture text -->
TS SSE<br>Islamabad “hen Tonge<br>OF ce bepecnea a © 90mmnone<br><!-- End of picture text -->

_Figure 7. Checkpoint 3: map div selected_ 

# **Part 4: Add the Map** 

Leaflet 1.9.4 was loaded from unpkg inside <head>, before the style block, and the map script was added just before </body>: 

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"> <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script> const map = L.map('map').setView([33.6844, 73.0479], 12); L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', { maxZoom: 19, attribution: '&copy; OpenStreetMap contributors' }).addTo(map); L.marker([33.6423, 72.9906]) .addTo(map) .bindPopup('NUST H-12, Islamabad') .openPopup(); 

The result is a pannable, zoomable map of Islamabad with a marker and open popup on the NUST H-12 campus. In the Elements panel the once-empty div now carries Leaflet's own classes. 



<!-- Start of picture text -->
€ © @ DM © 127001. @evo 7@:<br>Islamabad<br>\ ze eh wea Wee AR ote) ier "<br>o= Pe beecndéa a © 90 wmpone<br><!-- End of picture text -->

_Figure 8. Working map_ 

With **Disable cache** ticked and the page reloaded, the Network tab shows 18 requests (ignore websocket at 1 and livepreview script at 3) instead of one: index.html, leaflet.css, leaflet.js, marker icon images, and a set of .png map tiles from tile.openstreetmap.org, each initiated by TileLayer.js. 



<!-- Start of picture text -->
Islamabad xD LS bead EL = + ar)<br>D> rae res gies See<br>ox ice bzeGuea ee<br><!-- End of picture text -->

_Figure 9. Network tab, many requests_ 

## **Checkpoint 4** 

One tile request selected with its **Preview** tab open. The preview is a single 256 x 256 image/png square of map. 



<!-- Start of picture text -->
« Ca WM © wro00: @evo @:<br>ne ce bueoaan ne comm oe<br><!-- End of picture text -->

_Figure 10. Checkpoint 4: tile preview_ 

Dragging the map to pan it and zooming in made new tile requests arrive at the bottom of the list. 



<!-- Start of picture text -->
€ CaDM © woo: @eevo @:<br>Islamabad xd LY bed = + ar)<br>= oe emer Ba<br>a LO oc oN  OF*S y 128909 i Cs<br>\g ¥ {oOa” 2 gh ESene NK BANSz<br>ae ce bweoaan a © 90 wo yon<br><!-- End of picture text -->

_Figure 11. Panning triggers new tile requests_ 

# **Part 5: Publish It** 

## **Done: local repository and first commit** 

I utilized a much easier approach by installing GitHub Desktop and pushed my repository through the application instead of the terminal. 



<!-- Start of picture text -->
eto S80 7 OP pain ieee nao<br>ez No local changes<br>ozs wa bueoaame ne cen oes<br><!-- End of picture text -->

_Figure 12. Github  Desktop and Local Repository_ 

The report and screenshots were then committed as a second commit, Lab 01: report. 



<!-- Start of picture text -->
T “ . eB<br>oe<br>o 8<br>08<br>a<br>a<br>a<br>3&<br>E<br>c<br>ozs wa bueoaame nae caem os<br><!-- End of picture text -->

_Figure 13. Second commit: report and screenshots_ 

## **Push and GitHub Pages** 

With the repository webgis-537980 created on GitHub, the steps were: 

1. On github.com create a **public** repository webgis-537980 with no README, .gitignore or licence. 

2. Meanwhile, open Github Desktop and Push the commits to origin 



<!-- Start of picture text -->
aaa No local changes<br>eed Ba LELepecoeosaane a 299OM poms<br><!-- End of picture text -->

_Figure 14. Second Commit Pushed to Origin_ 

3. Repository **Settings > Pages > Source: Deploy from a branch > main, / (root) > Save** . Wait one to three minutes. 

4. Open https://tcantbenormal.github.io/webgis-537980/ and screenshot it for Checkpoint 5. 

## **Checkpoint 5** 

The published page at its public URL, served by GitHub Pages. The address bar shows tcantbenormal.github.io/webgis-537980/, and the map, marker and popup work exactly as they did on 127.0.0.1. 



<!-- Start of picture text -->
« SA CD % teantbenormal github ic @*#evo 7@:<br>Islamabad<br><!-- End of picture text -->

_Figure 15. Checkpoint 5: live GitHub Pages site_ 

# **Questions** 

**1. In Part 2 your page made one network request. After Part 4 it made dozens. Explain in two or three sentences what changed and why.** 

In Part 2 the page was self-contained, so the browser only had to fetch index.html. In Part 4 the page now asks for Leaflet's CSS and JavaScript from unpkg, and once Leaflet runs it requests a separate 256 x 256 PNG tile from OpenStreetMap for every tile needed to cover the visible map at zoom 12, plus the marker icon images. Each tile is its own HTTP request, so the count jumps to dozens, and panning or zooming keeps adding more. 

## **2. What is the difference between what HTML does and what CSS does? Give one example of each from your own file.** 

HTML tells _what exists_ on the page and how it is structured; CSS tells _how it looks_ . In my file, <div id="map"></div> is HTML: it declares that a map container element exists. #map { height: 480px; } is CSS: it gives that element a size, but creates nothing new. Likewise <h1>Islamabad</h1> creates the heading, and h1 { color: #0b2545; } colours it. 

## **3. Why does the `#map` rule need a height, when the `h1` rule does not?** 

An h1 contains text, and a block element's default height grows to fit its content, so the heading is as tall as its text with no help from CSS. The map div is empty, so its natural height is zero pixels. Leaflet fills 

whatever box it is given and does not enlarge it, so without an explicit height it draws the map into a 0 px tall box, the console stays clean, and nothing appears. 

## **4. You opened your page through Live Server at `127.0.0.1` instead of double-clicking the file. Give one reason this matters.** 

A page opened from file:/// has no proper web origin, so the browser's security rules block it from fetching other local files with JavaScript. Furthermore, running the page through live server allows it to run as a real web server environment and ensures that the code runs as it would on a live website without blocking the requests (as shown in console). Another reason is that live server automatically refreshes the browser every time the code is saved, which saves you from hitting refresh every time after every change. 

## **5. A classmate's marker appears in the sea near Africa instead of in Islamabad. What is almost certainly wrong, and how would you fix it?** 

The latitude and longitude are almost certainly in the wrong order. GeoJSON writes [longitude, latitude] but Leaflet's own functions take [latitude, longitude], so a point copied in GeoJSON order lands somewhere unknown. Swap the two numbers so the marker reads L.marker([33.6423, 72.9906]). (If the marker sits exactly on the equator at 0, 0 in the Gulf of Guinea, the coordinates were probably undefined or parsed as zero rather than swapped, but swapping is always the first thing to try.) 

# **Submission** 

- **Repository URL:** https://github.com/tcantbenormal/webgis-537980 

- **Live GitHub Pages URL:** https://tcantbenormal.github.io/webgis-537980/ 

