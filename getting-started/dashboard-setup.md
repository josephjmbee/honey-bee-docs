# Connecting the Web Dashboard

Honey Bee features a dedicated browser dashboard hosted at [buzzbee.free.nf](https://buzzbee.free.nf/dashboard) where you can manage your personal cards and server settings.

---

### Logging In

1. Head to [buzzbee.free.nf/dashboard](https://buzzbee.free.nf/dashboard).
2. Click **Login with Discord**.
3. Authorize the application. The bot requests:
   * `identify` — to fetch your Discord username and avatar.
   * `guilds` — to determine which servers you have Administrator or Manage Server permissions in.

---

### Uploading Custom Card Backgrounds

{% hint style="info" %}
Custom backgrounds require an active **HoneyBee Premium** pass.
{% endhint %}

1. Log into your dashboard.
2. In the **Canvas Card Wallpapers** section, locate the target card:
   * `/bee` Profile
   * `/hive` Card
   * `/feed` Card
   * `/ticket leaderboard`
3. Click **Update Image** and select a PNG, JPG, or WebP file (Max 8 MB).
4. The dashboard relays the image to the bot cluster, formats it, and stores it in your profile.

---

### Configuring Server Features

To set up Welcome/Leave messages or Auto-Roles:
1. Open the [Server Configuration Hub](https://buzzbee.free.nf/servers.php).
2. Select your server from the list.
3. If Honey Bee is missing any required permissions (`Manage Roles`, `Manage Channels`, etc.), a warning banner will highlight exactly which permissions need to be enabled in Discord.
