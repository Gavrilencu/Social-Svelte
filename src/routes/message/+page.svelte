<script>
   import Header from "../../lib/Header.svelte";
    let persoane = ["Persoana 1", "Persoana 2", "Persoana 3"];
    let mesaje = [
        { deLa: "Persoana 1", continut: "Salut, ce faci?" },
        { deLa: "Tu", continut: "Bine, tu?" },
    ];
    let mesajNou = "";

    function trimiteMesaj() {
        if (mesajNou.trim() !== "") {
            mesaje.push({ deLa: "Tu", continut: mesajNou });
            mesajNou = "";
        }
    }

    // Adaugă acestă funcție
    function esteMesajulMeu(deLa) {
        return deLa === "Tu";
    }
</script>

<main class="app">
    <Header/>
    <div class="container">
        <aside class="lista-persoane">
            {#each persoane as persoana}
                <div class="persoana">{persoana}</div>
            {/each}
        </aside>
        <section class="zona-mesaje">
            <div class="mesaje">
                {#each mesaje as mesaj}
                <div class="mesaj {esteMesajulMeu(mesaj.deLa) ? 'mesaj-meu' : ''}">
                    <strong>{mesaj.deLa}: </strong>{mesaj.continut}
                </div>
            {/each}
            </div>
            <form class="formular-trimitere" on:submit|preventDefault={trimiteMesaj}>
                <input type="text" bind:value={mesajNou} placeholder="Scrie un mesaj..." />
                <button type="submit">Trimite</button>
            </form>
        </section>
    </div>
</main>

<style>
    .app {
        width: 100%;
        height: 100dvh;
        display: flex;
        flex-direction: column;
    }
    .container {
        display: flex;
        height: 100%;
        width: 100%;
    }
    .lista-persoane {
        flex: 1;
        overflow-y: auto;
        border-right: 2px solid #e0e0e0;
        padding: 20px;
        background-color: #fafafa;
    }
    .zona-mesaje {
        flex: 3;
        display: flex;
        flex-direction: column;
        background-color: #fff;
        box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    }
    .mesaje {
        flex: 1;
        overflow-y: auto;
        padding: 20px;
    }
 
    .mesaj {
    margin-bottom: 10px;
    padding: 10px;
    border-radius: 8px;
    background-color: #f5f5f5;
    box-shadow: 0 2px 4px rgba(0,0,0,0.05);
    max-width: 80%;
}

.mesaj-meu {
    margin-left: auto;
    background-color: #007BFF;
    color: white;
}
    .formular-trimitere {
        background-color: #fafafa;
        padding: 20px;
        display: flex;
        border-top: 2px solid #e0e0e0;
    }
    .formular-trimitere input {
        flex: 1;
        padding: 10px;
        margin-right: 15px;
        border: 2px solid #e0e0e0;
        border-radius: 20px;
        outline: none;
    }
    .formular-trimitere button {
        border: none;
        background-color: #007BFF;
        color: white;
        padding: 10px 20px;
        border-radius: 20px;
        cursor: pointer;
        transition: background-color 0.3s;
    }
    .formular-trimitere button:hover {
        background-color: #0056b3;
    }
    .persoana {
        cursor: pointer;
        padding: 10px;
        border-radius: 8px;
        margin-bottom: 10px;
        transition: background-color 0.3s, box-shadow 0.3s;
        border: 2px solid transparent;
    }
    .persoana:hover {
        background-color: #f0f0f0;
        box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
</style>
