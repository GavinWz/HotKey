# HotKey
My AutoHotKey and Xmodmap

## (Windows下)AutoHotKey->CapsLock.ahk

常用快捷键
```
CapsLock + k: 上
CapsLock + j: 下
CapsLock + h: 左
CapsLock + l: 右
CapsLock + u: 页首
CapsLock + p: 页尾
CapsLock + u: 行首
CapsLock + o: 行尾
CapsLock + r: PowerShell
CapsLock + e: www.bing.com
CapsLock + t: VsCode.exe
CapsLock + f: 翻译
CapsLock + q: 关闭标签页
CapsLock + s: 切换标签页
CapsLock + a/x/c/v/z: 全选/剪切/复制/粘贴/撤销
CapsLock + w: 向后一个单词
CapsLock + b: 向前一个单词
CapsLock + ↑↓←→: 鼠标指针移动
CapsLock + Enter: 鼠标单击
CapsLock + ;: Enter
CapsLock + ~: 切换大小写
```
## (Linux下)Xmodmap->.xmodmap

常用快捷键
```
CapsLock + k: 上
CapsLock + j: 下
CapsLock + h: 左
CapsLock + l: 右
CapsLock + u: 页首
CapsLock + p: 页尾
CapsLock + u: 行首
CapsLock + o: 行尾
CapsLock + ;: 切换大小写
```
## 源文件

### CapsLock.ahk

```
;=====================================================================o
;                   Gavin Yang's AHK Script                         | 
;                      CapsLock Enhancement                           |
;---------------------------------------------------------------------o
;Description:                                                         |
;    This Script is wrote by Feng Ruohang via AutoHotKey Script. It   |
; Provieds an enhancement towards the "Useless Key" CapsLock, and     |
; turns CapsLock into an useful function Key just like Ctrl and Alt   |
; by combining CapsLock with almost all other keys in the keyboard.   |
;                                                                     |
;Summary:                                                             |
;o----------------------o---------------------------------------------o
;|CapsLock;             | {ESC}  Especially Convient for vim user     |
;|CaspLock + `          | {CapsLock}CapsLock Switcher as a Substituent|
;|CapsLock + hjklwb     | Vim-Style Cursor Mover                      |
;|CaspLock + uiop       | Convient Home/End PageUp/PageDn             |
;|CaspLock + nm,.       | Convient Delete Controller                  |
;|CapsLock + zxcvay     | Windows-Style Editor                        |
;|CapsLock + Direction  | Mouse Move                                  |
;|CapsLock + Enter      | Mouse Click                                 |
;|CaspLock + {F1}~{F6}  | Media Volume Controller                     |
;|CapsLock + qs         | Windows & Tags Control                      |
;|CapsLock + ;'[]       | Convient Key Mapping                        |
;|CaspLock + dfert      | Frequently Used Programs (Self Defined)     |
;|CaspLock + 123456     | Dev-Hotkey for Visual Studio (Self Defined) |
;|CapsLock + 67890-=    | Shifter as Shift                            |
;-----------------------o---------------------------------------------o
;|Use it whatever and wherever you like. Hope it help                 |
;=====================================================================o


;=====================================================================o
;                       CapsLock Initializer                         ;|
;---------------------------------------------------------------------o
SetCapsLockState, AlwaysOff                                          ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                       CapsLock Switcher:                           ;|
;---------------------------------o-----------------------------------o
;                    CapsLock + ` | {CapsLock}                       ;|
;---------------------------------o-----------------------------------o
CapsLock & `::                                                       ;|
GetKeyState, CapsLockState, CapsLock, T                              ;|
if CapsLockState = D                                                 ;|
    SetCapsLockState, AlwaysOff                                      ;|
else                                                                 ;|
    SetCapsLockState, AlwaysOn                                       ;|
KeyWait, ``                                                          ;|
return                                                               ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                         CapsLock Escaper:                          ;|
;----------------------------------o----------------------------------o
;                        CapsLock  |  {ESC}                          ;|
;----------------------------------o----------------------------------o
CapsLock::Send, {ESC}                                                ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                    CapsLock Direction Navigator                    ;|
;-----------------------------------o---------------------------------o
;                      CapsLock + h |  Left                          ;|
;                      CapsLock + j |  Down                          ;|
;                      CapsLock + k |  Up                            ;|
;                      CapsLock + l |  Right                         ;|
;                      Ctrl, Alt Compatible                          ;|
;-----------------------------------o---------------------------------o
CapsLock & h::                                                       ;|
if GetKeyState("control") = 0                                        ;|
{                                                                    ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, {Left}                                                 ;|
    else                                                             ;|
        Send, +{Left}                                                ;|
    return                                                           ;|
}                                                                    ;|
else {                                                               ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, ^{Left}                                                ;|
    else                                                             ;|
        Send, +^{Left}                                               ;|
    return                                                           ;|
}                                                                    ;|
return                                                               ;|
;-----------------------------------o                                ;|
CapsLock & j::                                                       ;|
if GetKeyState("control") = 0                                        ;|
{                                                                    ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, {Down}                                                 ;|
    else                                                             ;|
        Send, +{Down}                                                ;|
    return                                                           ;|
}                                                                    ;|
else {                                                               ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, ^{Down}                                                ;|
    else                                                             ;|
        Send, +^{Down}                                               ;|
    return                                                           ;|
}                                                                    ;|
return                                                               ;|
;-----------------------------------o                                ;|
CapsLock & k::                                                       ;|
if GetKeyState("control") = 0                                        ;|
{                                                                    ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, {Up}                                                   ;|
    else                                                             ;|
        Send, +{Up}                                                  ;|
    return                                                           ;|
}                                                                    ;|
else {                                                               ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, ^{Up}                                                  ;|
    else                                                             ;|
        Send, +^{Up}                                                 ;|
    return                                                           ;|
}                                                                    ;|
return                                                               ;|
;-----------------------------------o                                ;|
CapsLock & l::                                                       ;|
if GetKeyState("control") = 0                                        ;|
{                                                                    ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, {Right}                                                ;|
    else                                                             ;|
        Send, +{Right}                                               ;|
    return                                                           ;|
}                                                                    ;|
else {                                                               ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, ^{Right}                                               ;|
    else                                                             ;|
        Send, +^{Right}                                              ;|
    return                                                           ;|
}                                                                    ;|
return                                                               ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                     CapsLock Home/End Navigator                    ;|
;-----------------------------------o---------------------------------o
;                      CapsLock + i |  Home                          ;|
;                      CapsLock + o |  End                           ;|
;                      Ctrl, Alt Compatible                          ;|
;-----------------------------------o---------------------------------o
CapsLock & i::                                                       ;|
if GetKeyState("control") = 0                                        ;|
{                                                                    ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, {Home}                                                 ;|
    else                                                             ;|
        Send, +{Home}                                                ;|
    return                                                           ;|
}                                                                    ;|
else {                                                               ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, ^{Home}                                                ;|
    else                                                             ;|
        Send, +^{Home}                                               ;|
    return                                                           ;|
}                                                                    ;|
return                                                               ;|
;-----------------------------------o                                ;|
CapsLock & o::                                                       ;|
if GetKeyState("control") = 0                                        ;|
{                                                                    ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, {End}                                                  ;|
    else                                                             ;|
        Send, +{End}                                                 ;|
    return                                                           ;|
}                                                                    ;|
else {                                                               ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, ^{End}                                                 ;|
    else                                                             ;|
        Send, +^{End}                                                ;|
    return                                                           ;|
}                                                                    ;|
return                                                               ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                      CapsLock Page Navigator                       ;|
;-----------------------------------o---------------------------------o
;                      CapsLock + u |  PageUp                        ;|
;                      CapsLock + p |  PageDown                      ;|
;                      Ctrl, Alt Compatible                          ;|
;-----------------------------------o---------------------------------o
CapsLock & u::                                                       ;|
if GetKeyState("control") = 0                                        ;|
{                                                                    ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, {PgUp}                                                 ;|
    else                                                             ;|
        Send, +{PgUp}                                                ;|
    return                                                           ;|
}                                                                    ;|
else {                                                               ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, ^{PgUp}                                                ;|
    else                                                             ;|
        Send, +^{PgUp}                                               ;|
    return                                                           ;|
}                                                                    ;|
return                                                               ;|
;-----------------------------------o                                ;|
CapsLock & p::                                                       ;|
if GetKeyState("control") = 0                                        ;|
{                                                                    ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, {PgDn}                                                 ;|
    else                                                             ;|
        Send, +{PgDn}                                                ;|
    return                                                           ;|
}                                                                    ;|
else {                                                               ;|
    if GetKeyState("alt") = 0                                        ;|
        Send, ^{PgDn}                                                ;|
    else                                                             ;|
        Send, +^{PgDn}                                               ;|
    return                                                           ;|
}                                                                    ;|
return                                                               ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                     CapsLock Mouse Controller                      ;|
;-----------------------------------o---------------------------------o
;                   CapsLock + Up   |  Mouse Up                      ;|
;                   CapsLock + Down |  Mouse Down                    ;|
;                   CapsLock + Left |  Mouse Left                    ;|
;                  CapsLock + Right |  Mouse Right                   ;|
;    CapsLock + Enter(Push Release) |  Mouse Left Push(Release)      ;|
;-----------------------------------o---------------------------------o
CapsLock & Up::    MouseMove, 0, -10, 0, R                           ;|
CapsLock & Down::  MouseMove, 0, 10, 0, R                            ;|
CapsLock & Left::  MouseMove, -10, 0, 0, R                           ;|
CapsLock & Right:: MouseMove, 10, 0, 0, R                            ;|
;-----------------------------------o                                ;|
CapsLock & Enter::                                                   ;|
SendEvent {Blind}{LButton down}                                      ;|
KeyWait Enter                                                        ;|
SendEvent {Blind}{LButton up}                                        ;|
return                                                               ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                           CapsLock Deletor                         ;|
;-----------------------------------o---------------------------------o
;                     CapsLock + n  |  Ctrl + Delete (Delete a Word) ;|
;                     CapsLock + m  |  Delete                        ;|
;                     CapsLock + ,  |  BackSpace                     ;|
;                     CapsLock + .  |  Ctrl + BackSpace              ;|
;-----------------------------------o---------------------------------o
CapsLock & ,:: Send, {Del}                                           ;|
CapsLock & .:: Send, ^{Del}                                          ;|
CapsLock & m:: Send, {BS}                                            ;|
CapsLock & n:: Send, ^{BS}                                           ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                            CapsLock Editor                         ;|
;-----------------------------------o---------------------------------o
;                     CapsLock + z  |  Ctrl + z (Cancel)             ;|
;                     CapsLock + x  |  Ctrl + x (Cut)                ;|
;                     CapsLock + c  |  Ctrl + c (Copy)               ;|
;                     CapsLock + v  |  Ctrl + v (Paste)              ;|
;                     CapsLock + a  |  Ctrl + a (Select All)         ;|
;                     CapsLock + y  |  Ctrl + y (Yeild)              ;|
;                     CapsLock + w  |  Ctrl + Right(Move as [vim: w]);|
;                     CapsLock + b  |  Ctrl + Left (Move as [vim: b]);|
;-----------------------------------o---------------------------------o
CapsLock & z:: Send, ^z                                              ;|
CapsLock & x:: Send, ^x                                              ;|
CapsLock & c:: Send, ^c                                              ;|
CapsLock & v:: Send, ^v                                              ;|
CapsLock & a:: Send, ^a                                              ;|
CapsLock & y:: Send, ^y                                              ;|
CapsLock & w:: Send, ^{Right}                                        ;|
CapsLock & b:: Send, ^{Left}                                         ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                       CapsLock Media Controller                    ;|
;-----------------------------------o---------------------------------o
;                    CapsLock + F1  |  Volume_Mute                   ;|
;                    CapsLock + F2  |  Volume_Down                   ;|
;                    CapsLock + F3  |  Volume_Up                     ;|
;                    CapsLock + F3  |  Media_Play_Pause              ;|
;                    CapsLock + F5  |  Media_Next                    ;|
;                    CapsLock + F6  |  Media_Stop                    ;|
;-----------------------------------o---------------------------------o
CapsLock & F1:: Send, {Volume_Mute}                                  ;|
CapsLock & F2:: Send, {Volume_Down}                                  ;|
CapsLock & F3:: Send, {Volume_Up}                                    ;|
CapsLock & F4:: Send, {Media_Play_Pause}                             ;|
CapsLock & F5:: Send, {Media_Next}                                   ;|
CapsLock & F6:: Send, {Media_Stop}                                   ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                      CapsLock Window Controller                    ;|
;-----------------------------------o---------------------------------o
;                     CapsLock + s  |  Ctrl + Tab (Swith Tag)        ;|
;                     CapsLock + q  |  Ctrl + W   (Close Tag)        ;|
;   (Disabled)  Alt + CapsLock + s  |  AltTab     (Switch Windows)   ;|
;               Alt + CapsLock + q  |  Ctrl + Tab (Close Windows)    ;|
;                     CapsLock + g  |  AppsKey    (Menu Key)         ;|
;-----------------------------------o---------------------------------o
CapsLock & s::Send, ^{Tab}                                           ;|
;-----------------------------------o                                ;|
CapsLock & q::                                                       ;|
if GetKeyState("alt") = 0                                            ;|
{                                                                    ;|
    Send, ^w                                                         ;|
}                                                                    ;|
else {                                                               ;|
    Send, !{F4}                                                      ;|
    return                                                           ;|
}                                                                    ;|
return                                                               ;|
;-----------------------------------o                                ;|
CapsLock & g:: Send, {AppsKey}                                       ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                        CapsLock Self Defined Area                  ;|
;-----------------------------------o---------------------------------o
;                     CapsLock + d  |  Alt + d(Dictionary)           ;|
;                     CapsLock + f  |  Open translator               ;|
;                     CapsLock + e  |  Open Search Engine            ;|
;                     CapsLock + r  |  Open Shell                    ;|
;                     CapsLock + t  |  Open Text Editor              ;|
;-----------------------------------o---------------------------------o
CapsLock & d:: Send, !d                                              ;|
CapsLock & f:: Run "F:\Youdao\Dict\YoudaoDict.exe"                   ;|
CapsLock & e:: Run http://bing.com/                                  ;|
CapsLock & r:: Run Powershell                                        ;|
CapsLock & t:: Run "C:\Users\Gavin\AppData\Local\Programs\Microsoft VS Code\Code.exe" ;|
;---------------------------------------------------------------------o


;=====================================================================o
;                        CapsLock Char Mapping                       ;|
;-----------------------------------o---------------------------------o
;                     CapsLock + ;  |  Enter (Cancel)                ;|
;                     CapsLock + '  |  =                             ;|
;                     CapsLock + [  |  Back         (Visual Studio)  ;|
;                     CapsLock + ]  |  Goto Define  (Visual Studio)  ;|
;                     CapsLock + /  |  Comment      (Visual Studio)  ;|
;                     CapsLock + \  |  Uncomment    (Visual Studio)  ;|
;                     CapsLock + 1  |  Build and Run(Visual Studio)  ;|
;                     CapsLock + 2  |  Debuging     (Visual Studio)  ;|
;                     CapsLock + 3  |  Step Over    (Visual Studio)  ;|
;                     CapsLock + 4  |  Step In      (Visual Studio)  ;|
;                     CapsLock + 5  |  Stop Debuging(Visual Studio)  ;|
;                     CapsLock + 6  |  Shift + 6     ^               ;|
;                     CapsLock + 7  |  Shift + 7     &               ;|
;                     CapsLock + 8  |  Shift + 8     *               ;|
;                     CapsLock + 9  |  Shift + 9     (               ;|
;                     CapsLock + 0  |  Shift + 0     )               ;|
;-----------------------------------o---------------------------------o
CapsLock & `;:: Send, {Enter}                                        ;|
CapsLock & ':: Send, =                                               ;|
CapsLock & [:: Send, ^-                                              ;|
CapsLock & ]:: Send, {F12}                                           ;|
;-----------------------------------o                                ;|
CapsLock & /::                                                       ;|
Send, ^e                                                             ;|
Send, c                                                              ;|
return                                                               ;|
;-----------------------------------o                                ;|
CapsLock & \::                                                       ;|
Send, ^e                                                             ;|
Send, u                                                              ;|
return                                                               ;|
;-----------------------------------o                                ;|
CapsLock & 1:: Send,^{F5}                                            ;|
CapsLock & 2:: Send,{F5}                                             ;|
CapsLock & 3:: Send,{F10}                                            ;|
CapsLock & 4:: Send,{F11}                                            ;|
CapsLock & 5:: Send,+{F5}                                            ;|
;-----------------------------------o                                ;|
CapsLock & 6:: Send,+6                                               ;|
CapsLock & 7:: Send,+7                                               ;|
CapsLock & 8:: Send,+8                                               ;|
CapsLock & 9:: Send,+9                                               ;|
CapsLock & 0:: Send,+0                                               ;|
;---------------------------------------------------------------------o


```

### .xmodmap
```
!-- xmodmap ~/.Xmodmap --!
! Caps_Lock -> Mode_switch
clear  lock
add    mod5 = Caps_Lock
keycode  66 = Mode_switch

! Caps_Lock + space -> Escape
keycode  65 = space NoSymbol Escape

! Caps_Lock + r     -> Menu
keycode  27 = r R Menu

! Caps_Lock + ,     -> Delete
keycode  59 = comma less Delete

! Caps_Lock + m     -> BackSpace
keycode  58 = m M BackSpace

! Caps_Lock + u     -> Prior
keycode  30 = u U Prior

! Caps_Lock + p     -> Next
keycode  33 = p P Next

! Caps_Lock + k     -> Up
keycode  45 = k K Up

! Caps_Lock + j     -> Down
keycode  44 = j J Down

! Caps_Lock + h     -> Left
keycode  43 = h H Left

! Caps_Lock + l     -> Right
keycode  46 = l L Right

! Caps_Lock + i     -> Home
keycode  31 = i I Home

! Caps_Lock + ;     -> CapsLock
keycode  47 = semicolon colon Caps_Lock

! Caps_Lock + o     -> End
keycode  32 = o O End

```
