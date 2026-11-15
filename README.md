# EARTH Beat
 
Hear pictures of the Earth. Earth Beat plays satellite-style data as music you can turn by hand. It is built first for blind and low-vision listeners, and it works for everyone else too.
 
Made for the NASA Space Apps Challenge 2026. NASA does not endorse this project.
 
## Run it
 
Earth Beat is a single file, `Earth_Beat.html`. Open it in a modern browser. There is nothing to install and no account.
 
The page loads two fonts (Bebas Neue and Barlow) from Google Fonts. Without internet access it falls back to plain system fonts and everything else still works.
 
## How to use it
 
1. Pick a layer from the tabs at the top left.
2. Press **Play** to start the music. The globe turns slowly on its own.
3. Drag the globe, or use the arrow keys (Page Up and Page Down turn it further), to choose what you hear.
4. On **Night Lights** and **CO₂**, use the year control at the bottom to move through time.
5. Press **Export Audio** to record 30 seconds of the current layer and download it. Press again to stop early.
6. Press **Info** for a short guide inside the app.
## How it works
 
- **Latitude rings.** Eleven yellow rings mark latitude bands from 78°N to 46°S. The part of each band facing you sets its note.
- **Data becomes sound.** More signal sounds stronger. Change over time sounds like rising and falling notes.
- **One steady song.** The music runs at 96 bpm in D minor over the chords Dm, B♭, F and C, so every layer sounds like part of the same piece.
- **Beating Earth.** A small globe in the top-left corner pulses on every beat, harder on the first beat of each bar, and glows in the current layer's color.
## The layers
 
| Layer | Sound | Styled after |
| --- | --- | --- |
| Lightning | Clicks, denser where there are more flashes | ISS Lightning Imaging Sensor (SVS 5011) |
| Night Lights | Rising bright notes for growth, falling low notes for fading | NASA Black Marble, 2012 to 2023 (SVS 5313) |
| Ocean | Warmer water sounds stronger | Sea surface temperature (SVS 3912) |
| Currents | Long, sustained notes that follow the flow | Boundary currents (SVS 3912, 5425) |
| Aerosols | A dark drone | GEOS aerosols (SVS 5669) |
| CO₂ | A low pulse that rises with the yearly level | GEOS CO₂ (SVS 5196) and NOAA yearly means |
| Forests | Short, high plucks | GEDI canopy height (SVS 4950) |
| Moisture | Long, sustained notes along an atmospheric river | Atmospheric river (SVS 4960) |
| Warming | One note per year, 1880 to 2015 | NASA GISS GISTEMP |
 
## What is real and what is re-created
 
- **Real NASA numbers:** the **Warming** layer plays 136 yearly values of the NASA GISS global land-ocean temperature anomaly (GISTEMP), measured against the 1951 to 1980 average. Cooler years sound lower and warmer years higher. The values came from a published copy of an older release, so the series ends in 2015.
- **NOAA numbers:** the **CO₂** pulse follows NOAA's global yearly mean, 394 ppm in 2012 to 421 ppm in 2023.
- **Re-created layers:** the other eight layers use simplified, hand-placed data styled after NASA visualizations. They are not NASA imagery or measurements.
## Accessibility
 
- Arrow keys turn the globe, so a mouse is never required.
- A live text readout names the layer, the direction faced and the strongest latitude, for screen readers.
- Audio export saves 30 seconds of any layer.
- The beating Earth calms down for people who prefer reduced motion.
## Limitations
 
- Only Warming uses real NASA values, and it ends in 2015.
- Lightning covers only about 38° north and south, and forest height only about 52° north and south, matching the sensors the layers imitate.
- Audio export depends on the browser's recording support.
## Next steps
 
1. Replace the hand-placed layers with NASA gridded data, one layer at a time.
2. Extend Warming to the latest GISTEMP year.
3. Test the sounds with blind and low-vision listeners and tune them from their feedback.
## Credits
 
Data sources: NASA GISS GISTEMP, NOAA yearly CO₂ means, and the NASA Scientific Visualization Studio layers named above. Every number the app uses is listed in the appendix below.
 
---
 
# Data used in the app
 
Every number the app draws or plays is listed here, so the project can be checked and rebuilt. Longitudes are written as °E or °W and latitudes as °N or °S. A **weight** is a relative strength from 0 to 1 (a few go above 1 for the densest places).
 
## 1. How the synthetic points are generated
 
The eight re-created layers are made of points placed around the locations below. Each location is scattered into many points with a fixed random generator, so the picture is the same every time the page loads.
 
- Random generator: Lehmer, `seed = seed * 16807 mod 2147483647`, starting at seed **7**.
- A "spread" is a Gaussian-like scatter (the sum of three random numbers, scaled) around the listed place, in degrees.
- Each point keeps a weight (strength). Sound strength for a latitude ring is the sum of the weights of points within **±14° of longitude** facing you and **±5° of latitude** of the ring, multiplied by the layer's sensitivity.
## 2. Latitude rings and notes
 
| Ring | Latitude | Pentatonic offset (semitones) |
| --- | --- | --- |
| 1 | 46°S | 0 |
| 2 | 34°S | 2 |
| 3 | 18°S | 4 |
| 4 | 0°N | 7 |
| 5 | 12°N | 9 |
| 6 | 24°N | 12 |
| 7 | 36°N | 14 |
| 8 | 50°N | 16 |
| 9 | 62°N | 19 |
| 10 | 70°N | 21 |
| 11 | 78°N | 24 |
 
Ring notes in the tuned music use the D natural minor scale (offsets 0, 2, 3, 5, 7, 8, 10 semitones above D3 = 146.83 Hz), climbing an octave every 7 rings.
 
## 3. Real NASA data: global temperature (Warming layer)
 
NASA GISS GISTEMP, global annual land-ocean temperature anomaly in °C against the 1951 to 1980 average, 1880 to 2015 (136 values, older release as published in a public copy).
 
| Year | °C | Year | °C | Year | °C | Year | °C |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1880 | -0.20 | 1881 | -0.11 | 1882 | -0.09 | 1883 | -0.20 |
| 1884 | -0.27 | 1885 | -0.31 | 1886 | -0.30 | 1887 | -0.32 |
| 1888 | -0.19 | 1889 | -0.11 | 1890 | -0.36 | 1891 | -0.24 |
| 1892 | -0.26 | 1893 | -0.29 | 1894 | -0.30 | 1895 | -0.21 |
| 1896 | -0.14 | 1897 | -0.11 | 1898 | -0.28 | 1899 | -0.16 |
| 1900 | -0.09 | 1901 | -0.14 | 1902 | -0.28 | 1903 | -0.36 |
| 1904 | -0.44 | 1905 | -0.28 | 1906 | -0.22 | 1907 | -0.40 |
| 1908 | -0.43 | 1909 | -0.47 | 1910 | -0.43 | 1911 | -0.45 |
| 1912 | -0.35 | 1913 | -0.34 | 1914 | -0.16 | 1915 | -0.10 |
| 1916 | -0.33 | 1917 | -0.40 | 1918 | -0.25 | 1919 | -0.22 |
| 1920 | -0.26 | 1921 | -0.21 | 1922 | -0.27 | 1923 | -0.24 |
| 1924 | -0.28 | 1925 | -0.20 | 1926 | -0.09 | 1927 | -0.20 |
| 1928 | -0.21 | 1929 | -0.36 | 1930 | -0.14 | 1931 | -0.09 |
| 1932 | -0.17 | 1933 | -0.28 | 1934 | -0.14 | 1935 | -0.19 |
| 1936 | -0.15 | 1937 | -0.02 | 1938 | -0.03 | 1939 | -0.03 |
| 1940 | 0.08 | 1941 | 0.12 | 1942 | 0.10 | 1943 | 0.14 |
| 1944 | 0.26 | 1945 | 0.12 | 1946 | -0.03 | 1947 | -0.04 |
| 1948 | -0.09 | 1949 | -0.09 | 1950 | -0.18 | 1951 | -0.07 |
| 1952 | 0.01 | 1953 | 0.08 | 1954 | -0.12 | 1955 | -0.14 |
| 1956 | -0.19 | 1957 | 0.04 | 1958 | 0.06 | 1959 | 0.03 |
| 1960 | -0.03 | 1961 | 0.05 | 1962 | 0.02 | 1963 | 0.06 |
| 1964 | -0.21 | 1965 | -0.10 | 1966 | -0.05 | 1967 | -0.02 |
| 1968 | -0.07 | 1969 | 0.06 | 1970 | 0.03 | 1971 | -0.09 |
| 1972 | 0.01 | 1973 | 0.15 | 1974 | -0.08 | 1975 | -0.01 |
| 1976 | -0.11 | 1977 | 0.18 | 1978 | 0.07 | 1979 | 0.17 |
| 1980 | 0.27 | 1981 | 0.33 | 1982 | 0.13 | 1983 | 0.31 |
| 1984 | 0.16 | 1985 | 0.12 | 1986 | 0.19 | 1987 | 0.33 |
| 1988 | 0.40 | 1989 | 0.29 | 1990 | 0.43 | 1991 | 0.42 |
| 1992 | 0.23 | 1993 | 0.24 | 1994 | 0.31 | 1995 | 0.45 |
| 1996 | 0.34 | 1997 | 0.47 | 1998 | 0.63 | 1999 | 0.41 |
| 2000 | 0.42 | 2001 | 0.54 | 2002 | 0.62 | 2003 | 0.61 |
| 2004 | 0.54 | 2005 | 0.68 | 2006 | 0.63 | 2007 | 0.65 |
| 2008 | 0.53 | 2009 | 0.64 | 2010 | 0.71 | 2011 | 0.59 |
| 2012 | 0.62 | 2013 | 0.65 | 2014 | 0.74 | 2015 | 0.86 |
 
How it is played: one note per year, one year per eighth note (about 0.31 s). The note is chosen as `round((anomaly + 0.5) / 1.4 × 14)`, limited to 0 to 14, on the D minor scale. Every 4th year a bass note follows the centred five-year average, an octave lower. Years warmer than +0.30 °C add a quiet high note one octave higher (7 scale steps up) on every 2nd year. All 136 years loop in about 42.5 seconds.
 
## 4. Real NOAA data: carbon dioxide level (CO₂ layer)
 
Global yearly mean CO₂ in parts per million, used for the year control and the pitch of the CO₂ pulse.
 
| Year | ppm |
| --- | --- |
| 2012 | 394.06 |
| 2013 | 396.74 |
| 2014 | 398.81 |
| 2015 | 401.01 |
| 2016 | 404.41 |
| 2017 | 406.76 |
| 2018 | 408.72 |
| 2019 | 411.65 |
| 2020 | 414.21 |
| 2021 | 416.41 |
| 2022 | 418.53 |
| 2023 | 421.08 |
 
The CO₂ sound rises with `(ppm − 394.06) / (421.08 − 394.06)`, and every CO₂ point is made up to 60 % stronger across that range.
 
## 5. Land outlines
 
Simplified continent and island outlines, as longitude, latitude vertices. They draw the globe's land, the mini map, and decide which random points fall on land.
 
**1. North America** (32 vertices)
 
`(-168,66) (-156,71) (-125,70) (-95,72) (-80,68) (-62,58) (-56,50) (-67,45) (-76,38) (-81,31) (-80,25) (-84,30) (-90,29) (-97,26) (-98,19) (-92,18) (-87,21) (-83,15) (-78,8) (-80,8) (-86,11) (-92,14) (-105,20) (-110,24) (-115,30) (-118,34) (-124,41) (-124,48) (-135,58) (-150,60) (-165,55) (-158,58)`
 
**2. South America** (14 vertices)
 
`(-78,8) (-72,12) (-62,10) (-50,0) (-35,-6) (-40,-22) (-48,-26) (-58,-38) (-65,-42) (-68,-52) (-74,-50) (-72,-35) (-71,-18) (-81,-5)`
 
**3. Europe and Asia** (39 vertices)
 
`(-10,36) (-9,43) (-2,48) (5,53) (10,57) (18,60) (28,70) (60,69) (100,77) (140,72) (180,68) (170,60) (160,55) (142,52) (135,44) (128,39) (122,40) (121,31) (110,20) (106,10) (100,13) (103,1) (98,8) (92,22) (80,15) (77,8) (72,20) (67,25) (57,25) (50,30) (56,18) (44,12) (35,28) (35,33) (27,37) (22,37) (12,44) (8,44) (0,38)`
 
**4. Africa** (15 vertices)
 
`(-17,21) (-10,30) (10,37) (32,31) (43,12) (51,12) (40,-3) (40,-15) (33,-26) (20,-35) (14,-22) (12,-5) (9,4) (-8,4) (-17,14)`
 
**5. Australia** (10 vertices)
 
`(114,-22) (122,-18) (136,-12) (142,-11) (146,-19) (153,-27) (150,-37) (140,-38) (130,-32) (115,-34)`
 
**6. Greenland** (6 vertices)
 
`(-55,60) (-45,60) (-22,70) (-20,82) (-60,82) (-70,77)`
 
**7. Japan (Honshu area)** (5 vertices)
 
`(130,31) (140,35) (142,40) (141,45) (138,38)`
 
**8. Borneo** (12 vertices)
 
`(109,1.5) (109.5,-1) (110,-3) (114,-4) (116,-3.5) (116.5,-1) (117.5,1) (119,5) (117,7) (115,5) (113,3) (111,2)`
 
**9. Sumatra** (8 vertices)
 
`(95,5.5) (98,4) (104,-1) (106,-5.5) (104,-5.5) (101,-3) (98,0) (95.5,3)`
 
**10. Java** (4 vertices)
 
`(105.5,-6) (114,-7.5) (114.5,-8.5) (106,-7.5)`
 
**11. New Guinea** (7 vertices)
 
`(131,-1) (138,-1.5) (145,-4) (150,-10) (142,-9) (138,-8) (134,-3.5)`
 
**12. Madagascar** (6 vertices)
 
`(49,-12) (50.5,-15.5) (47,-25) (44,-24.5) (43.5,-17) (44.5,-16)`
 
**13. Great Britain** (8 vertices)
 
`(-5.5,50) (1.5,51) (1.5,53) (-2,57.5) (-5,58.5) (-6,56) (-3.5,54.5) (-4.5,52)`
 
**14. Ireland** (4 vertices)
 
`(-10,52) (-6,52) (-6,55) (-8,55)`
 
**15. New Zealand (North Island)** (4 vertices)
 
`(173,-35) (178,-38) (175,-41.5) (174,-39)`
 
**16. New Zealand (South Island)** (5 vertices)
 
`(172.5,-40.5) (174,-41.5) (171,-44.5) (167,-46.5) (166.5,-45.5)`
 
**17. Sri Lanka** (4 vertices)
 
`(80,9.5) (82,7.5) (81,6) (79.8,7)`
 
**18. Iceland** (4 vertices)
 
`(-24,65) (-14,66) (-14,64.3) (-22,63.4)`
 
## 6. Lightning layer
 
Hotspots styled after the ISS Lightning Imaging Sensor. 70 points per hotspot, spread 7° of longitude and 5° of latitude. Points beyond 38° north or south are dropped. Sensitivity 0.5.
 
| Hotspot | Location | Weight |
| --- | --- | --- |
| Congo basin | 25°E, 2°S | 1 |
| Lake Maracaibo | 71°W, 9°N | 1 |
| Himalayan foothills | 90°E, 25°N | 0.9 |
| Maritime Continent | 115°E, 0°N | 0.8 |
| Amazon | 62°W, 5°S | 0.6 |
| Florida | 82°W, 28°N | 0.7 |
| Argentina | 60°W, 30°S | 0.7 |
| Northern Australia | 132°E, 14°S | 0.6 |
| Mexico | 100°W, 22°N | 0.5 |
| US Gulf coast | 90°W, 32°N | 0.5 |
| Pakistan | 72°E, 31°N | 0.4 |
| Sahel | 0°E, 10°N | 0.5 |
| South African highveld | 28°E, 26°S | 0.5 |
 
Sound: noise clicks as hi-hats on busy rings, with a short square-wave note on the strongest ring.
 
## 7. Night lights layer
 
### 7a. City clusters
 
50 points per cluster, spread 2.5° by 2°. Each point gets a brightness of cluster weight × (0.4 to 1.0) and a change value (section 7d).
 
| Cluster | Weight |
| --- | --- |
| 74°W, 41°N | 1 |
| 88°W, 42°N | 0.8 |
| 118°W, 34°N | 0.9 |
| 99°W, 19°N | 0.8 |
| 46°W, 23°S | 0.9 |
| 0°E, 51°N | 0.8 |
| 2°E, 49°N | 0.8 |
| 31°E, 30°N | 0.7 |
| 3°E, 6°N | 0.6 |
| 77°E, 28°N | 0.9 |
| 73°E, 19°N | 0.9 |
| 116°E, 40°N | 1 |
| 121°E, 31°N | 1 |
| 139°E, 36°N | 1 |
| 127°E, 37°N | 0.9 |
| 107°E, 6°S | 0.8 |
| 37°E, 56°N | 0.7 |
| 151°E, 34°S | 0.6 |
| 28°E, 26°S | 0.6 |
| 29°E, 41°N | 0.7 |
| 104°E, 30°N | 0.8 |
| 113°E, 23°N | 0.9 |
| 90°E, 23°N | 0.7 |
| 80°W, 26°N | 0.6 |
| 122°W, 37°N | 0.7 |
 
### 7b. Regional glow bands
 
Random points inside each box, kept only if they fall on land. Brightness 0.06 to 0.36.
 
| Longitude | Latitude | Candidate points |
| --- | --- | --- |
| 10°W to 40°E | 36°N to 58°N | 320 |
| 90°W to 70°W | 32°N to 45°N | 160 |
| 70°E to 88°E | 10°N to 30°N | 160 |
| 104°E to 122°E | 23°N to 40°N | 200 |
| 130°E to 141°E | 32°N to 42°N | 80 |
| 5°W to 10°E | 4°N to 10°N | 50 |
| 28°E to 50°E | 26°N to 38°N | 80 |
 
### 7c. Nile valley line
 
130 points along this line, each 0.5 to 1.0 bright, change value +0.4: (31.2,30.2) → (31.2,27) → (32,25.5) → (32.7,24) → (32.9,22).
 
### 7d. Change since 2012
 
Each light gets a change value from its position, plus a random ±0.15. The first four areas are checked in order, then the remaining rows override where they apply. Positive grows (purple), negative fades (orange).
 
| Area (approximate) | Longitude | Latitude | Change |
| --- | --- | --- | --- |
| South and East Asia | 65°E to 125°E | 5°N to 42°N | +0.9 |
| Africa | 20°W to 52°E | 35°S to 15°N | +0.8 |
| Middle East | 34°E to 60°E | 15°N to 35°N | +0.4 |
| Northern South America | 85°W to 35°W | south of 12°N | +0.4 |
| US west coast | 125°W to 115°W | 32°N to 48°N | +0.2 |
| US east coast | 84°W to 70°W | 30°N to 45°N | −0.2 |
| Western Europe | 10°W to 15°E | 41°N to 56°N | −0.22 |
| Venezuela region | 73°W to 60°W | 1°N to 12°N | −0.5 |
| Ukraine region | 24°E to 40°E | 44°N to 52°N | −0.7 |
| Syria region | 36°E to 42°E | 32°N to 37°N | −0.7 |
| Yemen region | 42°E to 48°E | 12°N to 17°N | −0.6 |
 
The change grows linearly with the year: a light's strength in year Y is `weight × (1 + 1.2 × change × (Y − 2012) / 11)`. Lights with change above +0.5 draw purple, below −0.25 draw orange, the rest white. Rising and falling notes are played in proportion to growth and fading in each ring.
 
### 7e. Population map that shades the globe
 
The glowing night-side lights on the globe are painted from a 256 × 128 grid. Each cell adds a Gaussian bump (default sigma 1.6°) for every place below: `weight × exp(−distance² / (2 σ²))`, with longitude distance scaled by cos(latitude). Lights are drawn only on land between 60°S and 72°N, leaving out Greenland and the far north of Canada (75°W to 12°W, north of 58°N). Coasts glow 1.8× brighter.
 
| Place | Weight | Sigma (°) |
| --- | --- | --- |
| 0°E, 51.5°N | 1 | 1.6 |
| 2.3°E, 48.9°N | 1 | 1.6 |
| 3.7°W, 40.4°N | 0.8 | 1.6 |
| 2.2°E, 41.4°N | 0.7 | 1.6 |
| 9.1°W, 38.7°N | 0.6 | 1.6 |
| 12.5°E, 41.9°N | 0.8 | 1.6 |
| 9.2°E, 45.5°N | 0.9 | 1.6 |
| 13.4°E, 52.5°N | 0.8 | 1.6 |
| 7°E, 51.4°N | 1 | 1.6 |
| 4.9°E, 52.4°N | 0.9 | 1.6 |
| 4.4°E, 50.8°N | 0.8 | 1.6 |
| 16.4°E, 48.2°N | 0.6 | 1.6 |
| 21°E, 52.2°N | 0.7 | 1.6 |
| 14.4°E, 50.1°N | 0.5 | 1.6 |
| 19°E, 47.5°N | 0.6 | 1.6 |
| 23.7°E, 38°N | 0.6 | 1.6 |
| 29°E, 41°N | 1 | 1.6 |
| 32.9°E, 39.9°N | 0.6 | 1.6 |
| 37.6°E, 55.8°N | 1 | 1.6 |
| 30.3°E, 59.9°N | 0.7 | 1.6 |
| 30.5°E, 50.4°N | 0.6 | 1.6 |
| 26.1°E, 44.4°N | 0.5 | 1.6 |
| 31.2°E, 30°N | 1.2 | 1.6 |
| 29.9°E, 31.2°N | 0.6 | 1.6 |
| 34.8°E, 32.1°N | 0.8 | 1.6 |
| 46.7°E, 24.7°N | 0.8 | 1.6 |
| 51.4°E, 35.7°N | 0.9 | 1.6 |
| 44.4°E, 33.3°N | 0.7 | 1.6 |
| 55.3°E, 25.2°N | 0.8 | 1.6 |
| 3.4°E, 6.5°N | 0.9 | 1.6 |
| 3°E, 36.8°N | 0.5 | 1.6 |
| 7.6°W, 33.6°N | 0.5 | 1.6 |
| 28°E, 26.2°S | 0.8 | 1.6 |
| 36.8°E, 1.3°S | 0.5 | 1.6 |
| 77.2°E, 28.6°N | 1 | 1.6 |
| 72.9°E, 19°N | 1 | 1.6 |
| 88.4°E, 22.6°N | 0.9 | 1.6 |
| 90.4°E, 23.8°N | 1 | 1.6 |
| 67°E, 24.9°N | 0.8 | 1.6 |
| 74.3°E, 31.5°N | 0.8 | 1.6 |
| 100.5°E, 13.8°N | 0.8 | 1.6 |
| 106.8°E, 6.2°S | 0.9 | 1.6 |
| 121°E, 14.6°N | 0.8 | 1.6 |
| 116.4°E, 39.9°N | 1 | 1.6 |
| 121.5°E, 31.2°N | 1 | 1.6 |
| 113.3°E, 23.1°N | 1 | 1.6 |
| 127°E, 37.5°N | 1 | 1.6 |
| 139.7°E, 35.7°N | 1.2 | 1.6 |
| 135.5°E, 34.7°N | 0.9 | 1.6 |
| 151.2°E, 33.9°S | 0.6 | 1.6 |
| 74°W, 40.7°N | 1.2 | 1.6 |
| 77°W, 39°N | 0.8 | 1.6 |
| 87.6°W, 41.9°N | 0.9 | 1.6 |
| 118.2°W, 34°N | 1 | 1.6 |
| 122.4°W, 37.8°N | 0.6 | 1.6 |
| 97°W, 32.8°N | 0.6 | 1.6 |
| 95.4°W, 29.8°N | 0.6 | 1.6 |
| 84.4°W, 33.7°N | 0.6 | 1.6 |
| 80.2°W, 25.8°N | 0.6 | 1.6 |
| 99.1°W, 19.4°N | 1 | 1.6 |
| 46.6°W, 23.5°S | 1 | 1.6 |
| 43.2°W, 22.9°S | 0.8 | 1.6 |
| 58.4°W, 34.6°S | 0.8 | 1.6 |
| 74°W, 4.7°N | 0.6 | 1.6 |
| 77°W, 12°S | 0.6 | 1.6 |
 
Extra entries: broad glows at 10°E 48°N (weight 0.5, sigma 14°), 80°W 38°N (0.35, 9°), 78°E 23°N (0.35, 9°) and 113°E 32°N (0.4, 9°). A Nile line of 14 more points (weight 0.55, sigma 0.45°) runs from 30°N down the valley at 31.2°E (first 4), 31.5°E (next 4) and 32.4°E (last 6), every 0.6° of latitude.
 
## 8. Ocean layer
 
One point every 5° of longitude and latitude from 65°S to 65°N, kept only over water, with a ±0.03 random wobble. Sensitivity 0.2. Strength is a stylised annual-mean sea surface temperature:
 
- Base: `cos(latitude)^1.6`
- +0.06 for the western Pacific warm pool (100°E to 175°E, within 12° of the equator)
- −0.10 for the eastern Pacific cold tongue (150°W to 85°W, within 6° of the equator)
- −0.12 off Peru and Chile (85°W to 70°W, 5°S to 35°S)
- −0.10 off south-west Africa (0° to 15°E, 15°S to 35°S)
- +0.08 for the Gulf Stream region (82°W to 55°W, 25°N to 42°N)
- +0.06 for the Kuroshio region (125°E to 145°E, 22°N to 36°N)
- Limited to between 0.05 and 1.
## 9. Currents layer
 
Sensitivity 0.4. Points are laid along each path, 14 per segment, jittered by 1°.
 
- **Gulf Stream:** (-80,26) → (-79,30) → (-75.5,35) → (-70,38) → (-60,40) → (-50,43) → (-40,47)
- **Kuroshio:** (123,22) → (128,27) → (131,31) → (137,33.5) → (141,35.5) → (150,36) → (160,36)
- **Agulhas:** (34,-24) → (32.5,-28) → (30,-31.5) → (26,-34) → (21,-36.5) → (19,-38.5)
- **Brazil Current:** (-37,-12) → (-38,-18) → (-41,-23) → (-46,-28) → (-50,-33) → (-53.5,-37)
- **East Australian Current:** (150,-18) → (153,-25) → (154,-30) → (154.5,-33) → (157,-37) → (160,-40)
## 10. Aerosols layer
 
45 points per source, scattered by the spreads below. Types: 0 sea salt (blue), 1 dust (magenta), 2 smoke (orange), 3 sulfate (green). Sensitivity 0.3.
 
| Source | Weight | Type | Spread lon (°) | Spread lat (°) |
| --- | --- | --- | --- | --- |
| 10°E, 20°N | 1 | 1 dust | 8 | 5 |
| 30°W, 16°N | 0.8 | 1 dust | 10 | 3 |
| 65°W, 17°N | 0.5 | 1 dust | 6 | 3 |
| 66°W, 22°N | 0.8 | 0 sea salt | 5 | 3 |
| 120°W, 52°S | 0.5 | 0 sea salt | 25 | 4 |
| 0°E, 52°S | 0.5 | 0 sea salt | 25 | 4 |
| 120°E, 52°S | 0.5 | 0 sea salt | 25 | 4 |
| 40°W, 52°N | 0.4 | 0 sea salt | 20 | 4 |
| 170°E, 50°N | 0.4 | 0 sea salt | 20 | 4 |
| 20°E, 13°S | 0.9 | 2 smoke | 8 | 5 |
| 5°E, 12°S | 0.6 | 2 smoke | 8 | 4 |
| 6°W, 40°N | 0.7 | 2 smoke | 3 | 2 |
| 55°W, 10°S | 0.5 | 2 smoke | 8 | 5 |
| 120°W, 55°N | 0.4 | 2 smoke | 8 | 4 |
| 100°E, 60°N | 0.4 | 2 smoke | 8 | 4 |
| 157°W, 19.5°N | 0.6 | 3 sulfate | 5 | 1 |
| 15°E, 37.7°N | 0.7 | 3 sulfate | 6 | 1.5 |
| 22°E, 37°N | 0.4 | 3 sulfate | 5 | 1 |
| 115°E, 32°N | 0.6 | 3 sulfate | 6 | 4 |
| 80°E, 25°N | 0.6 | 3 sulfate | 6 | 4 |
 
## 11. CO₂ layer
 
Sensitivity 0.25. Industrial and fire sources, 50 points each, spread 6° by 4°:
 
| Source | Weight |
| --- | --- |
| 116°E, 36°N | 1 |
| 78°E, 24°N | 0.9 |
| 10°E, 50°N | 0.6 |
| 80°W, 39°N | 0.9 |
| 135°E, 36°N | 0.4 |
| 74°W, 41°N | 0.8 |
| 116.4°E, 40°N | 0.9 |
| 15°E, 8°N | 0.6 |
| 28°E, 4°N | 0.5 |
| 67°W, 6°N | 0.5 |
| 62°W, 9°S | 0.4 |
 
Plus a background grid: one point every 8° of longitude and 6° of latitude from 60°S to 70°N, weight 0.3 in the northern hemisphere and 0.12 in the southern.
 
## 12. Forests layer
 
Sensitivity 0.25. 70 points per area, spread 7° by 5°. Points are kept only on land and within 51.6° of the equator, because the GEDI instrument sees no further.
 
| Area | Weight |
| --- | --- |
| 62°W, 4°S | 0.75 |
| 52°W, 3°S | 0.7 |
| 22°E, 0°N | 0.75 |
| 12°E, 1°S | 0.75 |
| 114°E, 1.5°N | 0.9 |
| 102°E, 1°S | 0.7 |
| 140°E, 5°S | 0.7 |
| 123°W, 45°N | 1 |
| 80°W, 37°N | 0.4 |
| 72°W, 38°S | 0.6 |
| 147°E, 36.5°S | 0.8 |
| 15°E, 48°N | 0.3 |
 
## 13. Moisture layer
 
Sensitivity 0.4. Atmospheric river tracks, 18 points per segment, jittered by 1.5°.
 
- **Pacific river to the US west coast:** (-160,20) → (-150,28) → (-140,35) → (-130,40) → (-123,40)
- **North Atlantic river toward western Europe:** (-60,30) → (-40,40) → (-20,48) → (-5,52)
- **South-west Pacific river toward New Zealand:** (150,-25) → (160,-35) → (175,-42)
## 14. Sound design
 
- **Tempo and key:** 96 bpm, D natural minor, eighth-note steps of 0.3125 s.
- **Chord loop (one chord per bar of 8 steps):** Dm (root D, minor), B♭ (root offset 8, major), F (offset 3, major), C (offset 10, major). Pads are triangle waves with a low-pass filter at 1200 Hz; a sine bass plays the root an octave down every 4 steps.
- **Effects:** a short noise-burst reverb (2.2 s) and a compressor on the master output; master volume 0.5.
| Layer | Colour (RGB) | Sensitivity | Voice |
| --- | --- | --- | --- |
| Lightning | 255, 214, 10 | 0.5 | Noise clicks, hi-hats, square accent |
| Night Lights | 255, 214, 10 (purple for growth, orange for fading) | 0.5 (0.35 for change) | Triangle up-notes, sine down-notes |
| Ocean | 255, 214, 10 | 0.2 | Sine, 1 s |
| Currents | 110, 200, 255 | 0.4 | Sine, octave down, 1.2 s notes |
| Aerosols | 255, 150, 60 (types: 90,160,255 / 255,110,200 / 255,150,60 / 110,220,120) | 0.3 | Sawtooth, octave down, 1.6 s notes, low-pass 900 Hz |
| CO₂ | 255, 90, 90 | 0.25 | Square, octave down, 1.4 s notes, pitch rises up to 6 % with ppm |
| Forests | 120, 230, 120 | 0.25 | Sine, octave up, 0.3 s pluck |
| Moisture | 170, 170, 255 | 0.4 | Sine, 1.2 s notes |
| Warming | 255, 140, 60 | n/a | Triangle melody, sine bass, sine shimmer |
 
## 15. Display constants
 
- Globe tilt starts at 28° and can be dragged between −10° and 50°; starting rotation 20°E; the year control runs 2012 to 2023 (auto-play advances 0.5 years per second).
- Night Lights zooms the globe to 1.9× its normal size.
- The beating Earth is drawn at 96 × 96 pixels with a fixed 20° tilt and turns with the main globe.
- Mini map: 550 × 155 pixels, longitude and latitude plotted linearly.
- Stars: 180 fixed positions from the same random generator.
 
