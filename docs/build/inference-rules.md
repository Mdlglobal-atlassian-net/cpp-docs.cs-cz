---
title: Odvozená pravidla | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed45e5ad61ea1cc50172cd86716b357baa64fa39
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724381"
---
# <a name="inference-rules"></a>Odvozená pravidla

Odvozená pravidla zadat příkazy aktualizace cíle a odvodit závislé položky pro cíle. Odvozené pravidlo s rozšířeními shodovat s jedním cílem a závislé, které mají stejný základní název. Odvozená pravidla jsou definované uživatelem nebo předdefinovaný; Předdefinovaná pravidla lze předefinovat.

Pokud zastaralý závislostí nemá žádné příkazy a pokud [. PŘÍPONY](../build/dot-directives.md) obsahuje vlastnost extension závislé položky, používá NMAKE pravidlo, jehož rozšíření odpovídají cíl a existující soubor v adresáři zadané nebo aktuální. Pokud více než jedno pravidlo odpovídá existující soubory **. PŘÍPONY** seznam určuje, která bude použita; seznamu priority dělí zleva doprava. Pokud závislý soubor buď neexistuje, není uveden jako cíl v jiném bloku popis odvozené pravidlo můžete vytvořit chybějící závislé z jiného souboru se stejným základním názvem. Pokud blok popis cíl neobsahuje žádné závislé položky nebo příkazy, odvozené pravidlo aktualizovat cíl. Odvozená pravidla můžete vytvořit jiný cíl příkazového řádku, i v případě, že neexistuje žádný blok popis. NMAKE může vyvolat pravidla pro odvozené závislé, i v případě, že je zadán explicitní závislé.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Definice pravidla](../build/defining-a-rule.md)

[Pravidla dávkového režimu](../build/batch-mode-rules.md)

[Předdefinovaná pravidla](../build/predefined-rules.md)

[Odvozené závislé objekty a pravidla](../build/inferred-dependents-and-rules.md)

[Priorita odvozených pravidel](../build/precedence-in-inference-rules.md)

## <a name="see-also"></a>Viz také

[NMAKE – referenční zdroje](../build/nmake-reference.md)