<script lang="ts">
    import { invoke } from "@tauri-apps/api/tauri"
    import { Dashboard, Gear } from 'radix-icons-svelte'
    import {isActive} from '@roxi/routify'

    let app_version = "";

    (async () => {
        app_version = await invoke("get_app_version")
    })().catch(err => {
        console.error(err);
    });
</script>
<header id="header">
    <div class="logo">
        <a href="/" title="Хауди Хо!"><img src="/media/app-logo.png"></a>
        <div>
            <h1><a href="/">JARVIS</a></h1>
            <h2>v{app_version} beta</h2>
        </div>
    </div>
    <nav class="top-menu">
        <ul>
            <li><a href="/commands" class:active={$isActive('/commands')}><Dashboard /> Команды</a></li>
            <li><a href="/settings" class:active={$isActive('/settings')}><Gear /> Настройки</a></li>
        </ul>
    </nav>
</header>