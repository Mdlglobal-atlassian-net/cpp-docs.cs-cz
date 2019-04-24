---
title: Portování ze systému UNIX do Win32
ms.date: 08/02/2018
helpviewer_keywords:
- APIs [C++], porting to Win32
- Windows API [C++], migrating from UNIX
- migration [C++]
- UNIX [C++], porting to Win32
- porting to Win32 [C++], from UNIX
- porting to Win32 [C++]
- Win32 applications [C++], migrating from UNIX
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: 3146c94879532a5c58208369bb6d131a3a027c33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337346"
---
# <a name="porting-from-unix-to-win32"></a>Portování ze systému UNIX do Win32

Migrace aplikací ze systému UNIX do Windows, máte několik možností:

- Pomocí knihovny systému UNIX do portu aplikace ze systému UNIX do Win32

- Nativně portování aplikací ze systému UNIX do Win32

- Spouštění systému UNIX aplikací na Windows prostřednictvím podsystému POSIX

## <a name="unix-libraries"></a>Knihovny systému UNIX

Jednou z možností UNIX programátoři obvykle vezměte v úvahu používá unixových knihovny třetích stran, aby jejich UNIX kompilace kódu jako spustitelný soubor systému Win32. Několik obchodní (a aspoň jednu doménu public) knihovny udělat. Toto je možnost u některých aplikací. Výhodou těchto přenos knihoven je, že jejich minimalizovat úsilí pro počáteční přenos. Hlavní nevýhody konkurenční softwarového produktu, je, že nativního portu Win32 aplikace bude obecně rychlejší a bude mít nevyhnutelně další funkce. Může být není vhodný pro aplikaci, aby krok mimo jeho prostředí systému UNIX, pokud je potřeba provést volání Win32 získat větší výkon z Windows.

Následující seznam uvádí Microsoft a třetích stran pro přenos a podpora migrace systému UNIX do jazyka Visual C++:

### <a name="unix-migration-guides"></a>Průvodce migrací systému UNIX

[Průvodce migrací aplikace vlastní UNIX](https://technet.microsoft.com/library/bb656290.aspx) poskytuje technickou pomoc s migrace kódu ze systému UNIX do Win32 prostředí.

[Průvodce projektem migrace Unix](https://technet.microsoft.com/library/bb656287.aspx) doplňuje Průvodce migrací systému UNIX vlastní aplikace tím, že poskytuje základní nápovědy na migraci podstatné projekty ze systému UNIX do Win32. Průvodce poskytuje Rady na problémy, které je třeba zvážit v každé fázi migrace projektu.

### <a name="interopsystemscom"></a>InteropSystems.com

[http://www.interopsystems.com/](http://www.interopsystems.com/)

Server jiného výrobce pro společnost poskytující softwarem, který podporuje přenos ze systému UNIX do Win32.

### <a name="c-boost-web-site"></a>C++ Boost webové stránky

[http://boost.sourceforge.net/regression-logs/](http://boost.sourceforge.net/regression-logs/)

[http://boost.sourceforge.net/boost-build2/](http://boost.sourceforge.net/boost-build2/)

## <a name="porting-unix-applications-directly-to-win32"></a>Portování aplikací UNIX přímo do Win32

Další možností je přenesení aplikací systému UNIX do Win32 přímo. Pomocí knihovny ANSI jazyka C/C++ a obchodní knihovny kompilátoru jazyka C, řadu tradiční systém, který volá spoléhal na podle aplikací systému UNIX jsou k dispozici v aplikacích Win32.

Výstupní model **stdio**– na základě aplikací není potřeba změnit od konzoly Win32 API napodobují **stdio** model a verze *curses* existují, které používají rozhraní API konzoly Win32. Další informace najdete v tématu [SetConsoleCursorPosition](/windows/console/setconsolecursorposition).

Aplikace založené na soketu Berkeley potřebovat velmi málo změny pracovních jako aplikace typu Win32. Rozhraní Windows Sockets je navržená pro přenositelnost sokety BSD, s minimálními změnami, které jsou popsány v úvodní části specifikace rozhraní WinSock.

Windows podporuje CLS DCE, který RPC, tak, aby byly snadno použitelné aplikace založené na protokolu RPC. Zobrazit [RPC funkce](/windows/desktop/Rpc/rpc-functions).

Jedna z největších oblastí rozdíl je v modelu procesu. Se systémem UNIX `fork`; Win32 je nepodporuje. V závislosti na využívání `fork` a kódové základny Win32 má dvě rozhraní API, které je možné: `CreateProcess` a `CreateThread`. Aplikace systému UNIX, která větve více kopií sebe sama, může být přepracována v systému Win32 má více procesů nebo jednoho procesu s více vlákny. Pokud jsou používány více procesů, existují různé způsoby IPC, který slouží ke komunikaci mezi procesy, které (a možná se aktualizovat kód a data nového procesu vypadal nadřazeným prvkem, pokud funkce, která `fork` poskytuje je potřeba). Další informace o IPC najdete v tématu [meziprocesová komunikace](/windows/desktop/ipc/interprocess-communications).

Windows a UNIX Grafické modely se velmi liší. UNIX používá X okno systému grafického uživatelského rozhraní, zatímco Windows používá rozhraní GDI. Když je to podobný koncept, neexistuje jednoduchý mapování rozhraní API X GDI rozhraní API. Podpora OpenGL je ale k dispozici pro migraci aplikací založené na OpenGL systému UNIX. A jsou X klienti a servery pro Windows X. Zobrazit [kontexty zařízení](/windows/desktop/gdi/device-contexts) informace o rozhraní GDI.

Základní aplikace v systému UNIX, včetně mnoha aplikace CGI, by měl port snadno do prostředí Visual C++, které běží na Windows. Funkce jako `open`, `fopen`, `read`, `write` a ostatní jsou k dispozici v knihovně runtime Visual C++. Navíc existuje mapování 1: 1 mezi rozhraním API systému UNIX C a rozhraní API systému Win32: `open` k `CreateFile`, `read` k `ReadFile`, `write` k `WriteFile`, `ioctl` k `DeviceIOControl`, `close` k `CloseFile`, a tak dále.

## <a name="windows-posix-subsystem"></a>Subsystém Windows POSIX

Možnost UNIX programátoři podívat je subsystém Windows POSIX. Však podporuje pouze 1003.1 POSIX, která byla pouze verze POSIX standardizované při vytvoření Windows NT. Od té doby došlo malé nároky pro rozšíření subsystému, protože většina aplikací se převedl do Win32. Systém 1003.1 je omezená relevantní pro plně funkční aplikace, protože nezahrnuje mnoho možností (například ve verzi 1003.2 podporu sítě a tak dále). Úplné vybrané aplikace spuštěné v subsystému Windows POSIX nebudou mít přístup k funkcím Windows k dispozici pro aplikace Win32, jako jsou soubory mapované paměti, sítě a grafiky. Aplikace, jako je GREP, VI a LS jsou hlavního cíle podsystému Windows POSIX.

## <a name="see-also"></a>Viz také:

[Průvodce přenosem a upgradem Visual C++](visual-cpp-change-history-2003-2015.md)<br/>
[UNIX](../c-runtime-library/unix.md)<br/>
[Odvozená pravidla](../build/reference/inference-rules.md)
