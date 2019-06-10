---
title: Obecné vlastnosti (projektu C++ Linux) | Dokumentace Microsoftu
ms.date: 06/07/2019
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: ce3683f11d80c253195b751b5eed364fbc04b68a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821279"
---
# <a name="general-properties-linux-c"></a>Obecné vlastnosti (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range=">=vs-2017"

Vlastnost | Popis | Možnosti
--- | ---| ---
Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru; může obsahovat proměnné prostředí.
Zprostředkující adresář | Určuje relativní cestu k adresáři přechodového souboru; může obsahovat proměnné prostředí.
Cílový název | Určuje název souboru, který bude tento projekt generovat.
Cílová přípona | Určuje rozšíření souboru, který bude tento projekt generovat. (Příklad: .a)
Přípony odstraňované při čištění | Středníkem oddělená specifikace zástupných znaků určujících, které soubory v přechodovém adresáři odstranit při čištění nebo opětovném sestavení.
Soubor protokolu sestavení | Určuje soubor protokolu sestavení pro zápis při protokolování sestavení je povolená.
Sada nástrojů platformy | Určuje, nástrojů pro sestavení aktuální konfigurace. Pokud není využito set, výchozí sady nástrojů
Vzdálený sestavující počítač | Cílový počítač nebo zařízení pro vzdálené sestavení, nasazení a ladění. **Visual Studio 2019 verze 16.1** lze zadat jiný počítač pro ladění [ladění](debugging-linux.md) stránky.
Vzdálený Buildovací kořenový adresář | Určuje cestu k adresáři na vzdáleném počítači či zařízení.
Adresář projektu vzdáleného buildu | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení pro tento projekt.
Typ konfigurace | Určuje typ výstupu generovaného touto konfigurací. | **Dynamická knihovna (.so)** – dynamická knihovna (.so)<br>**Statická knihovna (.a)** – statická knihovna (.a)<br>**Aplikace (.out)** – aplikace (.out)<br>**Soubor pravidel** -souboru pravidel<br>
Použití STL | Určuje, která standardní knihovna C++ použít pro tuto konfiguraci. | **Knihovna sdílené GNU Standard C++**<br>**Knihovna statické GNU Standard C++ (-statické)**<br>

::: moniker-end

