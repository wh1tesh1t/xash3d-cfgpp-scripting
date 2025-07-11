## cfg++ learning
preview now works xash3d scripting cfg++

I'm [w_sh1t](https://github.com/wh1tesh1t) im player Xash3D from 2017, and it's my priview now works xash3d scripting.

# About Xash3D
Xash3D is ([pronounced](https://ipa-reader.com/?text=ks%C9%91%CA%82) `[ksɑʂ]`) FWGS is a game engine, aimed to provide compatibility with Half-Life Engine and extend it, as well as to give game developers well known workflow. [Link](https://github.com/wh1tesh1t/xash3d-fwgs)

**!! taken from README.MD**

# how to find all commands?
- Open game
- Open Console (if this button hiden type -console)
- Type 'makehelp'
- Close your gsme and open help.txt (in your game folder using Text Editors)

# 1 Level (Simple scripting)
## Alias method
```Alias
alias skip_scroll_up 'invprev ; wait;wait ; +attack;wait;-attack"
alias skip_scroll_down "invnext ; wait;wait ; +attack;wait;-attack"

// binds for test (you can delete it type unbind <key>)
bind z "skip_scroll_up"
bind x "skip_scroll_down"
```
## Milti config method
```MConfig
// drop_weapon.cfg
// Drops your current weapon when config executed
echo "^!dropping weapon"
drop
```
```MConfig
// connect.cfg
// Connects to localhost server (you can change ip:port to your value)
echo "connecting to 127.0.0.1:27015"
connect 127.0.0.1:27015 <gs/48/49>
````

## If else method
```ifelse
// when cl_showfps = 1 show notify else 0 set it to 1
// WARNING: You shold enable cmd_scripting before execute config
cmd_scripting 1

if $cl_showfps >= 1
:echo "^1cl_showfps is ^@$cl_showfps^1 ignore";else
:echo "^1cl_showfps is ^20^1 i set it to 1:)"
:cl_showfps 1

// activate sv_cheats & restart the server when value is 0
if $sv_cheats = 0
:set sv_cheats 1 ; wait ; restart
// without restart (for new engine)
// :set sv_cheats 1
```

# 2 Level (Normal scripting)
## Alias method (message loop)
```Alias
alias "say_cmd" "msg_1"
alias "msg_1" "say hello world ; wait;wait ; alias say_cmd msg_2"
alias "msg_1" "say bye world ; wait;wait ; alias say_cmd msg_1"
// etc...
```

## Multi config method (multi executing loop)
```
// loop.cfg
echo "^1hello world"
wait;wait // 1 wait = 1frame!
exec loop2.cfg

// loop2.cfg
echo "^2bye world"
wait;wait
exec loop3.cfg

// loop3.cfg
sv_cheats 1
wait;wait
give weapon_rpg
```

## If else method
```ifelse
// show your name / bottomcolor & topcolor if show_status = 1
cmd_scripting 1
if $show_status = 1
:echo "=     Test status     ="
:echo "Your name: $name"
:echo "Bottomcolor is $bottomcolor"
:echo "topcolor is $topcolor";else
:echo $show_status = 0 ignore"

// Give rpg when your name is kopaf1sh
if $name = kopaf1sh
:if $sv_cheats = 1
::give weapon_rpg
:else
::sv_cheats 1
:echo test script
```
