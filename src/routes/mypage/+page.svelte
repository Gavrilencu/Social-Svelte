<script>
  import Header from "../../lib/Header.svelte";
  import logo from "$lib/img/logo.png";
  import { onMount } from "svelte";
  onMount(() => {
    getFriends();
  });

  async function getFriends(myid) {
    try {
      // Înlocuiește URL-ul cu adresa reală a serverului tău și portul corespunzător
      const response = await fetch(
        `http://localhost:3000/friends/` + localStorage.getItem("id")
      );
      if (response.ok) {
        const data = await response.json();
        console.log("Datele primite:", data);
        localStorage.setItem("totalFriends", data.totalFriends);
        return data;
      }
    } catch (error) {
      console.error(
        "A apărut o eroare la preluarea datelor prietenilor:",
        error
      );
    }
  }
  let utilizator = {
    nume: "Ion",
    prenume: "Popescu",
    imagine: "src/lib/img/person.svg",
    prieteni: 150,
    despre:
      "Pasionat de tehnologie, natură și călătorii. Mereu în căutarea unei noi aventuri!",
    postari: [
      {
        id: 1,
        text: "Astăzi am explorat un traseu nou de munte! #aventura #natura",
      },
      {
        id: 2,
        text: "Am început să învăț Svelte și îmi place mult! #coding #svelte",
      },
    ],
    prieteniLista: [
      {
        id: 1,
        nume: "Andrei",
        prenume: "Mihai",
        imagine: "/calea/catre/imaginea1.jpg",
      },

      {
        id: 1,
        nume: "Andrei",
        prenume: "Mihai",
        imagine: "/calea/catre/imaginea1.jpg",
      },

      {
        id: 1,
        nume: "Andrei",
        prenume: "Mihai",
        imagine: "/calea/catre/imaginea1.jpg",
      },

      {
        id: 1,
        nume: "Andrei",
        prenume: "Mihai",
        imagine: "/calea/catre/imaginea1.jpg",
      },

      {
        id: 1,
        nume: "Andrei",
        prenume: "Mihai",
        imagine: "/calea/catre/imaginea1.jpg",
      },

      {
        id: 1,
        nume: "Andrei",
        prenume: "Mihai",
        imagine: "/calea/catre/imaginea1.jpg",
      },
      {
        id: 2,
        nume: "Ioana",
        prenume: "Georgescu",
        imagine: "/calea/catre/imaginea2.jpg",
      },

      // Adaugă restul prietenilor aici
    ],
  };
</script>

<main class="app">
  <Header />
  <div class="profil-container">
    <aside class="detalii-utilizator">
      <img
        src={utilizator.imagine}
        alt="Imagine Profil"
        class="imagine-profil"
      />
      <h2>{localStorage.getItem("name")} {localStorage.getItem("surname")}</h2>
      <p class="prieteni">
        <i class="fas fa-user-friends"></i>
        {localStorage.getItem("totalFriends")} Prieteni
      </p>
      <p class="despre">{utilizator.despre}</p>
    </aside>
    <div class="lista-prieteni">
      <h3>Prieteni</h3>
      <div class="prieteni-container">
        {#each utilizator.prieteniLista as prieten}
          <div class="prieten">
            <img src={prieten.imagine} alt="Prieten" />
            <p>{prieten.nume} {prieten.prenume}</p>
          </div>
        {/each}
      </div>
    </div>
  </div>
</main>
<section class="postari-utilizator">
  {#each utilizator.postari as postare}
    <div class="postare">
      <p>{postare.text}</p>
    </div>
  {/each}
</section>

<style>
  .lista-prieteni {
    margin-top: 20px;
    text-align: left;
  }

  .prieteni-container {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .prieten {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .prieten img {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    object-fit: cover;
  }

  .prieten p {
    font-size: 0.8rem;
    margin-top: 5px;
  }

  @media (max-width: 768px) {
    .profil-container {
      flex-direction: column;
      align-items: center;
    }

    .detalii-utilizator,
    .postari-utilizator {
      width: 100%;
      max-width: none;
    }

    .prieten img {
      width: 50px;
      height: 50px;
    }
  }

  :global(body) {
    font-family: "Arial", sans-serif;
    background-color: #f0f2f5;
    margin: 0;
    padding: 0;
  }
  .app {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
  }
  .profil-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 2rem;
    padding: 2rem;
  }
  .detalii-utilizator {
    background-color: #fff;
    padding: 20px;
    border-radius: 15px;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 300px;
  }
  .imagine-profil {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    object-fit: cover;
    background-color: white;
    border: 5px solid #fff;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    margin: -50px auto 10px;
  }
  .detalii-utilizator h2 {
    margin: 10px 0;
    color: #333;
  }
  .prieteni {
    margin: 10px 0;
    font-weight: bold;
    color: #555;
  }
  .despre {
    color: #666;
    font-size: 0.9rem;
  }
  .postari-utilizator {
    flex: 3;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .postare {
    width: 80%;
    background-color: #fff;
    margin-bottom: 1rem;
    text-align: center;
    padding: 1.5rem;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: transform 0.2s ease;
  }
  .postare:hover {
    transform: translateY(-5px);
  }
  .postare p {
    margin: 0;
    color: #444;
  }
</style>
