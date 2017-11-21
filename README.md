# Contest1
The First Contest


Country Checklist: (Obvy. credit to Muller, the guy who made the wiki on our subreddit)

To make things more understandable, I'll follow every step with an example. The example country I'll be creating is Transylvania (a region in the west of modern day Romania).

1. Create a tag for your country. A tag is a 3 character long identifier, usually typed in all caps, that is unique for every country. You can find existing tags in the /common/country_tags/00_countries.txt. Try to think of a tag that somewhat resembles the actual name of your country, but isn't taken yet. The first three letters of the country name are usually fine, but the important thing is to make it unique. Once you have it, add it to your mod's /common/country_tags folder in a .txt file like this:

TRA = "countries/Transylvania.txt"

2. Create the general graphical file for your country. This goes into the /common/countries folder (this is the file that we just referenced in the country_tags folder in the previous step). This file will determine the country's map color, and graphical culture. The file in my example is called Transylvania.txt, and looks like this:

graphical_culture = eastern_european_gfx
graphical_culture_2d = eastern_european_2d

color = rgb { 231 161 18 }
For a list of all possible graphical culture and 2d graphical culture choices, look for the /common/graphicalculturetype.txt file.

It's important to also add an entry to the colors.txt (also in the common/countries folder), that correpsonds to the color you defined in the file above. In my case, the entry there looks like this:

TRA = {
    color = rgb { 231 161 18 }
    color_ui = rgb { 231 161 18 }
}
The color_ui will determine the color of division badges (on the map), if divisions are set to have their country's color, as opposed to allegiance colors.

3. Create a history file for your country. This goes into the /history/countries folder, and like always, you're best off copying an existing one, and tweaking it to your liking. In this file you're able to set up the starting situation of the country. This includes researched technologies, political setup, leaders, capital city, and much more. I wont go into detail on how to do everything, as most of them are pretty trivial. For a detailed look at them, you can read up on the HOI4 wiki. The file's name should be "TAG - CountryName.txt". In my example this is "TRA - Transylvania.txt", the file's pastebin upload can be found here.

4. Create flag(s) for your country. Flags go into the /gfx/flags folder, and have to be added in 3 sizes:

large: 82x52 px

medium: 41x26 px

small: 10x7 px

All image files should be in .tga format, and uncompressed (or 32-bit RLE compression, if you're using Photoshop). You can have different flags for different ideologies, but you can also have a "default" flag, so that the country has a fallback flag, if it doesn't find an ideology-specific one.

"TAG.tga" - this is the default flag, which is selected, if there is no ideology-specific flag for the country. (example: "TRA.tga")

"TAG_neutrality.tga" - this is the non-aligned ideology flag. (example: "TRA_neutrality.tga")

"TAG_democratic.tga" - this is the democratic ideology flag. (example: "TRA_democratic.tga")

"TAG_communism.tga" - this is the communist ideology flag (example: "TRA_communism.tga")

"TAG_fascism.tga" - this is the fascist ideology flag (example: "TRA_fascism.tga")

Remember, that ALL flags have to exist in all 3 sizes, so if you have different flags for all 4 ideologies, you have to create 4*3 = 12 flags total. Also, don't forget to put each flag in its proper folder. The /gfx/flags foler has 2 subfolders, which contain the medium and small sized flags.

5. Add localisation for your country. In one of your localisation files, you have to give names to your country for all possible ideologies. Remember to insert a space in front of each line in your localisation file. The Transylvanian example looks like this:

 TRA_fascism:0 "Transylvania"
 TRA_fascism_DEF:0 "Transylvania"
 TRA_democratic:0 "Transylvanian Republic"
 TRA_democratic_DEF:0 "The Transylvanian Republic"
 TRA_neutrality:0 "Transylvania"
 TRA_neutrality_DEF:0 "Transylvania"
 TRA_communism:0 "Transylvanian People's Republic"
 TRA_communism_DEF:0 "The Transylvanian People's Republic"
 TRA_fascism_ADJ:0 "Transylvanian"
 TRA_democratic_ADJ:0 "Transylvanian" 
 TRA_neutrality_ADJ:0 "Transylvanian"
 TRA_communism_ADJ:0 "Transylvanian"
 
There are 3 lines for each ideology:

TAG_ideology: This is the actual name of the country, with that ideology.

TAG_ideology_DEF: This is the same as before, but with the proper article before it (if necessary). This is necessary, because some localisation files refer to tags just on their own (like "German Reich"), while others refer to them with an article (like "The German Reich").

TAG_ideology_ADJ: This is the adjective of the country (or rather its people). It is mostly the same for all ideologies, but you have the ability to do each ideology separately.

6. (optional) Add an OOB file to your country. If you studied some files in the /history/countries folder carefully, you might have noticed a line that says something like oob = "GER_1936". This refers to an OOB, or order of battle, which determines what kind of units, factory setups, and unit templates the country has. If you want your country to start out with some divisions and templates other than the default ones, you should create an OOB file. These go into the /history/units folder. Only the file name is important, as you'll be referring to the OOB through that. Again, I recommend copying an existing OOB file, and modifying it to your liking.

7. (optional) Add your country to the game. Unless you want to add your country through an event, or a focus, you should give your country some starting territory, or at the very least, cores from which it can be released. This can be done by looking up the state file of the state you wish to give to the country (these can be found in the /history/states folder), and adding ownership and a core for your country. These always go under the history section of the state file, and for ownership, the lowermost command is the dominant. This means, that if you set the owner of a state to France, and then later in the same history section, set its owner as Germany, Germany will end up owning it.

In my example adding ownership and a core would look like this:

history={
    ...
    owner = TRA
    add_core_of = TRA
    ...
}


So, to quickly recap,

1. TAG in /common/country_tags/00_countries.txt
2. General Graphical File in  /common/countries
3. History File in /history/countries
4. Flag in /gfx/flags
5. Localisation in /localisation
6. (optional) OOB in /history/countries
7. Add the country in the game by giving it ownership/cores/claims on states in /history/states

If you wanted more complicated features such as events and national focuses, please check out all the links on the subreddit, as well as the full wiki provided by Muller.
