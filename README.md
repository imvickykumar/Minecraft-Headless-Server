># `Minecraft Headless Server`
>
> - Join [Server](https://www.planetminecraft.com/server/maze-tower-smp/)
> - Read tutorial [Blog](https://www.planetminecraft.com/blog/how-to-host-a-minecraft-java-multiplayer-server-on-windows-or-ubuntu-with-playit-gg/)
>
>![image](https://github.com/user-attachments/assets/72a1d83a-e0f9-400d-9119-a3c86647f44a)

# 💡 **Minecraft Bedrock Server - Cheat & Admin Commands Help Sheet**

---

## ✅ **Teleport Commands**

* **Teleport one player to another:**

  ```bash
  /tp heyvickykumar imvickykumar
  ```

  This sends `heyvickykumar` to `imvickykumar`.

* **Teleport yourself to a location:**

  ```bash
  /tp 100 70 200
  ```

  Teleports you to X=100, Y=70, Z=200.

---

## 🛡️ **Permission Commands**

* **Give operator (admin) rights to a player:**

  ```bash
  /op imvickykumar
  ```

* **Remove operator rights:**

  ```bash
  /deop heyvickykumar
  ```

* **Set player gamemode:**

  ```bash
  /gamemode survival heyvickykumar
  /gamemode creative imvickykumar
  /gamemode adventure SomePlayer
  ```

---

## 🧑‍⚖️ **Set Player Role (visitor, member, operator)**

These changes are made in the `permissions.json` file (server side):

```json
[
  {
    "permission": "operator",
    "xuid": "2535418324842992"
  },
  {
    "permission": "visitor",
    "xuid": "2535416400643171"
  }
]
```

* `"visitor"` = can’t break/place blocks (read-only world)
* `"member"` = normal player (default)
* `"operator"` = full control & command access

> After editing, **restart the server** to apply changes.

---

## 🔐 **Allow or Disallow Users (Whitelist System)**

* In `server.properties`, set:

  ```properties
  allow-list=true
  ```

* Add players to `allowlist.json` like this:

```json
[
  {
    "name": "imvickykumar",
    "xuid": "2535418324842992"
  },
  {
    "name": "heyvickykumar",
    "xuid": "2535416400643171"
  }
]
```

> Players **not on the allowlist cannot join**, even if authenticated.

---

## 🆔 **How to Find a Player's XUID**

* Visit: [https://cxkes.me/xbox/xuid](https://cxkes.me/xbox/xuid)
* Enter the player’s **Xbox Gamertag**
* Copy the **XUID (DEC)** value
* Use that in your `permissions.json` or `allowlist.json`

---

## 📜 **Other Useful Commands**

* **Give an item:**

  ```bash
  /give imvickykumar diamond_sword 1
  ```

* **Change time of day:**

  ```bash
  /time set day
  /time set night
  ```

* **Change weather:**

  ```bash
  /weather clear
  /weather rain
  ```

* **Kill a player or entity:**

  ```bash
  /kill @e[type=zombie]
  /kill heyvickykumar
  ```

* **List all online players:**

  ```bash
  /list
  ```

---

## 🚀 **Pro Tips for Operators**

* Always **restart server** after changing `permissions.json` or `allowlist.json`.
* Use `/save hold`, `/save query`, `/save resume` to control auto-saving if doing heavy changes.
* Backup your `worlds` folder regularly.
