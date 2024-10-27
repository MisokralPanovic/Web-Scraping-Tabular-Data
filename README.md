```python
import requests
from bs4 import BeautifulSoup
import re
```


```python
url = "https://en.wikipedia.org/wiki/List_of_old-growth_forests"
```


```python
def get_html(url, path):
    response = requests.get(url)
    with open(path, "w", encoding = "utf-8") as f:
        f.write(response.text)
```


```python
get_html(url, path="wiki_test.html")
```


```python
with open("wiki_test.html", "r", encoding = "utf-8") as f:
    html = f.read()
```


```python
soup = BeautifulSoup(html, "html.parser")
soup.title
```




    <title>List of old-growth forests - Wikipedia</title>




```python
tables = soup.find_all("table", attrs={"class": "wikitable sortable"})
tables
```




    [<table class="wikitable sortable">
     <tbody><tr>
     <th>Country
     </th>
     <th>Area
     </th>
     <th>Old-growth extent
     </th>
     <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
     </th>
     <th>Old-growth forest type
     </th></tr>
     <tr>
     <td><a href="/wiki/Democratic_Republic_of_the_Congo" title="Democratic Republic of the Congo">Democratic Republic of the Congo</a>
     </td>
     <td><a href="/wiki/Salonga_National_Park" title="Salonga National Park">Salonga National Park</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Central_Congolian_lowland_forests" title="Central Congolian lowland forests">Central Congolian lowland forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/R%C3%A9union" title="Réunion">Réunion</a> (<a href="/wiki/France" title="France">France</a>)
     </td>
     <td>Réserve biologique intégrale du Bois des Nèfles
     </td>
     <td><span data-sort-value="7006179000000000000♠"></span>179 hectares (440 acres)
     </td>
     <td><a href="/wiki/Tropical_and_subtropical_dry_broadleaf_forests" title="Tropical and subtropical dry broadleaf forests">Tropical and subtropical dry broadleaf forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/R%C3%A9union" title="Réunion">Réunion</a> (<a href="/wiki/France" title="France">France</a>)
     </td>
     <td>Réserve biologique intégrale du Piton de la Fournaise
     </td>
     <td><span data-sort-value="7008210050000000000♠"></span>21,005 hectares (51,900 acres)
     </td>
     <td><a href="/wiki/Tropical_and_subtropical_moist_broadleaf_forests" title="Tropical and subtropical moist broadleaf forests">Tropical and subtropical moist broadleaf forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/R%C3%A9union" title="Réunion">Réunion</a> (<a href="/wiki/France" title="France">France</a>)
     </td>
     <td>Réserve biologique intégrale du Mazerin
     </td>
     <td><span data-sort-value="7007249100000000000♠"></span>2,491 hectares (6,160 acres)
     </td>
     <td><a href="/wiki/Tropical_and_subtropical_dry_broadleaf_forests" title="Tropical and subtropical dry broadleaf forests">Tropical and subtropical dry broadleaf forests</a>
     </td>
     <td><i><a href="/wiki/Pandanus" title="Pandanus">Pandanus</a></i> scrub
     </td></tr>
     <tr>
     <td><a href="/wiki/Kenya" title="Kenya">Kenya</a>
     </td>
     <td><a href="/wiki/Kakamega_Forest" title="Kakamega Forest">Kakamega Forest</a><sup class="noprint Inline-Template Template-Fact" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Citation_needed" title="Wikipedia:Citation needed"><span title="This claim needs references to reliable sources. (July 2012)">citation needed</span></a></i>]</sup>
     </td>
     <td>
     </td>
     <td>
     </td>
     <td>
     </td></tr></tbody></table>,
     <table class="wikitable sortable">
     <tbody><tr>
     <th>Country
     </th>
     <th>Area
     </th>
     <th>Old-growth extent
     </th>
     <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
     </th>
     <th>Old-growth forest type
     </th></tr>
     <tr>
     <td><a href="/wiki/Bangladesh" title="Bangladesh">Bangladesh</a> and <a href="/wiki/India" title="India">India</a>
     </td>
     <td><a href="/wiki/Sundarbans" title="Sundarbans">Sundarbans</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Sundarbans" title="Sundarbans">Sundarbans</a>
     </td>
     <td><a href="/wiki/Mangrove_forest" title="Mangrove forest">Mangrove forest</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Cambodia" title="Cambodia">Cambodia</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Prey_Lang" title="Prey Lang">Prey Lang</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Tropical_and_subtropical_dry_broadleaf_forests" title="Tropical and subtropical dry broadleaf forests">Tropical and subtropical dry broadleaf forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Georgia_(country)" title="Georgia (country)">Georgia</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Kintrishi_Protected_Landscape" title="Kintrishi Protected Landscape">Kintrishi Protected Landscape</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Euxine-Colchic_deciduous_forests" title="Euxine-Colchic deciduous forests">Euxine-Colchic deciduous forests</a>
     </td>
     <td>temperate broadleaf rainforest
     </td></tr>
     <tr>
     <td><a href="/wiki/Georgia_(country)" title="Georgia (country)">Georgia</a>
     </td>
     <td><a href="/wiki/Lagodekhi_Protected_Areas" title="Lagodekhi Protected Areas">Lagodekhi Protected Areas</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Caucasus_mixed_forests" title="Caucasus mixed forests">Caucasus mixed forests</a>
     </td>
     <td>temperate broadleaf forest
     </td></tr>
     <tr>
     <td><a href="/wiki/Georgia_(country)" title="Georgia (country)">Georgia</a>
     </td>
     <td><a href="/wiki/Mtirala_National_Park" title="Mtirala National Park">Mtirala National Park</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Euxine-Colchic_deciduous_forests" title="Euxine-Colchic deciduous forests">Euxine-Colchic deciduous forests</a>
     </td>
     <td>temperate broadleaf rainforest
     </td></tr>
     <tr>
     <td><a href="/wiki/India" title="India">India</a>
     </td>
     <td><a href="/wiki/Dudhatoli" title="Dudhatoli">Dudhatoli</a> Mountains, Uttarakhand
     </td>
     <td><span data-sort-value="7007600000000000000♠"></span>6,000 hectares (15,000 acres)
     </td>
     <td>Western Himalayan broadleaf forests and subalpine conifer forests
     </td>
     <td>temperate broadleaf mixed forests and montane forests biome
     </td></tr>
     <tr>
     <td><a href="/wiki/Indonesia" title="Indonesia">Indonesia</a>
     </td>
     <td><a href="/wiki/Leuser_Ecosystem" title="Leuser Ecosystem">Leuser Ecosystem</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Sumatran_montane_rain_forests" title="Sumatran montane rain forests">Sumatran montane rain forests</a>
     <p><a href="/wiki/Sumatran_lowland_rain_forests" title="Sumatran lowland rain forests">Sumatran lowland rain forests</a>
     </p>
     </td>
     <td><a href="/wiki/Tropical_rainforest" title="Tropical rainforest">tropical rainforest</a>
     <p><a href="/wiki/Montane_ecosystems" title="Montane ecosystems">tropical montane forest</a>
     </p>
     </td></tr>
     <tr>
     <td><a href="/wiki/Indonesia" title="Indonesia">Indonesia</a>
     </td>
     <td><a href="/wiki/Lorentz_National_Park" title="Lorentz National Park">Lorentz National Park</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/New_Guinea_mangroves" title="New Guinea mangroves">New Guinea mangroves</a><br/><a href="/wiki/Southern_New_Guinea_lowland_rain_forests" title="Southern New Guinea lowland rain forests">Southern New Guinea lowland forests</a><br/><a href="/wiki/Central_Range_montane_rain_forests" title="Central Range montane rain forests">New Guinea montane forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Indonesia" title="Indonesia">Indonesia</a>
     </td>
     <td><a href="/wiki/Mamberamo_Foja_Wildlife_Reserve" title="Mamberamo Foja Wildlife Reserve">Mamberamo Foja Wildlife Reserve</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Northern_New_Guinea_lowland_rain_and_freshwater_swamp_forests" title="Northern New Guinea lowland rain and freshwater swamp forests">Northern New Guinea lowland rain and freshwater swamp forests</a>
     <p><a href="/wiki/Northern_New_Guinea_montane_rain_forests" title="Northern New Guinea montane rain forests">Northern New Guinea montane rain forests</a>
     </p>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Iran" title="Iran">Iran</a>
     </td>
     <td>Coast along the Caspian Sea and the northern slopes of the Alborz mountains
     </td>
     <td>
     </td>
     <td>Caspian Hyrcanian mixed forest<sup class="reference" id="cite_ref-2"><a href="#cite_note-2"><span class="cite-bracket">[</span>2<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>temperate broadleaf and mixed forests biome
     </td></tr>
     <tr>
     <td><a href="/wiki/Japan" title="Japan">Japan</a>
     </td>
     <td><a href="/wiki/Shiretoko_National_Park" title="Shiretoko National Park">Shiretoko National Park</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Hokkaido_deciduous_forests" title="Hokkaido deciduous forests">Hokkaido deciduous forests</a>, <a class="mw-redirect" href="/wiki/Hokkaido_montane_conifer_forests" title="Hokkaido montane conifer forests">Hokkaido montane conifer forests</a><sup class="noprint Inline-Template Template-Fact" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Citation_needed" title="Wikipedia:Citation needed"><span title="This claim needs references to reliable sources. (March 2013)">citation needed</span></a></i>]</sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate" title="Temperate">temperate</a> and <a class="mw-redirect" href="/wiki/Subalpine" title="Subalpine">subalpine</a> <a class="mw-redirect" href="/wiki/Mixed_forest" title="Mixed forest">mixed forest</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Japan" title="Japan">Japan</a>
     </td>
     <td><a href="/wiki/Yakushima" title="Yakushima">Yakushima</a> Wilderness Area
     </td>
     <td>
     </td>
     <td><a href="/wiki/Nansei_Islands_subtropical_evergreen_forests" title="Nansei Islands subtropical evergreen forests">Nansei Islands subtropical evergreen forests</a>, <a href="/wiki/Taiheiyo_evergreen_forests" title="Taiheiyo evergreen forests">Taiheiyo evergreen forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Subtropical" title="Subtropical">subtropical</a> and <a href="/wiki/Temperate_rainforest" title="Temperate rainforest">temperate rainforest</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Japan" title="Japan">Japan</a>
     </td>
     <td><a href="/wiki/Kasuga-taisha#Kasugayama_Primeval_Forest" title="Kasuga-taisha">Kasugayama Primeval Forest</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Taiheiyo_evergreen_forests" title="Taiheiyo evergreen forests">Taiheiyo evergreen forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Malaysia" title="Malaysia">Malaysia</a>
     </td>
     <td><a href="/wiki/Belum-Temengor" title="Belum-Temengor">Belum-Temengor</a><sup class="reference" id="cite_ref-3"><a href="#cite_note-3"><span class="cite-bracket">[</span>3<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Peninsular_Malaysian_rain_forests" title="Peninsular Malaysian rain forests">Peninsular Malaysian rain forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Malaysia" title="Malaysia">Malaysia</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Danum_Valley" title="Danum Valley">Danum Valley</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Borneo_lowland_rain_forests" title="Borneo lowland rain forests">Borneo lowland rain forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Malaysia" title="Malaysia">Malaysia</a>
     </td>
     <td><a href="/wiki/Taman_Negara" title="Taman Negara">Taman Negara</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Peninsular_Malaysian_rain_forests" title="Peninsular Malaysian rain forests">Peninsular Malaysian rain forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Malaysia" title="Malaysia">Malaysia</a>
     </td>
     <td><a href="/wiki/Ulu_Muda_Forest" title="Ulu Muda Forest">Ulu Muda Forest</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Peninsular_Malaysian_rain_forests" title="Peninsular Malaysian rain forests">Peninsular Malaysian rain forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Russia" title="Russia">Russia</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Central_Sikhote-Alin" title="Central Sikhote-Alin">Central Sikhote-Alin</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Ussuri_broadleaf_and_mixed_forests" title="Ussuri broadleaf and mixed forests">Ussuri broadleaf and mixed forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Russia" title="Russia">Russia</a>
     </td>
     <td><a href="/wiki/Virgin_Komi_Forests" title="Virgin Komi Forests">Virgin Komi Forests</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Urals_montane_tundra_and_taiga" title="Urals montane tundra and taiga">Urals montane tundra and taiga</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coniferous" title="Coniferous">Coniferous</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Russia" title="Russia">Russia</a>
     </td>
     <td><a href="/wiki/Western_Caucasus" title="Western Caucasus">Western Caucasus</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Caucasus_mixed_forests" title="Caucasus mixed forests">Caucasus mixed forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Taiwan" title="Taiwan">Taiwan</a>
     </td>
     <td><a href="/wiki/Yushan_National_Park" title="Yushan National Park">Yushan National Park</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Taiwan_subtropical_evergreen_forests" title="Taiwan subtropical evergreen forests">Taiwan subtropical evergreen forests</a>
     </td>
     <td><a href="/wiki/Taiwania" title="Taiwania">Taiwania</a>
     </td></tr>
     </tbody></table>,
     <table class="wikitable sortable">
     <tbody><tr>
     <th>Country
     </th>
     <th>Area
     </th>
     <th>Old-growth extent
     </th>
     <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
     </th>
     <th class="unsortable">Old-growth forest type
     </th></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a href="/wiki/Walpole_Wilderness_Area" title="Walpole Wilderness Area">Walpole Wilderness Area</a>, <a href="/wiki/Western_Australia" title="Western Australia">Western Australia</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Jarrah-Karri_forest_and_shrublands" title="Jarrah-Karri forest and shrublands">Jarrah-Karri forest and shrublands</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Karri" title="Karri">Karri</a>, <a class="mw-redirect" href="/wiki/Jarrah" title="Jarrah">Jarrah</a>, <a href="/wiki/Eucalyptus_jacksonii" title="Eucalyptus jacksonii">Eucalyptus jacksonii</a>, <a href="/wiki/Eucalyptus_guilfoylei" title="Eucalyptus guilfoylei">Eucalyptus guilfoylei</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a href="/wiki/Barrington_Tops_National_Park" title="Barrington Tops National Park">Barrington Tops National Park</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Subtropical" title="Subtropical">subtropical</a> and <a class="mw-redirect" href="/wiki/Temperate" title="Temperate">temperate</a> <a href="/wiki/Rainforest" title="Rainforest">rainforest</a> and <a href="/wiki/Eucalypt" title="Eucalypt">eucalypt</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a href="/wiki/Greater_Blue_Mountains_Area" title="Greater Blue Mountains Area">Greater Blue Mountains Area</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>
     <td><a href="/wiki/Eucalypt" title="Eucalypt">eucalypt</a> forest
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a href="/wiki/Tarkine" title="Tarkine">Tarkine</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
     </td>
     <td>2,000 square kilometres (770 sq mi)
     </td>
     <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
     </td>
     <td><a href="/wiki/Temperate_rainforest" title="Temperate rainforest">Temperate rainforest</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Tasmanian_Wilderness" title="Tasmanian Wilderness">Tasmanian Wilderness</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
     </td>
     <td><a href="/wiki/Temperate_rainforest" title="Temperate rainforest">temperate rainforest</a> and <a href="/wiki/Eucalyptus" title="Eucalyptus">eucalypt</a> forest
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a href="/wiki/Goolengook" title="Goolengook">Goolengook</a>, <a href="/wiki/East_Gippsland" title="East Gippsland">East Gippsland</a>, <a class="mw-redirect" href="/wiki/Victoria_(Australia)" title="Victoria (Australia)">Victoria</a>
     </td>
     <td>Over 20 square kilometres (7.7 sq mi)
     </td>
     <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>
     <td>rare <a href="/wiki/Temperate_rainforest" title="Temperate rainforest">warm temperate/cool temperate</a> "Overlap Rainforest"
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Blue_Tier&amp;action=edit&amp;redlink=1" title="Blue Tier (page does not exist)">Blue Tier</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
     </td>
     <td>100 hectares (250 acres)<sup class="reference" id="cite_ref-8"><a href="#cite_note-8"><span class="cite-bracket">[</span>8<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
     </td>
     <td><a href="/wiki/Myrtaceae" title="Myrtaceae">myrtle</a> canopy, unusually diverse understorey for temperate rainforest (<a class="mw-redirect" href="/wiki/Celery_top_pine" title="Celery top pine">celery top pine</a>, <a href="/wiki/Waratah" title="Waratah">waratah</a>, <a href="/wiki/Sassafras" title="Sassafras">sassafras</a>, <a href="/wiki/Tree_fern" title="Tree fern">tree fern</a>), threatened <a class="new" href="/w/index.php?title=Simson%27s_Stag_Beetle&amp;action=edit&amp;redlink=1" title="Simson's Stag Beetle (page does not exist)">Simson's Stag Beetle</a>.
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Styx_Forest&amp;action=edit&amp;redlink=1" title="Styx Forest (page does not exist)">Styx Forest</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Weld_Forest&amp;action=edit&amp;redlink=1" title="Weld Forest (page does not exist)">Weld</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a href="/wiki/Upper_Florentine_Valley" title="Upper Florentine Valley">Upper Florentine Valley</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Badja_State_Forest&amp;action=edit&amp;redlink=1" title="Badja State Forest (page does not exist)">Badja State Forest</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-0"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>
     <td>Wet old-growth with sweeping <a class="mw-redirect" href="/wiki/Tree-fern" title="Tree-fern">tree-fern</a> understoreys. 10+ threatened species (including <a href="/wiki/Squirrel_glider" title="Squirrel glider">squirrel glider</a> and <a href="/wiki/Golden-tipped_bat" title="Golden-tipped bat">golden-tipped bat</a>)
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Dampier_State_Forest&amp;action=edit&amp;redlink=1" title="Dampier State Forest (page does not exist)">Dampier State Forest</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-1"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>
     <td>Wet old-growth. Most extensive rainforests in the South Coast.
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a href="/wiki/Wandella" title="Wandella">Wandella</a> / <a class="new" href="/w/index.php?title=Peak_Alone&amp;action=edit&amp;redlink=1" title="Peak Alone (page does not exist)">Peak Alone</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-2"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>
     <td>High old-growth and threatened species values. Important catchment value.
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Monga_State_Forest&amp;action=edit&amp;redlink=1" title="Monga State Forest (page does not exist)">Monga State Forest</a> / <a class="new" href="/w/index.php?title=Buckenbowra&amp;action=edit&amp;redlink=1" title="Buckenbowra (page does not exist)">Buckenbowra</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-3"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>
     <td>Pristine Buckenbowra River, including an area on the northern side of the river with a <a href="/wiki/Golden-tipped_bat" title="Golden-tipped bat">golden-tipped bat</a> record. Also an area around <a class="new" href="/w/index.php?title=McGregors_Creek&amp;action=edit&amp;redlink=1" title="McGregors Creek (page does not exist)">McGregors Creek</a>, nominated for wilderness, and important for old-growth and to increase the viability of the connection / link between Buckenbowra and <a href="/wiki/Deua_National_Park" title="Deua National Park">Deua National Park</a>.
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a href="/wiki/Dampier_County" title="Dampier County">Dampier</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-4"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>
     <td>Upper <a href="/wiki/Deua_River" title="Deua River">Deua River</a> (Identified Wilderness) and <a class="new" href="/w/index.php?title=Big_Belimba_Creek&amp;action=edit&amp;redlink=1" title="Big Belimba Creek (page does not exist)">Big Belimba Creek</a> catchment and contains extensive old-growth forests. Big Belimba Creek contains giant wet old-growth forest and extensive tree-fern forests.
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Tallaganda_State_Forest&amp;action=edit&amp;redlink=1" title="Tallaganda State Forest (page does not exist)">Tallaganda State Forest</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-5"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>
     <td>Tall wet old-growth forest.
     </td></tr>
     <tr>
     <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Gondwana_Rainforests_of_Australia" title="Gondwana Rainforests of Australia">Gondwana Rainforests of Australia</a>
     </td>
     <td>50 separate reserves totaling 366,500 hectares (906,000 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Subtropical_rainforest" title="Subtropical rainforest">Subtropical rainforest</a>
     </td>
     <td>The most extensive area of subtropical rainforest in the world. Extremely high conservation value; over 200 rare or threatened plant and animal species.
     </td></tr></tbody></table>,
     <table class="wikitable sortable">
     <tbody><tr>
     <th>Country
     </th>
     <th>Area
     </th>
     <th>Old-growth extent
     </th>
     <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
     </th>
     <th class="unsortable">Old-growth forest type
     </th></tr>
     <tr>
     <td>Azerbaijan
     </td>
     <td>Lankaran lowland and Talysh mountains
     </td>
     <td>
     </td>
     <td>Caspian Hyrcanian mixed forest
     </td>
     <td>temperate broadleaf and mixed forests biome
     </td></tr>
     <tr>
     <td><a href="/wiki/Belarus" title="Belarus">Belarus</a>, <a href="/wiki/Poland" title="Poland">Poland</a>
     </td>
     <td><a href="/wiki/Bia%C5%82owie%C5%BCa_Forest" title="Białowieża Forest">Białowieża Forest</a>
     </td>
     <td><span data-sort-value="7009308580000000000♠"></span>308,580 hectares (762,500 acres)
     </td>
     <td><a href="/wiki/Central_European_mixed_forests" title="Central European mixed forests">Central European mixed forests</a><sup class="noprint Inline-Template Template-Fact" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Citation_needed" title="Wikipedia:Citation needed"><span title="This claim needs references to reliable sources. (March 2013)">citation needed</span></a></i>]</sup>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Bosnia_and_Herzegovina" title="Bosnia and Herzegovina">Bosnia and Herzegovina</a>
     </td>
     <td><a href="/wiki/Peru%C4%87ica" title="Perućica">Perućica</a>
     </td>
     <td><span data-sort-value="7007143400000000000♠"></span>1,434 hectares (3,540 acres)
     </td>
     <td><a href="/wiki/Dinaric_Mountains_mixed_forests" title="Dinaric Mountains mixed forests">Dinaric Mountains mixed forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Bosnia_and_Herzegovina" title="Bosnia and Herzegovina">Bosnia and Herzegovina</a>
     </td>
     <td><a href="/wiki/Ravna_Vala" title="Ravna Vala">Ravna Vala</a>
     </td>
     <td><span data-sort-value="7005450400000000000♠"></span>45.04 hectares (111.3 acres)
     </td>
     <td><a href="/wiki/Dinaric_Mountains_mixed_forests" title="Dinaric Mountains mixed forests">Dinaric Mountains mixed forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Bulgaria" title="Bulgaria">Bulgaria</a><sup class="reference" id="cite_ref-gis.wwf.bg_10-0"><a href="#cite_note-gis.wwf.bg-10"><span class="cite-bracket">[</span>10<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Ancient_and_Primeval_Beech_Forests_of_the_Carpathians_and_Other_Regions_of_Europe" title="Ancient and Primeval Beech Forests of the Carpathians and Other Regions of Europe">Ancient and Primeval Beech Forests of Europe</a> in the <a href="/wiki/Central_Balkan_National_Park" title="Central Balkan National Park">Central Balkan National Park</a>
     </td>
     <td><span data-sort-value="7010109889100000000♠"></span>1,098,891 hectares (2,715,420 acres)
     </td>
     <td><a href="/wiki/Rodope_montane_mixed_forests" title="Rodope montane mixed forests">Rodope montane mixed forests</a>
     </td>
     <td>Temperate broadleaf and mixed forests biome
     </td></tr>
     <tr>
     <td><a href="/wiki/Bulgaria" title="Bulgaria">Bulgaria</a><sup class="reference" id="cite_ref-gis.wwf.bg_10-1"><a href="#cite_note-gis.wwf.bg-10"><span class="cite-bracket">[</span>10<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Bayuvi_Dupki%E2%80%93Dzhindzhiritsa" title="Bayuvi Dupki–Dzhindzhiritsa">Bayuvi Dupki–Dzhindzhiritsa</a> (<a href="/wiki/Temperate_coniferous_forest" title="Temperate coniferous forest">temperate coniferous forest</a>), <a href="/wiki/Pirin_National_Park" title="Pirin National Park">Pirin National Park</a>
     </td>
     <td><span data-sort-value="7007287300000000000♠"></span>2,873 hectares (7,100 acres)
     </td>
     <td><a href="/wiki/Rodope_montane_mixed_forests" title="Rodope montane mixed forests">Rodope montane mixed forests</a>
     </td>
     <td><a href="/wiki/Temperate_broadleaf_and_mixed_forests" title="Temperate broadleaf and mixed forests">Temperate broadleaf and mixed forests</a> biome
     </td></tr>
     <tr>
     <td><a href="/wiki/Bulgaria" title="Bulgaria">Bulgaria</a><sup class="reference" id="cite_ref-gis.wwf.bg_10-2"><a href="#cite_note-gis.wwf.bg-10"><span class="cite-bracket">[</span>10<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Mantaritza_Biosphere_Reserve" title="Mantaritza Biosphere Reserve">Mantaritza Biosphere Reserve</a> forests
     </td>
     <td><span data-sort-value="7007132000000000000♠"></span>1,320 hectares (3,300 acres)
     </td>
     <td><a href="/wiki/Rodope_montane_mixed_forests" title="Rodope montane mixed forests">Rodope montane mixed forests</a>
     </td>
     <td>Temperate broadleaf and mixed forests biome
     </td></tr>
     <tr>
     <td><a href="/wiki/Bulgaria" title="Bulgaria">Bulgaria</a><sup class="reference" id="cite_ref-gis.wwf.bg_10-3"><a href="#cite_note-gis.wwf.bg-10"><span class="cite-bracket">[</span>10<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>Parangalitsa Reserve forests, <a href="/wiki/Rila_National_Park" title="Rila National Park">Rila National Park</a>
     </td>
     <td><span data-sort-value="7007150900000000000♠"></span>1,509 hectares (3,730 acres)
     </td>
     <td><a href="/wiki/Rodope_montane_mixed_forests" title="Rodope montane mixed forests">Rodope montane mixed forests</a>
     </td>
     <td>Temperate broadleaf and mixed forests biome
     </td></tr>
     <tr>
     <td><a href="/wiki/Bulgaria" title="Bulgaria">Bulgaria</a><sup class="reference" id="cite_ref-gis.wwf.bg_10-4"><a href="#cite_note-gis.wwf.bg-10"><span class="cite-bracket">[</span>10<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Uzunbodzhak" title="Uzunbodzhak">Uzunbodzhak</a> Reserve <a href="/wiki/Temperate_rainforest" title="Temperate rainforest">temperate rainforest</a>, <a href="/wiki/Strandzha_Nature_Park" title="Strandzha Nature Park">Strandzha Nature Park</a>, <a href="/wiki/Strandzha" title="Strandzha">Strandzha</a> Mountain
     </td>
     <td><span data-sort-value="7007252960000000000♠"></span>2,529.6 hectares (6,251 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Euxine-Colchic_deciduous_forests" title="Euxine-Colchic deciduous forests">Euxine-Colchic deciduous forests</a>
     </td>
     <td>Temperate broadleaf and mixed forests biome (<a class="mw-redirect" href="/wiki/Euxine-Colchic_deciduous_forests" title="Euxine-Colchic deciduous forests">Euxine-Colchic deciduous forests</a>)
     </td></tr>
     <tr>
     <td><a href="/wiki/Czech_Republic" title="Czech Republic">Czech Republic</a>
     </td>
     <td>Boubin Primeval Forest
     </td>
     <td><span data-sort-value="7006685900000000000♠"></span>685.9 hectares (1,695 acres)
     </td></tr>
     <tr>
     <td><a href="/wiki/Estonia" title="Estonia">Estonia</a>
     </td>
     <td><a href="/wiki/J%C3%A4rvselja_Nature_Reserve" title="Järvselja Nature Reserve">Järvselja Nature Reserve</a>
     </td>
     <td><span data-sort-value="7006184000000000000♠"></span>184 hectares (450 acres)
     </td>
     <td><a href="/wiki/Scandinavian_and_Russian_taiga" title="Scandinavian and Russian taiga">Scandinavian and Russian taiga</a>
     </td>
     <td>Variety of succession stages between <a href="/wiki/Carr_(landform)" title="Carr (landform)">carrs</a> and <a class="mw-redirect" href="/wiki/Scots_pine" title="Scots pine">Scots pine</a> dominated <a href="/wiki/Taiga" title="Taiga">taiga</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Finland" title="Finland">Finland</a>
     </td>
     <td><a href="/wiki/Pyh%C3%A4-H%C3%A4kki_National_Park" title="Pyhä-Häkki National Park">Pyhä-Häkki National Park</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Scandinavian_and_Russian_taiga" title="Scandinavian and Russian taiga">Scandinavian and Russian taiga</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Scots_pine" title="Scots pine">Scots pine</a> and <a class="mw-redirect" href="/wiki/Norway_spruce" title="Norway spruce">Norway spruce</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale d'Assan
     </td>
     <td><span data-sort-value="7007103200000000000♠"></span>1,032 hectares (2,550 acres)
     </td>
     <td><a href="/wiki/Temperate_coniferous_forest" title="Temperate coniferous forest">Temperate coniferous forest</a>
     </td>
     <td><i><a href="/wiki/Pinus_sylvestris" title="Pinus sylvestris">Pinus sylvestris</a></i>, <i><a href="/wiki/Abies_alba" title="Abies alba">Abies alba</a></i>, <i><a href="/wiki/Larix_decidua" title="Larix decidua">Larix decidua</a></i>, <i><a href="/wiki/Juniperus_thurifera" title="Juniperus thurifera">Juniperus thurifera</a></i> and <i><a class="mw-redirect" href="/wiki/Pinus_uncinata" title="Pinus uncinata">Pinus uncinata</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td><a href="/wiki/Forest_of_Chaux" title="Forest of Chaux">Réserve Biologique Intégrale de Chaux</a>
     </td>
     <td><span data-sort-value="7006148000000000000♠"></span>148 hectares (370 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Abies_alba" title="Abies alba">Abies alba</a></i>, <i><a href="/wiki/Picea_abies" title="Picea abies">Picea abies</a></i> and <i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale de la Glacière
     </td>
     <td><span data-sort-value="7005280000000000000♠"></span>28 hectares (69 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Abies_alba" title="Abies alba">Abies alba</a></i>, <i><a href="/wiki/Picea_abies" title="Picea abies">Picea abies</a></i> and <i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale de la Sainte-Baume
     </td>
     <td><span data-sort-value="7006138000000000000♠"></span>138 hectares (340 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>, <i><a href="/wiki/Quercus_pubescens" title="Quercus pubescens">Quercus pubescens</a></i>, <i><a href="/wiki/Taxus_baccata" title="Taxus baccata">Taxus baccata</a></i>, <i><a href="/wiki/Ilex_aquifolium" title="Ilex aquifolium">Ilex aquifolium</a></i>, <i><a href="/wiki/Tilia_cordata" title="Tilia cordata">Tilia cordata</a></i>, <a href="/wiki/Maple" title="Maple">maple</a> and <i><a href="/wiki/Quercus_ilex" title="Quercus ilex">Quercus ilex</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale de la Sylve d’Argenson
     </td>
     <td><span data-sort-value="7007257900000000000♠"></span>2,579 hectares (6,370 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>, <i><a href="/wiki/Quercus_petraea" title="Quercus petraea">Quercus petraea</a></i>  and <i><a href="/wiki/Quercus_robur" title="Quercus robur">Quercus robur</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale de Saint-Pé-de-Bigorre
     </td>
     <td><span data-sort-value="7007101000000000000♠"></span>1,010 hectares (2,500 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>,  <i><a href="/wiki/Tilia_cordata" title="Tilia cordata">Tilia cordata</a></i> and <a href="/wiki/Maple" title="Maple">Maple</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale des Maures
     </td>
     <td><span data-sort-value="7007253100000000000♠"></span>2,531 hectares (6,250 acres)
     </td>
     <td><a href="/wiki/Mediterranean_forests,_woodlands,_and_scrub" title="Mediterranean forests, woodlands, and scrub">Mediterranean forests, woodlands, and scrub</a>
     </td>
     <td><i><a href="/wiki/Quercus_ilex" title="Quercus ilex">Quercus ilex</a></i>, <i><a href="/wiki/Quercus_suber" title="Quercus suber">Quercus suber</a></i>, <i><a href="/wiki/Castanea_sativa" title="Castanea sativa">Castanea sativa</a></i> and <i><a href="/wiki/Pinus_pinaster" title="Pinus pinaster">Pinus pinaster</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale du Mont Ventoux
     </td>
     <td><span data-sort-value="7006906000000000000♠"></span>906 hectares (2,240 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a class="mw-redirect" href="/wiki/Pinus_uncinata" title="Pinus uncinata">Pinus uncinata</a></i>, <i><a href="/wiki/Pinus_nigra" title="Pinus nigra">Pinus nigra</a></i>, <i><a href="/wiki/Pinus_sylvestris" title="Pinus sylvestris">Pinus sylvestris</a></i>, <i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i> and <i><a href="/wiki/Abies_alba" title="Abies alba">Abies alba</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale du Défilé de Straiture
     </td>
     <td><span data-sort-value="7006124000000000000♠"></span>124 hectares (310 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Abies_alba" title="Abies alba">Abies alba</a></i>, <i><a href="/wiki/Picea_abies" title="Picea abies">Picea abies</a></i> and <i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale d'Oléron - Saint-Trojan
     </td>
     <td><span data-sort-value="7006158000000000000♠"></span>158 hectares (390 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Quercus_ilex" title="Quercus ilex">Quercus ilex</a></i>, <i><a href="/wiki/Quercus_petraea" title="Quercus petraea">Quercus petraea</a></i>  and <i><a href="/wiki/Pinus_pinaster" title="Pinus pinaster">Pinus pinaster</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale du Bois du Ruère
     </td>
     <td><span data-sort-value="7005640000000000000♠"></span>64 hectares (160 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>, <i><a href="/wiki/Quercus_robur" title="Quercus robur">Quercus robur</a></i>, <i><a href="/wiki/Carpinus_betulus" title="Carpinus betulus">Carpinus betulus</a></i>, <i><a href="/wiki/Tilia_cordata" title="Tilia cordata">Tilia cordata</a></i> and <a href="/wiki/Maple" title="Maple">Maple</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/France" title="France">France</a>
     </td>
     <td>Réserve Biologique Intégrale du Vercors
     </td>
     <td><span data-sort-value="7007216000000000000♠"></span>2,160 hectares (5,300 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Abies_alba" title="Abies alba">Abies alba</a></i>, <i><a href="/wiki/Picea_abies" title="Picea abies">Picea abies</a></i> and <i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/Croatia" title="Croatia">Croatia</a>
     </td>
     <td>Klepina Duliba Old Growth forest
     </td>
     <td><span data-sort-value="7006118000000000000♠"></span>118 hectares (290 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Abies_alba" title="Abies alba">Abies alba</a></i>,<i><a href="/wiki/Picea_abies" title="Picea abies">Picea abies</a></i> and <i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/Italy" title="Italy">Italy</a>
     </td>
     <td>Valle Cervara
     </td>
     <td><span data-sort-value="7005500000000000000♠"></span>50 hectares (120 acres)
     </td>
     <td>Oldest beech forest in Europe<sup class="reference" id="cite_ref-11"><a href="#cite_note-11"><span class="cite-bracket">[</span>11<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>temperate broadleaf and mixed forests biome. <i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i> Taxus. /lex, several Betulaceae (Carpinus spp., Ostrya. Corylus, Alnus cordata in some areas, Betula), Ulmus spp. (surtout U glabra), Fraxinus ornus (more rarely F excelsior) and Acer (A. opalus s.l., A. pseudoplatanus, A. platanoides, A. /obelii)
     </td></tr>
     <tr>
     <td><a href="/wiki/Montenegro" title="Montenegro">Montenegro</a>
     </td>
     <td><a href="/wiki/Biogradska_Gora" title="Biogradska Gora">Biogradska Gora</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Dinaric_Mountains_mixed_forests" title="Dinaric Mountains mixed forests">Dinaric Mountains mixed forests</a>
     </td>
     <td>temperate broadleaf and mixed forest
     </td></tr>
     <tr>
     <td><a href="/wiki/Montenegro" title="Montenegro">Montenegro</a>
     </td>
     <td>Crna Poda
     </td>
     <td>
     </td>
     <td><a href="/wiki/Dinaric_Mountains_mixed_forests" title="Dinaric Mountains mixed forests">Dinaric Mountains mixed forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coniferous" title="Coniferous">Coniferous</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Norway" title="Norway">Norway</a>
     </td>
     <td><a href="/wiki/Trillemarka" title="Trillemarka">Trillemarka</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Scandinavian_and_Russian_taiga" title="Scandinavian and Russian taiga">Scandinavian and Russian taiga</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Norway" title="Norway">Norway</a>
     </td>
     <td><a href="/wiki/Stabbursdalen_National_Park" title="Stabbursdalen National Park">Stabbursdalen National Park</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Scandinavian_and_Russian_taiga" title="Scandinavian and Russian taiga">Scandinavian and Russian taiga</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Norway" title="Norway">Norway</a>
     </td>
     <td><a href="/wiki/%C3%98vre_Dividal_National_Park" title="Øvre Dividal National Park">Øvre Dividal National Park</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Scandinavian_and_Russian_taiga" title="Scandinavian and Russian taiga">Scandinavian and Russian taiga</a>, <a href="/wiki/Scandinavian_montane_birch_forest_and_grasslands" title="Scandinavian montane birch forest and grasslands">Scandinavian montane birch forest and grasslands</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Romania" title="Romania">Romania</a>
     </td>
     <td><a href="/wiki/Retezat_National_Park" title="Retezat National Park">Retezat National Park</a>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Carpathian_montane_conifer_forests" title="Carpathian montane conifer forests">Carpathian montane conifer forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Serbia" title="Serbia">Serbia</a>
     </td>
     <td><a href="/wiki/Vinatova%C4%8Da" title="Vinatovača">Vinatovača</a>
     </td>
     <td><span data-sort-value="7005370000000000000♠"></span>37 hectares (91 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Temperate_broadleaf_and_mixed_forest" title="Temperate broadleaf and mixed forest">Temperate broadleaf and mixed forest</a>
     </td>
     <td><i><a href="/wiki/Fagus_sylvatica" title="Fagus sylvatica">Fagus sylvatica</a></i>
     </td></tr>
     <tr>
     <td><a href="/wiki/Slovakia" title="Slovakia">Slovakia</a>
     </td>
     <td><a href="/wiki/Stu%C5%BEica" title="Stužica">Stužica</a>
     </td>
     <td><span data-sort-value="7006761500000000000♠"></span>761.5 hectares (1,882 acres)
     </td>
     <td><a href="/wiki/Pannonian_mixed_forests" title="Pannonian mixed forests">Pannonian mixed forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/European_Beech" title="European Beech">European Beech</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ukraine" title="Ukraine">Ukraine</a>
     </td>
     <td><a href="/wiki/Carpathian_Biosphere_Reserve" title="Carpathian Biosphere Reserve">Carpathian Biosphere Reserve</a>
     </td>
     <td>57,880 hectares (143,000 acres)
     </td>
     <td><a href="/wiki/Ancient_and_Primeval_Beech_Forests_of_the_Carpathians_and_Other_Regions_of_Europe" title="Ancient and Primeval Beech Forests of the Carpathians and Other Regions of Europe">Ancient and Primeval Beech Forests of the Carpathians and Other Regions of Europe</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/United_Kingdom" title="United Kingdom">United Kingdom</a>
     </td>
     <td><a href="/wiki/Forest_of_Dean" title="Forest of Dean">Forest of Dean</a>
     </td>
     <td>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Mixed_woodland" title="Mixed woodland">mixed woodland</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/United_Kingdom" title="United Kingdom">United Kingdom</a>
     </td>
     <td><a href="/wiki/Puzzlewood" title="Puzzlewood">Puzzlewood</a>
     </td>
     <td>
     </td>
     <td>
     </td>
     <td>
     </td></tr></tbody></table>,
     <table class="wikitable sortable">
     <tbody><tr>
     <th>Province
     </th>
     <th>Area
     </th>
     <th>Old-growth extent
     </th>
     <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
     </th>
     <th class="unsortable">Old-growth forest type
     </th></tr>
     <tr>
     <td><a href="/wiki/British_Columbia" title="British Columbia">British Columbia</a>
     </td>
     <td><a href="/wiki/Carmanah_Walbran_Provincial_Park" title="Carmanah Walbran Provincial Park">Carmanah Walbran Provincial Park</a>
     </td>
     <td>164 square kilometres (41,000 acres)
     </td>
     <td><a href="/wiki/Central_Pacific_coastal_forests" title="Central Pacific coastal forests">Central Pacific coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coniferous" title="Coniferous">coniferous</a> <a href="/wiki/Temperate_rainforest" title="Temperate rainforest">temperate rainforest</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/British_Columbia" title="British Columbia">British Columbia</a>
     </td>
     <td><a href="/wiki/Clayoquot_Sound" title="Clayoquot Sound">Clayoquot Sound</a>
     </td>
     <td>265,000 hectares (650,000 acres)
     </td>
     <td><a href="/wiki/Central_Pacific_coastal_forests" title="Central Pacific coastal forests">Central Pacific coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coniferous" title="Coniferous">coniferous</a> <a href="/wiki/Temperate_rainforest" title="Temperate rainforest">temperate rainforest</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/British_Columbia" title="British Columbia">British Columbia</a>
     </td>
     <td><a href="/wiki/Great_Bear_Rainforest" title="Great Bear Rainforest">Great Bear Rainforest</a>
     </td>
     <td>16,000 square kilometres (4,000,000 acres)
     </td>
     <td><a href="/wiki/British_Columbia_mainland_coastal_forests" title="British Columbia mainland coastal forests">British Columbia mainland coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coniferous" title="Coniferous">coniferous</a> <a href="/wiki/Temperate_rainforest" title="Temperate rainforest">temperate rainforest</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=North_River_Wilderness_Area&amp;action=edit&amp;redlink=1" title="North River Wilderness Area (page does not exist)">North River Wilderness Area</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-0"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Panuke_Lake_Nature_Reserve&amp;action=edit&amp;redlink=1" title="Panuke Lake Nature Reserve (page does not exist)">Panuke Lake Nature Reserve</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-1"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>47 hectares (120 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Red_Spruce" title="Red Spruce">Red Spruce</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Shelburne_Heritage_River&amp;action=edit&amp;redlink=1" title="Shelburne Heritage River (page does not exist)">Shelburne Heritage River</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-2"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, pine
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a href="/wiki/Pollett%27s_Cove" title="Pollett's Cove">Pollett's Cove</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-3"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Canadian_forests" title="Eastern Canadian forests">Eastern Canadian forests</a>, <a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td>boreal
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=French_River_Wilderness_Area&amp;action=edit&amp;redlink=1" title="French River Wilderness Area (page does not exist)">French River Wilderness Area</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-4"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Trout_Brook_Wilderness_Area&amp;action=edit&amp;redlink=1" title="Trout Brook Wilderness Area (page does not exist)">Trout Brook Wilderness Area</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-5"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td>
     <td>deciduous
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a href="/wiki/Tobeatic_Wilderness_Area" title="Tobeatic Wilderness Area">Tobeatic Wilderness Area</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-6"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, pine
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Portapique_River_Wilderness_Area&amp;action=edit&amp;redlink=1" title="Portapique River Wilderness Area (page does not exist)">Portapique River Wilderness Area</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-7"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Red_Spruce" title="Red Spruce">Red Spruce</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a href="/wiki/Waverley%E2%80%93Salmon_River_Long_Lake_Wilderness_Area" title="Waverley–Salmon River Long Lake Wilderness Area">Waverley–Salmon River Long Lake Wilderness Area</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-8"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Red_Pine" title="Red Pine">Red Pine</a>, <a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Boggy_Lake_Wilderness_Area&amp;action=edit&amp;redlink=1" title="Boggy Lake Wilderness Area (page does not exist)">Boggy Lake Wilderness Area</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-9"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a>, <a class="mw-redirect" href="/wiki/Yellow_Birch" title="Yellow Birch">Yellow Birch</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Great_Barren_%26_Quinan_Lakes_Nature_Reserve&amp;action=edit&amp;redlink=1" title="Great Barren &amp; Quinan Lakes Nature Reserve (page does not exist)">Great Barren &amp; Quinan Lakes Nature Reserve</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-10"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Red_Spruce" title="Red Spruce">Red Spruce</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=MacFarlane_Woods_Nature_Reserve&amp;action=edit&amp;redlink=1" title="MacFarlane Woods Nature Reserve (page does not exist)">MacFarlane Woods Nature Reserve</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-11"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a>, <a class="mw-redirect" href="/wiki/Yellow_Birch" title="Yellow Birch">Yellow Birch</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Bornish_Hill_Nature_Reserve&amp;action=edit&amp;redlink=1" title="Bornish Hill Nature Reserve (page does not exist)">Bornish Hill Nature Reserve</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-12"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td>hardwood
     </td></tr>
     <tr>
     <td><a href="/wiki/Nova_Scotia" title="Nova Scotia">Nova Scotia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Sporting_Lake_Nature_Reserve&amp;action=edit&amp;redlink=1" title="Sporting Lake Nature Reserve (page does not exist)">Sporting Lake Nature Reserve</a><sup class="reference" id="cite_ref-NovaScotiaProtectedAreas_12-13"><a href="#cite_note-NovaScotiaProtectedAreas-12"><span class="cite-bracket">[</span>12<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>25 hectares (62 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">White Pine</a>, <a class="mw-redirect" href="/wiki/Red_Spruce" title="Red Spruce">Red Spruce</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ontario" title="Ontario">Ontario</a>
     </td>
     <td>Gillies Grove, <a href="/wiki/Arnprior" title="Arnprior">Arnprior</a>
     </td>
     <td>18 hectares (44 acres)
     </td>
     <td><a href="/wiki/Eastern_Great_Lakes_lowland_forests" title="Eastern Great Lakes lowland forests">Eastern Great Lakes lowland forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ontario" title="Ontario">Ontario</a>
     </td>
     <td><a href="/wiki/Obabika_Old-Growth_Forest" title="Obabika Old-Growth Forest">Obabika Old-Growth Forest</a>
     </td>
     <td>2,400 hectares (5,900 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_forest-boreal_transition" title="Eastern forest-boreal transition">Eastern forest-boreal transition</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ontario" title="Ontario">Ontario</a>
     </td>
     <td><a href="/wiki/Quetico_Provincial_Park" title="Quetico Provincial Park">Quetico Provincial Park</a>
     </td>
     <td>1,500 square kilometres (370,000 acres)
     </td>
     <td><a href="/wiki/Western_Great_Lakes_forests" title="Western Great Lakes forests">Western Great Lakes forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ontario" title="Ontario">Ontario</a>
     </td>
     <td><a href="/wiki/White_Bear_Forest" title="White Bear Forest">White Bear Forest</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_forest-boreal_transition" title="Eastern forest-boreal transition">Eastern forest-boreal transition</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ontario" title="Ontario">Ontario</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Wolf_Lake_Forest_Reserve" title="Wolf Lake Forest Reserve">Wolf Lake Forest Reserve</a>
     </td>
     <td>336 hectares (830 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_forest-boreal_transition" title="Eastern forest-boreal transition">Eastern forest-boreal transition</a>
     </td>
     <td>red pine
     </td></tr>
     <tr>
     <td><a href="/wiki/Quebec" title="Quebec">Quebec</a>
     </td>
     <td><a href="/wiki/Bois_Beckett_Forest" title="Bois Beckett Forest">Bois Beckett Forest</a>,<sup class="reference" id="cite_ref-13"><a href="#cite_note-13"><span class="cite-bracket">[</span>13<span class="cite-bracket">]</span></a></sup> <a href="/wiki/Sherbrooke" title="Sherbrooke">Sherbrooke</a>
     </td>
     <td>6 ha (15 acres)
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td>hemlock, beech
     </td></tr>
     <tr>
     <td>Quebec
     </td>
     <td><a class="new" href="/w/index.php?title=Papineau_Woods&amp;action=edit&amp;redlink=1" title="Papineau Woods (page does not exist)">Papineau Woods</a>, <a href="/wiki/Laval,_Quebec" title="Laval, Quebec">Laval</a>,<sup class="reference" id="cite_ref-14"><a href="#cite_note-14"><span class="cite-bracket">[</span>14<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>100 ha (250 acres)
     </td>
     <td>
     </td>
     <td>
     </td></tr></tbody></table>,
     <table class="wikitable sortable">
     <tbody><tr>
     <th>State
     </th>
     <th>Area
     </th>
     <th>Old-growth extent
     </th>
     <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
     </th>
     <th class="unsortable">Old-growth forest type
     </th></tr>
     <tr>
     <td><a href="/wiki/Alabama" title="Alabama">Alabama</a>
     </td>
     <td><a href="/wiki/Sipsey_Wilderness" title="Sipsey Wilderness">Sipsey Wilderness</a><sup class="reference" id="cite_ref-ogEast_15-0"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Appalachian_mixed_mesophytic_forests" title="Appalachian mixed mesophytic forests">Appalachian mixed mesophytic forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a class="mw-redirect" href="/wiki/Sweet_Birch" title="Sweet Birch">Sweet Birch</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/Tulip_Poplar" title="Tulip Poplar">Tulip Poplar</a><sup class="reference" id="cite_ref-ogEast_15-1"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Alaska" title="Alaska">Alaska</a>
     </td>
     <td><a href="/wiki/Tongass_National_Forest" title="Tongass National Forest">Tongass National Forest</a><sup class="reference" id="cite_ref-tnf_16-0"><a href="#cite_note-tnf-16"><span class="cite-bracket">[</span>16<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7010218530246809600♠"></span>5,400,000 acres (2,200,000 ha)
     </td>
     <td><a href="/wiki/Northern_Pacific_coastal_forests" title="Northern Pacific coastal forests">Northern Pacific coastal forests</a>, <a href="/wiki/Pacific_Coastal_Mountain_icefields_and_tundra" title="Pacific Coastal Mountain icefields and tundra">Pacific Coastal Mountain icefields and tundra</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Western_Red_Cedar" title="Western Red Cedar">Western Red Cedar</a>, <a class="mw-redirect" href="/wiki/Sitka_Spruce" title="Sitka Spruce">Sitka Spruce</a>, <a class="mw-redirect" href="/wiki/Western_Hemlock" title="Western Hemlock">Western Hemlock</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Arkansas" title="Arkansas">Arkansas</a>
     </td>
     <td><a href="/wiki/White_River_National_Wildlife_Refuge" title="White River National Wildlife Refuge">White River National Wildlife Refuge</a><sup class="reference" id="cite_ref-ogEast_15-2"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006393759129899520♠"></span>973 acres (394 ha)<sup class="reference" id="cite_ref-ogEast_15-3"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Mississippi_lowland_forests" title="Mississippi lowland forests">Mississippi lowland forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/American_Sweetgum" title="American Sweetgum">American Sweetgum</a>, <a class="mw-redirect" href="/wiki/Nuttall%27s_Oak" title="Nuttall's Oak">Nuttall's Oak</a>, <a class="mw-redirect" href="/wiki/Willow_Oak" title="Willow Oak">Willow Oak</a>, <a class="mw-redirect" href="/wiki/Sugarberry" title="Sugarberry">Sugarberry</a>, <a class="mw-redirect" href="/wiki/American_Elm" title="American Elm">American Elm</a>, <a class="mw-redirect" href="/wiki/Green_Ash" title="Green Ash">Green Ash</a>, <a class="mw-redirect" href="/wiki/American_Sycamore" title="American Sycamore">American Sycamore</a>, <a href="/wiki/Pecan" title="Pecan">Pecan</a>, <a class="mw-redirect" href="/wiki/American_Elm" title="American Elm">American Elm</a>, <a class="mw-redirect" href="/wiki/Baldcypress" title="Baldcypress">Baldcypress</a><sup class="reference" id="cite_ref-ogEast_15-4"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Arkansas" title="Arkansas">Arkansas</a>
     </td>
     <td><a href="/wiki/Ouachita_National_Forest" title="Ouachita National Forest">Ouachita National Forest</a><sup class="reference" id="cite_ref-ogEast_15-5"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009323748513792000♠"></span>800,000 acres (320,000 ha)<sup class="reference" id="cite_ref-ogEast_15-6"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Post_Oak" title="Post Oak">Post Oak</a>, <a class="mw-redirect" href="/wiki/Shortleaf_Pine" title="Shortleaf Pine">Shortleaf Pine</a>, <a href="/wiki/Hickory" title="Hickory">Hickory</a>, <a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/Blackjack_Oak" title="Blackjack Oak">Blackjack Oak</a>, <a class="mw-redirect" href="/wiki/Eastern_Redcedar" title="Eastern Redcedar">Eastern Redcedar</a>, <a class="mw-redirect" href="/wiki/Gum_Bumelia" title="Gum Bumelia">Gum Bumelia</a>, <a class="mw-redirect" href="/wiki/Winged_Elm" title="Winged Elm">Winged Elm</a>, <a class="mw-redirect" href="/wiki/Yaupon" title="Yaupon">Yaupon</a><sup class="reference" id="cite_ref-ogEast_15-7"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Arkansas" title="Arkansas">Arkansas</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Ozark-St._Francis_National_Forest" title="Ozark-St. Francis National Forest">Ozark-St. Francis National Forest</a><sup class="reference" id="cite_ref-OzarkStFrancisFeis_17-0"><a href="#cite_note-OzarkStFrancisFeis-17"><span class="cite-bracket">[</span>17<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007445154206464000♠"></span>11,000 acres (4,500 ha)<sup class="reference" id="cite_ref-OzarkStFrancisFeis_17-1"><a href="#cite_note-OzarkStFrancisFeis-17"><span class="cite-bracket">[</span>17<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Shortleaf_Pine" title="Shortleaf Pine">Shortleaf Pine</a>, <a class="mw-redirect" href="/wiki/Post_Oak" title="Post Oak">Post Oak</a>, <a class="mw-redirect" href="/wiki/Blackjack_Oak" title="Blackjack Oak">Blackjack Oak</a>, <a class="mw-redirect" href="/wiki/Eastern_Black_Oak" title="Eastern Black Oak">Eastern Black Oak</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a><sup class="reference" id="cite_ref-OzarkStFrancisFeis_17-2"><a href="#cite_note-OzarkStFrancisFeis-17"><span class="cite-bracket">[</span>17<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Arkansas" title="Arkansas">Arkansas</a>
     </td>
     <td><a href="/wiki/Hot_Springs_National_Park" title="Hot Springs National Park">Hot Springs National Park</a><sup class="reference" id="cite_ref-ogEast_15-8"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006129499405516800♠"></span>320 acres (130 ha)<sup class="reference" id="cite_ref-ogEast_15-9"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Shortleaf_Pine" title="Shortleaf Pine">Shortleaf Pine</a>, <a class="mw-redirect" href="/wiki/Blackjack_Oak" title="Blackjack Oak">Blackjack Oak</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a><sup class="reference" id="cite_ref-ogEast_15-10"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Arkansas" title="Arkansas">Arkansas</a>
     </td>
     <td><a href="/wiki/Overflow_National_Wildlife_Refuge" title="Overflow National Wildlife Refuge">Overflow National Wildlife Refuge</a><sup class="reference" id="cite_ref-ogEast_15-11"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005930776977152000♠"></span>230 acres (93 ha)<sup class="reference" id="cite_ref-ogEast_15-12"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a><sup class="reference" id="cite_ref-ogEast_15-13"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Yosemite_National_Park" title="Yosemite National Park">Yosemite National Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-0"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008912606591815424♠"></span>225,510 acres (91,260 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-1"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Sierra_Nevada_forests" title="Sierra Nevada forests">Sierra Nevada forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Giant_Sequoia" title="Giant Sequoia">Giant Sequoia</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Sugar_Pine" title="Sugar Pine">Sugar Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/California_Incense_Cedar" title="California Incense Cedar">California Incense Cedar</a>, <a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a>, <a class="mw-redirect" href="/wiki/Western_White_Pine" title="Western White Pine">Western White Pine</a>, <a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a>, <a class="mw-redirect" href="/wiki/Foxtail_Pine" title="Foxtail Pine">Foxtail Pine</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Sequoia_National_Park" title="Sequoia National Park">Sequoia</a>-<a href="/wiki/Kings_Canyon_National_Park" title="Kings Canyon National Park">Kings Canyon National Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-2"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008819205145586432♠"></span>202,430 acres (81,920 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-3"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Sierra_Nevada_forests" title="Sierra Nevada forests">Sierra Nevada forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Giant_Sequoia" title="Giant Sequoia">Giant Sequoia</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Sugar_Pine" title="Sugar Pine">Sugar Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a>, <a class="mw-redirect" href="/wiki/California_Incense_Cedar" title="California Incense Cedar">California Incense Cedar</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Lassen_Volcanic_National_Park" title="Lassen Volcanic National Park">Lassen Volcanic National Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-4"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008109791214739712♠"></span>27,130 acres (10,980 ha)
     </td>
     <td><a class="mw-redirect" href="/wiki/Sierra_Nevada_forests" title="Sierra Nevada forests">Sierra Nevada forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Sugar_Pine" title="Sugar Pine">Sugar Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a>, <a class="mw-redirect" href="/wiki/Western_White_Pine" title="Western White Pine">Western White Pine</a>, <a class="mw-redirect" href="/wiki/Mountain_Hemlock" title="Mountain Hemlock">Mountain Hemlock</a>, <a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a>, <a class="mw-redirect" href="/wiki/Whitebark_Pine" title="Whitebark Pine">Whitebark Pine</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Redwood_National_and_State_Parks" title="Redwood National and State Parks">Redwood National and State Parks</a><sup class="reference" id="cite_ref-RedwoodNationalPark_19-0"><a href="#cite_note-RedwoodNationalPark-19"><span class="cite-bracket">[</span>19<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008157754557057996♠"></span>38,982 acres (15,775 ha) or more<sup class="reference" id="cite_ref-RedwoodNationalPark_19-1"><a href="#cite_note-RedwoodNationalPark-19"><span class="cite-bracket">[</span>19<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northern_California_coastal_forests" title="Northern California coastal forests">Northern California coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Redwood" title="Coast Redwood">Coast Redwood</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Humboldt_Redwoods_State_Park" title="Humboldt Redwoods State Park">Humboldt Redwoods State Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-5"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007955058115686400♠"></span>23,600 acres (9,600 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-6"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northern_California_coastal_forests" title="Northern California coastal forests">Northern California coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Redwood" title="Coast Redwood">Coast Redwood</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Muir_Woods_National_Monument" title="Muir Woods National Monument">Muir Woods National Monument</a><sup class="reference" id="cite_ref-ogCaOrWa_18-7"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005971245541376000♠"></span>240 acres (97 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-8"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/California_interior_chaparral_and_woodlands" title="California interior chaparral and woodlands">California interior chaparral and woodlands</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Redwood" title="Coast Redwood">Coast Redwood</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Samuel_P._Taylor_State_Park" title="Samuel P. Taylor State Park">Samuel P. Taylor State Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-9"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006242811385344000♠"></span>600 acres (240 ha)
     </td>
     <td><a href="/wiki/California_interior_chaparral_and_woodlands" title="California interior chaparral and woodlands">California interior chaparral and woodlands</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Redwood" title="Coast Redwood">Coast Redwood</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Big_Basin_Redwoods_State_Park" title="Big Basin Redwoods State Park">Big Basin Redwoods State Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-10"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007437060493619200♠"></span>10,800 acres (4,400 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-11"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northern_California_coastal_forests" title="Northern California coastal forests">Northern California coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Redwood" title="Coast Redwood">Coast Redwood</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Henry_Cowell_Redwoods_State_Park" title="Henry Cowell Redwoods State Park">Henry Cowell Redwoods State Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-12"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005809371284480000♠"></span>200 acres (81 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-13"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northern_California_coastal_forests" title="Northern California coastal forests">Northern California coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Redwood" title="Coast Redwood">Coast Redwood</a>, <a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Pacific_Madrone" title="Pacific Madrone">Pacific Madrone</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Headwaters_Forest_Reserve" title="Headwaters Forest Reserve">Headwaters Forest Reserve</a><sup class="reference" id="cite_ref-headwaters_20-0"><a href="#cite_note-headwaters-20"><span class="cite-bracket">[</span>20<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007124966926323712♠"></span>3,088 acres (1,250 ha)<sup class="reference" id="cite_ref-headwaters_20-1"><a href="#cite_note-headwaters-20"><span class="cite-bracket">[</span>20<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northern_California_coastal_forests" title="Northern California coastal forests">Northern California coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Redwood" title="Coast Redwood">Coast Redwood</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/California_oak_woodland" title="California oak woodland">Blue oak woodlands</a><sup class="reference" id="cite_ref-Stahle_21-0"><a href="#cite_note-Stahle-21"><span class="cite-bracket">[</span>21<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009202342821120000♠"></span>500,000–2,300,000 acres (200,000–930,000 ha)<sup class="reference" id="cite_ref-Stahle_21-1"><a href="#cite_note-Stahle-21"><span class="cite-bracket">[</span>21<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/California_interior_chaparral_and_woodlands" title="California interior chaparral and woodlands">California interior chaparral and woodlands</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Blue_Oak" title="Blue Oak">Blue Oak</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Angeles_National_Forest" title="Angeles National Forest">Angeles National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-0"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008117358836249600♠"></span>29,000 acres (12,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-1"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/California_montane_chaparral_and_woodlands" title="California montane chaparral and woodlands">California montane chaparral and woodlands</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-2"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Eldorado_National_Forest" title="Eldorado National Forest">Eldorado National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-3"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008493716483532800♠"></span>122,000 acres (49,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-4"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Sierra_Nevada_forests" title="Sierra Nevada forests">Sierra Nevada forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-5"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Inyo_National_Forest" title="Inyo National Forest">Inyo National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-6"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008963151828531200♠"></span>238,000 acres (96,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-7"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Sierra_Nevada_forests" title="Sierra Nevada forests">Sierra Nevada forests</a> – <a href="/wiki/Great_Basin_montane_forests" title="Great Basin montane forests">Great Basin montane forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Great_Basin_Bristlecone_Pine" title="Great Basin Bristlecone Pine">Great Basin Bristlecone Pine</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-8"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Klamath_National_Forest" title="Klamath National Forest">Klamath National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-9"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008679871878963200♠"></span>168,000 acres (68,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-10"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Klamath-Siskiyou_forests" title="Klamath-Siskiyou forests">Klamath-Siskiyou forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/California_Incense_Cedar" title="California Incense Cedar">California Incense Cedar</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-11"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Lassen_National_Forest" title="Lassen National Forest">Lassen National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-12"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008372310790860800♠"></span>92,000 acres (37,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-13"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a>, <a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-14"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Los_Padres_National_Forest" title="Los Padres National Forest">Los Padres National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-15"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007764855863833600♠"></span>18,900 acres (7,600 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-16"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Coast_Redwood" title="Coast Redwood">Coast Redwood</a>, <a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-17"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Mendocino_National_Forest" title="Mendocino National Forest">Mendocino National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-18"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008242811385344000♠"></span>60,000 acres (24,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-19"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Tanoak" title="Tanoak">Tanoak</a>, <a class="mw-redirect" href="/wiki/Pacific_madrone" title="Pacific madrone">Pacific madrone</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-20"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Modoc_National_Forest" title="Modoc National Forest">Modoc National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-21"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008175633568732160♠"></span>43,400 acres (17,600 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-22"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/California_Incense_Cedar" title="California Incense Cedar">California Incense Cedar</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-23"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Pfeiffer_Big_Sur_State_Park" title="Pfeiffer Big Sur State Park">Pfeiffer Big Sur State Park</a><sup class="reference" id="cite_ref-auto_23-0"><a href="#cite_note-auto-23"><span class="cite-bracket">[</span>23<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006407113756093440♠"></span>1,006 acres (407 ha)<sup class="reference" id="cite_ref-24"><a href="#cite_note-24"><span class="cite-bracket">[</span>24<span class="cite-bracket">]</span></a></sup><sup class="noprint Inline-Template noprint Template-Fact" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Verifiability#Wikipedia_and_sources_that_mirror_or_use_it" title="Wikipedia:Verifiability"><span title="This claim cites another Wikipedia article. Articles need references to reliable third-party sources. (June 2022)">circular reference</span></a></i>]</sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Sequoioideae" title="Sequoioideae">Redwood</a><sup class="reference" id="cite_ref-auto_23-1"><a href="#cite_note-auto-23"><span class="cite-bracket">[</span>23<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Plumas_National_Forest" title="Plumas National Forest">Plumas National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-24"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008513950765644800♠"></span>127,000 acres (51,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-25"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-26"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/San_Bernardino_National_Forest" title="San Bernardino National Forest">San Bernardino National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-27"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008353695251317760♠"></span>87,400 acres (35,400 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-28"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Bigcone_Douglas-fir" title="Bigcone Douglas-fir">Bigcone Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-29"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Sequoia_National_Forest" title="Sequoia National Forest">Sequoia National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-30"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008793183858790400♠"></span>196,000 acres (79,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-31"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Giant_Sequoia" title="Giant Sequoia">Giant Sequoia</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a>, <a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-32"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Shasta-Trinity_National_Forest" title="Shasta-Trinity National Forest">Shasta-Trinity National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-33"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008930776977152000♠"></span>230,000 acres (93,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-34"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Tanoak" title="Tanoak">Tanoak</a>, <a class="mw-redirect" href="/wiki/Pacific_madrone" title="Pacific madrone">Pacific madrone</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-35"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Sierra_National_Forest" title="Sierra National Forest">Sierra National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-36"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009154994600977920♠"></span>383,000 acres (155,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-37"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-38"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Six_Rivers_National_Forest" title="Six Rivers National Forest">Six Rivers National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-39"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008554419329868800♠"></span>137,000 acres (55,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-40"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Tanoak" title="Tanoak">Tanoak</a>, <a class="mw-redirect" href="/wiki/Pacific_madrone" title="Pacific madrone">Pacific madrone</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-41"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Stanislaus_National_Forest" title="Stanislaus National Forest">Stanislaus National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-42"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008562513042713600♠"></span>139,000 acres (56,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-43"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a>, <a class="mw-redirect" href="/wiki/Jeffrey_Pine" title="Jeffrey Pine">Jeffrey Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-44"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/California" title="California">California</a>
     </td>
     <td><a href="/wiki/Tahoe_National_Forest" title="Tahoe National Forest">Tahoe National Forest</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-45"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008339935939481600♠"></span>84,000 acres (34,000 ha)<sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-46"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Sugar_Pine" title="Sugar Pine">Sugar Pine</a>, <a class="mw-redirect" href="/wiki/California_Incense_Cedar" title="California Incense Cedar">California Incense Cedar</a>, <a class="mw-redirect" href="/wiki/California_Black_Oak" title="California Black Oak">California Black Oak</a>, <a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a><sup class="reference" id="cite_ref-PacificSouthwest2002Estimates_22-47"><a href="#cite_note-PacificSouthwest2002Estimates-22"><span class="cite-bracket">[</span>22<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Colorado" title="Colorado">Colorado</a>
     </td>
     <td><a href="/wiki/Arapaho_National_Forest" title="Arapaho National Forest">Arapaho National Forest</a><sup class="reference" id="cite_ref-Rebertus1992_25-0"><a href="#cite_note-Rebertus1992-25"><span class="cite-bracket">[</span>25<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007259000000000000♠"></span>2,590 hectares (6,400 acres)<sup class="reference" id="cite_ref-Rebertus1992_25-1"><a href="#cite_note-Rebertus1992-25"><span class="cite-bracket">[</span>25<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Subalpine_Fir" title="Subalpine Fir">Subalpine Fir</a>, <a class="mw-redirect" href="/wiki/Engelmann_Spruce" title="Engelmann Spruce">Engelmann Spruce</a><sup class="reference" id="cite_ref-Rebertus1992_25-2"><a href="#cite_note-Rebertus1992-25"><span class="cite-bracket">[</span>25<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Connecticut" title="Connecticut">Connecticut</a>
     </td>
     <td><a href="/wiki/Cathedral_Pines" title="Cathedral Pines">Cathedral Pines, Cornwall</a><sup class="reference" id="cite_ref-ogEast_15-14"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005169967969740800♠"></span>42 acres (17 ha)<sup class="reference" id="cite_ref-ogEast_15-15"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Pinus_strobus" title="Pinus strobus">White Pine</a>, <a href="/wiki/Tsuga" title="Tsuga">Hemlock</a><sup class="reference" id="cite_ref-ogEast_15-16"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Connecticut" title="Connecticut">Connecticut</a>
     </td>
     <td>Sages Ravine, Salisbury<sup class="reference" id="cite_ref-ogEast_15-17"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005404685642240000♠"></span>100 acres (40 ha)<sup class="reference" id="cite_ref-ogEast_15-18"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Tsuga" title="Tsuga">Hemlock</a>, <a href="/wiki/Oak" title="Oak">Oak</a><sup class="reference" id="cite_ref-ogEast_15-19"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Connecticut" title="Connecticut">Connecticut</a>
     </td>
     <td>Great Mountain Forest, Norfolk—North Forty Tract<sup class="reference" id="cite_ref-ogEast_15-20"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005161874256896000♠"></span>40 acres (16 ha)<sup class="reference" id="cite_ref-ogEast_15-21"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Tsuga" title="Tsuga">Hemlock</a>, <a class="mw-redirect" href="/wiki/Hardwoods" title="Hardwoods">Hardwoods</a>, White Pine<sup class="reference" id="cite_ref-ogEast_15-22"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Connecticut" title="Connecticut">Connecticut</a>
     </td>
     <td>Great Mountain Forest, Norfolk—Bigelow Pond Site<sup class="reference" id="cite_ref-ogEast_15-23"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7004202342821120000♠"></span>5 acres (2.0 ha)<sup class="reference" id="cite_ref-ogEast_15-24"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Tsuga" title="Tsuga">Hemlock</a><sup class="reference" id="cite_ref-ogEast_15-25"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Connecticut" title="Connecticut">Connecticut</a>
     </td>
     <td>Mount Riga Incorporated, Salisbury<sup class="reference" id="cite_ref-ogEast_15-26"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7004323748513792000♠"></span>8 acres (3.2 ha)<sup class="reference" id="cite_ref-ogEast_15-27"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>White Pine, <a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Yellow_Birch" title="Yellow Birch">Yellow Birch</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a><sup class="reference" id="cite_ref-ogEast_15-28"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Connecticut" title="Connecticut">Connecticut</a>
     </td>
     <td><a href="/wiki/Bear_Mountain_(Connecticut)" title="Bear Mountain (Connecticut)">Bear Mountain, Salisbury</a><sup class="reference" id="cite_ref-ogEast_15-29"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7004202342821120000♠"></span>5 acres (2.0 ha)<sup class="reference" id="cite_ref-ogEast_15-30"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Sweet_Birch" title="Sweet Birch">Sweet Birch</a>, <a class="mw-redirect" href="/wiki/Pitch_Pine" title="Pitch Pine">Pitch Pine</a><sup class="reference" id="cite_ref-ogEast_15-31"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Connecticut" title="Connecticut">Connecticut</a>
     </td>
     <td><a href="/wiki/Belden_Forest" title="Belden Forest">Belden Forest, Simsbury</a><sup class="reference" id="cite_ref-Belden_Forest_26-0"><a href="#cite_note-Belden_Forest-26"><span class="cite-bracket">[</span>26<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005161874256896000♠"></span>40 acres (16 ha)<sup class="reference" id="cite_ref-Belden_Forest_26-1"><a href="#cite_note-Belden_Forest-26"><span class="cite-bracket">[</span>26<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Pinus_strobus" title="Pinus strobus">Eastern White Pine</a><sup class="reference" id="cite_ref-27"><a href="#cite_note-27"><span class="cite-bracket">[</span>27<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Florida" title="Florida">Florida</a>
     </td>
     <td><a href="/wiki/Eglin_Air_Force_Base" title="Eglin Air Force Base">Eglin Air Force Base</a><sup class="reference" id="cite_ref-ogEast_15-32"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007274983893902080♠"></span>6,795 acres (2,750 ha)<sup class="reference" id="cite_ref-ogEast_15-33"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Longleaf_pine" title="Longleaf pine">longleaf pine</a><sup class="reference" id="cite_ref-ogEast_15-34"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Florida" title="Florida">Florida</a>
     </td>
     <td><a href="/wiki/Apalachicola_National_Forest" title="Apalachicola National Forest">Apalachicola National Forest</a><sup class="reference" id="cite_ref-ogEast_15-35"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Southeastern_conifer_forests" title="Southeastern conifer forests">Southeastern conifer forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Pondcypress" title="Pondcypress">Pondcypress</a>, <a class="mw-redirect" href="/wiki/Slash_Pine" title="Slash Pine">Slash Pine</a><sup class="reference" id="cite_ref-ogEast_15-36"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Florida" title="Florida">Florida</a>
     </td>
     <td><a href="/wiki/Big_Cypress_National_Preserve" title="Big Cypress National Preserve">Big Cypress National Preserve</a><sup class="reference" id="cite_ref-ogEast_15-37"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007930776977152000♠"></span>23,000 acres (9,300 ha)<sup class="reference" id="cite_ref-ogEast_15-38"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/South_Florida_rocklands" title="South Florida rocklands">South Florida rocklands</a>, <a href="/wiki/Everglades" title="Everglades">Everglades</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Slash_pine" title="Slash pine">slash pine</a><sup class="reference" id="cite_ref-ogEast_15-39"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Florida" title="Florida">Florida</a>
     </td>
     <td><a href="/wiki/Big_Cypress_National_Preserve" title="Big Cypress National Preserve">Big Cypress National Preserve</a><sup class="reference" id="cite_ref-ogEast_15-40"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008639403314739200♠"></span>158,000 acres (64,000 ha)<sup class="reference" id="cite_ref-ogEast_15-41"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/South_Florida_rocklands" title="South Florida rocklands">South Florida rocklands</a>, <a href="/wiki/Everglades" title="Everglades">Everglades</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Pondcypress" title="Pondcypress">pondcypress</a><sup class="reference" id="cite_ref-ogEast_15-42"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Florida" title="Florida">Florida</a>
     </td>
     <td><a href="/wiki/Tosohatchee_Wildlife_Management_Area" title="Tosohatchee Wildlife Management Area">Tosohatchee Wildlife Management Area</a><sup class="reference" id="cite_ref-ogEast_15-43"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006404685642240000♠"></span>1,000 acres (400 ha)
     </td>
     <td>
     </td>
     <td>Floodplain swamp
     </td></tr>
     <tr>
     <td><a href="/wiki/Florida" title="Florida">Florida</a>
     </td>
     <td><a href="/wiki/Tosohatchee_Wildlife_Management_Area" title="Tosohatchee Wildlife Management Area">Tosohatchee Wildlife Management Area</a><sup class="reference" id="cite_ref-ogEast_15-44"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>40 acres (16 ha)
     </td>
     <td>
     </td>
     <td>Mesic flatwoods
     </td></tr>
     <tr>
     <td><a href="/wiki/Florida" title="Florida">Florida</a>
     </td>
     <td><a href="/wiki/Tosohatchee_Wildlife_Management_Area" title="Tosohatchee Wildlife Management Area">Tosohatchee Wildlife Management Area</a><sup class="reference" id="cite_ref-ogEast_15-45"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>Unknown, up to 1000 acres
     </td>
     <td>
     </td>
     <td>Hydric hammock
     </td></tr>
     <tr>
     <td><a href="/wiki/Georgia_(U.S._state)" title="Georgia (U.S. state)">Georgia</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Chattahoochee_National_Forest" title="Chattahoochee National Forest">Chattahoochee National Forest</a><sup class="reference" id="cite_ref-mnfPlan_28-0"><a href="#cite_note-mnfPlan-28"><span class="cite-bracket">[</span>28<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006140021232215040♠"></span>346 acres (140 ha)<sup class="reference" id="cite_ref-mnfPlan_28-1"><a href="#cite_note-mnfPlan-28"><span class="cite-bracket">[</span>28<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td>River floodplain hardwood, Dry-mesic oak forest, Seasonally wet oak-hardwood woodland<sup class="reference" id="cite_ref-mnfPlan_28-2"><a href="#cite_note-mnfPlan-28"><span class="cite-bracket">[</span>28<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Georgia_(U.S._state)" title="Georgia (U.S. state)">Georgia</a>
     </td>
     <td><a href="/wiki/Fernbank_Forest" title="Fernbank Forest">Fernbank Forest</a>
     </td>
     <td><span data-sort-value="7005263045667456000♠"></span>65 acres (26 ha)
     </td>
     <td><a class="new" href="/w/index.php?title=Piedmont_Hardwood_Forest&amp;action=edit&amp;redlink=1" title="Piedmont Hardwood Forest (page does not exist)">Piedmont Hardwood Forest</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Tulip_Poplar" title="Tulip Poplar">Tulip Poplar</a> – <a href="/wiki/Oak" title="Oak">Oak</a> – <a href="/wiki/Hickory" title="Hickory">Hickory</a><sup class="noprint Inline-Template Template-Fact" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Citation_needed" title="Wikipedia:Citation needed"><span title="This claim needs references to reliable sources. (January 2023)">citation needed</span></a></i>]</sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Georgia_(U.S._state)" title="Georgia (U.S. state)">Georgia</a>
     </td>
     <td>Big Trees Forest Preserve
     </td>
     <td>30 acres (12 ha)
     </td>
     <td><a class="new" href="/w/index.php?title=Piedmont_Hardwood_Forest&amp;action=edit&amp;redlink=1" title="Piedmont Hardwood Forest (page does not exist)">Piedmont Hardwood Forest</a>
     </td>
     <td>oak-hickory-pine forest<sup class="reference" id="cite_ref-29"><a href="#cite_note-29"><span class="cite-bracket">[</span>29<span class="cite-bracket">]</span></a></sup><sup class="noprint Inline-Template" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Citing_sources#What_information_to_include" title="Wikipedia:Citing sources"><span title="A complete citation is needed. (January 2023)">full citation needed</span></a></i>]</sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Illinois" title="Illinois">Illinois</a>
     </td>
     <td><a href="/wiki/Shawnee_National_Forest" title="Shawnee National Forest">Shawnee National Forest</a><sup class="reference" id="cite_ref-ogEast_15-46"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007113311979827200♠"></span>2,800 acres (1,100 ha)<sup class="reference" id="cite_ref-ogEast_15-47"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Post_oak" title="Post oak">post oak</a> – <a class="mw-redirect" href="/wiki/Blackjack_oak" title="Blackjack oak">blackjack oak</a><sup class="reference" id="cite_ref-ogEast_15-48"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Illinois" title="Illinois">Illinois</a>
     </td>
     <td><a href="/wiki/Cache_River_State_Natural_Area" title="Cache River State Natural Area">Cache River State Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-49"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006647497027584000♠"></span>1,600 acres (650 ha)<sup class="reference" id="cite_ref-ogEast_15-50"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Illinois" title="Illinois">Illinois</a>
     </td>
     <td><a href="/wiki/Cypress_Creek_National_Wildlife_Refuge" title="Cypress Creek National Wildlife Refuge">Cypress Creek National Wildlife Refuge</a><sup class="reference" id="cite_ref-ogEast_15-51"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006202342821120000♠"></span>500 acres (200 ha)<sup class="reference" id="cite_ref-ogEast_15-52"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Illinois" title="Illinois">Illinois</a>
     </td>
     <td><a href="/wiki/Beall_Woods_State_Park" title="Beall Woods State Park">Beall Woods State Park</a><sup class="reference" id="cite_ref-ogEast_15-53"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006133141576296960♠"></span>329 acres (133 ha)<sup class="reference" id="cite_ref-ogEast_15-54"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Indiana" title="Indiana">Indiana</a>
     </td>
     <td><a href="/wiki/Hoosier_National_Forest" title="Hoosier National Forest">Hoosier National Forest</a><sup class="reference" id="cite_ref-ogEast_15-55"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006157827400473600♠"></span>390 acres (160 ha)<sup class="reference" id="cite_ref-ogEast_15-56"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Post_Oak" title="Post Oak">Post Oak</a><sup class="reference" id="cite_ref-ogEast_15-57"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Indiana" title="Indiana">Indiana</a>
     </td>
     <td>Douglas Woods<sup class="reference" id="cite_ref-Douglas_Woods_30-0"><a href="#cite_note-Douglas_Woods-30"><span class="cite-bracket">[</span>30<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006161874256896000♠"></span>400 acres (160 ha)<sup class="reference" id="cite_ref-Douglas_Woods_30-1"><a href="#cite_note-Douglas_Woods-30"><span class="cite-bracket">[</span>30<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Silver_Maple" title="Silver Maple">Silver Maple</a>, <a href="/wiki/Oak" title="Oak">Oak</a>, <a href="/wiki/Hickory" title="Hickory">Hickory</a><sup class="reference" id="cite_ref-Douglas_Woods_30-2"><a href="#cite_note-Douglas_Woods-30"><span class="cite-bracket">[</span>30<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Indiana" title="Indiana">Indiana</a>
     </td>
     <td><a href="/wiki/Wesselman_Woods_Nature_Preserve" title="Wesselman Woods Nature Preserve">Wesselman Woods</a>
     </td>
     <td><span data-sort-value="7005809371284480000♠"></span>200 acres (81 ha)
     </td>
     <td><a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td>Sugar Maple, Tulip Tree, Oak
     </td></tr>
     <tr>
     <td><a href="/wiki/Indiana" title="Indiana">Indiana</a>
     </td>
     <td><a href="/wiki/Pioneer_Mothers_Memorial_Forest" title="Pioneer Mothers Memorial Forest">Pioneer Mothers Memorial Forest</a><sup class="reference" id="cite_ref-pioneerMothers_31-0"><a href="#cite_note-pioneerMothers-31"><span class="cite-bracket">[</span>31<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005356123365171200♠"></span>88 acres (36 ha)<sup class="reference" id="cite_ref-pioneerMothers_31-1"><a href="#cite_note-pioneerMothers-31"><span class="cite-bracket">[</span>31<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td>Oak
     </td></tr>
     <tr>
     <td><a href="/wiki/Indiana" title="Indiana">Indiana</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Ginn_Woods&amp;action=edit&amp;redlink=1" title="Ginn Woods (page does not exist)">Ginn Woods</a><sup class="reference" id="cite_ref-ginnwoods_32-0"><a href="#cite_note-ginnwoods-32"><span class="cite-bracket">[</span>32<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005651543884006400♠"></span>161 acres (65 ha)<sup class="reference" id="cite_ref-ginnwoods_32-1"><a href="#cite_note-ginnwoods-32"><span class="cite-bracket">[</span>32<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Indiana" title="Indiana">Indiana</a>
     </td>
     <td><a href="/wiki/Meltzer_Woods" title="Meltzer Woods">Meltzer Woods</a><sup class="reference" id="cite_ref-meltzerwoods_33-0"><a href="#cite_note-meltzerwoods-33"><span class="cite-bracket">[</span>33<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005194249108275200♠"></span>48 acres (19 ha)<sup class="reference" id="cite_ref-ginnwoods_32-2"><a href="#cite_note-ginnwoods-32"><span class="cite-bracket">[</span>32<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Bur_oak" title="Bur oak">Bur oak</a>, <a href="/wiki/Fraxinus_nigra" title="Fraxinus nigra">Black ash</a>, <a class="mw-redirect" href="/wiki/Swamp_white_oak" title="Swamp white oak">Swamp white oak</a>, <a href="/wiki/Beech" title="Beech">Beech</a>, <a href="/wiki/Maple" title="Maple">Maples</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Indiana" title="Indiana">Indiana</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Bicentennial_Woods&amp;action=edit&amp;redlink=1" title="Bicentennial Woods (page does not exist)">Bicentennial Woods</a><sup class="reference" id="cite_ref-bicentennialwoods_34-0"><a href="#cite_note-bicentennialwoods-34"><span class="cite-bracket">[</span>34<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005319701657369600♠"></span>79 acres (32 ha)<sup class="reference" id="cite_ref-bicentennialwoods_34-1"><a href="#cite_note-bicentennialwoods-34"><span class="cite-bracket">[</span>34<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td><a href="/wiki/Oak" title="Oak">Oaks</a>, <a href="/wiki/Maple" title="Maple">Maples</a>, <a href="/wiki/Sycamore" title="Sycamore">Sycamores</a>, <a href="/wiki/Sassafras" title="Sassafras">Sassafras</a>, <a class="mw-redirect" href="/wiki/Slippery_elm" title="Slippery elm">Slippery elm</a> and <a class="mw-redirect" href="/wiki/Flowering_dogwood" title="Flowering dogwood">Flowering dogwood</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Kansas" title="Kansas">Kansas</a>
     </td>
     <td><a href="/wiki/Fort_Leavenworth" title="Fort Leavenworth">Fort Leavenworth</a><sup class="reference" id="cite_ref-ogEast_15-58"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006404685642240000♠"></span>1,000 acres (400 ha)<sup class="reference" id="cite_ref-ogEast_15-59"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Central_forest-grasslands_transition" title="Central forest-grasslands transition">Central forest-grasslands transition</a>
     </td>
     <td>Eastern floodplain<sup class="reference" id="cite_ref-ogEast_15-60"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Kentucky" title="Kentucky">Kentucky</a>
     </td>
     <td><a href="/wiki/Blanton_Forest" title="Blanton Forest">Blanton Forest</a><sup class="reference" id="cite_ref-ogEast_15-61"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006906091152975360♠"></span>2,239 acres (906 ha)<sup class="reference" id="cite_ref-ogEast_15-62"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Kentucky" title="Kentucky">Kentucky</a>
     </td>
     <td>Lilley Cornett Woods<sup class="reference" id="cite_ref-ogEast_15-63"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006101980781844480♠"></span>252 acres (102 ha)<sup class="reference" id="cite_ref-ogEast_15-64"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Maine" title="Maine">Maine</a>
     </td>
     <td><a href="/wiki/Baxter_State_Park" title="Baxter State Park">Baxter State Park</a><sup class="reference" id="cite_ref-ogEast_15-65"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007934581022189056♠"></span>23,094 acres (9,346 ha)<sup class="reference" id="cite_ref-ogEast_15-66"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Balsam_Fir" title="Balsam Fir">Balsam Fir</a><sup class="reference" id="cite_ref-ogEast_15-67"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Maine" title="Maine">Maine</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Mahoosuc_Mountains_Ecological_Reserve&amp;action=edit&amp;redlink=1" title="Mahoosuc Mountains Ecological Reserve (page does not exist)">Mahoosuc Mountains Ecological Reserve</a><sup class="reference" id="cite_ref-ogEast_15-68"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006989051709634560♠"></span>2,444 acres (989 ha)<sup class="reference" id="cite_ref-ogEast_15-69"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Balsam_Fir" title="Balsam Fir">Balsam Fir</a><sup class="reference" id="cite_ref-ogEast_15-70"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Maine" title="Maine">Maine</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Bigelow_Mountain_Ecological_Reserve&amp;action=edit&amp;redlink=1" title="Bigelow Mountain Ecological Reserve (page does not exist)">Bigelow Mountain Ecological Reserve</a><sup class="reference" id="cite_ref-ogEast_15-71"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007125452549094400♠"></span>3,100 acres (1,300 ha)<sup class="reference" id="cite_ref-ogEast_15-72"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Balsam_Fir" title="Balsam Fir">Balsam Fir</a><sup class="reference" id="cite_ref-ogEast_15-73"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Maine" title="Maine">Maine</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Big_Reed_Forest_Preserve&amp;action=edit&amp;redlink=1" title="Big Reed Forest Preserve (page does not exist)">Big Reed Forest Preserve</a><sup class="reference" id="cite_ref-ogEast_15-74"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007202342821120000♠"></span>5,000 acres (2,000 ha) or less
     </td>
     <td>
     </td>
     <td>northern hardwoods, spruce-fir, rich woods, and cedar swamps
     </td></tr>
     <tr>
     <td><a href="/wiki/Maryland" title="Maryland">Maryland</a>
     </td>
     <td><a href="/wiki/Belt_Woods" title="Belt Woods">Belt Woods</a><sup class="reference" id="cite_ref-ogEast_15-75"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005174014826163200♠"></span>43 acres (17 ha)<sup class="reference" id="cite_ref-ogEast_15-76"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Quercus_alba" title="Quercus alba">white oak</a> – <a class="mw-redirect" href="/wiki/Tulip_poplar" title="Tulip poplar">tulip poplar</a><sup class="reference" id="cite_ref-ogEast_15-77"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Maryland" title="Maryland">Maryland</a>
     </td>
     <td><a href="/wiki/Swallow_Falls_State_Park" title="Swallow Falls State Park">Swallow Falls State Park</a> ("Hemlock Grove")<sup class="reference" id="cite_ref-MarylandSierraClub_35-0"><a href="#cite_note-MarylandSierraClub-35"><span class="cite-bracket">[</span>35<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005157827400473600♠"></span>39 acres (16 ha)<sup class="reference" id="cite_ref-MarylandSierraClub_35-1"><a href="#cite_note-MarylandSierraClub-35"><span class="cite-bracket">[</span>35<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Appalachian_mixed_mesophytic_forests" title="Appalachian mixed mesophytic forests">Appalachian mixed mesophytic forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_hemlock" title="Eastern hemlock">eastern hemlock</a> – <a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">white pine</a><sup class="reference" id="cite_ref-MarylandSierraClub_35-2"><a href="#cite_note-MarylandSierraClub-35"><span class="cite-bracket">[</span>35<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Maryland" title="Maryland">Maryland</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Potomac-Garrett_State_Forest" title="Potomac-Garrett State Forest">Potomac-Garrett State Forest</a> ("<a href="/wiki/Backbone_Mountain#Notable_features" title="Backbone Mountain">Crabtree Woods</a>")<sup class="reference" id="cite_ref-PotomacGarrett_36-0"><a href="#cite_note-PotomacGarrett-36"><span class="cite-bracket">[</span>36<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006202342821120000♠"></span>500 acres (200 ha)<sup class="reference" id="cite_ref-PotomacGarrett_36-1"><a href="#cite_note-PotomacGarrett-36"><span class="cite-bracket">[</span>36<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Appalachian_mixed_mesophytic_forests" title="Appalachian mixed mesophytic forests">Appalachian mixed mesophytic forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Sugar_maple" title="Sugar maple">sugar maple</a> – <a href="/wiki/Quercus_rubra" title="Quercus rubra">red oak</a> – <a href="/wiki/Tilia_americana" title="Tilia americana">basswood</a> – <a href="/wiki/Magnolia_acuminata" title="Magnolia acuminata">cucumber tree</a><sup class="reference" id="cite_ref-PotomacGarrett_36-2"><a href="#cite_note-PotomacGarrett-36"><span class="cite-bracket">[</span>36<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Massachusetts" title="Massachusetts">Massachusetts</a>
     </td>
     <td><a href="/wiki/Mohawk_Trail_State_Forest" title="Mohawk Trail State Forest">Mohawk Trail State Forest</a><sup class="reference" id="cite_ref-ogEast_15-78"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006247667613050880♠"></span>612 acres (248 ha)<sup class="reference" id="cite_ref-ogEast_15-79"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_hardwood" title="Northern hardwood">northern hardwood</a><sup class="reference" id="cite_ref-ogEast_15-80"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Massachusetts" title="Massachusetts">Massachusetts</a>
     </td>
     <td><a href="/wiki/Ice_Glen" title="Ice Glen">Ice Glen</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_hardwood" title="Northern hardwood">northern hardwood</a><sup class="reference" id="cite_ref-cjb_37-0"><a href="#cite_note-cjb-37"><span class="cite-bracket">[</span>37<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Massachusetts" title="Massachusetts">Massachusetts</a>
     </td>
     <td><a href="/wiki/Monroe_State_Forest" title="Monroe State Forest">Monroe State Forest</a><sup class="reference" id="cite_ref-ogEast_15-81"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006110479180331520♠"></span>273 acres (110 ha)<sup class="reference" id="cite_ref-ogEast_15-82"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_hardwood" title="Northern hardwood">northern hardwood</a><sup class="reference" id="cite_ref-ogEast_15-83"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Massachusetts" title="Massachusetts">Massachusetts</a>
     </td>
     <td><a href="/wiki/Mount_Everett_State_Reservation" title="Mount Everett State Reservation">Mount Everett State Reservation</a><sup class="reference" id="cite_ref-ogEast_15-84"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006214483390387200♠"></span>530 acres (210 ha)<sup class="reference" id="cite_ref-ogEast_15-85"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_hardwood" title="Northern hardwood">northern hardwood</a><sup class="reference" id="cite_ref-ogEast_15-86"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Massachusetts" title="Massachusetts">Massachusetts</a>
     </td>
     <td><a href="/wiki/Mount_Greylock" title="Mount Greylock">Mount Greylock</a><sup class="reference" id="cite_ref-ogEast_15-87"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006224600531443200♠"></span>555 acres (225 ha)<sup class="reference" id="cite_ref-ogEast_15-88"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_hardwood" title="Northern hardwood">northern hardwood</a><sup class="reference" id="cite_ref-ogEast_15-89"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Massachusetts" title="Massachusetts">Massachusetts</a>
     </td>
     <td><a href="/wiki/Mount_Wachusett" title="Mount Wachusett">Mount Wachusett</a><sup class="reference" id="cite_ref-ogEast_15-90"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005890308412928000♠"></span>220 acres (89 ha)<sup class="reference" id="cite_ref-ogEast_15-91"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_hardwood" title="Northern hardwood">northern hardwood</a><sup class="reference" id="cite_ref-ogEast_15-92"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Massachusetts" title="Massachusetts">Massachusetts</a>
     </td>
     <td><a href="/wiki/Mount_Washington_State_Forest" title="Mount Washington State Forest">Mount Washington State Forest</a><sup class="reference" id="cite_ref-ogEast_15-93"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006121405692672000♠"></span>300 acres (120 ha)<sup class="reference" id="cite_ref-ogEast_15-94"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_hardwood" title="Northern hardwood">northern hardwood</a><sup class="reference" id="cite_ref-ogEast_15-95"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Massachusetts" title="Massachusetts">Massachusetts</a>
     </td>
     <td><a href="/wiki/William_Cullen_Bryant_Homestead" title="William Cullen Bryant Homestead">William Cullen Bryant Homestead</a><sup class="reference" id="cite_ref-38"><a href="#cite_note-38"><span class="cite-bracket">[</span>38<span class="cite-bracket">]</span></a></sup><sup class="reference" id="cite_ref-39"><a href="#cite_note-39"><span class="cite-bracket">[</span>39<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005441107350041600♠"></span>109 acres (44 ha)
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a href="/wiki/Prunus_serotina" title="Prunus serotina">Black Cherry</a>, <a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Michigan" title="Michigan">Michigan</a>
     </td>
     <td><a href="/wiki/Hartwick_Pines_State_Park" title="Hartwick Pines State Park">Hartwick Pines State Park</a><sup class="reference" id="cite_ref-ogEast_15-96"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005198295964697600♠"></span>49 acres (20 ha)<sup class="reference" id="cite_ref-HartwickPines_40-0"><a href="#cite_note-HartwickPines-40"><span class="cite-bracket">[</span>40<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Western_Great_Lakes_forests" title="Western Great Lakes forests">Western Great Lakes forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/Red_Pine" title="Red Pine">Red Pine</a>, <a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a href="/wiki/Beech" title="Beech">Beech</a>, <a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a><sup class="reference" id="cite_ref-ogEast_15-97"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Michigan" title="Michigan">Michigan</a>
     </td>
     <td><a href="/wiki/Porcupine_Mountains" title="Porcupine Mountains">Porcupine Mountains</a><sup class="reference" id="cite_ref-ogEast_15-98"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008125452549094400♠"></span>31,000 acres (13,000 ha)<sup class="reference" id="cite_ref-ogEast_15-99"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Western_Great_Lakes_forests" title="Western Great Lakes forests">Western Great Lakes forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_hardwood" title="Northern hardwood">northern hardwood</a><sup class="reference" id="cite_ref-ogEast_15-100"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Michigan" title="Michigan">Michigan</a>
     </td>
     <td><a href="/wiki/Sylvania_Wilderness" title="Sylvania Wilderness">Sylvania Wilderness</a><sup class="reference" id="cite_ref-ogEast_15-101"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007607028463360000♠"></span>15,000 acres (6,100 ha)<sup class="reference" id="cite_ref-ogEast_15-102"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Western_Great_Lakes_forests" title="Western Great Lakes forests">Western Great Lakes forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_hardwood" title="Northern hardwood">northern hardwood</a><sup class="reference" id="cite_ref-ogEast_15-103"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Michigan" title="Michigan">Michigan</a>
     </td>
     <td><a href="/wiki/Warren_Woods_State_Park" title="Warren Woods State Park">Warren Woods</a>
     </td>
     <td><span data-sort-value="7005809371284480000♠"></span>200 acres (81 ha)
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Beech-Maple_forest" title="Beech-Maple forest">Beech-Maple forest</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Minnesota" title="Minnesota">Minnesota</a>
     </td>
     <td><a href="/wiki/Boundary_Waters" title="Boundary Waters">Boundary Waters</a><sup class="reference" id="cite_ref-ogEast_15-104"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009162278942538240♠"></span>401,000 acres (162,000 ha)<sup class="reference" id="cite_ref-ogEast_15-105"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Western_Great_Lakes_forests" title="Western Great Lakes forests">Western Great Lakes forests</a>
     </td>
     <td>white pine, red pine, fir/birch, <a href="/wiki/Jack_pine" title="Jack pine">jack pine</a> – <a class="mw-redirect" href="/wiki/Black_spruce" title="Black spruce">black spruce</a>, maple, aspen<sup class="reference" id="cite_ref-ogEast_15-106"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Minnesota" title="Minnesota">Minnesota</a>
     </td>
     <td><a href="/wiki/Keeley_Creek_Natural_Area" title="Keeley Creek Natural Area">Keeley Creek Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-107"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006364217078016000♠"></span>900 acres (360 ha)<sup class="reference" id="cite_ref-ogEast_15-108"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Western_Great_Lakes_forests" title="Western Great Lakes forests">Western Great Lakes forests</a>
     </td>
     <td>bog and upland<sup class="reference" id="cite_ref-ogEast_15-109"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Minnesota" title="Minnesota">Minnesota</a>
     </td>
     <td><a href="/wiki/Itasca_State_Park" title="Itasca State Park">Itasca State Park</a><sup class="reference" id="cite_ref-ogEast_15-110"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007165678301933056♠"></span>4,094 acres (1,657 ha)<sup class="reference" id="cite_ref-ogEast_15-111"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Western_Great_Lakes_forests" title="Western Great Lakes forests">Western Great Lakes forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/Red_Pine" title="Red Pine">Red Pine</a><sup class="reference" id="cite_ref-ogEast_15-112"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Missouri" title="Missouri">Missouri</a>
     </td>
     <td><a href="/wiki/Mark_Twain_National_Forest" title="Mark Twain National Forest">Mark Twain National Forest</a><sup class="reference" id="cite_ref-ogEast_15-113"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008121405692672000♠"></span>30,000 acres (12,000 ha) or less<sup class="reference" id="cite_ref-ogEast_15-114"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Post_Oak" title="Post Oak">Post Oak</a> and <a class="mw-redirect" href="/wiki/Chinkapin_Oak" title="Chinkapin Oak">Chinkapin Oak</a> savanna and flatwoods<sup class="reference" id="cite_ref-ogEast_15-115"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Missouri" title="Missouri">Missouri</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Caney_Mountain&amp;action=edit&amp;redlink=1" title="Caney Mountain (page does not exist)">Caney Mountain</a><sup class="reference" id="cite_ref-ogEast_15-116"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007161874256896000♠"></span>4,000 acres (1,600 ha) or more<sup class="reference" id="cite_ref-ogEast_15-117"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td>post oak savanna<sup class="reference" id="cite_ref-ogEast_15-118"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Hampshire" title="New Hampshire">New Hampshire</a>
     </td>
     <td><a href="/wiki/Great_Gulf" title="Great Gulf">Great Gulf</a><sup class="reference" id="cite_ref-ogEast_15-119"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Hampshire" title="New Hampshire">New Hampshire</a>
     </td>
     <td><a href="/wiki/Crawford_Notch" title="Crawford Notch">Crawford Notch</a><sup class="reference" id="cite_ref-ogEast_15-120"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Hampshire" title="New Hampshire">New Hampshire</a>
     </td>
     <td>The Bowl Research Natural Area<sup class="reference" id="cite_ref-The_Bowl_41-0"><a href="#cite_note-The_Bowl-41"><span class="cite-bracket">[</span>41<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006206389677542400♠"></span>510 acres (210 ha)
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Red_Spruce" title="Red Spruce">Red Spruce</a>, <a class="mw-redirect" href="/wiki/Balsam_fir" title="Balsam fir">Balsam fir</a>, <a href="/wiki/Beech" title="Beech">Beech</a>, <a class="mw-redirect" href="/wiki/Yellow_birch" title="Yellow birch">Yellow birch</a>, <a class="mw-redirect" href="/wiki/Sugar_maple" title="Sugar maple">Sugar maple</a>, <a class="mw-redirect" href="/wiki/Paper_birch" title="Paper birch">Paper birch</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Hampshire" title="New Hampshire">New Hampshire</a>
     </td>
     <td><a href="/wiki/Hemenway_State_Forest" title="Hemenway State Forest">Hemenway State Forest</a><sup class="reference" id="cite_ref-hemenway_42-0"><a href="#cite_note-hemenway-42"><span class="cite-bracket">[</span>42<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005546325617024000♠"></span>135 acres (55 ha)<sup class="reference" id="cite_ref-hemenway_42-1"><a href="#cite_note-hemenway-42"><span class="cite-bracket">[</span>42<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a><sup class="reference" id="cite_ref-hemenway_42-2"><a href="#cite_note-hemenway-42"><span class="cite-bracket">[</span>42<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Hampshire" title="New Hampshire">New Hampshire</a>
     </td>
     <td>The Bowl Research Natural Area<sup class="reference" id="cite_ref-The_Bowl_41-1"><a href="#cite_note-The_Bowl-41"><span class="cite-bracket">[</span>41<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006206389677542400♠"></span>510 acres (210 ha)
     </td>
     <td><a class="mw-redirect" href="/wiki/New_England-Acadian_forests" title="New England-Acadian forests">New England-Acadian forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Red_Spruce" title="Red Spruce">Red Spruce</a>, <a class="mw-redirect" href="/wiki/Balsam_fir" title="Balsam fir">Balsam fir</a>, <a href="/wiki/Beech" title="Beech">Beech</a>, <a class="mw-redirect" href="/wiki/Yellow_birch" title="Yellow birch">Yellow birch</a>, <a class="mw-redirect" href="/wiki/Sugar_maple" title="Sugar maple">Sugar maple</a>, <a class="mw-redirect" href="/wiki/Paper_birch" title="Paper birch">Paper birch</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Jersey" title="New Jersey">New Jersey</a>
     </td>
     <td><a href="/wiki/Saddler%27s_Woods" title="Saddler's Woods">Saddler's Woods</a><sup class="reference" id="cite_ref-ogEast_15-121"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005101171410560000♠"></span>25 acres (10 ha)<sup class="reference" id="cite_ref-ogEast_15-122"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northeastern_coastal_forests" title="Northeastern coastal forests">Northeastern coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Black_Oak" title="Eastern Black Oak">Eastern Black Oak</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a class="mw-redirect" href="/wiki/Tulip_Poplar" title="Tulip Poplar">Tulip Poplar</a>, <a class="mw-redirect" href="/wiki/Red_Maple" title="Red Maple">Red Maple</a><sup class="reference" id="cite_ref-ogEast_15-123"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Jersey" title="New Jersey">New Jersey</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Bear_Swamp,_New_Jersey" title="Bear Swamp, New Jersey">Bear Swamp</a><sup class="reference" id="cite_ref-ogEast_15-124"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005870074130816000♠"></span>215 acres (87 ha)<sup class="reference" id="cite_ref-ogEast_15-125"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Atlantic_coastal_pine_barrens" title="Atlantic coastal pine barrens">Atlantic coastal pine barrens</a>
     </td>
     <td><a href="/wiki/Nyssa_sylvatica" title="Nyssa sylvatica">Black Gum</a>, <a class="mw-redirect" href="/wiki/American_Sweetgum" title="American Sweetgum">American Sweetgum</a>, <a class="mw-redirect" href="/wiki/Red_Maple" title="Red Maple">Red Maple</a>, <a class="mw-redirect" href="/wiki/Sweetbay_Magnolia" title="Sweetbay Magnolia">Sweetbay Magnolia</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a class="mw-redirect" href="/wiki/Swamp_White_Oak" title="Swamp White Oak">Swamp White Oak</a>, <a class="mw-redirect" href="/wiki/American_Holly" title="American Holly">American Holly</a><sup class="reference" id="cite_ref-ogEast_15-126"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Jersey" title="New Jersey">New Jersey</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/William_L._Hutcheson_Memorial_Forest" title="William L. Hutcheson Memorial Forest">William L. Hutcheson Memorial Forest</a><sup class="reference" id="cite_ref-ogEast_15-127"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005263045667456000♠"></span>65 acres (26 ha)<sup class="reference" id="cite_ref-ogEast_15-128"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northeastern_coastal_forests" title="Northeastern coastal forests">Northeastern coastal forests</a>
     </td>
     <td><a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/Eastern_Black_Oak" title="Eastern Black Oak">Eastern Black Oak</a>, <a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a><sup class="reference" id="cite_ref-ogEast_15-129"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Jersey" title="New Jersey">New Jersey</a>
     </td>
     <td><a href="/wiki/Stokes_State_Forest" title="Stokes State Forest">Tillman Ravine</a><sup class="reference" id="cite_ref-ogEast_15-130"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005101171410560000♠"></span>25 acres (10 ha)<sup class="reference" id="cite_ref-ogEast_15-131"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a><sup class="reference" id="cite_ref-ogEast_15-132"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_Jersey" title="New Jersey">New Jersey</a>
     </td>
     <td><a href="/wiki/Clayton_Park_(New_Jersey)" title="Clayton Park (New Jersey)">Clayton Park</a><sup class="reference" id="cite_ref-clayton_43-0"><a href="#cite_note-clayton-43"><span class="cite-bracket">[</span>43<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005315654800947200♠"></span>78 acres (32 ha)<sup class="reference" id="cite_ref-claytonwebsite_44-0"><a href="#cite_note-claytonwebsite-44"><span class="cite-bracket">[</span>44<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northeastern_coastal_forests" title="Northeastern coastal forests">Northeastern coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>,<a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a>, <a href="/wiki/Betula_populifolia" title="Betula populifolia">Gray birch</a><sup class="reference" id="cite_ref-clayton_43-1"><a href="#cite_note-clayton-43"><span class="cite-bracket">[</span>43<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_York_(state)" title="New York (state)">New York</a>
     </td>
     <td><a href="/wiki/Catskill_Mountains" title="Catskill Mountains">Catskill Mountains</a><sup class="reference" id="cite_ref-ogEast_15-133"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008242811385344000♠"></span>60,000 acres (24,000 ha) or more<sup class="reference" id="cite_ref-ogEast_15-134"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_York_(state)" title="New York (state)">New York</a>
     </td>
     <td><a href="/wiki/Adirondack_Mountains" title="Adirondack Mountains">Adirondack Mountains</a><sup class="reference" id="cite_ref-ogEast_15-135"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008607028463360000♠"></span>150,000 acres (61,000 ha) or more<sup class="reference" id="cite_ref-ogEast_15-136"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_forest-boreal_transition" title="Eastern forest-boreal transition">Eastern forest-boreal transition</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_York_(state)" title="New York (state)">New York</a>
     </td>
     <td><a href="/wiki/Thain_Family_Forest" title="Thain Family Forest">Thain Family Forest</a><sup class="reference" id="cite_ref-ogEast_15-137"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005202342821120000♠"></span>50 acres (20 ha) or more<sup class="reference" id="cite_ref-ogEast_15-138"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northern_hardwood_forest" title="Northern hardwood forest">Northern hardwood forest</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/New_York_(state)" title="New York (state)">New York</a>
     </td>
     <td><a href="/wiki/Mianus_River_Gorge" title="Mianus River Gorge">Mianus River Gorge Preserve</a><sup class="reference" id="cite_ref-:0_45-0"><a href="#cite_note-:0-45"><span class="cite-bracket">[</span>45<span class="cite-bracket">]</span></a></sup><sup class="reference" id="cite_ref-46"><a href="#cite_note-46"><span class="cite-bracket">[</span>46<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>60 - 100 acres (24 - 40.5 ha)<sup class="reference" id="cite_ref-47"><a href="#cite_note-47"><span class="cite-bracket">[</span>47<span class="cite-bracket">]</span></a></sup><sup class="reference" id="cite_ref-:0_45-1"><a href="#cite_note-:0-45"><span class="cite-bracket">[</span>45<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Appalachian_hemlock%E2%80%93northern_hardwood_forest" title="Appalachian hemlock–northern hardwood forest">Appalachian hemlock–northern hardwood forest</a>
     </td>
     <td>Eastern hemlock-beech forest
     </td></tr>
     <tr>
     <td><a href="/wiki/North_Carolina" title="North Carolina">North Carolina</a>
     </td>
     <td><a href="/wiki/Great_Smoky_Mountains" title="Great Smoky Mountains">Great Smoky Mountains</a><sup class="reference" id="cite_ref-ogEast_15-139"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008756762150988800♠"></span>187,000 acres (76,000 ha)<sup class="reference" id="cite_ref-ogEast_15-140"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/North_Carolina" title="North Carolina">North Carolina</a>
     </td>
     <td><a href="/wiki/Nantahala_National_Forest" title="Nantahala National Forest">Nantahala National Forest</a><sup class="reference" id="cite_ref-ogEast_15-141"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008124643177809920♠"></span>30,800 acres (12,500 ha)<sup class="reference" id="cite_ref-ogEast_15-142"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/North_Carolina" title="North Carolina">North Carolina</a>
     </td>
     <td><a href="/wiki/Pisgah_National_Forest" title="Pisgah National Forest">Pisgah National Forest</a><sup class="reference" id="cite_ref-ogEast_15-143"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008188583509283840♠"></span>46,600 acres (18,900 ha)<sup class="reference" id="cite_ref-ogEast_15-144"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/North_Carolina" title="North Carolina">North Carolina</a>
     </td>
     <td><a href="/wiki/Croatan_National_Forest" title="Croatan National Forest">Croatan National Forest</a><sup class="reference" id="cite_ref-ogEast_15-145"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007404685642240000♠"></span>10,000 acres (4,000 ha)<sup class="reference" id="cite_ref-ogEast_15-146"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Middle_Atlantic_coastal_forests" title="Middle Atlantic coastal forests">Middle Atlantic coastal forests</a>
     </td>
     <td><a href="/wiki/Pocosin" title="Pocosin">pocosin</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a href="/wiki/Goll_Woods_State_Nature_Preserve" title="Goll Woods State Nature Preserve">Goll Woods State Nature Preserve</a><sup class="reference" id="cite_ref-ogEast_15-147"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005566559899136000♠"></span>140 acres (57 ha)<sup class="reference" id="cite_ref-ogEast_15-148"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Fowler_Woods_State_Nature_Preserve&amp;action=edit&amp;redlink=1" title="Fowler Woods State Nature Preserve (page does not exist)">Fowler Woods State Nature Preserve</a><sup class="reference" id="cite_ref-ogEast_15-149"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005202342821120000♠"></span>50 acres (20 ha)<sup class="reference" id="cite_ref-ogEast_15-150"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Crall_Woods_National_Natural_Landmark&amp;action=edit&amp;redlink=1" title="Crall Woods National Natural Landmark (page does not exist)">Crall Woods National Natural Landmark</a><sup class="reference" id="cite_ref-ogEast_15-151"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005161874256896000♠"></span>40 acres (16 ha)<sup class="reference" id="cite_ref-ogEast_15-152"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a href="/wiki/Dysart_Woods" title="Dysart Woods">Dysart Woods</a><sup class="reference" id="cite_ref-ogEast_15-153"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005230670816076800♠"></span>57 acres (23 ha)<sup class="reference" id="cite_ref-ogEast_15-154"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Appalachian_mixed_mesophytic_forests" title="Appalachian mixed mesophytic forests">Appalachian mixed mesophytic forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td>Hawk Woods in <a class="mw-redirect" href="/wiki/Riddle_State_Nature_Preserve" title="Riddle State Nature Preserve">Riddle State Nature Preserve</a>
     </td>
     <td><span data-sort-value="7005428966780774400♠"></span>106 acres (43 ha)
     </td>
     <td><a href="/wiki/Appalachian_mixed_mesophytic_forests" title="Appalachian mixed mesophytic forests">Appalachian mixed mesophytic forests</a><sup class="noprint Inline-Template Template-Fact" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Citation_needed" title="Wikipedia:Citation needed"><span title="This claim needs references to reliable sources. (January 2023)">citation needed</span></a></i>]</sup>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td>Morgan Sisters Woods in <a href="/wiki/Wayne_National_Forest" title="Wayne National Forest">Wayne National Forest</a><sup class="reference" id="cite_ref-ogEast_15-155"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005809371284480000♠"></span>200 acres (81 ha)<sup class="reference" id="cite_ref-ogEast_15-156"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Appalachian_mixed_mesophytic_forests" title="Appalachian mixed mesophytic forests">Appalachian mixed mesophytic forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a href="/wiki/California_Woods_Nature_Preserve" title="California Woods Nature Preserve">California Woods Nature Preserve</a><sup class="reference" id="cite_ref-ogEast_15-157"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005161874256896000♠"></span>40 acres (16 ha)<sup class="reference" id="cite_ref-ogEast_15-158"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>, <a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Caldwell_Park_(Cincinnati)&amp;action=edit&amp;redlink=1" title="Caldwell Park (Cincinnati) (page does not exist)">Caldwell Park (Cincinnati)</a><sup class="reference" id="cite_ref-ogEast_15-159"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005493716483532800♠"></span>122 acres (49 ha) or less<sup class="reference" id="cite_ref-ogEast_15-160"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>, <a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Hueston_Woods_State_Nature_Preserve&amp;action=edit&amp;redlink=1" title="Hueston Woods State Nature Preserve (page does not exist)">Hueston Woods State Nature Preserve</a><sup class="reference" id="cite_ref-ogEast_15-161"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005667731309696000♠"></span>165–200 acres (67–81 ha)<sup class="reference" id="cite_ref-ogEast_15-162"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a href="/wiki/Davey_Woods_State_Nature_Preserve" title="Davey Woods State Nature Preserve">Davey Woods State Nature Preserve</a><sup class="reference" id="cite_ref-ogEast_15-163"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7004607028463360000♠"></span>15–40 acres (6.1–16.2 ha)<sup class="reference" id="cite_ref-ogEast_15-164"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Gross_(Samuel)_Memorial_Woods_State_Nature_Preserve&amp;action=edit&amp;redlink=1" title="Gross (Samuel) Memorial Woods State Nature Preserve (page does not exist)">Gross (Samuel) Memorial Woods State Nature Preserve</a><sup class="reference" id="cite_ref-ogEast_15-165"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005198295964697600♠"></span>49 acres (20 ha)<sup class="reference" id="cite_ref-ogEast_15-166"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Ohio" title="Ohio">Ohio</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Johnson_Woods_State_Nature_Preserve&amp;action=edit&amp;redlink=1" title="Johnson Woods State Nature Preserve (page does not exist)">Johnson Woods State Nature Preserve</a><sup class="reference" id="cite_ref-ogEast_15-167"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005833652423014400♠"></span>206 acres (83 ha)<sup class="reference" id="cite_ref-ogEast_15-168"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Southern_Great_Lakes_forests" title="Southern Great Lakes forests">Southern Great Lakes forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oklahoma" title="Oklahoma">Oklahoma</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Keystone_Ancient_Forest_Preserve&amp;action=edit&amp;redlink=1" title="Keystone Ancient Forest Preserve (page does not exist)">Keystone Ancient Forest Preserve</a><sup class="reference" id="cite_ref-ogEast_15-169"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006526091334912000♠"></span>1,300 acres (530 ha)<sup class="reference" id="cite_ref-ogEast_15-170"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="new" href="/w/index.php?title=Central_forest-grasslands_transition_zone&amp;action=edit&amp;redlink=1" title="Central forest-grasslands transition zone (page does not exist)">Central forest-grasslands transition zone</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Post_Oak" title="Post Oak">Post Oak</a>, <a class="mw-redirect" href="/wiki/Blackjack_Oak" title="Blackjack Oak">Blackjack Oak</a>, <a class="mw-redirect" href="/wiki/Eastern_Redcedar" title="Eastern Redcedar">Eastern Redcedar</a><sup class="reference" id="cite_ref-ogEast_15-171"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Crater_Lake_National_Park" title="Crater Lake National Park">Crater Lake National Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-14"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008202342821120000♠"></span>50,000 acres (20,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-15"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Deschutes_National_Forest" title="Deschutes National Forest">Deschutes National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-16"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009140871072063744♠"></span>348,100 acres (140,900 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-17"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Malheur_National_Forest" title="Malheur National Forest">Malheur National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-18"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009126261920378880♠"></span>312,000 acres (126,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-19"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Mount_Hood_National_Forest" title="Mount Hood National Forest">Mount Hood National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-20"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009139737952265472♠"></span>345,300 acres (139,700 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-21"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Western_Hemlock" title="Western Hemlock">Western Hemlock</a>, <a class="mw-redirect" href="/wiki/Western_Red_Cedar" title="Western Red Cedar">Western Red Cedar</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Ochoco_National_Forest" title="Ochoco National Forest">Ochoco National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-22"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008384451360128000♠"></span>95,000 acres (38,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-23"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Rogue_River-Siskiyou_National_Forest" title="Rogue River-Siskiyou National Forest">Rogue River-Siskiyou National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-24"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009139737952265472♠"></span>345,300 acres (139,700 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-25"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Klamath-Siskiyou_forests" title="Klamath-Siskiyou forests">Klamath-Siskiyou forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Port_Orford_Cedar" title="Port Orford Cedar">Port Orford Cedar</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/Sugar_Pine" title="Sugar Pine">Sugar Pine</a>, <a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/California_Incense_Cedar" title="California Incense Cedar">California Incense Cedar</a>, <a class="mw-redirect" href="/wiki/White_Fir" title="White Fir">White Fir</a>, <a class="mw-redirect" href="/wiki/Red_Fir" title="Red Fir">Red Fir</a>, <a class="mw-redirect" href="/wiki/Mountain_Hemlock" title="Mountain Hemlock">Mountain Hemlock</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Siuslaw_National_Forest" title="Siuslaw National Forest">Siuslaw National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-26"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008136783747077120♠"></span>33,800 acres (13,700 ha) (1993 estimate)<sup class="reference" id="cite_ref-ogCaOrWa_18-27"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Central_Pacific_coastal_forests" title="Central Pacific coastal forests">Central Pacific coastal forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Umatilla_National_Forest" title="Umatilla National Forest">Umatilla National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-28"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008771901440864998♠"></span>190,741 acres (77,190 ha) (1993 estimate)<sup class="reference" id="cite_ref-ogCaOrWa_18-29"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Umpqua_National_Forest" title="Umpqua National Forest">Umpqua National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-30"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009216628224291072♠"></span>535,300 acres (216,600 ha) (1993 estimate)<sup class="reference" id="cite_ref-ogCaOrWa_18-31"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Mountain_Hemlock" title="Mountain Hemlock">Mountain Hemlock</a>, <a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Wallowa-Whitman_National_Forest" title="Wallowa-Whitman National Forest">Wallowa-Whitman National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-32"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008700106161075200♠"></span>173,000 acres (70,000 ha) (1993 estimate)<sup class="reference" id="cite_ref-ogCaOrWa_18-33"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Willamette_National_Forest" title="Willamette National Forest">Willamette National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-34"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009240707020004352♠"></span>594,800 acres (240,700 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-35"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Western_Hemlock" title="Western Hemlock">Western Hemlock</a>, <a class="mw-redirect" href="/wiki/Western_Red_Cedar" title="Western Red Cedar">Western Red Cedar</a>, <a class="mw-redirect" href="/wiki/Bigleaf_Maple" title="Bigleaf Maple">Bigleaf Maple</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Winema_National_Forest" title="Winema National Forest">Winema National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-36"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009288004249755509♠"></span>711,674 acres (288,004 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-37"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Fremont_National_Forest" title="Fremont National Forest">Fremont National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-38"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009222496166103552♠"></span>549,800 acres (222,500 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-39"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Oregon" title="Oregon">Oregon</a>
     </td>
     <td><a href="/wiki/Emigrant_Springs_State_Heritage_Area" title="Emigrant Springs State Heritage Area">Emigrant Springs State Heritage Area</a>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Blue_Mountains_forests" title="Blue Mountains forests">Blue Mountains forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Cook_Forest_State_Park" title="Cook Forest State Park">Cook Forest State Park</a><sup class="reference" id="cite_ref-ogEast_15-172"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006607028463360000♠"></span>1,500–2,000 acres (610–810 ha)<sup class="reference" id="cite_ref-ogEast_15-173"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a href="/wiki/Prunus_serotina" title="Prunus serotina">Black Cherry</a>, <a class="mw-redirect" href="/wiki/Red_Maple" title="Red Maple">Red Maple</a>, <a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a href="/wiki/Fraxinus_americana" title="Fraxinus americana">White Ash</a>, <a class="mw-redirect" href="/wiki/Yellow_Birch" title="Yellow Birch">Yellow Birch</a>, <a href="/wiki/Betula_lenta" title="Betula lenta">Black Birch</a>, <a class="mw-redirect" href="/wiki/Cucumber_Magnolia" title="Cucumber Magnolia">Cucumber Magnolia</a><sup class="reference" id="cite_ref-ogEast_15-174"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Alan_Seeger_Natural_Area" title="Alan Seeger Natural Area">Alan Seeger Natural Area</a><sup class="reference" id="cite_ref-Fergus_48-0"><a href="#cite_note-Fergus-48"><span class="cite-bracket">[</span>48<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006157827400473600♠"></span>390 acres (160 ha)
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Bear_Meadows_Natural_Area" title="Bear Meadows Natural Area">Bear Meadows Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-175"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006129499405516800♠"></span>320 acres (130 ha)<sup class="reference" id="cite_ref-ogEast_15-176"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Black_Spruce" title="Black Spruce">Black Spruce</a>, <a class="mw-redirect" href="/wiki/Balsam_Fir" title="Balsam Fir">Balsam Fir</a> <a href="/wiki/Bog" title="Bog">bog</a><sup class="reference" id="cite_ref-ogEast_15-177"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Rothrock_State_Forest" title="Rothrock State Forest">Detweiler Run Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-178"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005748668438144000♠"></span>185 acres (75 ha)<sup class="reference" id="cite_ref-ogEast_15-179"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a><sup class="reference" id="cite_ref-ogEast_15-180"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Rothrock_State_Forest" title="Rothrock State Forest">Thickhead Mountain Wild Area</a><sup class="reference" id="cite_ref-ogEast_15-181"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005202342821120000♠"></span>50 acres (20 ha)<sup class="reference" id="cite_ref-ogEast_15-182"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Chestnut_Oak" title="Chestnut Oak">Chestnut Oak</a><sup class="reference" id="cite_ref-ogEast_15-183"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Woodbourne_Forest_and_Wildlife_Preserve" title="Woodbourne Forest and Wildlife Preserve">Woodbourne Forest and Wildlife Preserve</a><sup class="reference" id="cite_ref-ogEast_15-184"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005485622770688000♠"></span>120 acres (49 ha)<sup class="reference" id="cite_ref-ogEast_15-185"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Sweet_Birch" title="Sweet Birch">Sweet Birch</a>, <a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a>, <a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a>, <a href="/wiki/Fraxinus_americana" title="Fraxinus americana">White Ash</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a><sup class="reference" id="cite_ref-ogEast_15-186"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Holtwood_Environmental_Preserve" title="Holtwood Environmental Preserve">Holtwood Environmental Preserve</a><sup class="reference" id="cite_ref-ogEast_15-187"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005809371284480000♠"></span>200 acres (81 ha)<sup class="reference" id="cite_ref-ogEast_15-188"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northeastern_coastal_forests" title="Northeastern coastal forests">Northeastern coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Chestnut_Oak" title="Chestnut Oak">Chestnut Oak</a>, <a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Umbrella_Magnolia" title="Umbrella Magnolia">Umbrella Magnolia</a><sup class="reference" id="cite_ref-ogEast_15-189"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Anders_Run_Natural_Area" title="Anders Run Natural Area">Anders Run Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-190"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005202342821120000♠"></span>50 acres (20 ha)<sup class="reference" id="cite_ref-ogEast_15-191"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Cucumber_Magnolia" title="Cucumber Magnolia">Cucumber Magnolia</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a class="mw-redirect" href="/wiki/American_Hornbeam" title="American Hornbeam">American Hornbeam</a>, <a href="/wiki/Prunus_serotina" title="Prunus serotina">Black Cherry</a>, <a href="/wiki/Oak" title="Oak">oak</a><sup class="reference" id="cite_ref-ogEast_15-192"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Buchanan_State_Forest" title="Buchanan State Forest">Sweet Root Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-193"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005258998811033600♠"></span>64 acres (26 ha)<sup class="reference" id="cite_ref-ogEast_15-194"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Sweet_Birch" title="Sweet Birch">Sweet Birch</a>, <a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/American_Basswood" title="American Basswood">American Basswood</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a href="/wiki/Quercus_rubra" title="Quercus rubra">Red Oak</a><sup class="reference" id="cite_ref-ogEast_15-195"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Hearts_Content_Recreation_Area" title="Hearts Content Recreation Area">Hearts Content Recreation Area</a><sup class="reference" id="cite_ref-ogEast_15-196"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005493716483532800♠"></span>122 acres (49 ha)<sup class="reference" id="cite_ref-ogEast_15-197"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a><sup class="reference" id="cite_ref-ogEast_15-198"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Tionesta_Scenic_and_Research_Natural_Areas" title="Tionesta Scenic and Research Natural Areas">Tionesta Scenic and Research Natural Areas</a><sup class="reference" id="cite_ref-ogEast_15-199"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007161874256896000♠"></span>4,000 acres (1,600 ha)<sup class="reference" id="cite_ref-ogEast_15-200"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a><sup class="reference" id="cite_ref-ogEast_15-201"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Allegheny_Islands_Wilderness" title="Allegheny Islands Wilderness">Allegheny Islands Wilderness</a><sup class="reference" id="cite_ref-ogEast_15-202"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005631309601894400♠"></span>156 acres (63 ha)<sup class="reference" id="cite_ref-ogEast_15-203"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Silver_Maple" title="Silver Maple">Silver Maple</a>, <a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a>, <a class="mw-redirect" href="/wiki/American_Sycamore" title="American Sycamore">American Sycamore</a>, <a class="mw-redirect" href="/wiki/Slippery_Elm" title="Slippery Elm">Slippery Elm</a><sup class="reference" id="cite_ref-ogEast_15-204"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Tiadaghton_State_Forest" title="Tiadaghton State Forest">Bark Cabin Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-205"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005295420518835200♠"></span>73 acres (30 ha)<sup class="reference" id="cite_ref-ogEast_15-206"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a>, <a href="/wiki/Fraxinus_americana" title="Fraxinus americana">White Ash</a>, <a class="mw-redirect" href="/wiki/Bigtooth_Aspen" title="Bigtooth Aspen">Bigtooth Aspen</a>, <a href="/wiki/Hickory" title="Hickory">Hickories</a><sup class="reference" id="cite_ref-ogEast_15-207"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Johnson_Run_Natural_Area" title="Johnson Run Natural Area">Johnson Run Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-208"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005105218266982400♠"></span>26–50 acres (11–20 ha)<sup class="reference" id="cite_ref-ogEast_15-209"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a><sup class="reference" id="cite_ref-ogEast_15-210"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Forrest_H._Duttlinger_Natural_Area" title="Forrest H. Duttlinger Natural Area">Forrest H. Duttlinger Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-211"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005639403314739200♠"></span>158 acres (64 ha)<sup class="reference" id="cite_ref-ogEast_15-212"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a href="/wiki/Prunus_serotina" title="Prunus serotina">Black Cherry</a>, <a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a><sup class="reference" id="cite_ref-ogEast_15-213"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Pinchot_State_Forest" title="Pinchot State Forest">Pinchot State Forest</a>, Montage Mountain<sup class="reference" id="cite_ref-ogEast_15-214"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006485622770688000♠"></span>1,200 acres (490 ha)<sup class="reference" id="cite_ref-ogEast_15-215"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a href="/wiki/Prunus_serotina" title="Prunus serotina">Black Cherry</a>, <a class="mw-redirect" href="/wiki/Yellow_Birch" title="Yellow Birch">Yellow Birch</a>, <a href="/wiki/Quercus_rubra" title="Quercus rubra">Red Oak</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/Chestnut_Oak" title="Chestnut Oak">Chestnut Oak</a>, <a href="/wiki/Fraxinus" title="Fraxinus">Ash</a>, <a class="mw-redirect" href="/wiki/Tulip_Poplar" title="Tulip Poplar">Tulip Poplar</a>, <a class="mw-redirect" href="/wiki/Red_Maple" title="Red Maple">Red Maple</a><sup class="reference" id="cite_ref-ogEast_15-216"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Snyder_Middleswarth_Natural_Area" title="Snyder Middleswarth Natural Area">Snyder Middleswarth Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-217"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006101171410560000♠"></span>250 acres (100 ha)<sup class="reference" id="cite_ref-ogEast_15-218"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>, <a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/Pitch_Pine" title="Pitch Pine">Pitch Pine</a><sup class="reference" id="cite_ref-ogEast_15-219"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Tuscarora_State_Forest" title="Tuscarora State Forest">Hemlocks Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-220"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005485622770688000♠"></span>120 acres (49 ha)<sup class="reference" id="cite_ref-ogEast_15-221"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a><sup class="reference" id="cite_ref-ogEast_15-222"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a href="/wiki/Ricketts_Glen_State_Park" title="Ricketts Glen State Park">Ricketts Glen State Park</a><sup class="reference" id="cite_ref-ogEast_15-223"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006809371284480000♠"></span>2,000 acres (810 ha)<sup class="reference" id="cite_ref-ogEast_15-224"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_Hardwood_Forest" title="Northern Hardwood Forest">Northern Hardwood Forest</a><sup class="reference" id="cite_ref-ogEast_15-225"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Pennsylvania" title="Pennsylvania">Pennsylvania</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Peck_Natural_Area_in_Lake_Winola&amp;action=edit&amp;redlink=1" title="Peck Natural Area in Lake Winola (page does not exist)">Peck Natural Area in Lake Winola</a><sup class="reference" id="cite_ref-ogEast_15-226"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7004404685642240000♠"></span>10–20 acres (4.0–8.1 ha)<sup class="reference" id="cite_ref-ogEast_15-227"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Allegheny_Highlands_forests" title="Allegheny Highlands forests">Allegheny Highlands forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_Hardwood_Forest" title="Northern Hardwood Forest">Northern Hardwood Forest</a>, <a class="mw-redirect" href="/wiki/Eastern_White_Pine" title="Eastern White Pine">Eastern White Pine</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a><sup class="reference" id="cite_ref-ogEast_15-228"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Rhode_Island" title="Rhode Island">Rhode Island</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Great_Swamp_Wildlife_Management_Area&amp;action=edit&amp;redlink=1" title="Great Swamp Wildlife Management Area (page does not exist)">Great Swamp Wildlife Management Area</a><sup class="reference" id="cite_ref-ogEast_15-229"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007121405692672000♠"></span>3,000 acres (1,200 ha)<sup class="reference" id="cite_ref-ogEast_15-230"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northeastern_coastal_forests" title="Northeastern coastal forests">Northeastern coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Red_Maple" title="Red Maple">Red Maple</a>, <a class="mw-redirect" href="/wiki/Atlantic_White_Cedar" title="Atlantic White Cedar">Atlantic White Cedar</a>, <a href="/wiki/Nyssa_sylvatica" title="Nyssa sylvatica">Black Gum</a><sup class="reference" id="cite_ref-ogEast_15-231"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Rhode_Island" title="Rhode Island">Rhode Island</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Lawton%27s_Valley_Forest&amp;action=edit&amp;redlink=1" title="Lawton's Valley Forest (page does not exist)">Lawton's Valley Forest</a><sup class="reference" id="cite_ref-LawtonsValley_49-0"><a href="#cite_note-LawtonsValley-49"><span class="cite-bracket">[</span>49<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Northeastern_coastal_forests" title="Northeastern coastal forests">Northeastern coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Sugar_Maple" title="Sugar Maple">Sugar Maple</a>, <a href="/wiki/Fraxinus_americana" title="Fraxinus americana">White Ash</a>, <a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a class="mw-redirect" href="/wiki/Yellow_Birch" title="Yellow Birch">Yellow Birch</a>, <a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a><sup class="reference" id="cite_ref-LawtonsValley_49-1"><a href="#cite_note-LawtonsValley-49"><span class="cite-bracket">[</span>49<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Rhode_Island" title="Rhode Island">Rhode Island</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Oakland_Forest&amp;action=edit&amp;redlink=1" title="Oakland Forest (page does not exist)">Oakland Forest</a><sup class="reference" id="cite_ref-ogEast_15-232"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7004809371284480000♠"></span>20 acres (8.1 ha)<sup class="reference" id="cite_ref-ogEast_15-233"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northeastern_coastal_forests" title="Northeastern coastal forests">Northeastern coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/American_Beech" title="American Beech">American Beech</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/Red_Maple" title="Red Maple">Red Maple</a>, <a class="mw-redirect" href="/wiki/Scarlet_Oak" title="Scarlet Oak">Scarlet Oak</a><sup class="reference" id="cite_ref-ogEast_15-234"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Rhode_Island" title="Rhode Island">Rhode Island</a>
     </td>
     <td><a href="/wiki/Pawcatuck_River" title="Pawcatuck River">Pawcatuck River</a> floodplain forest<sup class="reference" id="cite_ref-ogEast_15-235"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006101171410560000♠"></span>250 acres (100 ha)<sup class="reference" id="cite_ref-ogEast_15-236"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Northeastern_coastal_forests" title="Northeastern coastal forests">Northeastern coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Red_Maple" title="Red Maple">Red Maple</a> floodplain<sup class="reference" id="cite_ref-ogEast_15-237"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/South_Carolina" title="South Carolina">South Carolina</a>
     </td>
     <td><a href="/wiki/Congaree_National_Park" title="Congaree National Park">Congaree National Park</a><sup class="reference" id="cite_ref-ogEast_15-238"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007445154206464000♠"></span>11,000 acres (4,500 ha)<sup class="reference" id="cite_ref-ogEast_15-239"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Middle_Atlantic_coastal_forests" title="Middle Atlantic coastal forests">Middle Atlantic coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Bottomland_hardwood_forest" title="Bottomland hardwood forest">bottomland hardwood forest</a><sup class="reference" id="cite_ref-ogEast_15-240"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/South_Carolina" title="South Carolina">South Carolina</a>
     </td>
     <td><a href="/wiki/Francis_Beidler_Forest" title="Francis Beidler Forest">Francis Beidler Forest</a><sup class="reference" id="cite_ref-ogEast_15-241"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006687965591808000♠"></span>1,700 acres (690 ha)<sup class="reference" id="cite_ref-ogEast_15-242"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Middle_Atlantic_coastal_forests" title="Middle Atlantic coastal forests">Middle Atlantic coastal forests</a>
     </td>
     <td>mixed hardwoods and cypress-tupelo swamp<sup class="reference" id="cite_ref-ogEast_15-243"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/South_Carolina" title="South Carolina">South Carolina</a>
     </td>
     <td><a href="/wiki/Ellicott_Rock_Wilderness" title="Ellicott Rock Wilderness">Ellicott Rock Wilderness</a><sup class="reference" id="cite_ref-ogEast_15-244"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006404685642240000♠"></span>1,000 acres (400 ha) or more<sup class="reference" id="cite_ref-ogEast_15-245"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Tennessee" title="Tennessee">Tennessee</a>
     </td>
     <td><a href="/wiki/Great_Smoky_Mountains" title="Great Smoky Mountains">Great Smoky Mountains</a><sup class="reference" id="cite_ref-ogEast_15-246"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008756762150988800♠"></span>187,000 acres (76,000 ha)<sup class="reference" id="cite_ref-ogEast_15-247"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Tennessee" title="Tennessee">Tennessee</a>
     </td>
     <td>Forest within <a href="/wiki/Nashville,_Tennessee" title="Nashville, Tennessee">Nashville</a><sup class="reference" id="cite_ref-nashville_50-0"><a href="#cite_note-nashville-50"><span class="cite-bracket">[</span>50<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005910542695040000♠"></span>225 acres (91 ha)<sup class="reference" id="cite_ref-nashville_50-1"><a href="#cite_note-nashville-50"><span class="cite-bracket">[</span>50<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Central_U.S._hardwood_forests" title="Central U.S. hardwood forests">Central U.S. hardwood forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Black_Walnut" title="Black Walnut">Black Walnut</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/American_Sycamore" title="American Sycamore">American Sycamore</a>, <a href="/wiki/Persimmon" title="Persimmon">Persimmon</a>, <a href="/wiki/Asimina_triloba" title="Asimina triloba">Pawpaw</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Tennessee" title="Tennessee">Tennessee</a>
     </td>
     <td><a href="/wiki/Old_Forest_Arboretum_of_Overton_Park" title="Old Forest Arboretum of Overton Park">Old Forest Arboretum of Overton Park</a>
     </td>
     <td><span data-sort-value="7005696059304652800♠"></span>172 acres (70 ha)
     </td>
     <td><sup class="noprint Inline-Template Template-Fact" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Citation_needed" title="Wikipedia:Citation needed"><span title="This claim needs references to reliable sources. (January 2023)">citation needed</span></a></i>]</sup>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Utah" title="Utah">Utah</a>
     </td>
     <td>Red Canyon-<a href="/wiki/Dixie_National_Forest" title="Dixie National Forest">Dixie National Forest</a><sup class="reference" id="cite_ref-51"><a href="#cite_note-51"><span class="cite-bracket">[</span>51<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006103194838771200♠"></span>255 acres (103 ha)
     </td>
     <td><a class="mw-redirect" href="/wiki/Wasatch_and_Uinta_montane_forest" title="Wasatch and Uinta montane forest">Wasatch and Uinta montane forest</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Ponderosa_Pine" title="Ponderosa Pine">Ponderosa Pine</a>, <a class="mw-redirect" href="/wiki/Douglas_Fir" title="Douglas Fir">Douglas Fir</a>, <a class="mw-redirect" href="/wiki/Pinyon-juniper_woodland" title="Pinyon-juniper woodland">Pinyon-juniper woodland</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Virginia" title="Virginia">Virginia</a>
     </td>
     <td><a href="/wiki/George_Washington_and_Jefferson_National_Forests" title="George Washington and Jefferson National Forests">George Washington and Jefferson National Forests</a><sup class="reference" id="cite_ref-ogEast_15-248"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008930776977152000♠"></span>230,000 acres (93,000 ha)<sup class="reference" id="cite_ref-ogEast_15-249"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/Virginia" title="Virginia">Virginia</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Caledon_Natural_Area" title="Caledon Natural Area">Caledon Natural Area</a><sup class="reference" id="cite_ref-ogEast_15-250"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006121405692672000♠"></span>300 acres (120 ha)
     </td>
     <td><a href="/wiki/Southeastern_mixed_forests" title="Southeastern mixed forests">Southeastern mixed forests</a>
     </td>
     <td>Upland <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a> – <a class="mw-redirect" href="/wiki/Tulip_Poplar" title="Tulip Poplar">Tulip Poplar</a><sup class="reference" id="cite_ref-ogEast_15-251"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Virginia" title="Virginia">Virginia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Warm_Springs_Mountain&amp;action=edit&amp;redlink=1" title="Warm Springs Mountain (page does not exist)">Warm Springs Mountain</a><sup class="reference" id="cite_ref-ogEast_15-252"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006171991397952000♠"></span>425 acres (172 ha)
     </td>
     <td><a class="mw-redirect" href="/wiki/Appalachian-Blue_Ridge_forests" title="Appalachian-Blue Ridge forests">Appalachian-Blue Ridge forests</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Oak-Hickory&amp;action=edit&amp;redlink=1" title="Oak-Hickory (page does not exist)">Oak-Hickory</a>, <a class="mw-redirect" href="/wiki/Pitch_Pine" title="Pitch Pine">Pitch Pine</a><sup class="reference" id="cite_ref-ogEast_15-253"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Virginia" title="Virginia">Virginia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=North_Landing_River_Preserve&amp;action=edit&amp;redlink=1" title="North Landing River Preserve (page does not exist)">North Landing River Preserve</a><sup class="reference" id="cite_ref-ogEast_15-254"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005809371284480000♠"></span>200 acres (81 ha)
     </td>
     <td><a href="/wiki/Middle_Atlantic_coastal_forests" title="Middle Atlantic coastal forests">Middle Atlantic coastal forests</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Pond_Pine" title="Pond Pine">Pond Pine</a>, <a class="mw-redirect" href="/wiki/Atlantic_White_Cedar" title="Atlantic White Cedar">Atlantic White Cedar</a> and scattered ancient <a class="mw-redirect" href="/wiki/Bald_cypress" title="Bald cypress">Bald cypress</a><sup class="reference" id="cite_ref-ogEast_15-255"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Virginia" title="Virginia">Virginia</a>
     </td>
     <td><a class="new" href="/w/index.php?title=James_Madison_Estate&amp;action=edit&amp;redlink=1" title="James Madison Estate (page does not exist)">James Madison Estate</a><sup class="reference" id="cite_ref-ogEast_15-256"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005809371284480000♠"></span>200 acres (81 ha)
     </td>
     <td><a href="/wiki/Southeastern_mixed_forests" title="Southeastern mixed forests">Southeastern mixed forests</a>
     <p><sup class="reference" id="cite_ref-ogEast_15-257"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </p>
     </td>
     <td><a class="mw-redirect" href="/wiki/Northern_Red_Oak" title="Northern Red Oak">Northern Red Oak</a>, <a href="/wiki/Quercus_alba" title="Quercus alba">White Oak</a>, <a class="mw-redirect" href="/wiki/Tulip_Tree" title="Tulip Tree">Tulip Tree</a> and <a href="/wiki/Hickory" title="Hickory">Hickory</a>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/Olympic_National_Park" title="Olympic National Park">Olympic National Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-40"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009148114945059840♠"></span>366,000 acres (148,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-41"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/North_Cascades_National_Park" title="North Cascades National Park">North Cascades National Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-42"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008955058115686400♠"></span>236,000 acres (96,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-43"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/Mount_Rainier_National_Park" title="Mount Rainier National Park">Mount Rainier National Park</a><sup class="reference" id="cite_ref-ogCaOrWa_18-44"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008368263934438400♠"></span>91,000 acres (37,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-45"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/Colville_National_Forest" title="Colville National Forest">Colville National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-46"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008859908427482931♠"></span>212,488 acres (85,991 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-47"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/Gifford_Pinchot_National_Forest" title="Gifford Pinchot National Forest">Gifford Pinchot National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-48"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7008801277571635200♠"></span>198,000 acres (80,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-49"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Mount_Baker-Snoqualmie_National_Forest" title="Mount Baker-Snoqualmie National Forest">Mount Baker-Snoqualmie National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-50"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009260415210781440♠"></span>643,500 acres (260,400 ha)
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/Okanogan%E2%80%93Wenatchee_National_Forest" title="Okanogan–Wenatchee National Forest">Okanogan–Wenatchee National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-51"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009127880662947840♠"></span>316,000 acres (128,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-52"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/Olympic_National_Forest" title="Olympic National Forest">Olympic National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-53"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009107970129349632♠"></span>266,800 acres (108,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-54"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/South_Whidbey_State_Park" title="South Whidbey State Park">South Whidbey State Park</a><sup class="reference" id="cite_ref-wasp20190412_52-0"><a href="#cite_note-wasp20190412-52"><span class="cite-bracket">[</span>52<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006154185229693440♠"></span>381 acres (154 ha)
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>, <a class="mw-redirect" href="/wiki/Sitka_spruce" title="Sitka spruce">Sitka spruce</a>, <a class="mw-redirect" href="/wiki/Western_Hemlock" title="Western Hemlock">Western Hemlock</a> and Western Red-cedar<sup class="reference" id="cite_ref-wasp20190412_52-1"><a href="#cite_note-wasp20190412-52"><span class="cite-bracket">[</span>52<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/Seward_Park_(Seattle)" title="Seward Park (Seattle)">Seward Park (Seattle)</a><sup class="reference" id="cite_ref-ogCaOrWa_18-55"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006121405692672000♠"></span>300 acres (120 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-56"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Coast_Douglas-fir" title="Coast Douglas-fir">Coast Douglas-fir</a>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a href="/wiki/Wenatchee_National_Forest" title="Wenatchee National Forest">Wenatchee National Forest</a><sup class="reference" id="cite_ref-ogCaOrWa_18-57"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7009129013782746112♠"></span>318,800 acres (129,000 ha)<sup class="reference" id="cite_ref-ogCaOrWa_18-58"><a href="#cite_note-ogCaOrWa-18"><span class="cite-bracket">[</span>18<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a class="mw-redirect" href="/wiki/Washington_(U.S._state)" title="Washington (U.S. state)">Washington</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Schmitz_Preserve_Park" title="Schmitz Preserve Park">Schmitz Preserve Park</a><sup class="noprint Inline-Template Template-Fact" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Citation_needed" title="Wikipedia:Citation needed"><span title="This claim needs references to reliable sources. (January 2023)">citation needed</span></a></i>]</sup>
     </td>
     <td>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/West_Virginia" title="West Virginia">West Virginia</a>
     </td>
     <td><a href="/wiki/Cathedral_State_Park" title="Cathedral State Park">Cathedral State Park</a><sup class="reference" id="cite_ref-ogEast_15-258"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7005534185047756799♠"></span>132 acres (53 ha)
     </td>
     <td>
     </td>
     <td><a class="mw-redirect" href="/wiki/Eastern_Hemlock" title="Eastern Hemlock">Eastern Hemlock</a>
     </td></tr>
     <tr>
     <td><a href="/wiki/West_Virginia" title="West Virginia">West Virginia</a>
     </td>
     <td><a href="/wiki/Monongahela_National_Forest" title="Monongahela National Forest">Monongahela National Forest</a><sup class="reference" id="cite_ref-mnfPlan1_53-0"><a href="#cite_note-mnfPlan1-53"><span class="cite-bracket">[</span>53<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006128690034232320♠"></span>318 acres (129 ha) in <a href="/wiki/Monongahela_National_Forest#Areas_of_interest_within_the_Monongahela_National_Forest" title="Monongahela National Forest">
     6 separate stands</a><sup class="reference" id="cite_ref-mnfPlan1_53-1"><a href="#cite_note-mnfPlan1-53"><span class="cite-bracket">[</span>53<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Wisconsin" title="Wisconsin">Wisconsin</a>
     </td>
     <td><a href="/wiki/Apostle_Islands_National_Lakeshore" title="Apostle Islands National Lakeshore">Apostle Islands National Lakeshore</a><sup class="reference" id="cite_ref-ogEast_15-259"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7006607028463360000♠"></span>1,500 acres (610 ha)<sup class="reference" id="cite_ref-ogEast_15-260"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Wisconsin" title="Wisconsin">Wisconsin</a>
     </td>
     <td><a class="mw-redirect" href="/wiki/Chequamegon-Nicolet_National_Forest" title="Chequamegon-Nicolet National Forest">Chequamegon-Nicolet National Forest</a><sup class="reference" id="cite_ref-ogEast_15-261"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td>
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Wisconsin" title="Wisconsin">Wisconsin</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Gerstberger_Pines&amp;action=edit&amp;redlink=1" title="Gerstberger Pines (page does not exist)">Gerstberger Pines</a><sup class="reference" id="cite_ref-GerstP_54-0"><a href="#cite_note-GerstP-54"><span class="cite-bracket">[</span>54<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7004809371284480000♠"></span>20 acres (8.1 ha)<sup class="reference" id="cite_ref-GerstP_54-1"><a href="#cite_note-GerstP-54"><span class="cite-bracket">[</span>54<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Tsuga_canadensis" title="Tsuga canadensis">Eastern Hemlock</a>, <a href="/wiki/Betula_alleghaniensis" title="Betula alleghaniensis">Yellow Birch</a>, <a href="/wiki/Quercus_rubra" title="Quercus rubra">Red Oak</a>, <a href="/wiki/Pinus_strobus" title="Pinus strobus">White Pine</a>, <a href="/wiki/Tilia_americana" title="Tilia americana">Basswood</a>, <a href="/wiki/Acer_rubrum" title="Acer rubrum">Red Maple</a><sup class="reference" id="cite_ref-GerstP_54-2"><a href="#cite_note-GerstP-54"><span class="cite-bracket">[</span>54<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Wisconsin" title="Wisconsin">Wisconsin</a>
     </td>
     <td><a class="new" href="/w/index.php?title=Namekagon_Barrens&amp;action=edit&amp;redlink=1" title="Namekagon Barrens (page does not exist)">Namekagon Barrens</a><sup class="reference" id="cite_ref-ogEast_15-262"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><span data-sort-value="7007161874256896000♠"></span>4,000 acres (1,600 ha)<sup class="reference" id="cite_ref-ogEast_15-263"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td>
     <td>
     </td>
     <td><a href="/wiki/Jack_pine" title="Jack pine">Jack pine</a> and scrub oak<sup class="reference" id="cite_ref-ogEast_15-264"><a href="#cite_note-ogEast-15"><span class="cite-bracket">[</span>15<span class="cite-bracket">]</span></a></sup>
     </td></tr>
     <tr>
     <td><a href="/wiki/Wyoming" title="Wyoming">Wyoming</a>
     </td>
     <td><a href="/wiki/Yellowstone_National_Park" title="Yellowstone National Park">Yellowstone National Park</a>
     </td>
     <td>
     </td>
     <td><sup class="noprint Inline-Template Template-Fact" style="white-space:nowrap;">[<i><a href="/wiki/Wikipedia:Citation_needed" title="Wikipedia:Citation needed"><span title="This claim needs references to reliable sources. (January 2023)">citation needed</span></a></i>]</sup>
     </td>
     <td><a class="mw-redirect" href="/wiki/Lodgepole_Pine" title="Lodgepole Pine">Lodgepole Pine</a>
     </td></tr></tbody></table>,
     <table class="wikitable sortable">
     <tbody><tr>
     <th>Country
     </th>
     <th>Area
     </th>
     <th>Old-growth extent
     </th>
     <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
     </th>
     <th class="unsortable">Old-growth forest type
     </th></tr>
     <tr>
     <td><a href="/wiki/Costa_Rica" title="Costa Rica">Costa Rica</a>
     </td>
     <td><a href="/wiki/Braulio_Carrillo_National_Park" title="Braulio Carrillo National Park">Braulio Carrillo National Park</a>
     </td>
     <td><span data-sort-value="7008428000000000000♠"></span>428 square kilometres (165 sq mi)
     </td>
     <td><a href="/wiki/Talamancan_montane_forests" title="Talamancan montane forests">Talamancan montane</a> and <a class="mw-redirect" href="/wiki/Isthmian-Atlantic_moist_forests" title="Isthmian-Atlantic moist forests">Isthmian-Atlantic moist</a> forests
     </td>
     <td>
     </td></tr>
     <tr>
     <td><a href="/wiki/Panama" title="Panama">Panama</a>
     </td>
     <td><a href="/wiki/Chagres_National_Park" title="Chagres National Park">Chagres National Park</a>
     </td>
     <td><span data-sort-value="7008428000000000000♠"></span>428 square kilometres (165 sq mi)
     </td>
     <td>
     </td>
     <td>coastal tropical
     </td></tr></tbody></table>,
     <table class="wikitable sortable">
     <tbody><tr>
     <th>Country
     </th>
     <th>Area
     </th>
     <th>Old-growth extent
     </th>
     <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
     </th>
     <th class="unsortable">Old-growth forest type
     </th></tr>
     <tr>
     <td><a href="/wiki/The_Bahamas" title="The Bahamas">The Bahamas</a>
     </td>
     <td><a href="/wiki/Primeval_Forest_National_Park" title="Primeval Forest National Park">Primeval Forest National Park</a>
     </td>
     <td>7.5 acres
     </td>
     <td><a href="/wiki/Bahamian_dry_forests" title="Bahamian dry forests">Bahamian dry forests</a>
     </td>
     <td>evergreen tropical hardwood
     </td></tr>
     <tr>
     <td><a href="/wiki/Puerto_Rico" title="Puerto Rico">Puerto Rico</a> (<a href="/wiki/United_States" title="United States">United States</a>)
     </td>
     <td><a href="/wiki/El_Toro_Wilderness" title="El Toro Wilderness">El Toro Wilderness</a>, <a href="/wiki/El_Yunque_National_Forest" title="El Yunque National Forest">El Yunque National Forest</a>
     </td>
     <td>13,700 acres<sup class="reference" id="cite_ref-:1_55-0"><a href="#cite_note-:1-55"><span class="cite-bracket">[</span>55<span class="cite-bracket">]</span></a></sup>
     </td>
     <td><a href="/wiki/Puerto_Rican_moist_forests" title="Puerto Rican moist forests">Puerto Rican moist forests</a>
     </td>
     <td><i><a href="/wiki/Ternstroemia_luquillensis" title="Ternstroemia luquillensis">Ternstroemia luquillensis</a></i> and <i><a href="/wiki/Dacryodes_excelsa" title="Dacryodes excelsa">Dacryodes excelsa</a></i> mature forests.<sup class="reference" id="cite_ref-:1_55-1"><a href="#cite_note-:1-55"><span class="cite-bracket">[</span>55<span class="cite-bracket">]</span></a></sup>
     </td></tr></tbody></table>,
     <table class="wikitable sortable">
     <tbody><tr>
     <th>Country
     </th>
     <th>Area
     </th>
     <th>Old-growth extent
     </th>
     <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
     </th>
     <th>Old-growth forest type
     </th></tr>
     <tr>
     <td><a href="/wiki/French_Guiana" title="French Guiana">French Guiana</a> (<a href="/wiki/France" title="France">France</a>)
     </td>
     <td><a href="/wiki/Lucifer_D%C3%A9kou-D%C3%A9kou_Biological_Reserve" title="Lucifer Dékou-Dékou Biological Reserve">Lucifer Dékou-Dékou Biological Reserve</a>
     </td>
     <td><span data-sort-value="7008643730000000000♠"></span>64,373 hectares (159,070 acres)
     </td>
     <td><a href="/wiki/Tropical_and_subtropical_moist_broadleaf_forests" title="Tropical and subtropical moist broadleaf forests">Tropical and subtropical moist broadleaf forests</a>
     </td>
     <td><a href="/wiki/Tropical_rainforest" title="Tropical rainforest">Tropical rainforest</a>
     </td></tr></tbody></table>]




```python
for table in tables:
    headings = table.find_previous_sibling()
    print(headings.text)
```

    Bwindi Impenetrable Forest, Uganda
    Yakushima, Japan
    In 2001, Western Australia became the first state in Australia to cease logging in old-growth forests.[7]
    
    Primeval Beech Forests of the Carpathians
    Carmanah Walbran Provincial Park, British Columbia
    Olympic National Park, Washington
    Braulio Carrillo National Park, Costa Rica
    Caribbean[edit]
    South America[edit]
    


```python
for table in tables:
    headings = table.find_previous_sibling(["h2", "h3"])
    print(headings)
```

    None
    None
    None
    None
    None
    None
    None
    None
    None
    


```python
data = {}
for table in tables:
    headings = table.find_previous(["h2", "h3"]).text
    print(headings)
    data[headings] = table
```

    Africa
    Asia
    Australia
    Europe
    Canada
    United States
    Central America
    Caribbean
    South America
    


```python
headings
```




    'South America'




```python
data["Australia"]
```




    <table class="wikitable sortable">
    <tbody><tr>
    <th>Country
    </th>
    <th>Area
    </th>
    <th>Old-growth extent
    </th>
    <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
    </th>
    <th class="unsortable">Old-growth forest type
    </th></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a href="/wiki/Walpole_Wilderness_Area" title="Walpole Wilderness Area">Walpole Wilderness Area</a>, <a href="/wiki/Western_Australia" title="Western Australia">Western Australia</a>
    </td>
    <td>
    </td>
    <td><a class="mw-redirect" href="/wiki/Jarrah-Karri_forest_and_shrublands" title="Jarrah-Karri forest and shrublands">Jarrah-Karri forest and shrublands</a>
    </td>
    <td><a class="mw-redirect" href="/wiki/Karri" title="Karri">Karri</a>, <a class="mw-redirect" href="/wiki/Jarrah" title="Jarrah">Jarrah</a>, <a href="/wiki/Eucalyptus_jacksonii" title="Eucalyptus jacksonii">Eucalyptus jacksonii</a>, <a href="/wiki/Eucalyptus_guilfoylei" title="Eucalyptus guilfoylei">Eucalyptus guilfoylei</a>
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a href="/wiki/Barrington_Tops_National_Park" title="Barrington Tops National Park">Barrington Tops National Park</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a>
    </td>
    <td>
    </td>
    <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
    </td>
    <td><a class="mw-redirect" href="/wiki/Subtropical" title="Subtropical">subtropical</a> and <a class="mw-redirect" href="/wiki/Temperate" title="Temperate">temperate</a> <a href="/wiki/Rainforest" title="Rainforest">rainforest</a> and <a href="/wiki/Eucalypt" title="Eucalypt">eucalypt</a>
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a href="/wiki/Greater_Blue_Mountains_Area" title="Greater Blue Mountains Area">Greater Blue Mountains Area</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a>
    </td>
    <td>
    </td>
    <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
    </td>
    <td><a href="/wiki/Eucalypt" title="Eucalypt">eucalypt</a> forest
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a href="/wiki/Tarkine" title="Tarkine">Tarkine</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
    </td>
    <td>2,000 square kilometres (770 sq mi)
    </td>
    <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
    </td>
    <td><a href="/wiki/Temperate_rainforest" title="Temperate rainforest">Temperate rainforest</a>
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a class="mw-redirect" href="/wiki/Tasmanian_Wilderness" title="Tasmanian Wilderness">Tasmanian Wilderness</a>
    </td>
    <td>
    </td>
    <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
    </td>
    <td><a href="/wiki/Temperate_rainforest" title="Temperate rainforest">temperate rainforest</a> and <a href="/wiki/Eucalyptus" title="Eucalyptus">eucalypt</a> forest
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a href="/wiki/Goolengook" title="Goolengook">Goolengook</a>, <a href="/wiki/East_Gippsland" title="East Gippsland">East Gippsland</a>, <a class="mw-redirect" href="/wiki/Victoria_(Australia)" title="Victoria (Australia)">Victoria</a>
    </td>
    <td>Over 20 square kilometres (7.7 sq mi)
    </td>
    <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
    </td>
    <td>rare <a href="/wiki/Temperate_rainforest" title="Temperate rainforest">warm temperate/cool temperate</a> "Overlap Rainforest"
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a class="new" href="/w/index.php?title=Blue_Tier&amp;action=edit&amp;redlink=1" title="Blue Tier (page does not exist)">Blue Tier</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
    </td>
    <td>100 hectares (250 acres)<sup class="reference" id="cite_ref-8"><a href="#cite_note-8"><span class="cite-bracket">[</span>8<span class="cite-bracket">]</span></a></sup>
    </td>
    <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
    </td>
    <td><a href="/wiki/Myrtaceae" title="Myrtaceae">myrtle</a> canopy, unusually diverse understorey for temperate rainforest (<a class="mw-redirect" href="/wiki/Celery_top_pine" title="Celery top pine">celery top pine</a>, <a href="/wiki/Waratah" title="Waratah">waratah</a>, <a href="/wiki/Sassafras" title="Sassafras">sassafras</a>, <a href="/wiki/Tree_fern" title="Tree fern">tree fern</a>), threatened <a class="new" href="/w/index.php?title=Simson%27s_Stag_Beetle&amp;action=edit&amp;redlink=1" title="Simson's Stag Beetle (page does not exist)">Simson's Stag Beetle</a>.
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a class="new" href="/w/index.php?title=Styx_Forest&amp;action=edit&amp;redlink=1" title="Styx Forest (page does not exist)">Styx Forest</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
    </td>
    <td>
    </td>
    <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
    </td>
    <td>
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a class="new" href="/w/index.php?title=Weld_Forest&amp;action=edit&amp;redlink=1" title="Weld Forest (page does not exist)">Weld</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
    </td>
    <td>
    </td>
    <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
    </td>
    <td>
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a href="/wiki/Upper_Florentine_Valley" title="Upper Florentine Valley">Upper Florentine Valley</a>, <a href="/wiki/Tasmania" title="Tasmania">Tasmania</a>
    </td>
    <td>
    </td>
    <td><a class="mw-redirect" href="/wiki/Tasmanian_temperate_rain_forests" title="Tasmanian temperate rain forests">Tasmanian temperate rain forests</a>
    </td>
    <td>
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a class="new" href="/w/index.php?title=Badja_State_Forest&amp;action=edit&amp;redlink=1" title="Badja State Forest (page does not exist)">Badja State Forest</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-0"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
    </td>
    <td>
    </td>
    <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
    </td>
    <td>Wet old-growth with sweeping <a class="mw-redirect" href="/wiki/Tree-fern" title="Tree-fern">tree-fern</a> understoreys. 10+ threatened species (including <a href="/wiki/Squirrel_glider" title="Squirrel glider">squirrel glider</a> and <a href="/wiki/Golden-tipped_bat" title="Golden-tipped bat">golden-tipped bat</a>)
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a class="new" href="/w/index.php?title=Dampier_State_Forest&amp;action=edit&amp;redlink=1" title="Dampier State Forest (page does not exist)">Dampier State Forest</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-1"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
    </td>
    <td>
    </td>
    <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
    </td>
    <td>Wet old-growth. Most extensive rainforests in the South Coast.
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a href="/wiki/Wandella" title="Wandella">Wandella</a> / <a class="new" href="/w/index.php?title=Peak_Alone&amp;action=edit&amp;redlink=1" title="Peak Alone (page does not exist)">Peak Alone</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-2"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
    </td>
    <td>
    </td>
    <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
    </td>
    <td>High old-growth and threatened species values. Important catchment value.
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a class="new" href="/w/index.php?title=Monga_State_Forest&amp;action=edit&amp;redlink=1" title="Monga State Forest (page does not exist)">Monga State Forest</a> / <a class="new" href="/w/index.php?title=Buckenbowra&amp;action=edit&amp;redlink=1" title="Buckenbowra (page does not exist)">Buckenbowra</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-3"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
    </td>
    <td>
    </td>
    <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
    </td>
    <td>Pristine Buckenbowra River, including an area on the northern side of the river with a <a href="/wiki/Golden-tipped_bat" title="Golden-tipped bat">golden-tipped bat</a> record. Also an area around <a class="new" href="/w/index.php?title=McGregors_Creek&amp;action=edit&amp;redlink=1" title="McGregors Creek (page does not exist)">McGregors Creek</a>, nominated for wilderness, and important for old-growth and to increase the viability of the connection / link between Buckenbowra and <a href="/wiki/Deua_National_Park" title="Deua National Park">Deua National Park</a>.
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a href="/wiki/Dampier_County" title="Dampier County">Dampier</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-4"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
    </td>
    <td>
    </td>
    <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
    </td>
    <td>Upper <a href="/wiki/Deua_River" title="Deua River">Deua River</a> (Identified Wilderness) and <a class="new" href="/w/index.php?title=Big_Belimba_Creek&amp;action=edit&amp;redlink=1" title="Big Belimba Creek (page does not exist)">Big Belimba Creek</a> catchment and contains extensive old-growth forests. Big Belimba Creek contains giant wet old-growth forest and extensive tree-fern forests.
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a class="new" href="/w/index.php?title=Tallaganda_State_Forest&amp;action=edit&amp;redlink=1" title="Tallaganda State Forest (page does not exist)">Tallaganda State Forest</a>, <a href="/wiki/New_South_Wales" title="New South Wales">New South Wales</a><sup class="reference" id="cite_ref-2015liaut_9-5"><a href="#cite_note-2015liaut-9"><span class="cite-bracket">[</span>9<span class="cite-bracket">]</span></a></sup>
    </td>
    <td>
    </td>
    <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
    </td>
    <td>Tall wet old-growth forest.
    </td></tr>
    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a class="mw-redirect" href="/wiki/Gondwana_Rainforests_of_Australia" title="Gondwana Rainforests of Australia">Gondwana Rainforests of Australia</a>
    </td>
    <td>50 separate reserves totaling 366,500 hectares (906,000 acres)
    </td>
    <td><a class="mw-redirect" href="/wiki/Subtropical_rainforest" title="Subtropical rainforest">Subtropical rainforest</a>
    </td>
    <td>The most extensive area of subtropical rainforest in the world. Extremely high conservation value; over 200 rare or threatened plant and animal species.
    </td></tr></tbody></table>




```python
table = data["Australia"]
first_row = table.tr
for td in first_row:
    print(td.text)
```

    
    
    Country
    
    
    
    Area
    
    
    
    Old-growth extent
    
    
    
    WWF ecoregion
    
    
    
    Old-growth forest type
    
    


```python
columns = []
for td in first_row:
    if td.text.strip() != "":
        columns.append(td.text.strip())

columns
```




    ['Country',
     'Area',
     'Old-growth extent',
     'WWF ecoregion',
     'Old-growth forest type']




```python
rows = table.tbody.find_all("tr")
rows[1]
```




    <tr>
    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>
    <td><a href="/wiki/Walpole_Wilderness_Area" title="Walpole Wilderness Area">Walpole Wilderness Area</a>, <a href="/wiki/Western_Australia" title="Western Australia">Western Australia</a>
    </td>
    <td>
    </td>
    <td><a class="mw-redirect" href="/wiki/Jarrah-Karri_forest_and_shrublands" title="Jarrah-Karri forest and shrublands">Jarrah-Karri forest and shrublands</a>
    </td>
    <td><a class="mw-redirect" href="/wiki/Karri" title="Karri">Karri</a>, <a class="mw-redirect" href="/wiki/Jarrah" title="Jarrah">Jarrah</a>, <a href="/wiki/Eucalyptus_jacksonii" title="Eucalyptus jacksonii">Eucalyptus jacksonii</a>, <a href="/wiki/Eucalyptus_guilfoylei" title="Eucalyptus guilfoylei">Eucalyptus guilfoylei</a>
    </td></tr>




```python
example_row = rows[1]
table_cells = example_row.find_all("td")
table_cells
```




    [<td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>,
     <td><a href="/wiki/Walpole_Wilderness_Area" title="Walpole Wilderness Area">Walpole Wilderness Area</a>, <a href="/wiki/Western_Australia" title="Western Australia">Western Australia</a>
     </td>,
     <td>
     </td>,
     <td><a class="mw-redirect" href="/wiki/Jarrah-Karri_forest_and_shrublands" title="Jarrah-Karri forest and shrublands">Jarrah-Karri forest and shrublands</a>
     </td>,
     <td><a class="mw-redirect" href="/wiki/Karri" title="Karri">Karri</a>, <a class="mw-redirect" href="/wiki/Jarrah" title="Jarrah">Jarrah</a>, <a href="/wiki/Eucalyptus_jacksonii" title="Eucalyptus jacksonii">Eucalyptus jacksonii</a>, <a href="/wiki/Eucalyptus_guilfoylei" title="Eucalyptus guilfoylei">Eucalyptus guilfoylei</a>
     </td>]




```python
row_data = {}
for i in range(len(table_cells)):
    row_data[columns[i]] = table_cells[i]

row_data["Country"]

```




    <td><a href="/wiki/Australia" title="Australia">Australia</a>
    </td>




```python
row_data["Old-growth forest type"]
```




    <td><a class="mw-redirect" href="/wiki/Karri" title="Karri">Karri</a>, <a class="mw-redirect" href="/wiki/Jarrah" title="Jarrah">Jarrah</a>, <a href="/wiki/Eucalyptus_jacksonii" title="Eucalyptus jacksonii">Eucalyptus jacksonii</a>, <a href="/wiki/Eucalyptus_guilfoylei" title="Eucalyptus guilfoylei">Eucalyptus guilfoylei</a>
    </td>




```python
def extract_row_data(columns, row):
    row_data = {}
    table_cells = row.find_all("td")
    for i in range(len(table_cells)):
        row_data[columns[i]] = table_cells[i]
    
    return row_data
```


```python
australia_table = []
```


```python
rows.pop(0)
```




    <tr>
    <th>Country
    </th>
    <th>Area
    </th>
    <th>Old-growth extent
    </th>
    <th><a href="/wiki/List_of_terrestrial_ecoregions_(WWF)" title="List of terrestrial ecoregions (WWF)">WWF ecoregion</a>
    </th>
    <th class="unsortable">Old-growth forest type
    </th></tr>




```python
for r in rows:
    australia_table.append(extract_row_data(columns=columns,row=r))
australia_table[0]
```




    {'Country': <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>,
     'Area': <td><a href="/wiki/Walpole_Wilderness_Area" title="Walpole Wilderness Area">Walpole Wilderness Area</a>, <a href="/wiki/Western_Australia" title="Western Australia">Western Australia</a>
     </td>,
     'Old-growth extent': <td>
     </td>,
     'WWF ecoregion': <td><a class="mw-redirect" href="/wiki/Jarrah-Karri_forest_and_shrublands" title="Jarrah-Karri forest and shrublands">Jarrah-Karri forest and shrublands</a>
     </td>,
     'Old-growth forest type': <td><a class="mw-redirect" href="/wiki/Karri" title="Karri">Karri</a>, <a class="mw-redirect" href="/wiki/Jarrah" title="Jarrah">Jarrah</a>, <a href="/wiki/Eucalyptus_jacksonii" title="Eucalyptus jacksonii">Eucalyptus jacksonii</a>, <a href="/wiki/Eucalyptus_guilfoylei" title="Eucalyptus guilfoylei">Eucalyptus guilfoylei</a>
     </td>}




```python
def clean_row_data(row: dict):

    for k in row.keys():
        val = row[k]
        if re.match("\s", val.text):
            row[k] = "No data"

        links = val.find_all("a")

        for l in links:
            if l.get("title") is not None and "(page does not exist)" in l.get("title"):
                l.replace_with(l.text)

            if "cite" in l.get("href"):
                l.parent.decompose()

        if k == "Old-growth extent" and row[k] != "No data":
            data = row[k].text.strip()

            data = data.replace("\xa0", " ")
            
            # 2,000, 7,800,000
            data = re.search("\d+(?:,\d{3})*(?:\.\d*)? (?:hectares|square kilometres|ha|acres)", data).group()

            parent = row[k].parent
            row[k].decompose()

            new_tag = soup.new_tag("td")
            new_tag.string = data
            parent.append(new_tag)

            row[k] = new_tag

            
    return row
```


```python
australia_table[5]
```




    {'Country': <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>,
     'Area': <td><a href="/wiki/Goolengook" title="Goolengook">Goolengook</a>, <a href="/wiki/East_Gippsland" title="East Gippsland">East Gippsland</a>, <a class="mw-redirect" href="/wiki/Victoria_(Australia)" title="Victoria (Australia)">Victoria</a>
     </td>,
     'Old-growth extent': <td>Over 20 square kilometres (7.7 sq mi)
     </td>,
     'WWF ecoregion': <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>,
     'Old-growth forest type': <td>rare <a href="/wiki/Temperate_rainforest" title="Temperate rainforest">warm temperate/cool temperate</a> "Overlap Rainforest"
     </td>}




```python
clean_row_data(australia_table[5])
```




    {'Country': <td><a href="/wiki/Australia" title="Australia">Australia</a>
     </td>,
     'Area': <td><a href="/wiki/Goolengook" title="Goolengook">Goolengook</a>, <a href="/wiki/East_Gippsland" title="East Gippsland">East Gippsland</a>, <a class="mw-redirect" href="/wiki/Victoria_(Australia)" title="Victoria (Australia)">Victoria</a>
     </td>,
     'Old-growth extent': <td>20 square kilometres</td>,
     'WWF ecoregion': <td><a href="/wiki/Eastern_Australian_temperate_forests" title="Eastern Australian temperate forests">Eastern Australian temperate forests</a>
     </td>,
     'Old-growth forest type': <td>rare <a href="/wiki/Temperate_rainforest" title="Temperate rainforest">warm temperate/cool temperate</a> "Overlap Rainforest"
     </td>}



# Generalising methods


```python
def prepare_table_data(columns, table):
    table_data = []

    rows = table.find_all("tr")
    rows.pop(0)

    for r in rows:
        r = extract_row_data(columns=columns, row=r)
        r = clean_row_data(r)
        table_data.append(r)

    return table_data
```


```python
def prepare_all_tables(columns, data):
    for k in data.keys():
        data[k] = prepare_table_data(columns, data[k])

    return data
```


```python
data = prepare_all_tables(columns, data)
data["Canada"]
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    Cell In[201], line 1
    ----> 1 data = prepare_all_tables(columns, data)
          2 data["Canada"]
    

    Cell In[198], line 3, in prepare_all_tables(columns, data)
          1 def prepare_all_tables(columns, data):
          2     for k in data.keys():
    ----> 3         data[k] = prepare_table_data(columns, data[k])
          5     return data
    

    Cell In[197], line 4, in prepare_table_data(columns, table)
          1 def prepare_table_data(columns, table):
          2     table_data = []
    ----> 4     rows = table.find_all("tr")
          5     rows.pop(0)
          7     for r in rows:
    

    AttributeError: 'list' object has no attribute 'find_all'



```python

```
