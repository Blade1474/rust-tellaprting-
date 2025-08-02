CustomTeleportManager
Version: 1.1.0
Author: Blade

Overview
CustomTeleportManager is a Rust server plugin that allows players to teleport to various key locations such as raid bases, helicopter towers, their home position, and friends. It features VIP-based cooldowns, daily home teleport limits, and a friend teleport request system with acceptance and denial options.

Features
Set and teleport to home location with a daily limit on home teleports.

Teleport to active raid bases owned by the player.

Teleport to helicopter towers, randomly chosen from admin-set locations.

Friend teleport requests, with a 30-second timeout to accept or deny.

Cooldowns based on player VIP status, with configurable cooldown times.

Permissions-based access control for commands and admin features.

Admin commands to add/remove heli towers.

Daily reset of home teleport limits.

Persistent data storage for homes, cooldowns, and teleport counts.

Commands
Command	Description	Permission
/sethome	Set your current position as your home.	teleportplugin.use
/home	Teleport to your set home (limit applies).	teleportplugin.use
/removehome	Remove your set home location.	teleportplugin.use
/tprb	Teleport to your active raid base.	teleportplugin.use
/tpheli	Teleport to a random helicopter tower.	teleportplugin.use
/addhelitower	Add your current position as a heli tower.	teleportplugin.admin
/removehelitower	Remove the last added heli tower.	teleportplugin.admin
/tpfriend <name>	Request to teleport to a friend.	teleportplugin.use
/tpaccept	Accept a friend’s teleport request.	teleportplugin.use
/tpdeny	Deny a friend’s teleport request.	teleportplugin.use

Permissions
Permission	Description
teleportplugin.use	Allows player to use teleport commands.
teleportplugin.admin	Allows admin to add/remove heli towers.
vip1	Reduces cooldown to VIP1 level (configurable).
vip2	Reduces cooldown to VIP2 level (lowest cooldown).

Configuration
Configurable in the plugin’s config file (CustomTeleportManager.json):

{
  "VipCooldowns": {
    "default": 300,      // cooldown in seconds for normal players
    "vip1": 180,         // cooldown for VIP1
    "vip2": 60           // cooldown for VIP2
  },
  "HomeTeleportLimit": 3,    // number of home teleports allowed per day
  "FriendRequestTimeoutSeconds": 30  // how long a friend teleport request lasts (seconds)
}


Data Persistence
Player homes, heli towers, player raid locations, teleport counts, and last teleport times are saved to disk automatically.

Home teleport counts reset daily at server uptime.

Installation
Place the compiled .cs file into the oxide/plugins directory on your Rust server.

Configure permissions using your server’s permission manager.

Adjust cooldowns and limits in the plugin config if needed.

Use /addhelitower as admin to add heli tower positions.

Notes
Player cooldowns and home teleport limits ensure balanced use.

Friend teleport requests require the other player’s consent.

Admins should regularly update heli towers to match map changes.

