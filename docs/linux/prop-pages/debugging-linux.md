---
title: Vlastnosti ladicího programu (Linux C++) | Dokumenty společnosti Microsoft
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: bebee7a2b3bcfd880a538acae35c9616b3b1bd46
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446175"
---
# <a name="c-debugging-properties-linux-c"></a>Vlastnosti ladění jazyka C++ (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

| Vlastnost | Popis | Choices |
|--|--|--|
| Vzdálený ladicí stroj | **Visual Studio 2019 verze 16.1**: Určuje počítač, na který má být program ladit. Může se lišit od vzdáleného počítače sestavení, který je zadán na stránce [Obecné.](general-linux.md) Připojení cílového počítače můžete přidat nebo upravit pomocí **nástroje** > **Options** > **Cross Platform** > **Connection Manager**. |
| Příkaz před spuštěním | Příkaz, který je spuštěn na prostředí před spuštěním ladicího programu, který lze použít k ovlivnění prostředí ladění. |
| Program | Úplná cesta vzdáleného systému k programu k ladění. Pokud zůstane prázdný nebo beze změny, výchozí aktuální výstup projektu. |
| Argumenty programu | Argumenty příkazového řádku, které mají být předávány laděné mu programu. |
| Pracovní adresář | Pracovní adresář vzdálené aplikace. Ve výchozím nastavení je domovský adresář uživatele. |
| Další příkazy ladicího programu | Další `gdb` příkazy pro ladicí program spustit před zahájením ladění. |
| Číslo portu ladicího programu | Číslo portu pro komunikaci ladicího programu se vzdáleným ladicím programem. Port nesmí být používán místně. Tato hodnota musí být kladná a mezi 1 a 65535. Pokud není dodáno, použije se číslo volného portu. |
| Číslo portu vzdáleného ladicího programu | Číslo portu, na kterém vzdálený `gdbserver` ladicí server naslouchá ve vzdáleném systému. Port nesmí být ve vzdáleném systému používán. Tato hodnota musí být kladná a mezi 1 a 65535. Pokud není dodáno, je použito číslo volného portu od 4444. |
| Režim ladění | Určuje, jak ladicí program `gdb`propojuje s aplikací . V *režimu gdb*přejde `gdb` ladicí program přes prostředí vzdáleného systému. V *režimu gdbserver*, `gdb` běží `gdbserver` místně a připojuje se ke spuštění vzdáleně. | **gdbserver**<br/>**Gdb** |
| Další cesty hledání symbolů | Další vyhledávací cesta pro ladicí symboly (solib-search-path). |
| Ladění podřízených procesů | Určuje, zda má být povolit ladění podřízených procesů. |
| Povolit python pěkný tisk | Povolit pěkný tisk hodnot výrazů. Podporováno pouze v režimu ladění gdb. |
| Vizualizační soubor | Výchozí nativní vizualizační soubor (.natvis) obsahující směrnic vizualizace pro typy SLT. Ostatní soubory .natvis, které patří k aktuálnímu řešení, se načítají automaticky. |
| Mapa cesty k dalším zdrojům | Další ekvivalence cesty pro ladicí program použít k mapování názvů zdrojových souborů systému Windows na názvy zdrojových souborů Linuxu. Formát je\<" windows-path\<>= linux-path>;...". Název zdrojového souboru nalezený pod cestou systému Windows je odkazován, jako by byl nalezen ve stejné relativní pozici pod cestou Linuxu. Soubory nalezené v místním projektu nevyžadují další mapování. |

::: moniker-end
