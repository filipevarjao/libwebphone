# Kazoo.js library v2.0
The goal of this library is to turn the browser in a softphone, using the correct protocol depending on the browser used by the client. On supported browsers, the goal is to allow calls using WebRTC, ~~and to fall back on the RTMP
protocol if WebRTC is not supported by the browser.~~


````
 _   _ _____ _____ ____       _      ____  _____    _    ____  __  __ _____   _____ ___ _     _____   ___ 
 | \ | | ____| ____|  _ \     / \    |  _ \| ____|  / \  |  _ \|  \/  | ____| |  ___|_ _| |   | ____| |__ \
 |  \| |  _| |  _| | | | |   / _ \   | |_) |  _|   / _ \ | | | | |\/| |  _|   | |_   | || |   |  _|     / /
 | |\  | |___| |___| |_| |  / ___ \  |  _ <| |___ / ___ \| |_| | |  | | |___  |  _|  | || |___| |___   |_| 
 |_| \_|_____|_____|____/  /_/   \_\ |_| \_\_____/_/   \_\____/|_|  |_|_____| |_|   |___|_____|_____|  (_) 
                                                                                                            
                                                                       xmHTTTTT%ms.
                                                                    z?!!!!!!!!!!!!!!?m
                                                                  z!!!!!!!!!!!!!!!!!!!!%
                                                               eHT!!!!!!!!!!!!!!!!!!!!!!!L
                                                              M!!!!!!!!!!!!!!!!!!!!!!!!!!!>
                                                           z!!!!!!!!!!XH!!!!!!!!!!!!!!!!!!X
                                                           "$$F*tX!!W?!!!!!!!!!!!!!!!!!!!!!
                                                           >     M!!!   4$$NX!!!!!!!!!!!!!t
                                                           tmem?!!!!?    ""   "X!!!!!!!!!!F
                                                      um@T!!!!!!!!!!!!s.      M!!!!!!!!!!F
                                                   .#!!!!!!!!!!!!!!!XX!!!!?mM!!!!!!!!!!t~
                                                  M!!!@!!!!X!!!!!!!!!!*U!!!!!!!!!!!!!!@
                                                 M!!t%!!!W?!!!XX!!!!!!!!!!!!!!!!!!!!X"
                                                :!!t?!!!@!!!!W?!!!!XWWUX!!!!!!!!!!!t
                                                4!!$!!!M!!!!8!!!!!@$$$$$$NX!!!!!!!!-
                                                 *P*!!!$!!!!E!!!!9$$$$$$$$%!!!!!!!K
                                                    "H*"X!!X&!!!!R**$$$*#!!!!!!!!!>
                                                        'TT!?W!!9!!!!!!!!!!!!!!!!M
                                                        '!!!!!!!!!!!!!!!!!!!!!!!!F
                                                        '!!!!!!!!!!!!!!!!!!!!!!!!>
                                                        '!!!!!!!!!!!!!!!!!!!!!!!M
                                                        J!!!!!!!!!!!!!!!!!!!!!!!F K!%n.
         @!!!!!??m.                                  x?F'X!!!!!!!!!!!!!!!!!!!!HP X!!!!!!?m.
Z?L      '%!!!!!!!!!?s                            .@!\~ MB!!!!!!!!!!!!!!!!!U#!F X!!!!!!!!X#!%.
E!!N!k     't!!!!!!!!!?:                       zTX?!t~ M!t!!!!!!!!!!!!!!UM!!!F 4!!!!!!!!t%!!!!?.
!!!!!!hzh.   "X!!!!!!!!!>                  .+?!!3?!X  Z!!!B!!!!!!!!!!UM!!!!!" 4!!!!!!!!t?!!!!!!!h
?!!!!!!!!!*!?L %!!!!!!!!?               .+?!!!!3!!\  P!!!!?X!!!!!!U#!!!!!!X" 4!!!!!!!!\%!!!!!!!!!?
'X!!!!!!!!!!!!?TTTT*U!!!!k            z?!!!!!!t!!!- J!!!!!!9!!X@T!!!!!!!!X~ d!!!!!!!!!%!!!!!!!!!!!!L
 4!!!!!!!!!!!!!!!!!!!!!!!M          'W!!!!!!!X%!!P  %!!!!!!!T!!!!!!!!!!!X~ J!!!!!!!!!P!!!!!!!!!!!!!!\
  5!!!!!!!!!!!!!!!!!!!!!!!?m.       .@Ti!!!!!Z!!t  d!!!!!!!!!!!!!!!!!!!X-.JUUUUX!!!!J!!!!!!!!!!!!!!!!!
   %!!!!!!!!!!!!!!!!!!!!!!!!!!!TnzT!!!!!#/!!?!!X"  ^"=4UU!!!!!!!!!!U@T!!!!!!!!!!!!Th2!!!!!!!!!!!!!!!!!!
    ^t!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!?K!K!!f               `""#X!!!!!!!!!!!!!!!!!?t!!!!!!!!!!!!!!!!(>
       "U!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!$!!F                      "tX!!!!!!!!!!!!!!!!b!!!!!!!!!!!!!!!(>
          '"*tUUX!X!!!!!!!!!!!!!!!!!!!!!!!!$!Z                          ^4!!!!!!!!!!!!!!!N!!!!!!!!!!!!!!!!
                 %!!!!!!!!!!!!!!!!!!!!!!!!X!X                              %W@@WX!!!!!!!!!N!!!!!!!!!!!!!!!
                  "X!!!!!!!!!!!!!!!!!!!!!@!!*        ..    ..  :m.. ETThmuM!!!!!!!!!!!!!!!!@m@*TTTT?!!!W!!
                    %!!!!!!!!!!!!!!!!!!W?!!X         M!!!TT?!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!9UU!!!!!!!!!M!f
                     't!!!!!!!!!!!!!!!P!!!!X          5!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!?NX!!!!!!L
                       "W!!!!!!!!!!!X#!!!!!R           "X!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!R!!!!!t
                         ^*X!!!!!!!t%!!!!!h              %X!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!>
                             "*U!!M!!!!!!X~ :?!!!T!+s...   *X!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
                                 :?!!!!!!> :?!!!!!!!!!!!!!!!!?tX!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!>
                                 %!!!!!!F .%!!!!!!!!!!!!!!!!!!!!!#4U!!!!!!!!!!!!U!!!!!!!!!!!!!!!!!!!!!!!!~
                                K!!!!!!Z  K!!!!!!!!!!!!!!!!!!!!!!!  F!!!!!?!!?X!!!!!!!!!!!!!!!!!!!!!!!!!Z
                               X!!!!!!t  H!!!!!!!!!!!!!!!!!!!!!!!!> !!!!!!!!!!!W!!!!!!!!!!!!!!!!!!!!!!!t
                               %!!!!!!F :!!!!!!!!!!!!!!!!!!!!!!!!!> !!!!!!!!!!!!#X!!!!!!!!!!!!!!!!!!!!X
                              '!!!!!!X  K!!!!!!!!!!!!!!!!!!!!!!!!!> K!!!!!!!!!!!!!?W!!!!!!!!!!!!!!!!X"
      __        ___   ___   __  _   _  ___ _____   ________ ___ ____  ____  _____ ____   ____   ___ 
      \ \      / / | | \ \ / / | \ | |/ _ \_   _| |__  / _ \_ _|  _ \| __ )| ____|  _ \ / ___| |__ \
       \ \ /\ / /| |_| |\ V /  |  \| | | | || |     / / | | | || | | |  _ \|  _| | |_) | |  _    / /
        \ V  V / |  _  | | |   | |\  | |_| || |    / /| |_| | || |_| | |_) | |___|  _ <| |_| |  |_| 
         \_/\_/  |_| |_| |_|   |_| \_|\___/ |_|   /____\___/___|____/|____/|_____|_| \_\\____|  (_) 
                                                                                               
````

More documentation coming soon, but developers can currently reference the initProperties functions to view available configuration properties.


## Contact
If you have any question or remark about the library or its documentation, feel free to come talk to us on IRC #2600hz on FreeNode.
