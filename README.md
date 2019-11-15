# Live Project

## Introduction
For the last two weeks of my time at the tech academy, I worked with my peers in a team developing a full scale Web site utilizing Python, Django, Beautifulsoup, and HTML. Working on a project that involved a larger team was a great learning oppertunity for collaborating, problem solving, cleaning up code, and adding requested features. I was able to see how other developers wrote code and could compare tequniques. I started with [back end cleanup](#back-end-cleanup) which allowed me to get familiar with the project and functionality of the site. Once more familiar with the working environment, I transistoned into developing [new apps/functions](#new-app) and then intergrating them into the front end for user enjoyment. This process involved me utilizing modules that were unfamiliar with me at the time, but by exploring the documentation and bouncing questions off my peers, I was able to quickly adapt with tact and resiliance. Over the two week sprint I also had the opportunity to devlope other non-coding [skills](#other-skills-learned) that I could utilize in the software development project management work environment. I'm confident I will use the skills again and again on future projects.
  
Below are descriptions of the stories I worked on, along with code snippets and navigation links. I also have some full code files in this repo for the larger functionalities I implemented.


## Back End Cleanup
* [New Consolidated App](#new-consolidated-app)
* [Deprecate webpages](#deprecate-webpages)



### New Consolidated App
The wiki apps, Mining wiki, Wiki, and Glossary were spread out into different sections of the project. I consolidated them into a new app, approaptley names Wikis. I also crested new templates for the HTML side of the app to display.

![Story 1](/images/story1.jpg)
Format: ![Alt Text](url)


 ### Deprecate Webpages
I was tasked with deprecating the ‘Webpages’ section of the project and ensuring any liks were redirected. This also involved removing any refrences to the old ‘Data Sciences’ section of the project. 
My steps were as follows:

1) Remove all url references from our landing pages (home, apis, wiki, etc) to the webpages and make sure instead they reference the index page of the appropriate app. Replace the references to Data Science with references to My Location Data (like in the nav bar drop down). 
2) Comment out the appropriate code from the main the_spacebar files, like the urls.py file and the settings file
3) Delete the webpages app folder
4) Run the program and test that there are no broken links or errors


## New App
* [Astronomical Objects App](#astronomical-objects-app)

### Astronomical Objects App
This story was to develop a new function as a part of the wikis app that utilized beautifulsoup by obtaining information from the ‘Astronomical Objects’ section of a Wikipedia page, then [displayed](#astronomical-base) that information with clickable links of the front end of the project.

#Astronomical Objects Function
def objects(request):
    #use requests module to get the wikipedia page
    page = requests.get("https://en.wikipedia.org/wiki/Lists_of_astronomical_objects")
    soup = BeautifulSoup(page.content, 'html.parser')

    #get the section title
    textTitle = soup.find('h1').get_text()

    #get smaller section titles
    textSection1 = soup.find_all('h2')[1].get_text().strip('[edit]')
    textSection1_2 = soup.find('dt').get_text().replace('List of', '')
    textSection2 = soup.find_all('h2')[2].get_text().strip('[edit]')
    textSection3 = soup.find_all('h2')[3].get_text().strip('[edit]')
    textSection4 = soup.find_all('h2')[4].get_text().strip('[edit]')
    textSection5 = soup.find_all('h2')[5].get_text().strip('[edit]')
    textSection6 = soup.find_all('h2')[6].get_text().strip('[edit]')
    textSection7 = soup.find_all('h2')[7].get_text().strip('[edit]')
    textSection8 = soup.find_all('h2')[8].get_text().strip('[edit]')
    textSection9 = soup.find_all('h2')[9].get_text().strip('[edit]')
    textSection10 = soup.find_all('h2')[10].get_text().strip('[edit]')

    #Get the individual paragraphs from the extraction techniques section
    #Solar system section
    urlSolarSystem = soup.find(id='Solar_System')
    astros = urlSolarSystem.find_next('ul').find_all('a')
    astro=[]
    for res in astros:
        astro.append({'url':res.get('href'),'title':res.get('title')})

    #Minors section
    urlMinor = soup.find(title='List of minor planets')
    minors = urlMinor.find_next('ul').find_all('a')
    minor=[]
    for res in minors:
        minor.append({'url':res.get('href'),'title':res.get('title')})

    #Exo Planets section
    urlExo = soup.find(id="Exo-planets_and_brown_dwarfs")
    exos = urlExo.find_next('ul').find_all('a')
    exo=[]
    for res in exos:
        exo.append({'url':res.get('href'),'title':res.get('title')})

    #Stars section
    urlStars = soup.find(id='Stars')
    stars = urlStars.find_next('ul').find_all('a')
    star=[]
    for res in stars:
        star.append({'url':res.get('href'),'title':res.get('title')})

    #Constellations section
    urlStarConstellations = soup.find(id='Star_constellations')
    constellations = urlStarConstellations.find_next('ul').find_all('a')
    constellation=[]
    for res in constellations:
        constellation.append({'url':res.get('href'),'title':res.get('title')})

    #Star Clusters section
    urlStarClusters = soup.find(id='Star_clusters')
    clusters = urlStarClusters.find_next('ul').find_all('a')
    cluster=[]
    for res in clusters:
        cluster.append({'url':res.get('href'),'title':res.get('title')})

    #Nebulae section
    urlNebulae = soup.find(id='Nebulae')
    nebulaes = urlNebulae.find_next('ul').find_all('a')
    nebulae=[]
    for res in nebulaes:
        nebulae.append({'url':res.get('href'),'title':res.get('title')})

    #Galaxies section
    urlGalaxies = soup.find(id='Galaxies')
    galaxies = urlGalaxies.find_next('ul').find_all('a')
    galaxy=[]
    for res in galaxies:
        galaxy.append({'url':res.get('href'),'title':res.get('title')})

    #Galaxies Groups section
    urlGalaxyGroups = soup.find(id='Galaxy_groups_and_clusters')
    galGroups = urlGalaxyGroups.find_next('ul').find_all('a')
    galGroup=[]
    for res in galGroups:
        galGroup.append({'url':res.get('href'),'title':res.get('title')})

    #Black Holes section
    urlBlackHoles = soup.find(id='Black_holes')
    holes = urlBlackHoles.find_next('ul').find_all('a')
    hole=[]
    for res in holes:
        hole.append({'url':res.get('href'),'title':res.get('title')})

    #Other lists section
    urlOther = soup.find(id='Other_lists')
    others = urlOther.find_next('ul').find_all('a')
    other=[]
    for res in others:
        other.append({'url':res.get('href'),'title':res.get('title')})

    #Context Table for HTML pull
    context = {'Title': textTitle, 'secTitle1': textSection1, 'secTitle1_2': textSection1_2,'secTitle2': textSection2, 'secTitle3': textSection3, 'secTitle4': textSection4, 'secTitle5': textSection5, 'secTitle6': textSection6, 
    'secTitle7': textSection7, 'secTitle8': textSection8, 'secTitle9': textSection9, 'secTitle10': textSection10,  
    'p1': astro, 'p1_2': minor, 'p2': exo, 'p3': star, 'p4': constellation, 'p5': cluster, 'p6': nebulae,
    'p7': galaxy, 'p8': galGroup, 'p9': hole, 'p10': other}

    return render(request, 'wikis/objects_index.html', context)


### Astronomical Base

<!-- Astronomical Objects section -->
<section id="extraction" class="about-section text-center">
    <div class="container">
      <div class="row">
        <div class="col-lg-10 mx-auto">
          <!-- Astro title -->
          <h1 class="text-white-50">{{ Title }}</h1>
        </div>
      </div>
      <br />
      <br />
      <!-- Solar System -->
      <div class="row justify-content-left">
        <div>          
          <h2 style="font-size:20px;" class="text-white-50 row justify-content-left">{{ secTitle1 }}</h2>
          <!-- Solar System 'for loop' to populate clickable orderd list -->
          {% for astro in p1 %}
          <div class="row justify-content-left">
            <a href="http://en.m.wikipedia.org{{astro.url}}">{{astro.title}}</a><br />
          </div>
          {% endfor %}
        </div>
      </div>
      <br />
        <!-- Minor Planets -->
        <div class="row justify-content-left">
        <div>          
            <h2 style="font-size:20px;" class="text-white-50 row justify-content-left">{{ secTitle1_2 }}</h2>
            <!-- Minor Planets 'for loop' to populate clickable orderd list -->
            {% for minor in p1_2 %}
            <div class="row justify-content-left">
              <a href="http://en.m.wikipedia.org{{minor.url}}">{{minor.title}}</a><br />
            </div>
            {% endfor %}
        </div>
      </div>
        <br />
      <div class="row justify-content-left">
        <!--Exo Planets-->
        <div>
          <h2 style="font-size:20px;" class="text-white-50 row justify-content-left">{{ secTitle2 }}</h2>
          <!-- Exo Planets 'for loop' to populate clickable orderd list -->
          {% for exo in p2 %}
          <div class="row justify-content-left">
            <a href="http://en.m.wikipedia.org{{exo.url}}">{{exo.title}}</a><br />
          </div>
          {% endfor %}
          <br />
        </div>
      </div>
      <div class="row justify-content-left">
        <!--Stars-->
        <div>
          <h2 style="font-size:20px;" class="text-white-50 row justify-content-left">{{ secTitle3 }}</h2>
          <!-- Stars 'for loop' to populate clickable orderd list -->
          {% for star in p3 %}
          <div class="row justify-content-left">
            <a href="http://en.m.wikipedia.org{{star.url}}">{{star.title}}</a><br />
          </div>
          {% endfor %}
          <br />
        </div>
      </div>
      <div class="row justify-content-left">
        <!--Star Constellations-->
        <div>
          <h2 style="font-size:20px;" class="text-white-50 row justify-content-left">{{ secTitle4 }}</h2>
          <!-- Star Constellations 'for loop' to populate clickable orderd list -->
          {% for constellation in p4 %}
          <div class="row justify-content-left">
            <a href="http://en.m.wikipedia.org{{constellation.url}}">{{constellation.title}}</a><br />
          </div>
          {% endfor %}
          <br />
        </div>
      </div>
      <div class="row justify-content-left">
        <!--Star Clusters-->
        <div>


*Jump to: [Front End Stories](#front-end-stories), [Back End Stories](#back-end-stories), [Other Skills](#other-skills-learned), [Page Top](#live-project)*

## Other Skills Learned
* Working with a group of developers to collbrativly develop a large project with many sub sections.
* Improving project flow by communicating expectations and difficulties.
* Learning new efficiencies from other developers by observing their workflow and asking questions and reviewing their code. 
* Learning new modules that were otherwise forign to me such as Beautifulsoup, and reviewing the documentation to get the desired outcome for my fuctions.
  
*Jump to: [Front End Stories](#front-end-stories), [Back End Stories](#back-end-stories), [Other Skills](#other-skills-learned), [Page Top](#live-project)*
