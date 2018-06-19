---
title: Ladicího programu vlastnosti (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 55f07d8903d8110410648e352d364151bf6d2a73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331097"
---
# <a name="c-debugging-properties-linux-c"></a>C++ – ladění vlastnosti (Linux C++)

Vlastnost | Popis | Možnosti
--- | ---| ---
Předem spuštění příkazu | Příkaz, který běží v prostředí před spuštěním ladění a před ladicí program běží a je možné mít vliv na prostředí ladění.
Program | Úplná cesta k programu k ladění na vzdáleném systému. To je cesta ve vzdáleném systému. Pokud prázdné nebo beze změny jeho výchozí aktuální výstupu projektu @.
Program argumenty | Argumenty příkazového řádku, které mají být předána do programu laděné.
Pracovní adresář | Vzdálené aplikace pracovní adresář. Ve výchozím nastavení domovského adresáře uživatele.
Příkazy Další ladicí program | Další gdb příkazy pro ladicí program ke spuštění před zahájením ladění.
Číslo portu ladicí program | Číslo portu pro komunikaci ladicí program pomocí vzdáleného ladicího programu. Port nesmí být používán místně. Tato hodnota musí být kladné mezi 1 a 65535. Pokud není zadaná číslo volné portu se použije.
Číslo portu vzdáleného ladicího programu | Číslo portu, na kterém je server vzdáleného ladicího programu (gdbserver) přijímá na ve vzdáleném systému. Port nesmí být používán ve vzdáleném systému. Tato hodnota musí být kladné mezi 1 a 65535. Pokud nejsou zadané číslo portu volné od 4444 se použije.
Režim ladění | Určuje, jak rozhraní ladicího programu s gdb. Ladicí program v režimu gdb jednotky gdb přes prostředí ve vzdáleném systému. V režimu gdbserver gdb běží místně a připojí k gdbserver systémem vzdáleně. | **gdbserver**<br>**gdb**<br>
Cesty hledání další Symbol | Další vyhledávací cesta pro symboly ladění (solib cesta hledání).
Ladění podřízené procesy | Určuje, jestli chcete povolit ladění podřízené procesy.
Povolit Python poměrně tisk | Povolte poměrně tisk hodnot výrazů. Podporuje jenom v gdb režim ladění.
Vizualizace souboru | Výchozí nativní vizualizace obsahující (.natvis) vizualizace direktivy pro typy SLT. Další .natvis soubory, které patří k aktuálnímu řešení se automaticky načte.
Další zdroje souboru cesty mapy | Další cesta rovnocenností ladicí program na používat k mapování Windows zdroje názvů souborů na názvy Linux zdrojových souborů. Formát je "\<cestu windows > =\<linux-path >;...". Se bude odkazovat název zdrojového souboru nalezen v cestě Windows jako, pokud je ve stejné relativní pozici, na cestě Linux nebyl nalezen. Soubory, které jsou v místním projektu nevyžadují další mapování.
