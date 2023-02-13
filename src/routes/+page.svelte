<script>
    let show = false;
    const showTitle = () => {
        show = true;
    }
    const hideTitle = () => {
        show = false;
    }
</script>

<body>
    <div class="topbar">
        <ul>
            <li><a href="/" on:mouseenter={showTitle} on:mouseleave={hideTitle}>1</a></li>
            {#if show}
                <p class="title">Account</p>
            {/if}
            <li><a href="/" on:mouseenter={showTitle} on:mouseleave={hideTitle}>2</a></li>
            <li><a href="/" on:mouseenter={showTitle} on:mouseleave={hideTitle}>3</a></li>
        </ul>
    </div>
</body>

<style>
    body {
        background-image: url(http://192.168.0.12:81/img/wallpaper02.20ce0a96.jpg);
        background-size: cover;
        background-repeat: no-repeat;
        width: 100vw;
        height: 100vh;
        margin: 0 auto;
        font-family: 'Roboto', sans-serif;
        color: #fff;
    }
    .topbar {
        box-sizing: border-box;
        width: 100%;
        height: 5%;
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
    li:nth-child(1) {
        margin-left: 1%;
    }
    a {
        text-decoration: none;
        color: #fff;
        cursor: pointer;
    }
    p.title {
        position: absolute;
        left: 4.5%;
        background-color: rgb(36, 35, 35);
        opacity: 0.99;
        padding: 10px;
        border-radius: 10px;
    }
</style>