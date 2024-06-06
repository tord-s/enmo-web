<script>
  import Lightning from "../lib/Lightning.svelte";
  import { dev } from "$app/environment";
  import { inject } from "@vercel/analytics";

  inject({ mode: dev ? "development" : "production" });
</script>

<Lightning />
<div class="wrapper">
  <h1>enmo.ai</h1>
  <h4>Energy Movement</h4>
  <br />
  <h4>Team:</h4>
  <p>CEO, Johan Vu, <a href="mailto:johan@enmo.ai"> johan@enmo.ai </a></p>
  <p>
    CTO, David Lekve, <a href="mailto:david@enmo.ai"> david@enmo.ai </a>
  </p>
  <p>CFO, Tord Søfteland, <a href="mailto:tord@enmo.ai"> tord@enmo.ai </a></p>
  <p>
    Developer, Endre Sørnes, <a href="mailto:endre@enmo.ai"> endre@enmo.ai </a>
  </p>
  <br />
  <h4>Partners:</h4>
  <p>
    Berggård Amundsen & Co, <a href="https://baelgros.no" target="_blank">
      www.baelgros.no
    </a>
  </p>
  <br />
  <h4>Mentors:</h4>
  <p>
    Sebastien Gros, Head of Engineering Cybernetics, <a
      href="https://www.ntnu.edu/employees/sebastien.gros"
      target="_blank"
    >
      NTNU
    </a>
  </p>
  <p>
    Karen Lindberg, Adjunct Associate Professor, <a
      href="https://www.ntnu.no/ansatte/karen.lindberg"
      target="_blank"
    >
      NTNU
    </a>
  </p>
  <p>
    Steve Völler, Associate Professor, <a
      href="https://www.ntnu.no/ansatte/steve.voller"
      target="_blank"
    >
      NTNU
    </a>
  </p>
  <iframe
    class="sendgrid"
    title="Investor Update"
    src="https://cdn.forms-content-1.sg-form.com/93b7d24e-23d0-11ef-bcc4-a2e4c946a3db"
  />
</div>

<style>
  .sendgrid {
    width: 384px;
    height: 620px;
    border: 1px solid #fff;
    margin: auto;
    margin-top: 50px;
    border-radius: 8px;
    padding: 0;
    z-index: 100;
    background: transparent;
  }

  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 5vh;
    background: transparent;
  }

  p {
    margin: 8px;
    color: #fff;
    text-align: center;
    z-index: 100;
  }

  h4 {
    margin: 8px;
    color: #fff;
    text-align: center;
  }

  a {
    color: #aaa;
  }

  @media (max-width: 800px) {
    .wrapper {
      font-size: 13px;
      line-height: 10px;
      z-index: 100;
    }
  }
</style>
