# Terminator-Issues

# Terminator Config
```
---
##############################################################
#                _   _                   _____             __ _       
#     /\        | | | |                 / ____|           / _(_)      
#    /  \  _   _| |_| |__   ___  _ __  | |     ___  _ __ | |_ _  __ _ 
#   / /\ \| | | | __| '_ \ / _ \| '__| | |    / _ \| '_ \|  _| |/ _` |
#  / ____ \ |_| | |_| | | | (_) | |    | |___| (_) | | | | | | | (_| |
# /_/    \_\__,_|\__|_| |_|\___/|_|     \_____\___/|_| |_|_| |_|\__, |
#                                                                __/ |
#                                                               |___/ 
##############################################################

config-author: "hachkingtohach1(DragoVN)"
config-version: "2.1.3"

##############################################################
# _                                              
#| |                                             
#| |     __ _ _ __   __ _ _   _  __ _  __ _  ___ 
#| |    / _` | '_ \ / _` | | | |/ _` |/ _` |/ _ \
#| |___| (_| | | | | (_| | |_| | (_| | (_| |  __/
#\_____/\__,_|_| |_|\__, |\__,_|\__,_|\__, |\___|
#                    __/ |             __/ |     
#                   |___/             |___/      
##############################################################

# You can define the message prefix here
prefix: '§7[§cTerminator§7]'

# Define the announcement message after the player is kicked out by anti-cheating
kick-format: 'player %player% was kicked because of cheating!'

# Should Terminator broadcast a message when a player is kicked?
kick-broadcast: true

# Define the format of the verbose message
# Verbose message just working when player in server is running Terminator
verbose-format: '§7%player% failed §c%check% §7check §8| §7%message% §8| §7vl:%vl% ping:%ping% tps:%tps%'

# Define Commands description
commands:
  verbose: 'Show/Hide Terminator verbose messages'
  notify: 'Send message to all online staff'
  toggle-notify: 'Toggle notify message output'
  kick: 'Kick a player'

# Define messages
messages:
  enable-verbose: '§aYou enabled verbose'
  disable-verbose: '§cYou disabled verbose'

misc:
  config:
    author: '§bConfig by §a%author-config%'
    version: '§bConfig version §a%version-config%'          

##############################################################
#   _____      _   _   _                 
#  / ____|    | | | | (_)                
# | (___   ___| |_| |_ _ _ __   __ _ ___ 
#  \___ \ / _ \ __| __| | '_ \ / _` / __|
#  ____) |  __/ |_| |_| | | | | (_| \__ \
# |_____/ \___|\__|\__|_|_| |_|\__, |___/
#                               __/ |    
#                              |___/     
##############################################################

# Should Terminator check update when starting up?
check_update: true

# PocketMine API (3/4/5) (default: 4)
pocketmine_api: 4

# Log Violations (default: true)
# Logs all violations to a file. Files can be found in /plugin_data/Terminator/logs
log_file: true

# Deny Bypass Permission (default: false)
disable_bypass_permission: false

# Server Lag Protection
# Automatically disables all checks when your server is lagging.
server_lag_protection:
  # Enable this feature?
  enable: true

  # Minimum TPS needed to trigger protection
  min_tps: 17.0

  # Lag spike threshold (millisecond)
  # If the server does not respond for a certain period of time, then close the check
  lag_threshold: 1000   

##############################################################
# _____ _               _        
#/  __ \ |             | |       
#| /  \/ |__   ___  ___| | _____ 
#| |   | '_ \ / _ \/ __| |/ / __|
#| \__/\ | | |  __/ (__|   <\__ \
# \____/_| |_|\___|\___|_|\_\___/
##############################################################     
checks:
  killaura:
    # Enable this check?
    enable: true

    # Max violations to kick/ban
    vl_weight: 5

    # Limit players can hit to
    reach: 4.31

    # Check if the player shows aiming characteristics similar to aimbot
    aimbot:
      check_aimbot_sync: true
      check_aimbot_shake: true
      check_aimbot_snap: true
      check_aimbot_sensitivity: true
      check_aimbot_acceleration: true
      check_aimbot_bad_rotation: true
      check_aimbot_mouse_speed: true
      
    check_per_seconds:
      attack: 10 
      next_attack: 1  

    # Map of violation levels to command
    commands:
      20: 'terminator notify %player% might be using combat hacks (KillAura)'
      35: 'terminator notify %player% is using combat hacks (KillAura) #2'
      45: 'terminator delay 5 terminator kick %player% KillAura'
  click:
    # Enable this check?
    enable: true

    # Max violations to kick/ban
    vl_weight: 5

    # What should the player's highest CPS be? When the player exceeds this cps, it will be detected        
    max_cps: 15

    check_per_seconds:        
      swing: 15
      air: 25 

    # Map of violation levels to command
    commands:
      20: 'terminator notify %player% might be using combat hacks (AutoClick)'
      35: 'terminator notify %player% is using combat hacks (AutoClick) #2'
      45: 'terminator delay 5 terminator kick %player% AutoClick'
  interact:
    # Enable this check?
    enable: true

    # Max violations to kick/ban
    vl_weight: 5

    # Limit the player can reach the block
    reach: 6

    # Pitch limits to which players can set blocks
    limit_pitch: 35

    check_per_seconds:
      min_pitch: 30
      max_pitch: 100

    # Map of violation levels to command
    commands:
      20: 'terminator notify %player% might be using interaction hacks (ReachBlock/Scaffold/Etc.)'
      35: 'terminator notify %player% is using interaction hacks (ReachBlock/Scaffold/Etc.) #2'
      45: 'terminator delay 5 terminator kick %player% ReachBlock/Scaffold/Etc.'
  move:
    # Enable this check?
    enable: true

    # Max violations to kick/ban
    vl_weight: 5

    fly_move_speed: 75       
    normal_move_speed: 63

    check_per_seconds:
        send_motion: 22
        send_movement: 5
    
    # Map of violation levels to command
    commands:
      20: 'terminator notify %player% might be using movement hacks (Fly/Speed/Etc.)'
      35: 'terminator notify %player% is using movement hacks (Fly/Speed/Etc.) #2'
      45: 'terminator delay 5 terminator kick %player% Fly/Speed/Etc.'
  inventory:
    # Enable this check?
    enable: true

    # Max violations to kick/ban
    vl_weight: 5

    check_per_seconds:
      pick_items: 20
      
    check_per_milliseconds:
      pick_items: 2
    
    # Map of violation levels to command
    commands:
      5: 'terminator notify %player% might be using inventory hacks (ChestAura/ChestStealer/Etc.)'
      7: 'terminator notify %player% is using inventory hacks (ChestAura/ChestStealer/Etc.) #2'
      10: 'terminator delay 5 terminator kick %player% ChestAura/ChestStealer/Etc.'
  fly:
    # Enable this check?
    enable: true

    # Max violations to kick/ban
    vl_weight: 5
    
    check_per_seconds:
      toggle_flight_on_ground: 4   
      toggle_flight_in_the_air: 2
      toggle_up_in_the_air: 1
      hold_move_in_the_air: 2
      in_the_air: 10

    # Map of violation levels to command
    commands:
      45: 'terminator notify %player% might be using fly hacks (Fly/AirJump/Etc.)'
      75: 'terminator notify %player% is using fly hacks (Fly/AirJump/Etc.) #2'
      145: 'terminator delay 5 terminator kick %player% Fly/AirJump/Etc.'
  badpackets:
    # Enable this check?
    enable: true

    # Max violations to kick/ban
    vl_weight: 5

    # Timer check settings
    timer:
      delay: 0.15
      min_send_packets: 22
      max_send_packets: 15
    
    # Map of violation levels to command
    commands:
      100: 'terminator notify %player% is sending unusual packets to server (BadPackets) #1'
      150: 'terminator notify %player% is sending unusual packets to server (BadPackets) #2'
      240: 'terminator kick %player% Sending Unusual Packets'
...
