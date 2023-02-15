<script>
    import { onMount } from 'svelte';
    let show1 = false;
    const showTitle1 = () => {
        show1 = true;
    }
    const hideTitle1 = () => {
        show1 = false;
    }
    let show2 = false;
    const showTitle2 = () => {
        show2 = true;
    }
    const hideTitle2 = () => {
        show2 = false;
    }
    let show3 = false;
    const showTitle3 = () => {
        show3 = true;
    }
    const hideTitle3 = () => {
        show3 = false;
    }

    let date = new Date();
    $: hour = date.getHours();
    $: minutes = date.getMinutes();
    let minuteFormat = false;

    onMount( () => {
        const interval = setInterval(() => {
        date = new Date(); 
        if (minutes < 10) {
            minuteFormat = true;
        }
        else {
            minuteFormat = false;
        }}, 1000);
    });

    import dayjs from 'dayjs'
    let format = 'dddd, MMMM D, YYYY'
    let internal
    const input = (x) => (internal = dayjs(x).format(format))
    const output = (x) => (date = dayjs(x, format).toDate())

    $: input(date)
    $: output(internal)

</script>

<body>
    <div class="topbar">
        <ul>
            <li><a href="/" on:mouseenter={showTitle1} on:mouseleave={hideTitle1}><i class="fas fa-user-gear"></i></a></li>
                {#if show1}
                    <p class="title1" draggable="no">Account</p>
                {/if}
            <li><a href="/" on:mouseenter={showTitle2} on:mouseleave={hideTitle2}><i class="fas fa-gear"></i></a></li>
                {#if show2}
                    <p class="title2" draggable="no">Settings</p>
                {/if}
            <li><a href="/" on:mouseenter={showTitle3} on:mouseleave={hideTitle3}><i class="fas fa-terminal"></i></a></li>
                {#if show3}
                    <p class="title3" draggable="no">Terminal</p>
                {/if}
        </ul>
    </div>

    <div class="bottomtab">
        <div class="logo">
            <img src="http://demo.casaos.io/img/logo.4b14f83d.png" alt="casaOS logo" class="logo">
            <p class="credits">Made with ❤️ by IceWhale and YOU! (UI recration by ThatBlokeJosh)</p>
        </div>
        <div class="navbar">
            <ul>
                <li><a href="/"><i class="fas fa-message"></i></a></li>
                <li><a href="/"><i class="fab fa-discord"></i></a></li>
                <li><a href="/"><i class="fab fa-github"></i></a></li>
                <li><a href="/"><i class="fas fa-comments"></i></a></li>
            </ul>
        </div>
    </div>

    <div class="content">
        <div class="contentLeft">
            <div class="item">
                <div class="clock">
                    {#if minuteFormat}
                        <h1 class="time">{hour}:0{minutes}</h1>
                    {:else}
                        <h1 class="time">{hour}:{minutes}</h1>
                    {/if}
                    <p class="date">{internal}</p>
                </div>
            </div>
            <div class="item">
                <div class="status">
                    <h1>System status</h1>
                </div>
            </div>
            <div class="item">
                <div class="storage">
                    <h1>Storage</h1>
                </div>
            </div>
            <div class="item">
                <div class="network">
                    <h1>Network status</h1>
                </div>
            </div>
            <div class="item">
                <div class="widgets">
                    <h1>Widget settings</h1>
                </div>
            </div> 
        </div>
        <div class="contentRight">
            <div class="item">
                <div class="search">
                    <h1>search</h1>
                </div>
            <div class="item">
                <div class="apps">
                    <div class="app1">
                        <h1>app 1</h1>
                    </div>
                    <div class="app2">
                        <h1>app 2</h1>
                </div>
            </div>
            <div class="item">
                <h1>App</h1>
                <div class="userApps">
                    <div class="app tooltip">
                            <img src="http://demo.casaos.io/img/appstore.02fca5a8.svg" alt="">
                        <span class="tooltiptext">
                            <p>Open</p>
                        </span>
                        <p>App Store</p>
                    </div>
                    <div class="app">
                        <img src="http://demo.casaos.io/img/files.25391a43.svg" alt="">
                        <p>Files</p>
                    </div>
                    <div class="app">
                        <img src="https://cdn.jsdelivr.net/gh/IceWhaleTech/CasaOS-AppStore@main/Apps/Jellyfin/icon.png" alt="">
                        <p>Jellyfin</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

</body>

<style>
    body {
        background-image: url(/background.jpg);
        background-size: cover;
        background-repeat: no-repeat;
        width: 100vw;
        height: 100vh;
        margin: 0 auto;
        font-family: 'Roboto', sans-serif;
        color: #fff;
    }
    .bottomtab {
        display: flex;
        position: absolute;
        bottom: 0;
        width: 99%;
    }
    .logo {
        display: flex;
        flex-direction: row;
        align-items: center;
    }
    img.logo  {
        width: 136px;
        height: 26px;
        margin: 20px;
    }
    .credits {
        font-size: 0.7rem;
        margin-bottom: 5px;
    }
    .navbar {
        position: absolute;
        right: 0;
    }
    .navbar > ul {
        display: flex;
        flex-direction: row;
        align-items: center;
        margin: 20px;
        gap: 20px;
    }
    .navbar > ul > li {
        font-size: large;
    }
    h1 {
        font-size: 1rem; margin: 10px; padding:10px;
    }
    .time {
        font-size: 2rem;
        font-weight: 100;
        margin: 0 auto;
        padding: 10px;
        position: relative;
    }
    .date {
        font-size: 1rem;
        font-weight: 100;
        margin: 0 auto;
        padding: 10px;
    }
    .content {
        width: 80%;
        height: 70%;
        position: absolute;
        top: 10%;
        left: 10%;
        display: grid;
        grid-template-columns: 1fr 4fr;
        grid-template-rows: 1fr 1fr 1fr;
        gap: 1%;
        margin: 0 auto;
    }

    .item {
        height: max-content;
        position: relative;
    }
    .clock {
        height: max-content;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
    }
    .status {
        height: 10em;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        height: max-content;
    }
    .apps {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1%;
        height: max-content;
    }
    .app1 {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
    }
    .app2 {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
    }
    .search {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        height: max-content;
        margin-bottom: 1%;
    }
    .userApps {
        height: max-content;
        display: flex;
    }
    @media screen and (max-width: 768px) {
        .userApps {
            flex-direction: column;
        }
    }
    .app {
        display: flex;
        flex-direction: column;
        align-items: center;
        position: relative;
        width: 150px;
        height: 150px;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        gap: 10px;
        margin: 10px;
        transition: all 0.2s ease-in-out;
    }
    .app:hover {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.7);
        cursor: pointer;
    }
    .app > img {
        width: 64px;
        height: 64px;
        position: absolute;
        top: 15%;
        transition: all 0.3s;
    }
    .app > img:hover {
        cursor: pointer;
        transform: scale(1.1);
    }
    
    .app > p {
        position: absolute;
        bottom: 10px;
    }
    .storage {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        height: max-content;
    }
    .network {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        height: max-content;
    }
    .widgets {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        height: min-content;
    }
    .topbar {
        box-sizing: border-box;
        width: 100%;
        height: max-content;
        position: absolute;
        top: 0;
        left: 0;
        background-color: rgb(41, 41, 41);
    }
    ul {
        list-style-type: none;
        display: flex;
        align-items: center;
        gap: 1%;
    }
    li {
        transition: all 0.5s ease-in-out;
    }
    li:hover {
       transform: scale(1.1); 
    }
    li:nth-child(1) {
        margin-left: 1%;
    }
    a {
        text-decoration: none;
        color: #fff;
        cursor: pointer;
    }
    .title1 {
        position: absolute;
        left: 5%;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgb(39, 39, 39);
        padding: 10px;
        border-radius: 10px;
        animation: fade-in 0.5s ease-in-out;
    }
    .title2 {
        position: absolute;
        left: 7%;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgb(39, 39, 39);
        padding: 10px;
        border-radius: 10px;
        animation: fade-in 0.5s ease-in-out;
    }
    .title3 {
        position: absolute;
        left: 9%;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgb(39, 39, 39);
        padding: 10px;
        border-radius: 10px;
        animation: fade-in 0.7s ease-in-out;
    }
    .tooltiptext {
    visibility: hidden;
    width: 120px;
    background-color: black;
    color: #fff;
    text-align: center;
    border-radius: 6px;
    padding: 5px 0;
    position: absolute;
    z-index: 1;
    bottom: 150%;
    left: 50%;
    margin-left: -60px;
    }

    .tooltiptext::after {
    content: "";
    position: absolute;
    top: 100%;
    left: 50%;
    margin-left: -5px;
    border-width: 5px;
    border-style: solid;
    border-color: black transparent transparent transparent;
    }

    .tooltip:hover .tooltiptext {
    visibility: visible;
    }

    @keyframes fade-in {
        0% {
            opacity: 0;
        }
        100% {
            opacity: 1;
        }
    }
</style>