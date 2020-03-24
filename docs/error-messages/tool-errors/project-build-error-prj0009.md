---
title: Chyba sestavení projektu PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: d02325504b04a13cd15dee0bd70891bf5a63b62e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192957"
---
# <a name="project-build-error-prj0009"></a>Chyba sestavení projektu PRJ0009

Protokol buildu nelze otevřít pro zápis.

**Ujistěte se, že soubor není otevřen jiným procesem a není chráněn proti zápisu.**

Po nastavení vlastnosti **protokolování sestavení** na **Ano** a provedení sestavení nebo opětovného sestavení se vizuál C++ nepodařilo otevřít protokol sestavení ve výhradním režimu.

Zkontrolujte nastavení **protokolování sestavení** otevřením dialogového okna **Možnosti** (v nabídce **nástroje** klikněte na příkaz **Možnosti** ) a potom ve složce **Projects (projekty** ) vyberte **sestavení VC + +** . Soubor buildu se nazývá BuildLog. htm a zapisuje se do zprostředkujícího adresáře $ (IntDir).

Možné důvody pro tuto chybu:

- Spouštíte dva procesy vizuálu C++ a snažíte se současně sestavit stejnou konfiguraci stejného projektu.

- Soubor protokolu sestavení je otevřen v procesu, který soubor zamkne.

- Uživatel nemá oprávnění k vytvoření souboru.

- Aktuální uživatel nemá oprávnění k zápisu do souboru BuildLog. htm.
