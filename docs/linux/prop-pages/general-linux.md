---
title: Obecné vlastnosti (projekt C++ pro Linux)
description: Popisuje vlastnosti projektu pro Linux, které lze nastavit v sadě Visual Studio na stránce Obecné vlastnosti.
ms.date: 01/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: 6d598e9d52037d709cba87d98ad375455d8c00b0
ms.sourcegitcommit: 49e4fb3e0300fe86c814130661f1bf68b16e72e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "76031347"
---
# <a name="general-properties-linux-c"></a>Obecné vlastnosti (Linux C++)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Vlastnost | Popis | Choices
--- | ---| ---
Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru. Může obsahovat proměnné prostředí.
Zprostředkující adresář | Určuje relativní cestu k adresáři zprostředkujícího souboru. Může obsahovat proměnné prostředí.
Název cíle | Určuje název souboru, který tento projekt vygeneruje.
Cílová Přípona | Určuje příponu souboru (například `.a`), který tento projekt vygeneruje.
Přípony k odstranění při čištění | Střední-oddělená specifikace zástupných znaků, pro které se soubory v mezilehlém adresáři odstraňují při čištění nebo opětovném sestavení.
Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do kterého se má zapisovat, pokud je povolené protokolování sestavení.
Sada nástrojů platformy | Určuje sadu nástrojů použitou pro sestavení aktuální konfigurace. Pokud není nastavena, je použita výchozí sada nástrojů.
Vzdálený sestavovací počítač | Cílový počítač nebo zařízení, které se má použít pro vzdálené sestavení, nasazení a ladění. **Visual Studio 2019 verze 16,1** Na stránce [ladění](debugging-linux.md) můžete zadat jiný počítač pro ladění.
Kořenový adresář vzdáleného buildu | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení.
Adresář vzdáleného projektu sestavení | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení pro daný projekt.
Adresář vzdáleného nasazení | **Visual Studio 2019 verze 16,1** Určuje cestu k adresáři na vzdáleném počítači nebo zařízení pro nasazení projektu.
Vzdálené kopírování – adresáře zahrnutí | **Visual Studio 2019 verze 16,5**  Seznam adresářů, které se mají rekurzivně kopírovat z cíle systému Linux. Tato vlastnost má vliv na vzdálenou kopii hlavičky pro technologii IntelliSense, ale ne na sestavení. Dá se použít, když **IntelliSense používá výchozí hodnoty kompilátoru** nastavenou na false. Použijte **Další adresáře include** na kartě C/C++ obecné a určete další adresáře zahrnutí pro technologii IntelliSense i sestavení.
Vzdálené kopírování adresáře pro vyloučení | **Visual Studio 2019 verze 16,5** Seznam *adresářů, které se* nekopírují z cíle systému Linux. Obvykle se tato vlastnost používá k odebrání podadresářů adresáře include.
IntelliSense používá výchozí hodnoty kompilátoru | **Visual Studio 2019 verze 16,5** Určuje, zda se má dotaz na kompilátor, na který odkazuje tento projekt, ve výchozím seznamu vložených umístění. Tato umístění se automaticky přidají do seznamu vzdálených adresářů, které se mají zkopírovat. Tuto vlastnost nastavte na hodnotu false pouze v případě, že kompilátor nepodporuje parametry typu RSZ. Kompilátory RSZ i Clang podporují dotazy pro adresáře include (například `g++ -x c++ -E -v -std=c++11`).
Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (. so)**<br/>**Statická knihovna (. a)**<br/>**Aplikace (. out)**<br/>**Makefile**
Použití STL | Určuje, C++ která standardní knihovna se má použít pro tuto konfiguraci. | **Sdílená knihovna C++ GNU Standard**<br/>**Statická knihovna GNU C++ Standard (-static)**

::: moniker-end
