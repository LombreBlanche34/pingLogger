just a ping checker / logger in batch
<br />
check every 3 secondes (can be edit)

```batch
@echo off
set pingOk=0
set pingPas=0
:loop
cls
title OK: %pingOk% PAS: %pingPas%
type ping.log
ping google.com -n 2 >NUL
rem imagine google down
if not errorlevel 1 (
	echo [%DATE% %TIME%] PING OK>>ping.log
	set /a pingOk = %pingOk% + 1
) else (
	echo [%DATE% %TIME%] XXX PING PAS XXX>>ping.log
	set /a pingPas = %pingPas% + 1
)
ping 127.0.0.1 -n 3 >NUL
goto loop
```
