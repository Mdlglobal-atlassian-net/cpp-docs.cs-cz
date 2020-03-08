---
title: Vlastnosti ladicího programu C++(Linux) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: 8a57e983a32e1ef1eca2bf2452df2cd39d453467
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883704"
---
# <a name="c-debugging-properties-linux-c"></a>C++Vlastnosti ladění (Linux C++)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Vlastnost | Popis | Vlastnit
--- | ---| ---
Vzdálený ladicí počítač | **Visual Studio 2019 verze 16,1**: Určuje počítač, na kterém chcete program ladit. Může se lišit od vzdáleného počítače sestavení, který je zadaný na stránce [Obecné](general-linux.md) . Připojení k cílovému počítači můžete přidat nebo upravit pomocí **nástrojů** > **možností** >  > **Správce připojení**pro **různé platformy** .
Příkaz před spuštěním | Příkaz, který je spuštěn v prostředí před spuštěním ladicího programu, který lze použít pro ovlivnění ladicího prostředí.
Program | Úplná cesta ke vzdálenému systému pro program, který se má ladit. Pokud je ponecháno prázdné nebo nezměněné, použije se výchozí výstup aktuálního projektu.
Argumenty programu | Argumenty příkazového řádku, které se mají předat laděnému programu
Pracovní adresář | Pracovní adresář vzdálené aplikace. Ve výchozím nastavení se jedná o domovský adresář uživatele.
Další příkazy ladicího programu | Další `gdb` příkazy pro ladicí program ke spuštění před spuštěním ladění.
Číslo portu ladicího programu | Číslo portu pro komunikaci ladicího programu se vzdáleným ladicím programem. Port se nesmí používat místně. Tato hodnota musí být kladná a v rozmezí od 1 do 65535. Pokud není zadaný, použije se bezplatné číslo portu.
Číslo portu vzdáleného ladicího programu | Číslo portu, na kterém `gdbserver` vzdáleného ladicího serveru naslouchá na vzdáleném systému. Port se nesmí používat na vzdáleném systému. Tato hodnota musí být kladná a v rozmezí od 1 do 65535. Pokud není zadaný, použije se volné číslo portu začínající od 4444.
Režim ladění | Určuje způsob, jakým se `gdb`rozhraní ladicího programu. V *režimu GDB*se jednotky ladicího programu `gdb` přes prostředí na vzdáleném systému. V *režimu gdbserver*se `gdb` spouští místně a připojuje se k `gdbserver` se spouští vzdáleně. | **gdbserver**<br/>**GDB**
Další cesty pro hledání symbolů | Další cesta hledání pro symboly ladění (SOLIB-Search-Path).
Ladit podřízené procesy | Určuje, zda má být povoleno ladění podřízených procesů.
Povolit velmi pro tisk v Pythonu | Povolí poměrně tisk hodnot výrazu. Podporováno pouze v režimu ladění GDB.
Soubor vizualizace | Výchozí nativní soubor vizualizace (. Natvis) obsahující direktivy vizualizace pro SLT typy. Další soubory. Natvis, které patří k aktuálnímu řešení, se načítají automaticky.
Mapa cesty k souboru dalších zdrojů | Další cesta je rovnocenná, aby ladicí program mohl použít k mapování názvů zdrojových souborů Windows na Linux názvů zdrojových souborů. Formát je "\<Windows-Path > =\<Linux-Path >;...". Název zdrojového souboru, který se nachází pod cestou Windows, se odkazuje, jako by se našel ve stejné relativní pozici v cestě Linux. Soubory nalezené v místním projektu nevyžadují další mapování.

::: moniker-end
