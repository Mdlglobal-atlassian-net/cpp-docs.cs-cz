---
title: Obecné vlastnosti (linuxový projekt C++)
description: Popisuje vlastnosti projektu Linux, které můžete nastavit v sadě Visual Studio na stránce Obecné vlastnosti.
ms.date: 01/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: 832f10ca2c95e40ff7ece23462105fa49014aa5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446162"
---
# <a name="general-properties-linux-c"></a>Obecné vlastnosti (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

| Vlastnost | Popis | Choices |
|--|--|--|
| Výstupní adresář | Určuje relativní cestu k výstupnímu adresáři souboru. Může obsahovat proměnné prostředí. |
| Zprostředkující adresář | Určuje relativní cestu k zprostředkujícímu adresáři souborů. Může obsahovat proměnné prostředí. |
| Cílový název | Určuje název souboru, který tento projekt generuje. |
| Rozšíření cíle | Určuje příponu souboru `.a`(například), kterou tento projekt generuje. |
| Rozšíření odstranit při čištění | Specifikace se stupněm čárka se zástupnými znaky, pro které soubory v zprostředkujícím adresáři odstranit při čištění nebo znovu sestavit. |
| Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do který se má zapisovat, když je povoleno protokolování sestavení. |
| Sada nástrojů platformy | Určuje sadu nástrojů použitou pro sestavení aktuální konfigurace. Pokud není nastavena, použije se výchozí sada nástrojů. |
| Vzdálený stroj sestavení | Zobrazí cílový počítač nebo zařízení, které se má použít pro vzdálené sestavení, nasazení a ladění. Připojení cílového počítače můžete přidat nebo upravit pomocí **nástroje** > **Options** > **Cross Platform** > **Connection Manager**.<br /> **Visual Studio 2019 verze 16.1** Můžete zadat jiný počítač pro ladění na stránce [ladění.](debugging-linux.md) |
| Kořenový adresář vzdáleného sestavení | Určuje cestu k adresáři ve vzdáleném počítači nebo zařízení. |
| Vzdálený adresář projektu sestavení | Určuje cestu k adresáři ve vzdáleném počítači nebo zařízení projektu. |
| Vzdálený adresář nasazení | **Visual Studio 2019 verze 16.1** Určuje cestu k adresáři ve vzdáleném počítači nebo zařízení k nasazení projektu. |
| Vzdálená kopie zahrnují adresáře | **Visual Studio 2019 verze 16.5**  Seznam adresářů pro rekurzivně kopírování z linuxového cíle. Tato vlastnost ovlivňuje vzdálenou kopii záhlaví pro technologie IntelliSense, ale nikoli sestavení. Lze jej použít, když je výchozí hodnota **kompilátoru IntelliSense** nastavena na hodnotu false. Pomocí **dalších adresářů zahrnutí** na kartě C/C++ Obecné určete další adresáře zahrnutí, které se mají použít jak pro technologie IntelliSense, tak pro sestavení. |
| Vzdálené kopie vyloučit adresáře | **Visual Studio 2019 verze 16.5** Seznam *adresářů,* které nelze kopírovat z linuxového cíle. Tato vlastnost se obvykle používá k odebrání podadresářů zahrnutí adresářů. |
| Technologie IntelliSense používá výchozí hodnoty kompilátoru. | **Visual Studio 2019 verze 16.5** Určuje, zda má být kompilátor odkazovaný tímto projektem dotazován na výchozí seznam umístění zahrnutí. Tato umístění jsou automaticky přidána do seznamu vzdálených adresářů ke kopírování. Tuto vlastnost nastavte pouze na hodnotu false, pokud kompilátor nepodporuje parametry gcc-like. Kompilátory gcc i clang podporují dotazy na adresáře zahrnutí `g++ -x c++ -E -v -std=c++11`(například). |
| Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (.so)**<br/><br/>**Statická knihovna (.a)**<br/><br/>**Aplikace (.out)**<br/><br/>**Makefile** |
| Použití STL | Určuje, která standardní knihovna jazyka C++ se má pro tuto konfiguraci použít. | **Sdílená knihovna GNU Standard C++**<br/><br/>**Statická GNU Standardní C++ knihovna (-statická)** |

::: moniker-end
