<script>
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
</script>

<body>
    <div class="topbar">
        <ul>
            <li><a href="/" on:mouseenter={showTitle1} on:mouseleave={hideTitle1}><i class="fas fa-user-gear"></i></a></li>
            {#if show1}
                <p class="title1">Account</p>
            {/if}
            {#if !show1}
                <li><a href="/" on:mouseenter={showTitle2} on:mouseleave={hideTitle2}><i class="fas fa-gear"></i></a></li>
                {#if show2}
                    <p class="title2">Settings</p>
                {/if}
                {#if !show2}
                    <li><a href="/" on:mouseenter={showTitle3} on:mouseleave={hideTitle3}><i class="fas fa-terminal"></i></a></li>
                    {#if show3}
                        <p class="title3">Terminal</p>
                    {/if}
                {/if}
            {/if}
        </ul>
    </div>

    <div class="content">
        <div class="contentLeft">
            <div class="item">
                <div class="clock">
                    <h1>time</h1>
                </div>
            </div>
            <div class="item">
                <div class="status">
                    <h1>status</h1>
                </div>
            </div>
            <div class="item">
                <div class="storage">
                    <h1>storage</h1>
                </div>
            </div>
            <div class="item">
                <div class="network">
                    <h1>network</h1>
                </div>
            </div>
            <div class="item">
                <div class="widgets">
                    <p style="font-weight: 500;">Widget settings</p>
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
                <h1 style="font-size: 1rem;">App</h1>
                <div class="userApps">
                    <h1>qBit</h1>
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
    .content {
        width: 80%;
        height: 80%;
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
        height: min-content;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
    }
    .status {
        height: 10em;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        height: 15em;
    }
    .apps {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1%;
        height: 15em;
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
        height: 4em;
        margin-bottom: 1%;
    }
    .userApps {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        height: 20em;
    }
    .storage {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        height: 7.5em;
    }
    .network {
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        background-color: rgba(71, 71, 71, 0.5);
        border-radius: 10px;
        height: 15em;
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
        padding: 10px;
        border-radius: 10px;
        animation: fade-in 0.5s ease-in-out;
    }
    .title2 {
        position: absolute;
        left: 7%;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        padding: 10px;
        border-radius: 10px;
        animation: fade-in 0.5s ease-in-out;
    }
    .title3 {
        position: absolute;
        left: 9%;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
        padding: 10px;
        border-radius: 10px;
        animation: fade-in 0.7s ease-in-out;
    }
    @keyframes fade-in {
        0% {
            opacity: 0.4;
        }
        100% {
            opacity: 1;
        }
    }
</style>