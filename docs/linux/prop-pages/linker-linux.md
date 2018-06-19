---
title: Vlastnosti linkeru (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 9187222d2ced21ece2f183655591c483abc8d500
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333102"
---
# <a name="linker-properties-linux-c"></a>Vlastnosti linkeru (Linux C++)

## <a name="general"></a>Obecné

Vlastnost | Popis | Možnosti
--- | ---| ---
Výstupní soubor | Možnost přepíše výchozí název a umístění program, který vytvoří linkeru. (-o).
Ukázat průběh | Zprávy o průběhu Linkeru výtisků.
Version | -Verze informuje – možnost linkeru uvést číslo verze v hlavičce ke spustitelnému souboru.
Povolit podrobný výstup | -Verbose – možnost informuje linkeru pro výstup podrobných zpráv pro ladění.
trasování | --Trasování informuje – možnost linkeru do výstupního vstupní soubory, jako jsou zpracovávány.
Symboly trasování | Tisk seznamu souborů, ve kterých se zobrazí symbol. (– symbol trasování = symbol)
Tisk – mapy | --Tisk mapy informuje – možnost linkeru do výstupního mapu odkaz.
Odkazy na symboly nerozpoznané sestavy | Tuto možnost, pokud je povoleno oznámí odkazy na symboly nevyřešená.
Optimalizace pro využití paměti | Optimalizujte pro využití paměti rereading tabulky symbolů podle potřeby.
Sdílené knihovny cesty pro hledání | Umožňuje uživateli k naplnění cesta hledání sdílenou knihovnu. (link - rpath-= cesta)
Další knihovny adresáře | Umožňuje uživateli přepsat cestu prostředí knihovny. (-L složku).
Linkeru | Určuje program, který má být vyvolán při propojování nebo cestu k linkeru do vzdáleného systému.
Časový limit odkaz | Vzdálené propojení vypršení časového limitu v milisekundách.
Kopírovat výstup | Určuje, jestli zkopírujte výstupní soubor sestavení ze vzdáleného systému v místním počítači.

## <a name="input"></a>Vstup

Vlastnost | Popis | Možnosti
--- | ---| ---
Ignorovat konkrétní výchozí knihovny | Určuje jeden nebo více názvů výchozí knihovny ignorovat. (--vyloučení knihovny lib, lib)
Ignorovat výchozí knihovny | Ignorovat výchozí knihovny a vyhledávat pouze knihovny explicitně zadat.
Vynutit odkazy na nedefinované symboly | Vynutí symbolu, které je třeba zadat ve výstupním souboru jako nedefinované symbol. (- u symbol – undefined = symbol)
Závislosti knihovny | Tato možnost umožňuje zadat další knihovny pro přidání do příkazového řádku linkeru. Další knihovny přidá na konec příkazového řádku linkeru s předponou 'lib' a konec s příponou '.a'.  (-lFILE)
Další závislosti | Určuje další položek, které chcete přidat do příkazového řádku odkaz.

## <a name="debugging"></a>Ladění

Vlastnost | Popis | Možnosti
--- | ---| ---
Ladicí program informací o symbolu | Ladicí program informací o symbolu z výstupního souboru. | **Zahrnout všechny**<br>**Vynechat pouze informace symbolu ladicí program**<br>**Vynechat všech informací o symbolu**<br>
Mapování názvu souboru | Možnost mapy informuje linkeru pro vytvoření souboru s mapováním se zadaným názvem uživatele. (-Mapy =)

## <a name="advanced"></a>Upřesnit

Vlastnost | Popis | Možnosti
--- | ---| ---
Po přemístění označte proměnné určené jen pro čtení | Tato možnost označí proměnné jen pro čtení po přemístění.
Povolit okamžitou funkce vazby | Tato možnost označí objektu pro vazbu okamžitou funkce.
Nevyžadují spustitelné zásobníku | Tato možnost označí výstup jako nevyžadující spustitelné zásobníku.
Celý archivu | Celý archivu používá všechny kódu ze zdroje a další závislosti.
