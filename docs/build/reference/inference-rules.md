---
title: Odvozená pravidla
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: 0c1db9150c3b2c36c35e6802bfcd639af45bdc82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291272"
---
# <a name="inference-rules"></a>Odvozená pravidla

Odvozená pravidla zadat příkazy aktualizace cíle a odvodit závislé položky pro cíle. Odvozené pravidlo s rozšířeními shodovat s jedním cílem a závislé, které mají stejný základní název. Odvozená pravidla jsou definované uživatelem nebo předdefinovaný; Předdefinovaná pravidla lze předefinovat.

Pokud zastaralý závislostí nemá žádné příkazy a pokud [. PŘÍPONY](dot-directives.md) obsahuje vlastnost extension závislé položky, používá NMAKE pravidlo, jehož rozšíření odpovídají cíl a existující soubor v adresáři zadané nebo aktuální. Pokud více než jedno pravidlo odpovídá existující soubory **. PŘÍPONY** seznam určuje, která bude použita; seznamu priority dělí zleva doprava. Pokud závislý soubor buď neexistuje, není uveden jako cíl v jiném bloku popis odvozené pravidlo můžete vytvořit chybějící závislé z jiného souboru se stejným základním názvem. Pokud blok popis cíl neobsahuje žádné závislé položky nebo příkazy, odvozené pravidlo aktualizovat cíl. Odvozená pravidla můžete vytvořit jiný cíl příkazového řádku, i v případě, že neexistuje žádný blok popis. NMAKE může vyvolat pravidla pro odvozené závislé, i v případě, že je zadán explicitní závislé.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Definice pravidla](defining-a-rule.md)

[Pravidla dávkového režimu](batch-mode-rules.md)

[Předdefinovaná pravidla](predefined-rules.md)

[Odvozené závislé objekty a pravidla](inferred-dependents-and-rules.md)

[Priorita odvozených pravidel](precedence-in-inference-rules.md)

## <a name="see-also"></a>Viz také:

[NMAKE – referenční zdroje](nmake-reference.md)