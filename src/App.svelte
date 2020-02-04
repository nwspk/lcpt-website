<script>
  import Loading from "./Loading.svelte";
  import Event from "./Event.svelte";

  let events = localStorage.events ? JSON.parse(localStorage.events) : null;
  const isProduction = !window.location.host.includes("localhost");
  const api = isProduction
    ? "https://lcpt-api.herokuapp.com"
    : "http://lcpt.local:12180";
  import { onMount } from "svelte";

  function getJSON(url) {
    return fetch(url).then(r => r.json());
  }

  let collegeData;
  $: upcomingEvents = events ? events.futureEvents.reverse() : null;
  $: pastEvents = events ? events.pastEvents : null;
  onMount(async () => {
    collegeData = await getJSON(`${api}/api/college.json`);
    events = collegeData.events;
    localStorage.events = JSON.stringify(events);
  });
</script>

<style>
  .cont {
    margin-top: 2vw;
    margin-left: 3vw;
    max-width: 800px;
    min-width: 500px;
    width: 80%;
    display: flex;
    flex-wrap: wrap;
  }

  .events-cont {
    max-width: 1100px;
  }

  .title-cont {
    display: flex;
    flex-direction: row;
    justify-content: left;
    margin-left: 6vw;
    margin-top: 6vw;
  }

  .title-cont img {
    height: 122px;
    margin-top: 20px;
    margin-right: 40px;
  }

  section {
    padding: 0 3vw;
    position: relative;
    /* border: 1px solid #ddd; */
    /* border-top: 5px solid #333; */
    margin: 2vw;
    width: 100%;
    /* text-align:justify; */
  }

  section.top {
    margin-top: 1vw;
  }

  .link-cont {
    position: absolute;
    right: 0;
    top: 0;
    padding: 30px;
  }

  nav {
    display: flex;
    flex-direction: row;
    justify-content: left;
    flex-wrap: wrap;
  }

  nav > div {
    width: 50%;
    padding: 10px 0;
    flex: 0 1 auto;
  }

  nav > div > .description {
    display: block;
    opacity: 0.8;
  }

  .events {
    padding: 0;
  }


  @media (max-width: 700px) {
    .cont {
      margin-left: 0;
    }

    section {
      margin-left: 0;
      margin-right: 0;
    }
  }
</style>

<div class="title-cont">
  <img src="/icon.svg" alt="" />
  <h1 class="Clarendon-Heavy">
    The London College of
    <br />
    Political Technologists
  </h1>
</div>
<div class="cont">
  <section class="top">
    <p class="description">
      A society of researchers and practitioners established in 2015 to study, nurture and inspire emerging communities of practice across the public sector and civil society in the UK. Our goal is the operational reform of civic institutions, including (but not limited to) government departments, thinktanks, activist networks, libraries, charities, universities, trade unions, newspapers, and political parties.
    </p>
    <p>
      <a href="mailto:hello@political.tech">hello@political.tech</a>
    </p>
    <nav>
      <div>
        <a href="#library" class="Clarendon-Heavy">Library</a>
        <span class="description">Research, tools, data, and more</span>
      </div>
      <div>
        <a href="#news" class="Clarendon-Heavy">News</a>
        <span class="description">What people have been writing about us</span>
      </div>
      <div>
        <a href="#fellowship" class="Clarendon-Heavy">Fellowship</a>
        <span class="description">Members recognised for their outstanding achievements</span>
      </div>
       <div>
        <a href="#residency" class="Clarendon-Heavy">Residency Programme</a>
        <span class="description">Study with us to prepare for your fellowship</span>
      </div>
       <div>
        <a href="#board" class="Clarendon-Heavy">Board</a>
        <span class="description">Members responsible for the governance of the college</span>
      </div>
       <div>
        <a href="#campuses" class="Clarendon-Heavy">Campuses</a>
        <span class="description">The college is a confederation of independent campuses in the UK</span>
      </div>
       <div>
        <a href="#membership" class="Clarendon-Heavy">Membership</a>
        <span class="description">Join a network of pioneers in UK public sector and civil society</span>
      </div>
      <div>
        <a href="#events" class="Clarendon-Heavy">Public Events</a>
        <span class="description">Workshops, hackathons, conferences, meetups, lectures, and more</span>
      </div>
       <div>
        <a href="#eventarchive" class="Clarendon-Heavy">Event Archive</a>
        <span class="description">Everything that's ever happened at the college</span>
      </div>
    </nav>
  </section>

  <section id="approach">
    <h2 class="Clarendon-Heavy">
      <a href="#approach" class="hash-link">Approach</a>
    </h2>
    <p>
      Our approach responds to limitations in the model of think tanks and
      university research centres which:
    </p>
    <ol>

      <li>
        Determine research questions internally, with academic literature
        providing the main external reference points (“inside-out” approach)
      </li>
      <li>
        Publish reports in formats (print / pdf) and media (eg paywalled
        academic journals) which impede discoverability by wider audiences
      </li>
      <li>
        Disseminate research findings through channels which have limited
        scalability and measurability (eg launch events)
      </li>
      <li>Find it difficult to attribute real-world decisions to research</li>
      <li>Produce outputs which are static, leading to slow decay over time</li>
      <li>Operate as closed communities</li>
    </ol>

    <p>By contrast we:</p>

    <li>
      Determine focus areas based on user research and insight into unmet needs
      (“outside-in” approach)
    </li>
    <li>
      Produce outputs that are inherently re-usable and discoverable at a URL –
      for example, software-as-a-service products, data sets, content in HTML
      format, APIs, wikis, training manuals
    </li>
    <li>
      Disseminate outputs through networks and scalable digital channels,
      including “inbound” channels such as Search Engine Optimization / Content
      Marketing and API
    </li>
    <li>
      Measure impact using volume of inbound hyperlinks, API calls, app
      installs, and downloads
    </li>
    <li>
      Produce outputs which are dynamic: over time, they are iterated, improved,
      or deprecated if no longer relevant. New fellows often build on outputs
      developed by alumni
    </li>
    <li>Operate as an open community</li>

    <p>
      We place a strong emphasis on networking and knowledge transfer, creating
      connections between practitioner communities in advocacy, public sector,
      service design, digital government, cultural transformation, internet
      governance, and technology ethics. Our campuses act as a physical hub for
      these communities, hosting hundreds of events each year. Past events
      include Extinction Rebellion’s non-violent direct action training, the
      launch of the Labour Party’s Digital Manifesto, and hackathons on local
      finance and tactical voting.
    </p>
  </section>

  <section id="library">
    <h2 class="Clarendon-Heavy">
      <a href="#library" class="hash-link">Library</a>
    </h2>
    <h3>Latest Research</h3>
    <ul>
      <li>
        The Election Tech Handbook: the primary resource & community for
        developers building anything to do with UK elections, whether
        journalists, campaigners or curious citizens
      </li>
      <li>Society Scraper</li>
      <li>Linkbaby.io</li>
      <li>
        CharityBase: a searchable online database of information on the
        activities, locations and finances of every charity in the UK, with an
        API
      </li>
      <li>
        Who Targets Me?: a leading NGO in the debate around targeted political
        advertising, centred around research enabled by a custom browser
        extension that allows citizens to see which political organizations are
        targeting them. Has been installed by over 30,000 users.
      </li>
    </ul>
    <h3>Collections</h3>
    <ul>
      <li>Discussion spaces</li>
      <li>Jobs boards</li>
      <li>Organising tools</li>
      <li>Election Tech</li>
    </ul>
  </section>
  <section id="news">
    <h2 class="Clarendon-Heavy">
      <a href="#news" News class="hash-link">News Coverage</a>
    </h2>
    <li>
      “Election Results Mean All Nighters For Politicians, Pundits—And Wikipedia
      Editors”, Fortune, 13 December 2019
    </li>
    <li>
      “Democracy? There’s an app for that – the tech upstarts trying to ‘hack’
      British politics”, The Guardian, 6 June 2017
    </li>
    <li>
      “The way social media is shaping our politics is truly terrifying”, The
      Telegraph, 18 September 2018
    </li>
  </section>
  <section id="fellowship">
    <h2 class="Clarendon-Heavy">
      <a href="#fellowship" class="hash-link">Fellowship</a>
    </h2>
    <p>
      Fellows are members of the London College of Political Technologists who
      are recognised as having created a highly influential piece of research or
      made a landmark discovery.
    </p>
    <h3>Apply for Fellowship</h3>
    <p>
      Fellowship candidates may submit their projects or discoveries for
      consideration [by some process].
    </p>
    <h3>Fellowship Directory</h3>
    <h5>Notable Alumni</h5>
    <ul>
      <!-- {#each alumni as alum}
      <li>{alum.name}</li>
    {/each} -->
      <li>Josie Fraser Head of Social Technology, DCMS</li>
      <li>Imeh Akpan GOV.UK User Insights Lead, Government Digital Service</li>
      <li>
        Dr Lisa Murphy National Medical Director’s Clinical Fellow, Public
        Health England
      </li>
      <li>
        Dr Rufus Pollock Founder & President, Open Knowledge; Shuttleworth
        Fellow
      </li>
      <li>
        Dee Harding Head of Intelligence, Equality & Human Rights Commission
      </li>
      <li>
        Jonathan Penn Google Tech Policy Fellow; MIT Media Lab; Berkman Klein
        Centre
      </li>
      <li>
        Carl Miller Research Director, Centre for the Analysis of Social Media,
        Demos
      </li>
      <li>Areeq Chowdhury Head of Future Advocacy Think Tank</li>
      <li>Tamara Borine Data Scientist, Competition Markets Authority</li>
      <li>John Cummings Wikimedian in Residence, UNESCO</li>
      <li>Rich Mason Researcher, RSA Future Work Centre</li>
      <li>James Moulding Extinction Rebellion Election Coordinator</li>
      <li>Phoebe Tickell Digital Grants, National Lottery Community Fund</li>
      <li>Jo Kerr Head of Digital, Turn2us anti-poverty charity</li>
    </ul>
  </section>
  <section id="residency">
    <h2 class="Clarendon-Heavy">
      <a href="#residency" Residency class="hash-link">Residency Programme</a>
    </h2>
    <p>
      LCPT’s campuses admit students for a six month residency of research and
      teaching in preparation for a fellowship application. Residencies start
      every three months, and there are a range of scholarships for which
      students may apply. Applications are made through a central admissions
      process, but prospective students can nominate their preferred campus.
    </p>
  </section>
  <section id="board">
    <h2 class="Clarendon-Heavy">
      <a href="#board" class="hash-link">Board</a>
    </h2>
    <p>
      The board of the London College of Political Technology is responsible for
      student admissions, disbursement of scholarships, co-ordination of
      peer-review, and appointment of fellows.
    </p>
    <h3>Edward Saperia</h3>
    <p>
      is the founder of the London College of Political Technology and Dean of
      Newspeak House campus. He was previously Community Strategist at The Green
      Party and Techhub, and Conference Director at Wikimania 2014. He began his
      career at Barclays Investment Bank.
    </p>
    <h3>Mustafa Warsi</h3>
    <p>
      is a Quantitative Researcher at the hedge fund Marshall Wace and Dean of
      Fahrenheit campus. He studied Mathematics at the University of Cambridge
      and began his career at JP Morgan.
    </p>
    <h3>Ned Younger</h3>
    <p>
      is a Director at Koreo, and Dean of the [Impact Hub Islington] campus.
      Since joining Koreo in 2010 he has specialised in building partnerships
      and projects dedicated to building capacity in the social sector
      ecosystem. He has led projects across Koreo’s work, developing
      cross-sector programmes to national scale including Charityworks, 2027,
      and Change100, and is currently working on a programme of civic leadership
      development with partners including The Local Trust and Greater London
      Authority.
    </p>
    <h3>Stephanie Sherman</h3>
    <p>
      is a director, researcher, curator, and strategist working across design,
      art, and culture. She is Dean of Suspicion campus. Stephanie reprograms
      outmoded sites and systems as collaborative platforms. These platforms
      find form in organizations, texts, plans, and experiences that reassemble
      material and immaterial surplus to construct words and worlds. A serial
      founder, she works with artists, architects, economists, scientists,
      technologists, media-makers, urbanists, and neighbors. Stephanie is
      currently completing a PhD in Design at the University of California.
    </p>
    <h3>Sam Gilbert</h3>
    <p>
      is an entrepreneur and researcher working at the intersection of politics
      and technology. He was Employee No.1 and Chief Marketing Officer at Bought
      By Many, the multi-award winning fintech ranked No. 13 in The Sunday Times
      TechTrack100. Previously, he was Head of Strategy and Development at
      Experian, and Head of Consumer Finance at Santander. An affiliated
      researcher at the Bennett Institute for Public Policy at the University of
      Cambridge, he also advises early-stage tech businesses on growth strategy
      and digital marketing.
    </p>
  </section>
  <section id="campuses">
    <h2 class="Clarendon-Heavy">
      <a href="#campuses" class="hash-link">Campuses</a>
    </h2>
    {#if collegeData}
      {#each collegeData.campuses as campus}
        <h3>{campus.name}</h3>
        <p>
          {#if campus.dean}
            Dean: {campus.dean.name}
            <br />
          {/if}
          Address: {campus.address}
        </p>
      {/each}
    {:else}
      <Loading />
    {/if}
  </section>
  <section id="membership">
    <h2 class="Clarendon-Heavy">
      <a href="#membership" class="hash-link">Membership</a>
    </h2>
    <p>
      To be a member of The London College of Political Technology is a
      commitment to…
    </p>
    <h3>Join</h3>
    <h3>Merchandise</h3>
  </section>
</div>

<div class="events-cont cont">
  <section id="events">
    <h2 class="Clarendon-Heavy">
      <a href="#events" class="hash-link">Public Events</a>
    </h2>
    <div class="link-cont">
      <a href="asdfasdf.ics">subscribe</a>
    </div>
    {#if upcomingEvents}
      <ul class="events">
        {#each upcomingEvents as event}
          <Event {event} />
        {/each}
      </ul>
    {:else}
      <Loading />
    {/if}
      <h2 class="Clarendon-Heavy">
        <a href="#eventarchive" class="hash-link">Event Archive</a>
      </h2>
    {#if pastEvents}
      <ul class="events">
        {#each pastEvents as event}
          <Event {event} isPast={true} />
        {/each}
      </ul>
    {:else}
      <Loading />
    {/if}
  </section>
</div>
