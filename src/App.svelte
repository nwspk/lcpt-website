<script>
  import Loading from "./Loading.svelte";

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
  * {
    box-sizing: border-box;
  }

  .cont {
    margin-top: 10vw;
  }

  h1 {
    text-align: center;
    margin: 0 auto;
    font-size: 1.5em;
    text-transform: uppercase;
    margin: 0 0 0.5em 0;
  }
  .description {
    width: 100%;
    max-width: 800px;
    text-align: center;
  }

  p {
    margin: 1em auto;
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 2em;
    }
  }
  section {
    padding: 0 10vw;
    border-left: 1px solid rgba(0, 0, 0, 0.3);
  }

  h3 {
    margin-top: 5vw;
    padding: 10vw 10vw;
    background-image: url("/rust.jpg");
    background-size: cover;
    color: white;
  }
</style>

<svelte:head>
  <title>London College of Political Technologists</title>
</svelte:head>

<div class="cont">
  <h1 class="Clarendon-Heavy">
    The London College of
    <br />
    Political Technologists
  </h1>
  <br />
  <section>
    <p class="description">
      A fellowship established in 2015 to study, nurture and inspire emerging
      communities of practice across civil society and the public sector in the
      UK. Our goal is the technological operational reform of civic
      institutions, including (but not limited to) government departments,
      thinktanks, activist networks, libraries, charities, trade unions,
      newspapers, and political parties.
    </p>
  </section>

  <h3 id="contact" style="background-image:url('/typewriter.jpg');">Contact</h3>
  <section>
    <ul>
      <li>hello@political.tech</li>
    </ul>
  </section>

  <h3 id="approach" style="background-image:url('/gear.jpg');">Approach</h3>
  <section>
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

  <h3 id="library" style="background-image:url('/library.jpg');">Library</h3>
  <section>
    <h4>Latest Research</h4>
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
    <h4>Collections</h4>
    <ul>
      <li>Discussion spaces</li>
      <li>Jobs boards</li>
      <li>Organising tools</li>
      <li>Election Tech</li>
    </ul>
  </section>
  <h3 id="news" style="background-image:url('/typewriter.jpg');">
    News Coverage
  </h3>
  <section>
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
  <h3 id="fellowship" style="background-image:url('/gear.jpg');">Fellowship</h3>
  <section>
    <p>
      Fellows are members of the London College of Political Technologists who
      are recognised as having created a highly influential piece of research or
      made a landmark discovery.
    </p>
    <h4>Apply for Fellowship</h4>
    <p>
      Fellowship candidates may submit their projects or discoveries for
      consideration [by some process].
    </p>
    <h4>Fellowship Directory</h4>
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
  <h3 id="residency">Residency Programme</h3>
  <section>
    <p>
      LCPT’s campuses admit students for a six month residency of research and
      teaching in preparation for a fellowship application. Residencies start
      every three months, and there are a range of scholarships for which
      students may apply. Applications are made through a central admissions
      process, but prospective students can nominate their preferred campus.
    </p>
  </section>
  <h3 id="board">Board</h3>
  <section>
    <p>
      The board of the London College of Political Technology is responsible for
      student admissions, disbursement of scholarships, co-ordination of
      peer-review, and appointment of fellows.
    </p>
    <h4>Edward Saperia</h4>
    <p>
      is the founder of the London College of Political Technology and Dean of
      Newspeak House campus. He was previously Community Strategist at The Green
      Party and Techhub, and Conference Director at Wikimania 2014. He began his
      career at Barclays Investment Bank.
    </p>
    <h4>Mustafa Warsi</h4>
    <p>
      is a Quantitative Researcher at the hedge fund Marshall Wace and Dean of
      Fahrenheit campus. He studied Mathematics at the University of Cambridge
      and began his career at JP Morgan.
    </p>
    <h4>Ned Younger</h4>
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
    <h4>Stephanie Sherman</h4>
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
    <h4>Sam Gilbert</h4>
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
  <h3 id="campuses">Campuses</h3>
  <section>
    {#if collegeData}
      {#each collegeData.campuses as campus}
        <h4>{campus.name}</h4>
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

  <h3 id="membership">Membership</h3>
  <p>
    To be a member of The London College of Political Technology is a commitment
    to…
  </p>
  <h4>Join</h4>
  <h4>Merchandise</h4>
  <h3 id="events">Public Events</h3>
  <h3>Upcoming</h3>
  {#if upcomingEvents}
    <ul>
      {#each upcomingEvents as event}
        <li>
          <a href={event.url}>{event.summary}</a>
          @ {event.location} - {event.start}
        </li>
      {/each}
    </ul>
  {:else}
    <Loading />
  {/if}
  <h3>Past</h3>
  {#if pastEvents}
    <ul>
      {#each pastEvents as event}
        <li>
          <a href={event.url}>{event.summary}</a>
          @ {event.location} - {event.start}
        </li>
      {/each}
    </ul>
  {:else}
    <Loading />
  {/if}
</div>
