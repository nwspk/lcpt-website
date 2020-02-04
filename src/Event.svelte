<script>
  export let event;
  export let isPast = false;
  import { DateTime } from "luxon";
</script>

<style>
  .button {
    /* border-radius: 4px; */
    /* border: 2px solid rgb(221, 221, 221); */
    background-color: #333;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
    color: #f2f2f2 !important;
    padding: 30px 50px 10px 20px !important;
    display: inline-block;
    margin-bottom: 50px;
  }

  .event {
    display: flex;
    flex-direction: row;
    justify-content: left;
    flex-wrap: wrap;
    margin-top: 5px;
  }
  .event .datetime {
    flex: 1 0 auto;
    text-align: center;
    width: 25%;
    color: #f2f2f2;
    background: #333;
    box-shadow: inset 0 0 20px 4px rgba(0, 0, 0, 0.3);
  }
  .event .datetime-cont {
    font-family: monospace;
    /* background:#333; */
    padding: 1vw;
    /* border-bottom:5px solid white; */
    text-align: left;
  }
  .event .body {
    flex: 1 1 auto;
    width: 75%;
    padding-left: 25px;
    min-width: 500px;
    padding-top: 0.5vw;
    /* border-left:3px solid #333; */
  }

  .event .title {
    font-size: 200%;
    font-weight: bold;
    display: block;
    color: #333;
  }
  .event .organiser {
    font-size: 100%;
    color: #888;
    text-decoration: underline;
  }

  .past .body .title {
    color: #888;
  }
  .past .body .organiser {
    color: #999;
  }
  .past .button {
    background: #999;
  }
  .past .datetime {
    background: #888;
  }
</style>

<li class="event" class:past={isPast} id={`event-${event.uid}`}>
  <a class="datetime" href={`#event-${event.uid}`}>
    <div class="datetime-cont">
      <div>{DateTime.fromISO(event.start).toFormat('HH:mm dd LLL yyyy')}</div>
      <div>NEWSPEAK HOUSE,</div>
      <div>GREAT HALL</div>
    </div>
  </a>
  <div class="body">
    <a href={event.url} class="title Clarendon-Heavy" target="_blank">
      {event.summary}
    </a>
    <a href={event.organizer.val} class="organiser" target="_blank">
      {event.organizer.params.CN}
    </a>

    <br />
    <p>
      {@html event.description}
    </p>
    <a href={event.url} class="button Clarendon-Heavy" target="_blank">
      Register Now →
    </a>
    <br />
  </div>
</li>
