---
title: Odvozená pravidla
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: d3d7ca41d96d3845237b445edefff05044dacdc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170511"
---
# <a name="inference-rules"></a>Odvozená pravidla

Odvozená pravidla poskytují příkazy pro aktualizaci cílů a odvodit závislosti pro cíle. Rozšíření v pravidle odvození se shodují s jedním cílem a závislým, který má stejný základní název. Odvozená pravidla jsou definovaná uživatelem nebo předdefinovaným. Předdefinovaná pravidla lze předefinovat.

Pokud nezávislá závislost nemá žádné příkazy a pokud [. PŘÍPONY](dot-directives.md) obsahují rozšíření závislé na objektu, NMAKE používá pravidlo, jehož rozšíření odpovídají cíli a existujícímu souboru v aktuálním nebo zadaném adresáři. Pokud více než jedno pravidlo odpovídá existujícím souborům, bude **. Seznam přípon** určuje, který z nich se má použít. zobrazí dolní pravé stranu v seznamu zleva doprava. Pokud závislý soubor neexistuje a není uveden jako cíl v jiném bloku popisu, pravidlo odvození může vytvořit chybějící závislou událost z jiného souboru se stejným základním názvem. Pokud cíl bloku popisu nemá žádné závislé položky nebo příkazy, pravidlo odvození může aktualizovat cíl. Odvozená pravidla mohou vytvořit cíl příkazového řádku i v případě, že žádný blok popisu neexistuje. NMAKE může vyvolat pravidlo pro odvozenou závislost, i když je zadaný explicitní závislý parametr.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

[Definování pravidla](defining-a-rule.md)

[Pravidla dávkového režimu](batch-mode-rules.md)

[Předdefinovaná pravidla](predefined-rules.md)

[Odvozené závislé objekty a pravidla](inferred-dependents-and-rules.md)

[Priorita pro odvozená pravidla](precedence-in-inference-rules.md)

## <a name="see-also"></a>Viz také

[NMAKE – referenční zdroje](nmake-reference.md)
