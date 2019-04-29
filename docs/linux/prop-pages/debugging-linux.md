---
title: Ladicí program vlastnosti (C++ pro Linux) | Dokumentace Microsoftu
ms.date: 9/26/2017
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: ac5992ca9921a87616b9ff10e5744791510b7a7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393061"
---
# <a name="c-debugging-properties-linux-c"></a>C++ vlastnosti ladění (Linux C++)

Vlastnost | Popis | Možnosti
--- | ---| ---
Před spuštěním příkazu | Příkaz, který běží v prostředí před zahájením ladění a před ladicí program běží a je možné ovlivnit ladicí prostředí.
Program | Úplná cesta k programu pro ladění na vzdáleném systému. Toto je cesta ve vzdáleném systému. Pokud zůstane prázdná nebo nezměněná, výchozí aktuální výstup projektu.
Argumenty programu | Argumenty příkazového řádku k laděnému programu předat.
Pracovní adresář | Pracovní adresář vzdálené aplikace. Ve výchozím nastavení je to domovský adresář uživatele.
Další příkazy ladicího programu | Další příkazy gdb pro ladicí program ke spuštění před zahájením ladění.
Číslo portu ladicího programu | Číslo portu pro komunikaci ladicího programu se vzdálený ladicí program. Port nesmí být používán místně. Tato hodnota musí být kladné číslo mezi 1 a 65535. Pokud není zadán volné číslo portu se použije.
Číslo portu vzdáleného ladicího programu | Číslo portu, na kterém server vzdáleného ladicího programu (gdbserver) naslouchá ve vzdáleném systému. Port nesmí být používán na vzdáleném systému. Tato hodnota musí být kladné číslo mezi 1 a 65535. Pokud nejsou zadané volné číslo portu od 4444 se použije.
Režim ladění | Určuje, jak rozhraní ladicího programu s gdb. V režimu gdb použije ladicí program řídí gdb místo prostředí ve vzdáleném systému. V režimu gdbserver gdb běží místně a připojuje k gdbserver vzdálené spouštění. | **gdbserver**<br>**gdb**<br>
Další cesty hledání symbolů | Další cesty hledání symbolů ladění (solib-search-path).
Ladit podřízené procesy | Určuje, zda chcete povolit ladění podřízených procesů.
Povolte Python přehledný výpis | Povolí přehledný výpis u hodnot výrazu. Podporováno pouze v režimu ladění gdb.
Soubor vizualizace | Výchozí nativní soubor vizualizace (.natvis) obsahuje direktivy vizualizace pro typy SLT. Další soubory .natvis, které patří do aktuálního řešení budou načteny automaticky.
Mapování cesty souborů dalších zdrojů | Další ekvivalence cest pro ladicí program má použít k mapování Windows zdroje názvy souborů s názvy souborů zdrojového systému Linux. Formát je "\<windows-path > =\<linux-path >;...". Bude odkazovat název zdrojového souboru nalezený v cestě Windows jako kdyby se našla ve stejné relativní pozici v rámci cesta v Linuxu. Soubory nalezené v místním projektu nevyžadují dodatečné mapování.
