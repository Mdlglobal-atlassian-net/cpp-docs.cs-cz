---
title: Ladicí program vlastnosti (C++ pro Linux) | Dokumentace Microsoftu
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: d76e398d648db7c5cf65e4ca2bb1665aef4359ad
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821398"
---
# <a name="c-debugging-properties-linux-c"></a>C++ vlastnosti ladění (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range=">=vs-2017"

Vlastnost | Popis | Možnosti
--- | ---| ---
Vzdálený ladicí počítač | **Visual Studio 2019 version 16.1**: Určuje počítač, chcete-li ladit program na. Může být jiné než vzdálený sestavující počítač, který je zadaný na [Obecné](general-linux.md) stránky.
Před spuštěním příkazu | Spustí příkaz, který běží v prostředí před ladicí program, který je možné ovlivnit ladicí prostředí.
Program | Úplná cesta ve vzdáleném systému k programu pro ladění. Pokud necháte prázdné nebo beze změny, bude výchozí aktuální výstup projektu.
Argumenty programu | Argumenty příkazového řádku k laděnému programu předat.
Pracovní adresář | Pracovní adresář vzdálené aplikace. Ve výchozím nastavení je to domovský adresář uživatele.
Další příkazy ladicího programu | Další `gdb` příkazy pro ladicí program ke spuštění před zahájením ladění.
Číslo portu ladicího programu | Číslo portu pro komunikaci ladicího programu se vzdálený ladicí program. Port nesmí být používán místně. Tato hodnota musí být kladná a od 1 do 65535. Pokud není zadaný, použije se volné číslo portu.
Číslo portu vzdáleného ladicího programu | Číslo portu, na kterém vzdáleného ladícího programu serveru `gdbserver` naslouchá ve vzdáleném systému. Port nesmí být používán na vzdáleném systému. Tato hodnota musí být kladná a od 1 do 65535. Pokud není zadaný, použije se volné číslo portu od 4444.
Režim ladění | Určuje, jak rozhraní ladicího programu s `gdb`. V *režimu gdb použije*, ladicí program jednotky `gdb` místo prostředí ve vzdáleném systému. V *režimu gdbserver*, `gdb` používá místně a připojuje k `gdbserver` vzdálené spouštění. | **gdbserver**<br/>**gdb**
Další cesty hledání symbolů | Další cesty hledání symbolů ladění (solib-search-path).
Ladit podřízené procesy | Určuje, zda chcete povolit ladění podřízených procesů.
Povolte Python přehledný výpis | Povolí přehledný výpis u hodnot výrazu. Podporováno pouze v režimu ladění gdb.
Soubor vizualizace | Výchozí nativní soubor vizualizace (.natvis) obsahuje direktivy vizualizace pro typy SLT. Další soubory .natvis, které patří do aktuálního řešení jsou načteny automaticky.
Mapování cesty souborů dalších zdrojů | Další ekvivalence cest pro ladicí program má použít k mapování Windows zdroje názvy souborů s názvy souborů zdrojového systému Linux. Formát je "\<windows-path > =\<linux-path >;...". Název zdrojového souboru nalezený v cestě Windows se odkazuje, jako kdyby se nachází ve stejné relativní pozici v rámci cesta v Linuxu. Soubory nalezené v místním projektu nevyžadují dodatečné mapování.

::: moniker-end
