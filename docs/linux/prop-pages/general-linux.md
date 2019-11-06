---
title: Obecné vlastnosti (projekt C++ pro Linux) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: c17a5e0214e6365d604a80bd4b3891858f0f9186
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626817"
---
# <a name="general-properties-linux-c"></a>Obecné vlastnosti (Linux C++)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Vlastnost | Popis | Vlastnit
--- | ---| ---
Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru. může obsahovat proměnné prostředí.
Zprostředkující adresář | Určuje relativní cestu k adresáři zprostředkujícího souboru. může obsahovat proměnné prostředí.
Cílový název | Určuje název souboru, který bude tento projekt generovat.
Cílová Přípona | Určuje příponu souboru, kterou bude tento projekt generovat. (Příklad:. a)
Přípony k odstranění při čištění | Středníky oddělená specifikace zástupných znaků, pro které se soubory v zprostředkujícím adresáři odstraňují při čištění nebo opětovném sestavení.
Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do kterého se má zapisovat, pokud je povolené protokolování sestavení.
Sada nástrojů platformy | Určuje sadu nástrojů použitou pro sestavení aktuální konfigurace. Pokud není nastavená, použije se výchozí sada nástrojů.
Vzdálený sestavovací počítač | Cílový počítač nebo zařízení, které se má použít pro vzdálené sestavení, nasazení a ladění. **Visual Studio 2019 verze 16,1** Na stránce [ladění](debugging-linux.md) lze zadat jiný počítač pro ladění.
Kořenový adresář vzdáleného buildu | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení.
Adresář vzdáleného projektu sestavení | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení pro daný projekt.
Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (. so)** – dynamická knihovna (. so)<br>**Statická knihovna (. a)** – statická knihovna (. a)<br>**Aplikace (. out)** – aplikace (. out)<br>**Makefile** -makefile<br>
Použití STL | Určuje, C++ která standardní knihovna se má použít pro tuto konfiguraci. | **Sdílená knihovna C++ GNU Standard**<br>**Statická knihovna GNU C++ Standard (-static)**<br>

::: moniker-end
