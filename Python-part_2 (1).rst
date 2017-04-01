
Requests HTTP Library
~~~~~~~~~~~~~~~~~~~~~

1 GET The GET method is used to retrieve information from the given
server using a given URI. Requests using GET should only retrieve data
and should have no other effect on the data.

2 HEAD Same as GET, but transfers the status line and header section
only.

3 POST A POST request is used to send data to the server, for example,
customer information, file upload, etc. using HTML forms.

4 PUT Replaces all current representations of the target resource with
the uploaded content.

5 DELETE Removes all current representations of the target resource
given by a URI.

6 CONNECT Establishes a tunnel to the server identified by a given URI.

7 OPTIONS Describes the communication options for the target resource.

8 TRACE Performs a message loop-back test along the path to the target
resource.

.. code:: ipython2

    import requests
    r = requests.get('https://google.com')
    #c = r.content
    print r.status_code
    #print c
    r = requests.post('http://httpbin.org/post', data = {'key':'value'})
    r.headers
    r = requests.put('http://httpbin.org/put', data = {'key':'value'})
    r = requests.delete('http://httpbin.org/delete')
    r = requests.head('http://httpbin.org/get')
    r = requests.options('http://httpbin.org/get')

Many cool things can be done using requests You can try out using
Facebook Graph API, to publish text or get pics from facebook
https://developers.facebook.com/docs/graph-api/overview

Beautiful soup library
~~~~~~~~~~~~~~~~~~~~~~

.. code:: ipython2

    html_doc = """
    <html><head><title>The Dormouse's story</title></head>
    <body>
    <p class="title"><b>The Dormouse's story</b></p>
    
    <p class="story">Once upon a time there were three little sisters; and their names were
    <a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>,
    <a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
    <a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
    and they lived at the bottom of a well.</p>
    
    <p class="story">...</p>
    """

.. code:: ipython2

    #sudo pip install beautifulsoup4

.. code:: ipython2

    from bs4 import BeautifulSoup
    soup = BeautifulSoup(html_doc, 'html.parser')
    
    print(soup.prettify())



.. parsed-literal::

    <html>
     <head>
      <title>
       The Dormouse's story
      </title>
     </head>
     <body>
      <p class="title">
       <b>
        The Dormouse's story
       </b>
      </p>
      <p class="story">
       Once upon a time there were three little sisters; and their names were
       <a class="sister" href="http://example.com/elsie" id="link1">
        Elsie
       </a>
       ,
       <a class="sister" href="http://example.com/lacie" id="link2">
        Lacie
       </a>
       and
       <a class="sister" href="http://example.com/tillie" id="link3">
        Tillie
       </a>
       ;
    and they lived at the bottom of a well.
      </p>
      <p class="story">
       ...
      </p>
     </body>
    </html>


.. code:: ipython2

    soup.title
    # <title>The Dormouse's story</title>
    
    soup.title.name
    # u'title'
    
    soup.title.string
    # u'The Dormouse's story'
    
    soup.title.parent.name
    # u'head'
    
    soup.p
    # <p class="title"><b>The Dormouse's story</b></p>
    
    soup.p['class']
    # u'title'
    
    soup.a
    # <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
    
    soup.find_all('a')
    # [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
    #  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
    #  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
    
    soup.find(id="link3")
    # <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>




.. parsed-literal::

    <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>



.. code:: ipython2

    url = 'https://en.wikipedia.org/wiki/Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology'
    import requests
    from bs4 import BeautifulSoup
    result = requests.get(url)
    
    c = result.content
    soup = BeautifulSoup(c,"lxml")
    print soup.prettify()


.. parsed-literal::

    <!DOCTYPE html>
    <html class="client-nojs" dir="ltr" lang="en">
     <head>
      <meta charset="utf-8"/>
      <title>
       Dhirubhai Ambani Institute of Information and Communication Technology - Wikipedia
      </title>
      <script>
       document.documentElement.className = document.documentElement.className.replace( /(^|\s)client-nojs(\s|$)/, "$1client-js$2" );
      </script>
      <script>
       (window.RLQ=window.RLQ||[]).push(function(){mw.config.set({"wgCanonicalNamespace":"","wgCanonicalSpecialPageName":false,"wgNamespaceNumber":0,"wgPageName":"Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology","wgTitle":"Dhirubhai Ambani Institute of Information and Communication Technology","wgCurRevisionId":765059875,"wgRevisionId":765059875,"wgArticleId":400258,"wgIsArticle":true,"wgIsRedirect":false,"wgAction":"view","wgUserName":null,"wgUserGroups":["*"],"wgCategories":["CS1 maint: Multiple names: authors list","Coordinates on Wikidata","Pages using deprecated image syntax","Pages using infobox university with unknown parameters","Commons category with page title same as on Wikidata","Universities and colleges in Gujarat","Engineering colleges in Gujarat","Education in Gandhinagar","Reliance Anil Dhirubhai Ambani Group","Communications in Gujarat","2001 establishments in India"],"wgBreakFrames":false,"wgPageContentLanguage":"en","wgPageContentModel":"wikitext","wgSeparatorTransformTable":["",""],"wgDigitTransformTable":["",""],"wgDefaultDateFormat":"dmy","wgMonthNames":["","January","February","March","April","May","June","July","August","September","October","November","December"],"wgMonthNamesShort":["","Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"],"wgRelevantPageName":"Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology","wgRelevantArticleId":400258,"wgRequestId":"WKBdAQpAAEEAAdNU-KEAAACW","wgIsProbablyEditable":true,"wgRestrictionEdit":[],"wgRestrictionMove":[],"wgFlaggedRevsParams":{"tags":{}},"wgStableRevisionId":null,"wgWikiEditorEnabledModules":{"toolbar":true,"dialogs":true,"preview":false,"publish":false},"wgBetaFeaturesFeatures":[],"wgMediaViewerOnClick":true,"wgMediaViewerEnabledByDefault":true,"wgVisualEditor":{"pageLanguageCode":"en","pageLanguageDir":"ltr","usePageImages":true,"usePageDescriptions":true},"wgPreferredVariant":"en","wgMFDisplayWikibaseDescriptions":{"search":true,"nearby":true,"watchlist":true,"tagline":true},"wgRelatedArticles":null,"wgRelatedArticlesUseCirrusSearch":true,"wgRelatedArticlesOnlyUseCirrusSearch":false,"wgULSCurrentAutonym":"English","wgNoticeProject":"wikipedia","wgCentralNoticeCookiesToDelete":[],"wgCentralNoticeCategoriesUsingLegacy":["Fundraising","fundraising"],"wgCategoryTreePageCategoryOptions":"{\"mode\":0,\"hideprefix\":20,\"showcount\":true,\"namespaces\":false}","wgCoordinates":{"lat":23.188333333333,"lon":72.628055555556},"wgWikibaseItemId":"Q5269618","wgCentralAuthMobileDomain":false,"wgVisualEditorToolbarScrollOffset":0,"wgEditSubmitButtonLabelPublish":false});mw.loader.state({"ext.globalCssJs.user.styles":"ready","ext.globalCssJs.site.styles":"ready","site.styles":"ready","noscript":"ready","user.styles":"ready","user":"ready","user.options":"loading","user.tokens":"loading","ext.cite.styles":"ready","wikibase.client.init":"ready","ext.visualEditor.desktopArticleTarget.noscript":"ready","ext.uls.interlanguage":"ready","ext.wikimediaBadges":"ready","mediawiki.legacy.shared":"ready","mediawiki.legacy.commonPrint":"ready","mediawiki.sectionAnchor":"ready","mediawiki.skinning.interface":"ready","skins.vector.styles":"ready","ext.globalCssJs.user":"ready","ext.globalCssJs.site":"ready"});mw.loader.implement("user.options@0j3lz3q",function($,jQuery,require,module){mw.user.options.set({"variant":"en"});});mw.loader.implement("user.tokens@1dqfd7l",function ( $, jQuery, require, module ) {
    mw.user.tokens.set({"editToken":"+\\","patrolToken":"+\\","watchToken":"+\\","csrfToken":"+\\"});/*@nomin*/;
    
    });mw.loader.load(["ext.cite.a11y","mediawiki.toc","mediawiki.action.view.postEdit","site","mediawiki.page.startup","mediawiki.user","mediawiki.hidpi","mediawiki.page.ready","mediawiki.legacy.wikibits","mediawiki.searchSuggest","ext.gadget.teahouse","ext.gadget.ReferenceTooltips","ext.gadget.watchlist-notice","ext.gadget.DRN-wizard","ext.gadget.charinsert","ext.gadget.refToolbar","ext.gadget.extra-toolbar-buttons","ext.gadget.switcher","ext.gadget.featured-articles-links","ext.centralauth.centralautologin","mmv.head","mmv.bootstrap.autostart","ext.visualEditor.desktopArticleTarget.init","ext.visualEditor.targetLoader","ext.eventLogging.subscriber","ext.wikimediaEvents","ext.navigationTiming","ext.uls.eventlogger","ext.uls.init","ext.uls.interface","ext.quicksurveys.init","ext.centralNotice.geoIP","ext.centralNotice.startUp","skins.vector.js"]);});
      </script>
      <link href="/w/load.php?debug=false&amp;lang=en&amp;modules=ext.cite.styles%7Cext.uls.interlanguage%7Cext.visualEditor.desktopArticleTarget.noscript%7Cext.wikimediaBadges%7Cmediawiki.legacy.commonPrint%2Cshared%7Cmediawiki.sectionAnchor%7Cmediawiki.skinning.interface%7Cskins.vector.styles%7Cwikibase.client.init&amp;only=styles&amp;skin=vector" rel="stylesheet"/>
      <script async="" src="/w/load.php?debug=false&amp;lang=en&amp;modules=startup&amp;only=scripts&amp;skin=vector">
      </script>
      <meta content="" name="ResourceLoaderDynamicStyles"/>
      <link href="/w/load.php?debug=false&amp;lang=en&amp;modules=site.styles&amp;only=styles&amp;skin=vector" rel="stylesheet"/>
      <meta content="MediaWiki 1.29.0-wmf.11" name="generator"/>
      <meta content="origin-when-cross-origin" name="referrer"/>
      <meta content="https://upload.wikimedia.org/wikipedia/commons/3/3d/Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology.png" property="og:image"/>
      <meta content="summary_large_image" name="twitter:card"/>
      <link href="android-app://org.wikipedia/http/en.m.wikipedia.org/wiki/Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology" rel="alternate"/>
      <link href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit" rel="alternate" title="Edit this page" type="application/x-wiki"/>
      <link href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit" rel="edit" title="Edit this page"/>
      <link href="/static/apple-touch/wikipedia.png" rel="apple-touch-icon"/>
      <link href="/static/favicon/wikipedia.ico" rel="shortcut icon"/>
      <link href="/w/opensearch_desc.php" rel="search" title="Wikipedia (en)" type="application/opensearchdescription+xml"/>
      <link href="//en.wikipedia.org/w/api.php?action=rsd" rel="EditURI" type="application/rsd+xml"/>
      <link href="//creativecommons.org/licenses/by-sa/3.0/" rel="copyright"/>
      <link href="https://en.wikipedia.org/wiki/Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology" rel="canonical"/>
      <link href="//login.wikimedia.org" rel="dns-prefetch"/>
      <link href="//meta.wikimedia.org" rel="dns-prefetch"/>
     </head>
     <body class="mediawiki ltr sitedir-ltr mw-hide-empty-elt ns-0 ns-subject page-Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology rootpage-Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology skin-vector action-view">
      <div class="noprint" id="mw-page-base">
      </div>
      <div class="noprint" id="mw-head-base">
      </div>
      <div class="mw-body" id="content" role="main">
       <a id="top">
       </a>
       <div id="siteNotice">
        <!-- CentralNotice -->
       </div>
       <div class="mw-indicators">
       </div>
       <h1 class="firstHeading" id="firstHeading" lang="en">
        Dhirubhai Ambani Institute of Information and Communication Technology
       </h1>
       <div class="mw-body-content" id="bodyContent">
        <div id="siteSub">
         From Wikipedia, the free encyclopedia
        </div>
        <div id="contentSub">
        </div>
        <div class="mw-jump" id="jump-to-nav">
         Jump to:
         <a href="#mw-head">
          navigation
         </a>
         ,
         <a href="#p-search">
          search
         </a>
        </div>
        <div class="mw-content-ltr" dir="ltr" id="mw-content-text" lang="en">
         <p>
          <span style="font-size: small;">
           <span id="coordinates">
            <a href="/wiki/Geographic_coordinate_system" title="Geographic coordinate system">
             Coordinates
            </a>
            :
            <span class="plainlinks nourlexpansion">
             <a class="external text" href="//tools.wmflabs.org/geohack/geohack.php?pagename=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;params=23_11_18_N_72_37_41_E_">
              <span class="geo-default">
               <span class="geo-dms" title="Maps, aerial photos, and other data for this location">
                <span class="latitude">
                 23°11′18″N
                </span>
                <span class="longitude">
                 72°37′41″E
                </span>
               </span>
              </span>
              <span class="geo-multi-punct">
               ﻿ / ﻿
              </span>
              <span class="geo-nondefault">
               <span class="geo-dec" title="Maps, aerial photos, and other data for this location">
                23.18833°N 72.62806°E
               </span>
               <span style="display:none">
                ﻿ /
                <span class="geo">
                 23.18833; 72.62806
                </span>
               </span>
              </span>
             </a>
            </span>
           </span>
          </span>
         </p>
         <table class="infobox vcard" style="width:22em">
          <caption class="fn org">
           Dhirubhai Ambani Institute of Information and Communication Technology
          </caption>
          <tr>
           <td colspan="2" style="text-align:center">
            <a class="image" href="/wiki/File:Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology.png" title="Dhirubhai Ambani Institute of Information and Communication Technology">
             <img alt="Dhirubhai Ambani Institute of Information and Communication Technology" data-file-height="241" data-file-width="241" height="241" src="//upload.wikimedia.org/wikipedia/commons/3/3d/Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology.png" width="241"/>
            </a>
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            Motto
           </th>
           <td>
            <span>
             Knowledge is Leadership
            </span>
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            Type
           </th>
           <td>
            Private
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            Established
           </th>
           <td>
            August 6, 2001
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            <a class="mw-redirect" href="/wiki/University_president" title="University president">
             President
            </a>
           </th>
           <td>
            <a href="/wiki/Anil_Ambani" title="Anil Ambani">
             Anil Ambani
            </a>
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            Director
           </th>
           <td>
            Dr. R. Nagaraj
            <sup class="reference" id="cite_ref-1">
             <a href="#cite_note-1">
              [1]
             </a>
            </sup>
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            <div style="padding:0.1em 0;line-height:1.2em;">
             Academic staff
            </div>
           </th>
           <td>
            45
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            <div style="padding:0.1em 0;line-height:1.2em;">
             Administrative staff
            </div>
           </th>
           <td>
            70
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            Students
           </th>
           <td>
            1,110
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            <a href="/wiki/Undergraduate_education" title="Undergraduate education">
             Undergraduates
            </a>
           </th>
           <td>
            1020
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            <a href="/wiki/Postgraduate_education" title="Postgraduate education">
             Postgraduates
            </a>
           </th>
           <td>
            150
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            <div style="padding:0.1em 0;line-height:1.2em;">
             <a href="/wiki/Doctorate" title="Doctorate">
              Doctoral students
             </a>
            </div>
           </th>
           <td>
            10
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            Address
           </th>
           <td class="adr">
            <span class="street-address">
             Near GH-0
            </span>
            ,
            <span class="locality">
             <a href="/wiki/Gandhinagar" title="Gandhinagar">
              Gandhinagar
             </a>
            </span>
            ,
            <span class="state">
             <a href="/wiki/Gujarat" title="Gujarat">
              Gujarat
             </a>
            </span>
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            Campus
           </th>
           <td>
            60 acres (240,000 m
            <sup>
             2
            </sup>
            )
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            <a href="/wiki/Athletic_nickname" title="Athletic nickname">
             Nickname
            </a>
           </th>
           <td>
            DA-IICT
           </td>
          </tr>
          <tr>
           <th scope="row" style="padding-right:0.65em;">
            Website
           </th>
           <td>
            <a class="external text" href="http://www.daiict.ac.in" rel="nofollow">
             www.daiict.ac.in
            </a>
           </td>
          </tr>
         </table>
         <p>
          <b>
           Dhirubhai Ambani Institute of Information and Communication Technology
          </b>
          (
          <b>
           DA-IICT
          </b>
          ), is a technological university located in
          <a href="/wiki/Gandhinagar" title="Gandhinagar">
           Gandhinagar
          </a>
          ,
          <a href="/wiki/Gujarat" title="Gujarat">
           Gujarat
          </a>
          ,
          <a href="/wiki/India" title="India">
           India
          </a>
          . It is named after the Gujarati
          <a class="mw-redirect" href="/wiki/Entrepreneur" title="Entrepreneur">
           entrepreneur
          </a>
          and
          <a class="mw-redirect" href="/wiki/Reliance_Industries_Limited" title="Reliance Industries Limited">
           Reliance group
          </a>
          founder
          <a href="/wiki/Dhirubhai_Ambani" title="Dhirubhai Ambani">
           Dhirubhai Ambani
          </a>
          . It is run by the Dhirubhai Ambani Foundation and is promoted by the
          <a class="mw-redirect" href="/wiki/Anil_Dhirubhai_Ambani_Group" title="Anil Dhirubhai Ambani Group">
           Anil Dhirubhai Ambani Group
          </a>
          .
          <sup class="reference" id="cite_ref-2">
           <a href="#cite_note-2">
            [2]
           </a>
          </sup>
         </p>
         <p>
          DA-IICT began admitting students in August 2001, with an intake of 240 undergraduate students for its Bachelor of Technology (B.Tech.) program in Information and Communication Technology (ICT). Since then, it has expanded to include postgraduate courses such as Master of Technology (M. Tech.) in ICT, Master of Science (M.Sc.) in Information Technology, Master of Science (ICT) in Agriculture and Rural Development, Master in Design (M. Des.), a five-year dual degree program, along with a Doctorate program. The duration of the bachelor's program is 4 years. The first batch of DA-IICT post-graduates passed out in 2004 and the first batch of graduates in 2005.
         </p>
         <p>
         </p>
         <div class="toc" id="toc">
          <div id="toctitle">
           <h2>
            Contents
           </h2>
          </div>
          <ul>
           <li class="toclevel-1 tocsection-1">
            <a href="#Admission">
             <span class="tocnumber">
              1
             </span>
             <span class="toctext">
              Admission
             </span>
            </a>
           </li>
           <li class="toclevel-1 tocsection-2">
            <a href="#Academic_programs">
             <span class="tocnumber">
              2
             </span>
             <span class="toctext">
              Academic programs
             </span>
            </a>
           </li>
           <li class="toclevel-1 tocsection-3">
            <a href="#Student_achievements">
             <span class="tocnumber">
              3
             </span>
             <span class="toctext">
              Student achievements
             </span>
            </a>
           </li>
           <li class="toclevel-1 tocsection-4">
            <a href="#Infrastructure">
             <span class="tocnumber">
              4
             </span>
             <span class="toctext">
              Infrastructure
             </span>
            </a>
            <ul>
             <li class="toclevel-2 tocsection-5">
              <a href="#Laboratory_building">
               <span class="tocnumber">
                4.1
               </span>
               <span class="toctext">
                Laboratory building
               </span>
              </a>
             </li>
             <li class="toclevel-2 tocsection-6">
              <a href="#Faculty_and_administrative_block">
               <span class="tocnumber">
                4.2
               </span>
               <span class="toctext">
                Faculty and administrative block
               </span>
              </a>
             </li>
             <li class="toclevel-2 tocsection-7">
              <a href="#Resource_centre">
               <span class="tocnumber">
                4.3
               </span>
               <span class="toctext">
                Resource centre
               </span>
              </a>
             </li>
             <li class="toclevel-2 tocsection-8">
              <a href="#Sports_and_Cultural_Complex">
               <span class="tocnumber">
                4.4
               </span>
               <span class="toctext">
                Sports and Cultural Complex
               </span>
              </a>
             </li>
             <li class="toclevel-2 tocsection-9">
              <a href="#Halls_of_residence">
               <span class="tocnumber">
                4.5
               </span>
               <span class="toctext">
                Halls of residence
               </span>
              </a>
             </li>
             <li class="toclevel-2 tocsection-10">
              <a href="#Medical_facility">
               <span class="tocnumber">
                4.6
               </span>
               <span class="toctext">
                Medical facility
               </span>
              </a>
             </li>
            </ul>
           </li>
           <li class="toclevel-1 tocsection-11">
            <a href="#Culture_and_student_life">
             <span class="tocnumber">
              5
             </span>
             <span class="toctext">
              Culture and student life
             </span>
            </a>
           </li>
           <li class="toclevel-1 tocsection-12">
            <a href="#Notable_alumni">
             <span class="tocnumber">
              6
             </span>
             <span class="toctext">
              Notable alumni
             </span>
            </a>
           </li>
           <li class="toclevel-1 tocsection-13">
            <a href="#See_also">
             <span class="tocnumber">
              7
             </span>
             <span class="toctext">
              See also
             </span>
            </a>
           </li>
           <li class="toclevel-1 tocsection-14">
            <a href="#Notes">
             <span class="tocnumber">
              8
             </span>
             <span class="toctext">
              Notes
             </span>
            </a>
           </li>
           <li class="toclevel-1 tocsection-15">
            <a href="#External_links">
             <span class="tocnumber">
              9
             </span>
             <span class="toctext">
              External links
             </span>
            </a>
           </li>
          </ul>
         </div>
         <p>
         </p>
         <h2>
          <span class="mw-headline" id="Admission">
           Admission
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=1" title="Edit section: Admission">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h2>
         <p>
          Thousands of students apply every year. Due to limited seats, selection is done on the basis of the
          <a href="/wiki/Joint_Entrance_Examination" title="Joint Entrance Examination">
           Joint Entrance Examination
          </a>
          (JEE Main) rank. A few seats are reserved for Non-Residential Indians (
          <a href="/wiki/Non-resident_Indian_and_person_of_Indian_origin" title="Non-resident Indian and person of Indian origin">
           NRIs
          </a>
          ) and Foreign Nationals (FNs), who are admitted through the Direct Admission of Foreign Student (DAFS) channel.
         </p>
         <h2>
          <span class="mw-headline" id="Academic_programs">
           Academic programs
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=2" title="Edit section: Academic programs">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h2>
         <p>
          It is the first institute in India to offer undergraduate and postgraduate degrees in Information and Communication Technology.
         </p>
         <div class="thumb tright">
          <div class="thumbinner" style="width:222px;">
           <a class="image" href="/wiki/File:Lotus_fountain,_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_(Gandhinagar,_Gujarat,_-_May_31_2009).jpg">
            <img alt="" class="thumbimage" data-file-height="768" data-file-width="1024" height="165" src="//upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Lotus_fountain%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_-_May_31_2009%29.jpg/220px-Lotus_fountain%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_-_May_31_2009%29.jpg" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Lotus_fountain%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_-_May_31_2009%29.jpg/330px-Lotus_fountain%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_-_May_31_2009%29.jpg 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Lotus_fountain%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_-_May_31_2009%29.jpg/440px-Lotus_fountain%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_-_May_31_2009%29.jpg 2x" width="220"/>
           </a>
           <div class="thumbcaption">
            <div class="magnify">
             <a class="internal" href="/wiki/File:Lotus_fountain,_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_(Gandhinagar,_Gujarat,_-_May_31_2009).jpg" title="Enlarge">
             </a>
            </div>
            Lotus pond
           </div>
          </div>
         </div>
         <div class="thumb tright">
          <div class="thumbinner" style="width:222px;">
           <a class="image" href="/wiki/File:DA-IICT_Night_View.jpg">
            <img alt="" class="thumbimage" data-file-height="361" data-file-width="485" height="164" src="//upload.wikimedia.org/wikipedia/commons/thumb/3/3d/DA-IICT_Night_View.jpg/220px-DA-IICT_Night_View.jpg" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/3/3d/DA-IICT_Night_View.jpg/330px-DA-IICT_Night_View.jpg 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/3/3d/DA-IICT_Night_View.jpg/440px-DA-IICT_Night_View.jpg 2x" width="220"/>
           </a>
           <div class="thumbcaption">
            <div class="magnify">
             <a class="internal" href="/wiki/File:DA-IICT_Night_View.jpg" title="Enlarge">
             </a>
            </div>
            Campus at night
           </div>
          </div>
         </div>
         <div class="thumb tright">
          <div class="thumbinner" style="width:222px;">
           <a class="image" href="/wiki/File:Daiict-campus.jpg">
            <img alt="" class="thumbimage" data-file-height="768" data-file-width="1024" height="165" src="//upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Daiict-campus.jpg/220px-Daiict-campus.jpg" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Daiict-campus.jpg/330px-Daiict-campus.jpg 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Daiict-campus.jpg/440px-Daiict-campus.jpg 2x" width="220"/>
           </a>
           <div class="thumbcaption">
            <div class="magnify">
             <a class="internal" href="/wiki/File:Daiict-campus.jpg" title="Enlarge">
             </a>
            </div>
            Campus
           </div>
          </div>
         </div>
         <div class="thumb tright">
          <div class="thumbinner" style="width:222px;">
           <a class="image" href="/wiki/File:Resource_Centre,_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_(Gandhinagar,_Gujarat,_India_-_19_Feb_2006).jpg">
            <img alt="" class="thumbimage" data-file-height="1200" data-file-width="1600" height="165" src="//upload.wikimedia.org/wikipedia/en/thumb/b/b6/Resource_Centre%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_India_-_19_Feb_2006%29.jpg/220px-Resource_Centre%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_India_-_19_Feb_2006%29.jpg" srcset="//upload.wikimedia.org/wikipedia/en/thumb/b/b6/Resource_Centre%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_India_-_19_Feb_2006%29.jpg/330px-Resource_Centre%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_India_-_19_Feb_2006%29.jpg 1.5x, //upload.wikimedia.org/wikipedia/en/thumb/b/b6/Resource_Centre%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_India_-_19_Feb_2006%29.jpg/440px-Resource_Centre%2C_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_%28Gandhinagar%2C_Gujarat%2C_India_-_19_Feb_2006%29.jpg 2x" width="220"/>
           </a>
           <div class="thumbcaption">
            <div class="magnify">
             <a class="internal" href="/wiki/File:Resource_Centre,_Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology_(Gandhinagar,_Gujarat,_India_-_19_Feb_2006).jpg" title="Enlarge">
             </a>
            </div>
            Resource Centre, DAIICT
           </div>
          </div>
         </div>
         <p>
          <b>
           B.Tech. Honours (CS*) and
          </b>
          <b>
           B.Tech (ICT) - Bachelor of Technology in Information and Communication Technology
          </b>
         </p>
         <p>
          The institute's flagship B.Tech program in Information and Communication Technology (ICT) is a 4-year program starting in July or August and consisting of eight semesters. Students at undergraduate level take foundation courses in Computer Science, Electronics, and Communications for two years. From third year onwards, students opt for elective courses alongside some compulsory ones. Open electives are compulsory for all students. Undergraduate students take summer/winter internships in rural sites, industry, or academic institutions, including DA-IICT. Hostel residence is compulsory for all B.Tech. (ICT) students.
         </p>
         <p>
          The program includes:
         </p>
         <ul>
          <li>
           Core courses in Computer Science and Engineering (CSE), Electronics and Communication Engineering (ECE), basic sciences and mathematics, humanities and social sciences, communication skills.
          </li>
          <li>
           Technical, science, and open electives.
          </li>
          <li>
           Two of the three offered internships in breaks (summer or winter).
          </li>
          <li>
           B Tech project (full semester). There are 27 core courses (including two individual seminar courses), two track core courses, two science courses (as elective), six technical electives and three open electives along with two internships and one B.Tech. Project.
          </li>
         </ul>
         <p>
          <b>
           MTech (ICT) - Master of Technology in Information and Communication Technology
          </b>
         </p>
         <ul>
          <li>
           This is a full-time two-year program open to graduates in ICT, Computer Science, Electronics and Communication, Electrical Engineering, Electronics and Instrumentation, IT or equivalent OR MSc degree in Physics, Electronics, Mathematics or Statistics, Bio-Technology. The M.Tech (ICT) program meets the needs of students who wish to work in the area of Information and Communication Technology.
          </li>
         </ul>
         <p>
          <b>
           MSc (IT) - Master of Science in Information Technology
          </b>
         </p>
         <ul>
          <li>
           This is a full-time two-year program open to graduates in any discipline. Applicants must have at least two courses of Mathematics or Statistics in their undergraduate curriculum and must have completed at least one course on computer programming.
          </li>
          <li>
           The program produces software developers to meet the needs of the IT industry. Subjects are Communications, Programming Paradigms, Algorithms, Network Programming, Software Engineering. At the end of the first year, the students undergo summer internship and during the last six months of the course, students do industrial training.
          </li>
         </ul>
         <p>
          <b>
           MSc (ICT-ARD) - Master of Science in Information and Communication Technology for Agriculture and Rural Development
          </b>
         </p>
         <ul>
          <li>
           The program is a full-time two-year program open to graduates in agricultural sciences, engineering and allied fields. The program is designed to meet the needs for professionals who can apply Information Technology in agricultural and rural development and agri-business.
          </li>
         </ul>
         <p>
          <b>
           M Des - Master's in Design (Communication Design)
          </b>
         </p>
         <ul>
          <li>
           M Des (CD) is a full time two-year program, which is divided into four semesters that offers specializations in Visual Communication Design and Interaction Design. It's unique pedagogic format encourages learning of basic design skills, the use of digital technologies and an understanding of the cultural and aesthetic aspects of communication practices. The program prepares young professionals for careers in the creative media industries and the academia. This program blends Design concepts, skills and practices with inputs from the disciplines of Sociology, Anthropology and Cultural studies. Students are encouraged to understand and engage with real life contexts and evolve habits of critical thinking for effective problem solving. At the end of the 2 year program students are expected to understand Design processes and methods and be able to conceptualize and prototype solutions to communication problems in various social and cultural contexts. The M Des program is one of the very few in the country that is open to graduates from all disciplines. Design that makes a difference is at its core. The detailed course structure consisting of both core courses and elective courses can be found on Institute website at
           <a class="external free" href="http://mdes.daiict.ac.in/" rel="nofollow">
            http://mdes.daiict.ac.in/
           </a>
          </li>
         </ul>
         <p>
          <b>
           Ph.D. - Doctor of Philosophy
          </b>
         </p>
         <ul>
          <li>
           A three- to five-year program. The doctoral program leading towards the award of the degree of Doctor of Philosophy (Ph.D) provides the students an opportunity to train for independent research as a preparation for a career in academia or in R&amp;D establishments. The program comprises both course and research work. The research work to be undertaken for Ph.D must include original work, and culminates in a thesis to be submitted for the doctoral degree.
          </li>
         </ul>
         <h2>
          <span class="mw-headline" id="Student_achievements">
           Student achievements
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=3" title="Edit section: Student achievements">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h2>
         <ul>
          <li>
           17 students from DA-IICT selected for the prestigious Google Summer Of Code, 2013.
          </li>
          <li>
           Team DA-Developers represented DA-IICT at the Imagine Cup 2013 National Finals and stood third in India for Imagine Cup World Citizenship contest with their app "Read For Blind".
           <sup class="reference" id="cite_ref-3">
            <a href="#cite_note-3">
             [3]
            </a>
           </sup>
          </li>
          <li>
           Team of 4 students stood 3rd at the National Finals for "Samsung USID Design Challenge", 2012 for their app "Location Alarm".
           <sup class="reference" id="cite_ref-4">
            <a href="#cite_note-4">
             [4]
            </a>
           </sup>
          </li>
          <li>
           17 students selected for Google Summer of Code, 2012, the highest number in India and third highest in the world.
          </li>
          <li>
           A student won Innovate4Women Award of the Microsoft Imagine Cup 2010
           <sup class="reference" id="cite_ref-5">
            <a href="#cite_note-5">
             [5]
            </a>
           </sup>
           and One of its team were National Finalist in Microsoft Imagine Cup India.
           <sup class="reference" id="cite_ref-6">
            <a href="#cite_note-6">
             [6]
            </a>
           </sup>
          </li>
          <li>
           Team of 4 students won the Unlimited Potential Multipoint Education Award of the Microsoft Imagine Cup 2009, World Finals.
           <sup class="reference" id="cite_ref-7">
            <a href="#cite_note-7">
             [7]
            </a>
           </sup>
           The same team stood 3rd in the National Finals in the Software Design category of the Microsoft Imagine Cup 2009, India Finals
          </li>
          <li>
           Two students won Google Women Engineering Award in year 2009 and 2010
           <sup class="reference" id="cite_ref-8">
            <a href="#cite_note-8">
             [8]
            </a>
           </sup>
           <sup class="reference" id="cite_ref-9">
            <a href="#cite_note-9">
             [9]
            </a>
           </sup>
          </li>
          <li>
           Two of its teams were winners at the Microsoft, High Performance Computing Scholars Program 2008
           <sup class="reference" id="cite_ref-10">
            <a href="#cite_note-10">
             [10]
            </a>
           </sup>
          </li>
          <li>
           Teams of four students each won the Microsoft Imagine cup for two consecutive years in 2006 and 2007
           <sup class="reference" id="cite_ref-11">
            <a href="#cite_note-11">
             [11]
            </a>
           </sup>
           <sup class="reference" id="cite_ref-12">
            <a href="#cite_note-12">
             [12]
            </a>
           </sup>
           <sup class="reference" id="cite_ref-13">
            <a href="#cite_note-13">
             [13]
            </a>
           </sup>
           <sup class="reference" id="cite_ref-14">
            <a href="#cite_note-14">
             [14]
            </a>
           </sup>
          </li>
          <li>
           Student teams won the TI DSP Design Competition in 2005, 2006 and 2007
           <sup class="reference" id="cite_ref-15">
            <a href="#cite_note-15">
             [15]
            </a>
           </sup>
          </li>
         </ul>
         <p>
          In 2004, three MSc (IT) students of DA-IICT challenged in the Gujarat High Court, the IIMA decision to not offer admission interviews to them citing their eligibility criteria (AIU or AICTE affiliation was needed at that time). The judgement was passed in the favour of students and the CAT eligibility criteria were subsequently modified.
          <sup class="reference" id="cite_ref-16">
           <a href="#cite_note-16">
            [16]
           </a>
          </sup>
         </p>
         <h2>
          <span class="mw-headline" id="Infrastructure">
           Infrastructure
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=4" title="Edit section: Infrastructure">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h2>
         <p>
          DA-IICT has a modern, networked campus with optical fibre cable connectivity between buildings. It has IT infrastructure, computing and communication resources, electronic access controls and a payment system through smart cards.
         </p>
         <p>
          The environment of the institute — a cluster of minimalistic structures in the midst of the trees, shrubs and well-laid out lawns — provides a serene ambience to the campus. The campus has three air-cooled lecture theatres, two with a seating capacity of more than 200 and one with a seating capacity of about 250, with audio and video presentation systems. The classrooms and tutorial rooms are equipped with audio-visual aids and have Internet connectivity.
         </p>
         <p>
          Utilities and services such as the cafeteria, food courts, ATM, medical centre, campus shop, telephone kiosk, photocopying facility, open-air theatre are on the campus.
         </p>
         <h3>
          <span class="mw-headline" id="Laboratory_building">
           Laboratory building
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=5" title="Edit section: Laboratory building">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h3>
         <div class="thumb tright">
          <div class="thumbinner" style="width:222px;">
           <a class="image" href="/wiki/File:Daiict_campus.jpg">
            <img alt="Daiict campus.jpg" class="thumbimage" data-file-height="320" data-file-width="320" height="220" src="//upload.wikimedia.org/wikipedia/commons/thumb/5/54/Daiict_campus.jpg/220px-Daiict_campus.jpg" srcset="//upload.wikimedia.org/wikipedia/commons/5/54/Daiict_campus.jpg 1.5x" width="220"/>
           </a>
           <div class="thumbcaption">
            <div class="magnify">
             <a class="internal" href="/wiki/File:Daiict_campus.jpg" title="Enlarge">
             </a>
            </div>
           </div>
          </div>
         </div>
         <p>
          More than 1200 nodes connected via 100 Mbit/s switches and a 1 Gbit/s fiber backbone form the superstructure of the network. Each computer is at least a Pentium IV multi OS, fully connected terminal. Thus ensuring that there is at least one high-end computer available to each student and faculty on the campus.
         </p>
         <p>
          The laboratory building houses teaching and research laboratories for electronics, communications, computers and networks. More than 800 computers are installed in these laboratories. Students use resources of laboratories (open until midnight) to solve problems, perform developmental experiments and work on projects guided by faculty.
         </p>
         <p>
          By granting 24 hours lab facility and access to the network from each classroom and lecture theater information is made easily accessible from any point on campus. The students are provided a 16 Mbit/s line for their hostel rooms.
         </p>
         <p>
          The lab structure is divided as follows:
         </p>
         <ul>
          <li>
           <b>
            Multimedia labs
           </b>
           have a main Apple Xserver having a 2.5 terabyte capacity, Apple iMate, iBooks (G5) and HP based high-end systems. The software available to students in this lab includes Apple Works, Maya, Adobe Photoshop CS2, Sony Soundforge Pro, AutoCAD and 3DMax.
          </li>
          <li>
           The
           <b>
            Grid lab
           </b>
           has 20 servers build using a Globus toolkit. This lab is where most of the research into service-oriented computing and distributed computing, especially different grid architectures, take place.
          </li>
          <li>
           The
           <b>
            Network lab
           </b>
           allows students to operate and configure networking equipment like routers, mail/http/name servers, and to use and create wireless networks. There are LAN trainer kits and network simulators.
          </li>
          <li>
           <b>
            VLSI lab
           </b>
           consists of three labs: the two main labs have access to the tools required for design and implementation in VLSI including access to Xilinx FPGAs, mentor graphics tools (multi-user licenses) and Cadence tools.
          </li>
          <li>
           <b>
            RF lab
           </b>
           consists of RF equipment including three types of spectrum analyzer: Agilent in the range of 3 kHz to 3 GHz, Hameg around 1 GHz and LG within frequency range of 9 kHz to 2.75 GHz. Signal generators from Agilent that are able to operate over the range of 250 kHz – 3 GHz and Network Analyzers are part of the lab. There are CDMA trainers and Antenna training sets.
          </li>
          <li>
           <b>
            English Language lab
           </b>
           with Linguaphone and Globarena software. Though the software can be used independently, as there is self-monitoring feed back facility for users, there is provision for Teaching Assistants’ help as an additional resource for the students with language handicaps.
          </li>
         </ul>
         <h3>
          <span class="mw-headline" id="Faculty_and_administrative_block">
           Faculty and administrative block
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=6" title="Edit section: Faculty and administrative block">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h3>
         <p>
          The Faculty Building Complex consists of four faculty blocks, each with eighteen faculty rooms and two teaching assistant rooms. The administrative block houses the offices of the director, registar and other support services.
         </p>
         <h3>
          <span class="mw-headline" id="Resource_centre">
           Resource centre
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=7" title="Edit section: Resource centre">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h3>
         <p>
          DAIICT Resource centre have various kind of book related to information technology,electronics, mathematics, science , economics, environment etc. and Daiict has Digital Resource centre of CDs and DVDs.There are many magazine also subscribed.
         </p>
         <h3>
          <span class="mw-headline" id="Sports_and_Cultural_Complex">
           Sports and Cultural Complex
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=8" title="Edit section: Sports and Cultural Complex">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h3>
         <p>
          The Sports and Cultural Complex has facilities for outdoor sports such as cricket, football, basketball, volleyball and indoor games like badminton, table tennis, chess and carom. It has a gymnasium and a music room.
         </p>
         <h3>
          <span class="mw-headline" id="Halls_of_residence">
           Halls of residence
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=9" title="Edit section: Halls of residence">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h3>
         <p>
          There are two residence halls, one for men and one for women. The men's hall has eight wings labelled A to H. Each wing has about 60 rooms. The total capacity of the eight wings is about 900 students on twin sharing basis.
         </p>
         <p>
          The women's hall has two wings, the J and K wings, with a capacity of 195 residents. The women's hall has a guest room for mothers of residents. For students using their own computers in the room, internet facility is provided at a per-semester charge.
         </p>
         <p>
          Hot water (using solar panels), laundry (dhobis come to collect and deliver clothes) and TV rooms with Dish TV are available at both halls of residence. A convenience store, local/STD/ISD facility and student warehouse are available at the men's hall of residence.
         </p>
         <p>
          Residence at the halls is compulsory for B.Tech. students. Male postgraduate students are provided rooms subject to availability. All female post-graduate students, who choose to stay on campus, can be provided accommodation in the women's hall of residence.
         </p>
         <h3>
          <span class="mw-headline" id="Medical_facility">
           Medical facility
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=10" title="Edit section: Medical facility">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h3>
         <p>
          The institute has a Medical Centre with two doctors visiting the centre at specified hours. The students can consult them without any charge. DA-IICT has arrangements with the Apollo and SAL Hospitals which allows the students to be admitted on concessional rates without advanced deposit. All students are covered under the Group Mediclaim Insurance Policy and Personal Accident Insurance Policy. A cashless transaction facility has been provided to the students under the Mediclaim scheme.
         </p>
         <h2>
          <span class="mw-headline" id="Culture_and_student_life">
           Culture and student life
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=11" title="Edit section: Culture and student life">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h2>
         <div class="thumb tright">
          <div class="thumbinner" style="width:222px;">
           <a class="image" href="/wiki/File:Synapse_2015.jpg">
            <img alt="" class="thumbimage" data-file-height="640" data-file-width="960" height="147" src="//upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Synapse_2015.jpg/220px-Synapse_2015.jpg" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Synapse_2015.jpg/330px-Synapse_2015.jpg 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Synapse_2015.jpg/440px-Synapse_2015.jpg 2x" width="220"/>
           </a>
           <div class="thumbcaption">
            <div class="magnify">
             <a class="internal" href="/wiki/File:Synapse_2015.jpg" title="Enlarge">
             </a>
            </div>
            Synapse 2015
           </div>
          </div>
         </div>
         <p>
          Extracurricular activities include solving rural and urban problems, organisation of national level events and workshops, social service, stage and street plays, critical appreciation of films, learning foreign languages, appreciating cultural events organised by SPICMACAY and the like. The college celebrates an annual techno-cultural festival, Synapse, annual sports festival, Concours, and an annual tech festival, iFest. These festivals see participants from various colleges in Gandhinagar and Ahmedabad.
         </p>
         <h2>
          <span class="mw-headline" id="Notable_alumni">
           Notable alumni
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=12" title="Edit section: Notable alumni">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h2>
         <ul>
          <li>
           Chitra Gurnani Daga, CEO &amp; Co-founder of
           <a href="/wiki/Thrillophilia" title="Thrillophilia">
            Thrillophilia
           </a>
           <sup class="reference" id="cite_ref-17">
            <a href="#cite_note-17">
             [17]
            </a>
           </sup>
          </li>
          <li>
           Bhavesh Manglani, Co-Founder of Delhivery
          </li>
          <li>
           Swapnil Khandelwal and Rubish Gupta, Founder of Alma Connect
          </li>
          <li>
           Pavitar Singh, Vice President, Product Development at Sprinklr
          </li>
         </ul>
         <h2>
          <span class="mw-headline" id="See_also">
           See also
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=13" title="Edit section: See also">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h2>
         <ul>
          <li>
           <a href="/wiki/Education_in_India" title="Education in India">
            Education in India
           </a>
          </li>
          <li>
           <a href="/wiki/List_of_universities_in_India" title="List of universities in India">
            List of universities in India
           </a>
          </li>
          <li>
           <a class="mw-redirect" href="/wiki/Universities_and_colleges_in_India" title="Universities and colleges in India">
            Universities and colleges in India
           </a>
          </li>
         </ul>
         <h2>
          <span class="mw-headline" id="Notes">
           Notes
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=14" title="Edit section: Notes">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h2>
         <ol class="references">
          <li id="cite_note-1">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-1">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             TNN, Jan 17, 2015, 07.31pm IST (2015-01-17).
             <a class="external text" href="http://timesofindia.indiatimes.com/city/ahmedabad/DA-IICT-replaces-director-ahead-of-convocation/articleshow/45923777.cms" rel="nofollow">
              "DA-IICT replaces director ahead of convocation"
             </a>
             . The Times of India
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2015-01-20
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.au=TNN%2C+Jan+17%2C+2015%2C+07.31pm+IST&amp;rft.btitle=DA-IICT+replaces+director+ahead+of+convocation&amp;rft.date=2015-01-17&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Ftimesofindia.indiatimes.com%2Fcity%2Fahmedabad%2FDA-IICT-replaces-director-ahead-of-convocation%2Farticleshow%2F45923777.cms&amp;rft.pub=The+Times+of+India&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
            <span class="citation-comment" style="display:none; color:#33aa33">
             CS1 maint: Multiple names: authors list (
             <a href="/wiki/Category:CS1_maint:_Multiple_names:_authors_list" title="Category:CS1 maint: Multiple names: authors list">
              link
             </a>
             )
            </span>
           </span>
          </li>
          <li id="cite_note-2">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-2">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             <a class="external text" href="http://www.relianceadagroup.com/ada/index.html" rel="nofollow">
              "Reliance Dhirubhai Ambani Group - Quicklinks"
             </a>
             . Relianceadagroup.com
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.btitle=Reliance+Dhirubhai+Ambani+Group+-+Quicklinks&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fwww.relianceadagroup.com%2Fada%2Findex.html&amp;rft.pub=Relianceadagroup.com&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-3">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-3">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             witlia (2013-04-23).
             <a class="external text" href="http://www.moneycontrol.com/news/special-videos/microsoft-imagine-cup-a-sneek-peek_856076-1.html" rel="nofollow">
              "Imagine Cup 2013"
             </a>
             . MoneyControl.com
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2013-04-23
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.au=witlia&amp;rft.btitle=Imagine+Cup+2013&amp;rft.date=2013-04-23&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fwww.moneycontrol.com%2Fnews%2Fspecial-videos%2Fmicrosoft-imagine-cup-a-sneek-peek_856076-1.html&amp;rft.pub=MoneyControl.com&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-4">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-4">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <a class="external text" href="http://www.usidfoundation.org/index.php?option=com_content&amp;view=article&amp;id=237&amp;Itemid=1282" rel="nofollow">
             Link to the source http://www.usidfoundation.org/index.php?option=com_content&amp;view=article&amp;id=237&amp;Itemid=1282
            </a>
           </span>
          </li>
          <li id="cite_note-5">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-5">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             witlia (2010-04-30).
             <a class="external text" href="https://web.archive.org/web/20110106132033/http://blogs.msdn.com:80/b/icindia/archive/2010/04/30/innovate4women-awards.aspx" rel="nofollow">
              "Innovate4Women Awards"
             </a>
             . Blogs.msdn.com. Archived from
             <a class="external text" href="http://blogs.msdn.com/b/icindia/archive/2010/04/30/innovate4women-awards.aspx" rel="nofollow">
              the original
             </a>
             on 2011-01-06
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.au=witlia&amp;rft.btitle=Innovate4Women+Awards&amp;rft.date=2010-04-30&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fblogs.msdn.com%2Fb%2Ficindia%2Farchive%2F2010%2F04%2F30%2Finnovate4women-awards.aspx&amp;rft.pub=Blogs.msdn.com&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-6">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-6">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             witlia (2010-04-05).
             <a class="external text" href="https://web.archive.org/web/20100406192111/http://blogs.msdn.com:80/icindia/archive/2010/04/05/mmlia-results.aspx" rel="nofollow">
              "MMLIA Preliminary Results - Imagine Cup India - Site Home - MSDN Blogs"
             </a>
             . Blogs.msdn.com. Archived from
             <a class="external text" href="http://blogs.msdn.com/icindia/archive/2010/04/05/mmlia-results.aspx" rel="nofollow">
              the original
             </a>
             on 2010-04-06
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.au=witlia&amp;rft.btitle=MMLIA+Preliminary+Results+-+Imagine+Cup+India+-+Site+Home+-+MSDN+Blogs&amp;rft.date=2010-04-05&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fblogs.msdn.com%2Ficindia%2Farchive%2F2010%2F04%2F05%2Fmmlia-results.aspx&amp;rft.pub=Blogs.msdn.com&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-7">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-7">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             <a class="external text" href="http://news.microsoft.com/2009/07/07/microsoft-announces-imagine-cup-2009-worldwide-winners/" rel="nofollow">
              "Microsoft Announces Imagine Cup 2009 Worldwide Winners"
             </a>
             .
             <i>
              News Center
             </i>
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2016-01-19
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.atitle=Microsoft+Announces+Imagine+Cup+2009+Worldwide+Winners&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fnews.microsoft.com%2F2009%2F07%2F07%2Fmicrosoft-announces-imagine-cup-2009-worldwide-winners%2F&amp;rft.jtitle=News+Center&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Ajournal">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-8">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-8">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             <a class="external text" href="http://www.google.co.in/jobs/womeninengineering/2010/award.html" rel="nofollow">
              "Google India Women in Engineering Award"
             </a>
             . Google.co.in
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.btitle=Google+India+Women+in+Engineering+Award&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fwww.google.co.in%2Fjobs%2Fwomeninengineering%2F2010%2Faward.html&amp;rft.pub=Google.co.in&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-9">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-9">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             <a class="external text" href="http://www.google.co.in/jobs/womeninengineering/2010/award2009.html" rel="nofollow">
              "Google India Women in Engineering Award"
             </a>
             . Google.co.in
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.btitle=Google+India+Women+in+Engineering+Award&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fwww.google.co.in%2Fjobs%2Fwomeninengineering%2F2010%2Faward2009.html&amp;rft.pub=Google.co.in&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-10">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-10">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             <a class="external text" href="http://www.microsoft.com/india/hpcacad/" rel="nofollow">
              "Microsoft Scholar Vs Scholar 2008"
             </a>
             . Microsoft.com
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.btitle=Microsoft+Scholar+Vs+Scholar+2008&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fwww.microsoft.com%2Findia%2Fhpcacad%2F&amp;rft.pub=Microsoft.com&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-11">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-11">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <a class="external text" href="http://www.ciol.com/da-iict-wins-microsoft-imagine-cup-national-finals/" rel="nofollow">
             DA-IICT wins Microosoft Imagine Cup National Finals
            </a>
           </span>
          </li>
          <li id="cite_note-12">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-12">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             <a class="external text" href="http://www.thehindubusinessline.com/2007/05/07/stories/2007050700960200.htm" rel="nofollow">
              "Microsoft Cup Finalists"
             </a>
             . Thehindubusinessline.com. 2007-05-07
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.btitle=Microsoft+Cup+Finalists&amp;rft.date=2007-05-07&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fwww.thehindubusinessline.com%2F2007%2F05%2F07%2Fstories%2F2007050700960200.htm&amp;rft.pub=Thehindubusinessline.com&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-13">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-13">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             <a class="external text" href="http://www.efytimes.com/efytimes/fullnews.asp?edid=18743" rel="nofollow">
              "Microsoft Imagine Cup India 2007"
             </a>
             . Efytimes.com
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.btitle=Microsoft+Imagine+Cup+India+2007&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fwww.efytimes.com%2Fefytimes%2Ffullnews.asp%3Fedid%3D18743&amp;rft.pub=Efytimes.com&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-14">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-14">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             <a class="external text" href="http://www.hinduonnet.com/thehindu/thscrip/print.pl?file=2006070303511300.htm&amp;date=2006/07/03/&amp;prd=th&amp;" rel="nofollow">
              "Indians' Sonic Map impresses Gates"
             </a>
             . Hinduonnet.com
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.btitle=Indians%27+Sonic+Map+impresses+Gates&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Fwww.hinduonnet.com%2Fthehindu%2Fthscrip%2Fprint.pl%3Ffile%3D2006070303511300.htm%26date%3D2006%2F07%2F03%2F%26prd%3Dth%26&amp;rft.pub=Hinduonnet.com&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
           </span>
          </li>
          <li id="cite_note-15">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-15">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            Presentation of Winning Entry in TI India 2005 Design Contest: "OmniBook" by Deepak Jagdish and Rahul Sawhney of DA-IICT
            <a class="external autonumber" href="http://tii.developerconference.ext.ti.com/symposium.html" rel="nofollow">
             [1]
            </a>
           </span>
          </li>
          <li id="cite_note-16">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-16">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <cite class="citation web">
             TNN, Apr 16, 2005, 09.57pm IST (2005-04-16).
             <a class="external text" href="http://articles.timesofindia.indiatimes.com/2005-04-16/ahmedabad/27853985_1_cat-group-iim-ahmedabad-cat-bulletin" rel="nofollow">
              "High Court rules against CAT stipulation"
             </a>
             . The Times of India
             <span class="reference-accessdate">
              . Retrieved
              <span class="nowrap">
               2010-12-31
              </span>
             </span>
             .
            </cite>
            <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3ADhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;rft.au=TNN%2C+Apr+16%2C+2005%2C+09.57pm+IST&amp;rft.btitle=High+Court+rules+against+CAT+stipulation&amp;rft.date=2005-04-16&amp;rft.genre=unknown&amp;rft_id=http%3A%2F%2Farticles.timesofindia.indiatimes.com%2F2005-04-16%2Fahmedabad%2F27853985_1_cat-group-iim-ahmedabad-cat-bulletin&amp;rft.pub=The+Times+of+India&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook">
             <span style="display:none;">
             </span>
            </span>
            <span class="citation-comment" style="display:none; color:#33aa33">
             CS1 maint: Multiple names: authors list (
             <a href="/wiki/Category:CS1_maint:_Multiple_names:_authors_list" title="Category:CS1 maint: Multiple names: authors list">
              link
             </a>
             )
            </span>
           </span>
          </li>
          <li id="cite_note-17">
           <span class="mw-cite-backlink">
            <b>
             <a href="#cite_ref-17">
              ^
             </a>
            </b>
           </span>
           <span class="reference-text">
            <a class="external text" href="http://www.woolor.com/e-company/entertainment/thrillophilia/" rel="nofollow">
             thrillophilia Woolor
            </a>
           </span>
          </li>
         </ol>
         <h2>
          <span class="mw-headline" id="External_links">
           External links
          </span>
          <span class="mw-editsection">
           <span class="mw-editsection-bracket">
            [
           </span>
           <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit&amp;section=15" title="Edit section: External links">
            edit
           </a>
           <span class="mw-editsection-bracket">
            ]
           </span>
          </span>
         </h2>
         <table class="mbox-small plainlinks sistersitebox" role="presentation" style="border:1px solid #aaa;background-color:#f9f9f9">
          <tr>
           <td class="mbox-image">
            <a class="image" href="/wiki/File:Commons-logo.svg">
             <img alt="" class="noviewer" data-file-height="1376" data-file-width="1024" height="40" src="//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/30px-Commons-logo.svg.png" srcset="//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/45px-Commons-logo.svg.png 1.5x, //upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/59px-Commons-logo.svg.png 2x" width="30"/>
            </a>
           </td>
           <td class="mbox-text plainlist">
            Wikimedia Commons has media related to
            <i>
             <b>
              <a class="extiw" href="https://commons.wikimedia.org/wiki/Category:Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology" title="commons:Category:Dhirubhai Ambani Institute of Information and Communication Technology">
               Dhirubhai Ambani Institute of Information and Communication Technology
              </a>
             </b>
            </i>
            .
           </td>
          </tr>
         </table>
         <ul>
          <li>
           <span class="official-website">
            <span class="url">
             <a class="external text" href="http://www.daiict.ac.in" rel="nofollow">
              Official website
             </a>
            </span>
           </span>
          </li>
         </ul>
         <div aria-labelledby="IIIT" class="navbox" role="navigation" style="padding:3px">
          <table class="nowraplinks collapsible autocollapse navbox-inner" style="border-spacing:0;background:transparent;color:inherit">
           <tr>
            <th class="navbox-title" colspan="2" scope="col">
             <div class="plainlinks hlist navbar mini">
              <ul>
               <li class="nv-view">
                <a href="/wiki/Template:IIIT" title="Template:IIIT">
                 <abbr style=";;background:none transparent;border:none;" title="View this template">
                  v
                 </abbr>
                </a>
               </li>
               <li class="nv-talk">
                <a href="/wiki/Template_talk:IIIT" title="Template talk:IIIT">
                 <abbr style=";;background:none transparent;border:none;" title="Discuss this template">
                  t
                 </abbr>
                </a>
               </li>
               <li class="nv-edit">
                <a class="external text" href="//en.wikipedia.org/w/index.php?title=Template:IIIT&amp;action=edit">
                 <abbr style=";;background:none transparent;border:none;" title="Edit this template">
                  e
                 </abbr>
                </a>
               </li>
              </ul>
             </div>
             <div id="IIIT" style="font-size:114%">
              <a href="/wiki/Indian_Institutes_of_Information_Technology" title="Indian Institutes of Information Technology">
               IIIT
              </a>
             </div>
            </th>
           </tr>
           <tr style="height:2px">
            <td colspan="2">
            </td>
           </tr>
           <tr>
            <th class="navbox-group" scope="row" style="text-align: left;">
             <a class="mw-redirect" href="/wiki/MHRD" title="MHRD">
              MHRD
             </a>
             –funded
            </th>
            <td class="navbox-list navbox-odd hlist" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
             <div style="padding:0em 0.25em">
              <ul>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Allahabad" title="Indian Institute of Information Technology, Allahabad">
                 Allahabad
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology_and_Management,_Gwalior" title="Indian Institute of Information Technology and Management, Gwalior">
                 Gwalior
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Design_and_Manufacturing,_Jabalpur" title="Indian Institute of Information Technology, Design and Manufacturing, Jabalpur">
                 Jabalpur
                </a>
               </li>
               <li>
                <a class="mw-redirect" href="/wiki/Indian_Institute_of_Information_Technology_Design_%26_Manufacturing_Kancheepuram" title="Indian Institute of Information Technology Design &amp; Manufacturing Kancheepuram">
                 Kancheepuram
                </a>
               </li>
               <li>
                <a class="mw-redirect" href="/wiki/Indian_Institute_of_Information_Technology,_Kurnool" title="Indian Institute of Information Technology, Kurnool">
                 Kurnool
                </a>
               </li>
              </ul>
             </div>
            </td>
           </tr>
           <tr style="height:2px">
            <td colspan="2">
            </td>
           </tr>
           <tr>
            <th class="navbox-group" scope="row" style="text-align: left;">
             <a href="/wiki/Public%E2%80%93private_partnership" title="Public–private partnership">
              PPP
             </a>
             –funded
            </th>
            <td class="navbox-list navbox-even hlist" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
             <div style="padding:0em 0.25em">
              <ul>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Dharwad" title="Indian Institute of Information Technology, Dharwad">
                 Dharwad
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Guwahati" title="Indian Institute of Information Technology, Guwahati">
                 Guwahati
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Kalyani" title="Indian Institute of Information Technology, Kalyani">
                 Kalyani
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Kota" title="Indian Institute of Information Technology, Kota">
                 Kota
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Kottayam" title="Indian Institute of Information Technology, Kottayam">
                 Kottayam
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Lucknow" title="Indian Institute of Information Technology, Lucknow">
                 Lucknow
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Manipur" title="Indian Institute of Information Technology, Manipur">
                 Manipur
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Nagpur" title="Indian Institute of Information Technology, Nagpur">
                 Nagpur
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Pune" title="Indian Institute of Information Technology, Pune">
                 Pune
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Ranchi" title="Indian Institute of Information Technology, Ranchi">
                 Ranchi
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Sonepat" title="Indian Institute of Information Technology, Sonepat">
                 Sonepat
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Sri_City" title="Indian Institute of Information Technology, Sri City">
                 Sri City
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Srirangam" title="Indian Institute of Information Technology, Srirangam">
                 Trichy
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology_Una" title="Indian Institute of Information Technology Una">
                 Una
                </a>
               </li>
               <li>
                <a href="/wiki/Indian_Institute_of_Information_Technology,_Vadodara" title="Indian Institute of Information Technology, Vadodara">
                 Vadodara
                </a>
               </li>
              </ul>
             </div>
            </td>
           </tr>
           <tr style="height:2px">
            <td colspan="2">
            </td>
           </tr>
           <tr>
            <th class="navbox-group" scope="row" style="text-align: left;">
             State-funded
            </th>
            <td class="navbox-list navbox-odd hlist" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
             <div style="padding:0em 0.25em">
              <ul>
               <li>
                <a href="/wiki/International_Institute_of_Information_Technology,_Bhubaneswar" title="International Institute of Information Technology, Bhubaneswar">
                 Bhubaneswar
                </a>
               </li>
               <li>
                <a class="mw-redirect" href="/wiki/Indraprastha_Institute_of_Information_Technology,_Delhi" title="Indraprastha Institute of Information Technology, Delhi">
                 Delhi
                </a>
               </li>
               <li>
                <abbr title="International Institute of Information Technology, Naya Raipur">
                 Naya Raipur
                </abbr>
               </li>
              </ul>
             </div>
            </td>
           </tr>
           <tr style="height:2px">
            <td colspan="2">
            </td>
           </tr>
           <tr>
            <th class="navbox-group" scope="row" style="text-align: left;">
             Private
            </th>
            <td class="navbox-list navbox-even hlist" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
             <div style="padding:0em 0.25em">
              <ul>
               <li>
                <a href="/wiki/International_Institute_of_Information_Technology,_Bangalore" title="International Institute of Information Technology, Bangalore">
                 Bangalore
                </a>
               </li>
               <li>
                <a href="/wiki/International_Institute_of_Information_Technology,_Hyderabad" title="International Institute of Information Technology, Hyderabad">
                 Hyderabad
                </a>
               </li>
               <li>
                <a href="/wiki/International_Institute_of_Information_Technology,_Pune" title="International Institute of Information Technology, Pune">
                 Pune
                </a>
               </li>
              </ul>
             </div>
            </td>
           </tr>
          </table>
         </div>
         <div aria-labelledby="Reliance_Anil_Dhirubhai_Ambani_Group" class="navbox" role="navigation" style="padding:3px">
          <table class="nowraplinks hlist collapsible collapsed navbox-inner" style="border-spacing:0;background:transparent;color:inherit">
           <tr>
            <th class="navbox-title" colspan="2" scope="col">
             <div class="plainlinks hlist navbar mini">
              <ul>
               <li class="nv-view">
                <a href="/wiki/Template:Reliance_Anil_Dhirubhai_Ambani_Group" title="Template:Reliance Anil Dhirubhai Ambani Group">
                 <abbr style=";;background:none transparent;border:none;" title="View this template">
                  v
                 </abbr>
                </a>
               </li>
               <li class="nv-talk">
                <a href="/wiki/Template_talk:Reliance_Anil_Dhirubhai_Ambani_Group" title="Template talk:Reliance Anil Dhirubhai Ambani Group">
                 <abbr style=";;background:none transparent;border:none;" title="Discuss this template">
                  t
                 </abbr>
                </a>
               </li>
               <li class="nv-edit">
                <a class="external text" href="//en.wikipedia.org/w/index.php?title=Template:Reliance_Anil_Dhirubhai_Ambani_Group&amp;action=edit">
                 <abbr style=";;background:none transparent;border:none;" title="Edit this template">
                  e
                 </abbr>
                </a>
               </li>
              </ul>
             </div>
             <div id="Reliance_Anil_Dhirubhai_Ambani_Group" style="font-size:114%">
              <a href="/wiki/Reliance_Anil_Dhirubhai_Ambani_Group" title="Reliance Anil Dhirubhai Ambani Group">
               Reliance Anil Dhirubhai Ambani Group
              </a>
             </div>
            </th>
           </tr>
           <tr style="height:2px">
            <td colspan="2">
            </td>
           </tr>
           <tr>
            <th class="navbox-group" scope="row">
             Companies
            </th>
            <td class="navbox-list navbox-odd" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
             <div style="padding:0em 0.25em">
             </div>
             <table class="nowraplinks navbox-subgroup" style="border-spacing:0">
              <tr>
               <th class="navbox-group" scope="row">
                Communication
               </th>
               <td class="navbox-list navbox-odd" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
                <div style="padding:0em 0.25em">
                 <ul>
                  <li>
                   <a href="/wiki/Reliance_Communications" title="Reliance Communications">
                    Reliance Communications
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Zapak" title="Zapak">
                    Zapak
                   </a>
                  </li>
                  <li>
                   <a class="new" href="/w/index.php?title=Java_Green&amp;action=edit&amp;redlink=1" title="Java Green (page does not exist)">
                    Java Green
                   </a>
                  </li>
                  <li>
                   <a class="mw-redirect" href="/wiki/Reliance_World" title="Reliance World">
                    Reliance World
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Fiber-Optic_Link_Around_the_Globe" title="Fiber-Optic Link Around the Globe">
                    Fiber-Optic Link Around the Globe
                   </a>
                  </li>
                 </ul>
                </div>
               </td>
              </tr>
              <tr style="height:2px">
               <td colspan="2">
               </td>
              </tr>
              <tr>
               <th class="navbox-group" scope="row">
                Power
               </th>
               <td class="navbox-list navbox-even" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
                <div style="padding:0em 0.25em">
                 <ul>
                  <li>
                   <a href="/wiki/Reliance_Power" title="Reliance Power">
                    Reliance Power
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Reliance_Natural_Resources_Limited" title="Reliance Natural Resources Limited">
                    Reliance Natural Resources
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Dhirubhai_Ambani_Solar_Park" title="Dhirubhai Ambani Solar Park">
                    Dhirubhai Ambani Solar Park
                   </a>
                  </li>
                 </ul>
                </div>
               </td>
              </tr>
              <tr style="height:2px">
               <td colspan="2">
               </td>
              </tr>
              <tr>
               <th class="navbox-group" scope="row">
                Infrastructure
               </th>
               <td class="navbox-list navbox-odd" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
                <div style="padding:0em 0.25em">
                 <ul>
                  <li>
                   <a href="/wiki/Reliance_Infrastructure" title="Reliance Infrastructure">
                    Reliance Infrastructure
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Mumbai_Metro" title="Mumbai Metro">
                    Mumbai Metro One
                   </a>
                  </li>
                  <li>
                   <a class="mw-redirect" href="/wiki/Nanded_Airport" title="Nanded Airport">
                    Nanded Airport
                   </a>
                  </li>
                 </ul>
                </div>
               </td>
              </tr>
              <tr style="height:2px">
               <td colspan="2">
               </td>
              </tr>
              <tr>
               <th class="navbox-group" scope="row">
                Knowledge
               </th>
               <td class="navbox-list navbox-even" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
                <div style="padding:0em 0.25em">
                 <ul>
                  <li>
                   <a class="mw-redirect" href="/wiki/Dhirubhai_Ambani_Knowledge_Center" title="Dhirubhai Ambani Knowledge Center">
                    Dhirubhai Ambani Knowledge Center
                   </a>
                  </li>
                  <li>
                   <a class="mw-redirect" href="/wiki/Reliance_Venture" title="Reliance Venture">
                    Reliance Venture
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Reliance_Health" title="Reliance Health">
                    Reliance Health
                   </a>
                  </li>
                 </ul>
                </div>
               </td>
              </tr>
              <tr style="height:2px">
               <td colspan="2">
               </td>
              </tr>
              <tr>
               <th class="navbox-group" scope="row">
                Media Delivery Channels
               </th>
               <td class="navbox-list navbox-odd" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
                <div style="padding:0em 0.25em">
                 <ul>
                  <li>
                   <a class="mw-redirect" href="/wiki/BIG_Cinemas" title="BIG Cinemas">
                    BIG Cinemas
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/BIGFlix" title="BIGFlix">
                    BIGFlix
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/BIG_FM_92.7" title="BIG FM 92.7">
                    BIG FM 92.7
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Reliance_Digital_TV" title="Reliance Digital TV">
                    BIG TV
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/BIGADDA" title="BIGADDA">
                    BIGADDA
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/BIG_Star_Entertainment_Awards" title="BIG Star Entertainment Awards">
                    BIG Star Entertainment Awards
                   </a>
                  </li>
                 </ul>
                </div>
               </td>
              </tr>
              <tr style="height:2px">
               <td colspan="2">
               </td>
              </tr>
              <tr>
               <th class="navbox-group" scope="row">
                Media Software
               </th>
               <td class="navbox-list navbox-even" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
                <div style="padding:0em 0.25em">
                 <ul>
                  <li>
                   <a href="/wiki/Reliance_MediaWorks" title="Reliance MediaWorks">
                    Reliance MediaWorks
                   </a>
                  </li>
                  <li>
                   <a class="mw-redirect" href="/wiki/Reliance_BIG_Entertainment" title="Reliance BIG Entertainment">
                    BIG Entertainment
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Big_CBS_Prime" title="Big CBS Prime">
                    Big CBS Prime
                   </a>
                  </li>
                  <li>
                   <a class="mw-redirect" href="/wiki/Big_CBS_Spark" title="Big CBS Spark">
                    Big CBS Spark
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Big_CBS_Love" title="Big CBS Love">
                    Big CBS Love
                   </a>
                  </li>
                 </ul>
                </div>
               </td>
              </tr>
              <tr style="height:2px">
               <td colspan="2">
               </td>
              </tr>
              <tr>
               <th class="navbox-group" scope="row">
                Finance Companies
               </th>
               <td class="navbox-list navbox-odd" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
                <div style="padding:0em 0.25em">
                 <ul>
                  <li>
                   <a href="/wiki/Reliance_Capital" title="Reliance Capital">
                    Reliance Capital
                   </a>
                  </li>
                  <li>
                   <a class="mw-redirect" href="/wiki/Reliance_General_Insurance" title="Reliance General Insurance">
                    Reliance General Insurance
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Reliance_Life_Insurance" title="Reliance Life Insurance">
                    Reliance Life Insurance
                   </a>
                  </li>
                  <li>
                   <a href="/wiki/Reliance_Anil_Dhirubhai_Ambani_Group" title="Reliance Anil Dhirubhai Ambani Group">
                    Reliance Anil Dhirubhai Ambani Group
                   </a>
                  </li>
                 </ul>
                </div>
               </td>
              </tr>
             </table>
            </td>
           </tr>
           <tr style="height:2px">
            <td colspan="2">
            </td>
           </tr>
           <tr>
            <th class="navbox-group" scope="row">
             Notable non-Indian Companies
            </th>
            <td class="navbox-list navbox-even" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
             <div style="padding:0em 0.25em">
              <ul>
               <li>
                <a href="/wiki/Lowry_Digital" title="Lowry Digital">
                 Lowry Digital
                </a>
               </li>
               <li>
                <a href="/wiki/Amblin_Partners" title="Amblin Partners">
                 Amblin Partners
                </a>
                (Part)
                <ul>
                 <li>
                  <a href="/wiki/Amblin_Entertainment" title="Amblin Entertainment">
                   Amblin Entertainment
                  </a>
                 </li>
                 <li>
                  <a href="/wiki/DreamWorks" title="DreamWorks">
                   DreamWorks
                  </a>
                 </li>
                 <li>
                  <a href="/wiki/Amblin_Television" title="Amblin Television">
                   Amblin Television
                  </a>
                 </li>
                </ul>
               </li>
               <li>
                <a class="mw-redirect" href="/wiki/Vanco" title="Vanco">
                 Vanco
                </a>
               </li>
               <li>
                <a href="/wiki/Codemasters" title="Codemasters">
                 Codemasters
                </a>
               </li>
              </ul>
             </div>
            </td>
           </tr>
           <tr style="height:2px">
            <td colspan="2">
            </td>
           </tr>
           <tr>
            <th class="navbox-group" scope="row">
             Technological Institute
            </th>
            <td class="navbox-list navbox-odd" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
             <div style="padding:0em 0.25em">
              <ul>
               <li>
                <strong class="selflink">
                 DA-IICT
                </strong>
               </li>
              </ul>
             </div>
            </td>
           </tr>
           <tr style="height:2px">
            <td colspan="2">
            </td>
           </tr>
           <tr>
            <th class="navbox-group" scope="row">
             Notable People
            </th>
            <td class="navbox-list navbox-even" style="text-align:left;border-left-width:2px;border-left-style:solid;width:100%;padding:0px">
             <div style="padding:0em 0.25em">
              <ul>
               <li>
                <a href="/wiki/Dhirubhai_Ambani" title="Dhirubhai Ambani">
                 Dhirubhai Ambani
                </a>
               </li>
               <li>
                <a href="/wiki/Anil_Ambani" title="Anil Ambani">
                 Anil Ambani
                </a>
               </li>
               <li>
                <a href="/wiki/Tina_Ambani" title="Tina Ambani">
                 Tina Ambani
                </a>
               </li>
               <li>
                <a href="/wiki/Lalit_Jalan" title="Lalit Jalan">
                 Lalit Jalan
                </a>
               </li>
              </ul>
             </div>
            </td>
           </tr>
          </table>
         </div>
         <!-- 
    NewPP limit report
    Parsed by mw1252
    Cached time: 20170212130223
    Cache expiry: 2592000
    Dynamic content: false
    CPU time usage: 0.236 seconds
    Real time usage: 0.292 seconds
    Preprocessor visited node count: 1521/1000000
    Preprocessor generated node count: 0/1500000
    Post‐expand include size: 69258/2097152 bytes
    Template argument size: 1508/2097152 bytes
    Highest expansion depth: 12/40
    Expensive parser function count: 0/500
    Lua time usage: 0.103/10.000 seconds
    Lua memory usage: 5.45 MB/50 MB
    -->
         <!--
    Transclusion expansion time report (%,ms,calls,template)
    100.00%  221.150      1 -total
     31.53%   69.726      1 Template:Infobox_University
     27.54%   60.914     13 Template:Cite_web
     26.37%   58.309      1 Template:Infobox
     13.41%   29.666      1 Template:Coord
      9.93%   21.962      1 Template:Convert
      7.91%   17.483      3 Template:Navbox
      6.55%   14.486      1 Template:Commons_category
      5.32%   11.762      1 Template:Commons
      5.19%   11.467      2 Template:Br_separated_entries
    -->
         <!-- Saved in parser cache with key enwiki:pcache:idhash:400258-0!*!0!!en!4!* and timestamp 20170212130222 and revision id 765059875
     -->
         <noscript>
          <img alt="" height="1" src="//en.wikipedia.org/wiki/Special:CentralAutoLogin/start?type=1x1" style="border: none; position: absolute;" title="" width="1"/>
         </noscript>
        </div>
        <div class="printfooter">
         Retrieved from "
         <a dir="ltr" href="https://en.wikipedia.org/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;oldid=765059875">
          https://en.wikipedia.org/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;oldid=765059875
         </a>
         "
        </div>
        <div class="catlinks" data-mw="interface" id="catlinks">
         <div class="mw-normal-catlinks" id="mw-normal-catlinks">
          <a href="/wiki/Help:Category" title="Help:Category">
           Categories
          </a>
          :
          <ul>
           <li>
            <a href="/wiki/Category:Universities_and_colleges_in_Gujarat" title="Category:Universities and colleges in Gujarat">
             Universities and colleges in Gujarat
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Engineering_colleges_in_Gujarat" title="Category:Engineering colleges in Gujarat">
             Engineering colleges in Gujarat
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Education_in_Gandhinagar" title="Category:Education in Gandhinagar">
             Education in Gandhinagar
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Reliance_Anil_Dhirubhai_Ambani_Group" title="Category:Reliance Anil Dhirubhai Ambani Group">
             Reliance Anil Dhirubhai Ambani Group
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Communications_in_Gujarat" title="Category:Communications in Gujarat">
             Communications in Gujarat
            </a>
           </li>
           <li>
            <a href="/wiki/Category:2001_establishments_in_India" title="Category:2001 establishments in India">
             2001 establishments in India
            </a>
           </li>
          </ul>
         </div>
         <div class="mw-hidden-catlinks mw-hidden-cats-hidden" id="mw-hidden-catlinks">
          Hidden categories:
          <ul>
           <li>
            <a href="/wiki/Category:CS1_maint:_Multiple_names:_authors_list" title="Category:CS1 maint: Multiple names: authors list">
             CS1 maint: Multiple names: authors list
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Coordinates_on_Wikidata" title="Category:Coordinates on Wikidata">
             Coordinates on Wikidata
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Pages_using_deprecated_image_syntax" title="Category:Pages using deprecated image syntax">
             Pages using deprecated image syntax
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Pages_using_infobox_university_with_unknown_parameters" title="Category:Pages using infobox university with unknown parameters">
             Pages using infobox university with unknown parameters
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Commons_category_with_page_title_same_as_on_Wikidata" title="Category:Commons category with page title same as on Wikidata">
             Commons category with page title same as on Wikidata
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div class="visualClear">
        </div>
       </div>
      </div>
      <div id="mw-navigation">
       <h2>
        Navigation menu
       </h2>
       <div id="mw-head">
        <div aria-labelledby="p-personal-label" class="" id="p-personal" role="navigation">
         <h3 id="p-personal-label">
          Personal tools
         </h3>
         <ul>
          <li id="pt-anonuserpage">
           Not logged in
          </li>
          <li id="pt-anontalk">
           <a accesskey="n" href="/wiki/Special:MyTalk" title="Discussion about edits from this IP address [n]">
            Talk
           </a>
          </li>
          <li id="pt-anoncontribs">
           <a accesskey="y" href="/wiki/Special:MyContributions" title="A list of edits made from this IP address [y]">
            Contributions
           </a>
          </li>
          <li id="pt-createaccount">
           <a href="/w/index.php?title=Special:CreateAccount&amp;returnto=Dhirubhai+Ambani+Institute+of+Information+and+Communication+Technology" title="You are encouraged to create an account and log in; however, it is not mandatory">
            Create account
           </a>
          </li>
          <li id="pt-login">
           <a accesskey="o" href="/w/index.php?title=Special:UserLogin&amp;returnto=Dhirubhai+Ambani+Institute+of+Information+and+Communication+Technology" title="You're encouraged to log in; however, it's not mandatory. [o]">
            Log in
           </a>
          </li>
         </ul>
        </div>
        <div id="left-navigation">
         <div aria-labelledby="p-namespaces-label" class="vectorTabs" id="p-namespaces" role="navigation">
          <h3 id="p-namespaces-label">
           Namespaces
          </h3>
          <ul>
           <li class="selected" id="ca-nstab-main">
            <span>
             <a accesskey="c" href="/wiki/Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology" title="View the content page [c]">
              Article
             </a>
            </span>
           </li>
           <li id="ca-talk">
            <span>
             <a accesskey="t" href="/wiki/Talk:Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology" rel="discussion" title="Discussion about the content page [t]">
              Talk
             </a>
            </span>
           </li>
          </ul>
         </div>
         <div aria-labelledby="p-variants-label" class="vectorMenu emptyPortlet" id="p-variants" role="navigation">
          <h3 id="p-variants-label">
           <span>
            Variants
           </span>
           <a href="#">
           </a>
          </h3>
          <div class="menu">
           <ul>
           </ul>
          </div>
         </div>
        </div>
        <div id="right-navigation">
         <div aria-labelledby="p-views-label" class="vectorTabs" id="p-views" role="navigation">
          <h3 id="p-views-label">
           Views
          </h3>
          <ul>
           <li class="selected" id="ca-view">
            <span>
             <a href="/wiki/Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology">
              Read
             </a>
            </span>
           </li>
           <li id="ca-edit">
            <span>
             <a accesskey="e" href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=edit" title="Edit this page [e]">
              Edit
             </a>
            </span>
           </li>
           <li class="collapsible" id="ca-history">
            <span>
             <a accesskey="h" href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=history" title="Past revisions of this page [h]">
              View history
             </a>
            </span>
           </li>
          </ul>
         </div>
         <div aria-labelledby="p-cactions-label" class="vectorMenu emptyPortlet" id="p-cactions" role="navigation">
          <h3 id="p-cactions-label">
           <span>
            More
           </span>
           <a href="#">
           </a>
          </h3>
          <div class="menu">
           <ul>
           </ul>
          </div>
         </div>
         <div id="p-search" role="search">
          <h3>
           <label for="searchInput">
            Search
           </label>
          </h3>
          <form action="/w/index.php" id="searchform">
           <div id="simpleSearch">
            <input accesskey="f" id="searchInput" name="search" placeholder="Search Wikipedia" title="Search Wikipedia [f]" type="search"/>
            <input name="title" type="hidden" value="Special:Search"/>
            <input class="searchButton mw-fallbackSearchButton" id="mw-searchButton" name="fulltext" title="Search Wikipedia for this text" type="submit" value="Search"/>
            <input class="searchButton" id="searchButton" name="go" title="Go to a page with this exact name if it exists" type="submit" value="Go"/>
           </div>
          </form>
         </div>
        </div>
       </div>
       <div id="mw-panel">
        <div id="p-logo" role="banner">
         <a class="mw-wiki-logo" href="/wiki/Main_Page" title="Visit the main page">
         </a>
        </div>
        <div aria-labelledby="p-navigation-label" class="portal" id="p-navigation" role="navigation">
         <h3 id="p-navigation-label">
          Navigation
         </h3>
         <div class="body">
          <ul>
           <li id="n-mainpage-description">
            <a accesskey="z" href="/wiki/Main_Page" title="Visit the main page [z]">
             Main page
            </a>
           </li>
           <li id="n-contents">
            <a href="/wiki/Portal:Contents" title="Guides to browsing Wikipedia">
             Contents
            </a>
           </li>
           <li id="n-featuredcontent">
            <a href="/wiki/Portal:Featured_content" title="Featured content – the best of Wikipedia">
             Featured content
            </a>
           </li>
           <li id="n-currentevents">
            <a href="/wiki/Portal:Current_events" title="Find background information on current events">
             Current events
            </a>
           </li>
           <li id="n-randompage">
            <a accesskey="x" href="/wiki/Special:Random" title="Load a random article [x]">
             Random article
            </a>
           </li>
           <li id="n-sitesupport">
            <a href="https://donate.wikimedia.org/wiki/Special:FundraiserRedirector?utm_source=donate&amp;utm_medium=sidebar&amp;utm_campaign=C13_en.wikipedia.org&amp;uselang=en" title="Support us">
             Donate to Wikipedia
            </a>
           </li>
           <li id="n-shoplink">
            <a href="//shop.wikimedia.org" title="Visit the Wikipedia store">
             Wikipedia store
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div aria-labelledby="p-interaction-label" class="portal" id="p-interaction" role="navigation">
         <h3 id="p-interaction-label">
          Interaction
         </h3>
         <div class="body">
          <ul>
           <li id="n-help">
            <a href="/wiki/Help:Contents" title="Guidance on how to use and edit Wikipedia">
             Help
            </a>
           </li>
           <li id="n-aboutsite">
            <a href="/wiki/Wikipedia:About" title="Find out about Wikipedia">
             About Wikipedia
            </a>
           </li>
           <li id="n-portal">
            <a href="/wiki/Wikipedia:Community_portal" title="About the project, what you can do, where to find things">
             Community portal
            </a>
           </li>
           <li id="n-recentchanges">
            <a accesskey="r" href="/wiki/Special:RecentChanges" title="A list of recent changes in the wiki [r]">
             Recent changes
            </a>
           </li>
           <li id="n-contactpage">
            <a href="//en.wikipedia.org/wiki/Wikipedia:Contact_us" title="How to contact Wikipedia">
             Contact page
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div aria-labelledby="p-tb-label" class="portal" id="p-tb" role="navigation">
         <h3 id="p-tb-label">
          Tools
         </h3>
         <div class="body">
          <ul>
           <li id="t-whatlinkshere">
            <a accesskey="j" href="/wiki/Special:WhatLinksHere/Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology" title="List of all English Wikipedia pages containing links to this page [j]">
             What links here
            </a>
           </li>
           <li id="t-recentchangeslinked">
            <a accesskey="k" href="/wiki/Special:RecentChangesLinked/Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology" rel="nofollow" title="Recent changes in pages linked from this page [k]">
             Related changes
            </a>
           </li>
           <li id="t-upload">
            <a accesskey="u" href="/wiki/Wikipedia:File_Upload_Wizard" title="Upload files [u]">
             Upload file
            </a>
           </li>
           <li id="t-specialpages">
            <a accesskey="q" href="/wiki/Special:SpecialPages" title="A list of all special pages [q]">
             Special pages
            </a>
           </li>
           <li id="t-permalink">
            <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;oldid=765059875" title="Permanent link to this revision of the page">
             Permanent link
            </a>
           </li>
           <li id="t-info">
            <a href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;action=info" title="More information about this page">
             Page information
            </a>
           </li>
           <li id="t-wikibase">
            <a accesskey="g" href="https://www.wikidata.org/wiki/Q5269618" title="Link to connected data repository item [g]">
             Wikidata item
            </a>
           </li>
           <li id="t-cite">
            <a href="/w/index.php?title=Special:CiteThisPage&amp;page=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;id=765059875" title="Information on how to cite this page">
             Cite this page
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div aria-labelledby="p-coll-print_export-label" class="portal" id="p-coll-print_export" role="navigation">
         <h3 id="p-coll-print_export-label">
          Print/export
         </h3>
         <div class="body">
          <ul>
           <li id="coll-create_a_book">
            <a href="/w/index.php?title=Special:Book&amp;bookcmd=book_creator&amp;referer=Dhirubhai+Ambani+Institute+of+Information+and+Communication+Technology">
             Create a book
            </a>
           </li>
           <li id="coll-download-as-rdf2latex">
            <a href="/w/index.php?title=Special:Book&amp;bookcmd=render_article&amp;arttitle=Dhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;returnto=Dhirubhai+Ambani+Institute+of+Information+and+Communication+Technology&amp;oldid=765059875&amp;writer=rdf2latex">
             Download as PDF
            </a>
           </li>
           <li id="t-print">
            <a accesskey="p" href="/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;printable=yes" title="Printable version of this page [p]">
             Printable version
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div aria-labelledby="p-wikibase-otherprojects-label" class="portal" id="p-wikibase-otherprojects" role="navigation">
         <h3 id="p-wikibase-otherprojects-label">
          In other projects
         </h3>
         <div class="body">
          <ul>
           <li class="wb-otherproject-link wb-otherproject-commons">
            <a href="https://commons.wikimedia.org/wiki/Category:Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology" hreflang="en">
             Wikimedia Commons
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div aria-labelledby="p-lang-label" class="portal" id="p-lang" role="navigation">
         <h3 id="p-lang-label">
          Languages
         </h3>
         <div class="body">
          <ul>
           <li class="interlanguage-link interwiki-gu">
            <a class="interlanguage-link-target" href="https://gu.wikipedia.org/wiki/%E0%AA%A7%E0%AB%80%E0%AA%B0%E0%AB%81%E0%AA%AD%E0%AA%BE%E0%AA%87_%E0%AA%85%E0%AA%82%E0%AA%AC%E0%AA%BE%E0%AA%A3%E0%AB%80_%E0%AA%87%E0%AA%A8%E0%AB%8D%E0%AA%B8%E0%AB%8D%E0%AA%9F%E0%AA%BF%E0%AA%9F%E0%AB%8D%E0%AA%AF%E0%AB%81%E0%AA%9F_%E0%AA%93%E0%AA%AB_%E0%AA%87%E0%AA%A8%E0%AB%8D%E0%AA%AB%E0%AB%8B%E0%AA%B0%E0%AB%8D%E0%AA%AE%E0%AB%87%E0%AA%B6%E0%AA%A8_%E0%AA%8F%E0%AA%A8%E0%AB%8D%E0%AA%A1_%E0%AA%95%E0%AA%AE%E0%AB%8D%E0%AA%AF%E0%AB%81%E0%AA%A8%E0%AA%BF%E0%AA%95%E0%AB%87%E0%AA%B6%E0%AA%A8_%E0%AA%9F%E0%AB%87%E0%AA%95%E0%AB%8D%E0%AA%A8%E0%AB%8B%E0%AA%B2%E0%AB%8B%E0%AA%9C%E0%AB%80" hreflang="gu" lang="gu" title="ધીરુભાઇ અંબાણી ઇન્સ્ટિટ્યુટ ઓફ ઇન્ફોર્મેશન એન્ડ કમ્યુનિકેશન ટેક્નોલોજી – Gujarati">
             ગુજરાતી
            </a>
           </li>
           <li class="interlanguage-link interwiki-ne">
            <a class="interlanguage-link-target" href="https://ne.wikipedia.org/wiki/%E0%A4%A7%E0%A5%80%E0%A4%B0%E0%A5%82%E0%A4%AD%E0%A4%BE%E0%A4%88_%E0%A4%85%E0%A4%82%E0%A4%AC%E0%A4%BE%E0%A4%A8%E0%A5%80_%E0%A4%B8%E0%A5%82%E0%A4%9A%E0%A4%A8%E0%A4%BE_%E0%A4%8F%E0%A4%B5%E0%A4%82_%E0%A4%B8%E0%A4%82%E0%A4%9A%E0%A4%BE%E0%A4%B0_%E0%A4%AA%E0%A5%8D%E0%A4%B0%E0%A5%8C%E0%A4%A6%E0%A5%8D%E0%A4%AF%E0%A5%8B%E0%A4%97%E0%A4%BF%E0%A4%95%E0%A5%80_%E0%A4%B8%E0%A4%82%E0%A4%B8%E0%A5%8D%E0%A4%A5%E0%A4%BE%E0%A4%A8" hreflang="ne" lang="ne" title="धीरूभाई अंबानी सूचना एवं संचार प्रौद्योगिकी संस्थान – Nepali">
             नेपाली
            </a>
           </li>
          </ul>
          <div class="after-portlet after-portlet-lang">
           <span class="wb-langlinks-edit wb-langlinks-link">
            <a class="wbc-editpage" href="https://www.wikidata.org/wiki/Q5269618#sitelinks-wikipedia" title="Edit interlanguage links">
             Edit links
            </a>
           </span>
          </div>
         </div>
        </div>
       </div>
      </div>
      <div id="footer" role="contentinfo">
       <ul id="footer-info">
        <li id="footer-info-lastmod">
         This page was last modified on 12 February 2017, at 13:02.
        </li>
        <li id="footer-info-copyright">
         Text is available under the
         <a href="//en.wikipedia.org/wiki/Wikipedia:Text_of_Creative_Commons_Attribution-ShareAlike_3.0_Unported_License" rel="license">
          Creative Commons Attribution-ShareAlike License
         </a>
         <a href="//creativecommons.org/licenses/by-sa/3.0/" rel="license" style="display:none;">
         </a>
         ;
    additional terms may apply.  By using this site, you agree to the
         <a href="//wikimediafoundation.org/wiki/Terms_of_Use">
          Terms of Use
         </a>
         and
         <a href="//wikimediafoundation.org/wiki/Privacy_policy">
          Privacy Policy
         </a>
         . Wikipedia® is a registered trademark of the
         <a href="//www.wikimediafoundation.org/">
          Wikimedia Foundation, Inc.
         </a>
         , a non-profit organization.
        </li>
       </ul>
       <ul id="footer-places">
        <li id="footer-places-privacy">
         <a class="extiw" href="https://wikimediafoundation.org/wiki/Privacy_policy" title="wmf:Privacy policy">
          Privacy policy
         </a>
        </li>
        <li id="footer-places-about">
         <a href="/wiki/Wikipedia:About" title="Wikipedia:About">
          About Wikipedia
         </a>
        </li>
        <li id="footer-places-disclaimer">
         <a href="/wiki/Wikipedia:General_disclaimer" title="Wikipedia:General disclaimer">
          Disclaimers
         </a>
        </li>
        <li id="footer-places-contact">
         <a href="//en.wikipedia.org/wiki/Wikipedia:Contact_us">
          Contact Wikipedia
         </a>
        </li>
        <li id="footer-places-developers">
         <a href="https://www.mediawiki.org/wiki/Special:MyLanguage/How_to_contribute">
          Developers
         </a>
        </li>
        <li id="footer-places-cookiestatement">
         <a href="https://wikimediafoundation.org/wiki/Cookie_statement">
          Cookie statement
         </a>
        </li>
        <li id="footer-places-mobileview">
         <a class="noprint stopMobileRedirectToggle" href="//en.m.wikipedia.org/w/index.php?title=Dhirubhai_Ambani_Institute_of_Information_and_Communication_Technology&amp;mobileaction=toggle_view_mobile">
          Mobile view
         </a>
        </li>
       </ul>
       <ul class="noprint" id="footer-icons">
        <li id="footer-copyrightico">
         <a href="https://wikimediafoundation.org/">
          <img alt="Wikimedia Foundation" height="31" src="/static/images/wikimedia-button.png" srcset="/static/images/wikimedia-button-1.5x.png 1.5x, /static/images/wikimedia-button-2x.png 2x" width="88"/>
         </a>
        </li>
        <li id="footer-poweredbyico">
         <a href="//www.mediawiki.org/">
          <img alt="Powered by MediaWiki" height="31" src="/static/images/poweredby_mediawiki_88x31.png" srcset="/static/images/poweredby_mediawiki_132x47.png 1.5x, /static/images/poweredby_mediawiki_176x62.png 2x" width="88"/>
         </a>
        </li>
       </ul>
       <div style="clear:both">
       </div>
      </div>
      <script>
       (window.RLQ=window.RLQ||[]).push(function(){mw.config.set({"wgPageParseReport":{"limitreport":{"cputime":"0.236","walltime":"0.292","ppvisitednodes":{"value":1521,"limit":1000000},"ppgeneratednodes":{"value":0,"limit":1500000},"postexpandincludesize":{"value":69258,"limit":2097152},"templateargumentsize":{"value":1508,"limit":2097152},"expansiondepth":{"value":12,"limit":40},"expensivefunctioncount":{"value":0,"limit":500},"entityaccesscount":{"value":1,"limit":400},"timingprofile":["100.00%  221.150      1 -total"," 31.53%   69.726      1 Template:Infobox_University"," 27.54%   60.914     13 Template:Cite_web"," 26.37%   58.309      1 Template:Infobox"," 13.41%   29.666      1 Template:Coord","  9.93%   21.962      1 Template:Convert","  7.91%   17.483      3 Template:Navbox","  6.55%   14.486      1 Template:Commons_category","  5.32%   11.762      1 Template:Commons","  5.19%   11.467      2 Template:Br_separated_entries"]},"scribunto":{"limitreport-timeusage":{"value":"0.103","limit":"10.000"},"limitreport-memusage":{"value":5719308,"limit":52428800}},"cachereport":{"origin":"mw1252","timestamp":"20170212130223","ttl":2592000,"transientcontent":false}}});});
      </script>
      <script>
       (window.RLQ=window.RLQ||[]).push(function(){mw.config.set({"wgBackendResponseTime":80,"wgHostname":"mw1270"});});
      </script>
     </body>
    </html>
    


.. code:: ipython2

    for link in soup.find_all('a'):
        print(link.get('href'))


.. parsed-literal::

    http://example.com/elsie
    http://example.com/lacie
    http://example.com/tillie


For furhter help/Tutorial
https://www.dataquest.io/blog/web-scraping-tutorial-python/

Beautiful Soup transforms a complex HTML document into a complex tree of
Python objects. But you’ll only ever have to deal with about four kinds
of objects: Tag, NavigableString, BeautifulSoup, and Comment.

Youtube downloader

.. code:: ipython2

    import requests
    import os,sys
    from bs4 import BeautifulSoup
    search = raw_input('Enter the name of the song: ')
    url = 'https://www.youtube.com/results?search_query='+search
    sc = requests.get(url)
    soup = BeautifulSoup(sc.text,'html.parser')
    title = soup.findAll('h3',{'class':'yt-lockup-title '})
    
    link = []
    for i in range(min(10,len(title))):
        link.append(title[i].find('a')['href'])
    for i in range(min(10,len(title))):
        print (str(i+1)+'. '+title[i].find('a').text)

.. code:: ipython2

    os.system("youtube-dl --extract-audio --audio-format mp3 " + 'https://www.youtube.com'+link[2])

Selenium Automation
~~~~~~~~~~~~~~~~~~~

.. code:: ipython2

    #DA_AUTO LOGIN SCRIPT
    #Vineet Mehta
    from selenium import webdriver
    from selenium.webdriver.support import ui
    from selenium.webdriver.common.keys import Keys
    import time
    def page_is_loaded(driver):
        return driver.find_element_by_tag_name("body") != None
    options = webdriver.ChromeOptions()
    #options.add_argument('--ignore-certificate-errors')
    
    driver = webdriver.Chrome('/home/vineet/Downloads/chromedriver',chrome_options=options)
    driver.get("https://10.100.56.55:8090/httpclient.html")
    wait = ui.WebDriverWait(driver, 10)
    wait.until(page_is_loaded)
    email_field = driver.find_element_by_name("username")
    email_field.send_keys("ID")
    password_field = driver.find_element_by_name("password")
    password_field.send_keys("PASSWORD")
    password_field.send_keys(Keys.RETURN)
    time.sleep(5)
    driver.quit();



Virtual Environment
~~~~~~~~~~~~~~~~~~~

How does virtualenv help?

virtualenv solves this problem by creating a completely isolated virtual
environment for each of your programs. An environment is simply a
directory that contains a complete copy of everything needed to run a
Python program, including a copy of the python binary itself, a copy of
the entire Python standard library, a copy of the pip installer, and
(crucially) a copy of the site-packages directory mentioned above. When
you install a package from PyPI using the copy of pip that's created by
the virtualenv tool, it will install the package into the site-packages
directory inside the virtualenv directory. You can then use it in your
program just as before.

.. code:: ipython2

    $sudo pip install virtualenv
    $cd ~/code/myproject/
    $virtualenv env
    $ls env
    $which python
    /usr/bin/python
    $ source env/bin/activate
    $ deactivate

pip is a tool for installing packages from the Python Package Index.

virtualenv is a tool for creating isolated Python environments
containing their own copy of python, pip, and their own place to keep
libraries installed from PyPI.

It's designed to allow you to work on multiple projects with different
dependencies at the same time on the same machine. After installing it,
run virtualenv env to create a new environment inside a directory called
env.

You'll need one of these environments for each of your projects. Make
sure you exclude these directories from your version control system.

To use the versions of python and pip inside the environment, type
env/bin/python and env/bin/pip respectively.

You can "activate" an environment with source env/bin/activate and
deactivate one with deactivate. This is entirely optional but might make
life a little easier.

Running virtualenv with the option --no-site-packages will not include
the packages that are installed globally. This can be useful for keeping
the package list clean in case it needs to be accessed later. [This is
the default behavior for virtualenv 1.7 and later.]
