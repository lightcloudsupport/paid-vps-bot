<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=220&section=header&text=Paid%20VPS%20Bot&fontSize=56&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=LXC%20%2F%20LXD%20VPS%20Discord%20Bot&descSize=20&descAlignY=60" width="100%"/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=2F8FFF&center=true&vCenter=true&width=600&lines=Create+VPS+from+Discord;SSH+access+in+seconds;Port+forwarding+%2B+multi-node;Fully+automated+installer" alt="Typing SVG"/>

<br/>

![Ubuntu](https://img.shields.io/badge/UBUNTU-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Debian](https://img.shields.io/badge/DEBIAN-A81D33?style=for-the-badge&logo=debian&logoColor=white)
![Python](https://img.shields.io/badge/PYTHON-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Discord](https://img.shields.io/badge/DISCORD.PY-5865F2?style=for-the-badge&logo=discord&logoColor=white)
![LXD](https://img.shields.io/badge/LXC%20%2F%20LXD-333333?style=for-the-badge&logo=linuxcontainers&logoColor=white)

![Made by](https://img.shields.io/badge/MADE%20BY-CRIMSON-ff3366?style=for-the-badge)
![Status](https://img.shields.io/badge/STATUS-ACTIVE-00ff88?style=for-the-badge)
![Version](https://img.shields.io/badge/VERSION-9.0--PRO-2f8fff?style=for-the-badge)

</div>

---

## ✨ Features

| Feature | Description | Status |
|---|---|:---:|
| 🖥️ **VPS Creation** | Deploy containers with custom RAM, CPU and disk | ![ok](https://img.shields.io/badge/Ready-00c853?style=flat-square) |
| 🔑 **SSH Access** | Auto root password + tunnel address sent by DM | ![ok](https://img.shields.io/badge/Ready-00c853?style=flat-square) |
| 🔌 **Port Forwarding** | TCP and UDP forwards with per-user quotas | ![ok](https://img.shields.io/badge/Ready-00c853?style=flat-square) |
| 🌐 **Multi-Node** | Manage local and remote nodes from one bot | ![ok](https://img.shields.io/badge/Ready-00c853?style=flat-square) |
| 📸 **Snapshots & Clone** | Back up, restore and clone any VPS | ![ok](https://img.shields.io/badge/Ready-00c853?style=flat-square) |
| 🛡️ **Admin Panel** | Suspend, resize, whitelist, monitor resources | ![ok](https://img.shields.io/badge/Ready-00c853?style=flat-square) |
| 🧩 **Custom Commands** | Drop your own cogs into a folder | ![ok](https://img.shields.io/badge/Ready-00c853?style=flat-square) |

---

## 📋 Requirements

| Requirement | Details |
|---|---|
| 🐧 **OS** | Ubuntu or Debian |
| 👑 **Access** | Root |
| 🤖 **Bot Token** | From the [Discord Developer Portal](https://discord.com/developers/applications) |
| 🔓 **Intents** | Server Members + Message Content |
| 🆔 **Admin ID** | Your Discord user ID |

---

## 🚀 Clone & Install

```bash
git clone https://github.com/lightcloudsupport/paid-vps-bot.git
cd paid-vps-bot
chmod +x install.sh
sudo ./install.sh
```

> 💡 The installer sets up LXD, Python, the bot and a systemd service, then asks for your **token**, **admin ID** and an optional **logo URL**.

---

## ⚙️ Service Commands

| Action | Command |
|---|---|
| 📊 Status | `systemctl status bot` |
| 🔄 Restart | `systemctl restart bot` |
| 📜 Live logs | `journalctl -u bot -f` |

---

## 🔧 Configuration

Edit `/etc/systemd/system/bot.service`, then run `systemctl daemon-reload && systemctl restart bot`.

| Variable | Description | Default |
|---|---|---|
| `DISCORD_TOKEN` | Bot token **(required)** | none |
| `MAIN_ADMIN_ID` | Main admin ID(s), comma separated **(required)** | none |
| `BOT_NAME` | Name shown in embeds | `LightCloud` |
| `PREFIX` | Command prefix | `!` |
| `LOGO_URL` | Public image URL for embed logo | empty |
| `COMMANDS_DIR` | Folder with extra command files | `cogs` |
| `YOUR_SERVER_IP` | Fallback IP for port forwards | `127.0.0.1` |

---

## 🧩 Custom Commands (Cogs)

Put your files in a `cogs` folder next to `bot.py`. Each file needs a `setup` function:

```python
from discord.ext import commands

class Example(commands.Cog):
    def __init__(self, bot):
        self.bot = bot

    @commands.command()
    async def hello(self, ctx):
        await ctx.send("Hello!")

async def setup(bot):
    await bot.add_cog(Example(bot))
```

---

## 🎮 Commands

### 👤 Users

| Command | Description |
|---|---|
| `!myvps` | View your VPS dashboard |
| `!manage` | Start, stop, reinstall, SSH, stats |
| `!ports` | Manage port forwards |
| `!share-user @user 1` | Share a VPS |
| `!ping` · `!help` | Latency and full command list |

### 🛡️ Admins

| Command | Description |
|---|---|
| `!create <ram> <cpu> <disk> @user` | Create a VPS |
| `!delete-vps @user <n>` | Delete a VPS |
| `!suspend-vps` · `!unsuspend-vps` | Suspend or restore |
| `!resize-vps` · `!add-resources` | Change resources |
| `!snapshot` · `!clone-vps` | Backups and cloning |
| `!node create` · `!node list` | Node management |
| `!serverstats` · `!status` | System overview |

---

## 🔒 Security Notes

> ⚠️ VPS containers run in **privileged mode** so Docker works. Only give VPS access to people you trust.

- 🔐 Keep your bot token private and never commit it
- 🗄️ Root passwords are stored in `vps.db`, so protect that file

---

## 🔄 Updating

```bash
cd paid-vps-bot
git pull
sudo cp bot.py /root/bot.py
sudo systemctl restart bot
```

---

<div align="center">

![GitHub stars](https://img.shields.io/github/stars/lightcloudsupport/paid-vps-bot?style=for-the-badge&color=ffd700)
![GitHub forks](https://img.shields.io/github/forks/lightcloudsupport/paid-vps-bot?style=for-the-badge&color=2f8fff)
![GitHub issues](https://img.shields.io/github/issues/lightcloudsupport/paid-vps-bot?style=for-the-badge&color=ff3366)

**Made with ❤️ by Crimson**

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=120&section=footer" width="100%"/>

</div>
