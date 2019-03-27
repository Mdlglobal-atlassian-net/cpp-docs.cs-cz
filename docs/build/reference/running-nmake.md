---
title: Spuštění příkazu NMAKE
ms.date: 09/05/2018
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: dac5e9c1676278d150dd9802697a8ae8959a40e5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823320"
---
# <a name="running-nmake"></a>Spuštění příkazu NMAKE

## <a name="syntax"></a>Syntaxe

> **NMAKE** [*možnost* ...] [*makra* ...] [*cíle* ...] [**\@**<em>commandfile</em> ...]

## <a name="remarks"></a>Poznámky

Zadat jenom sestavení NMAKE *cíle* nebo, pokud není zadaný žádný, první cíl v souboru pravidel. Může být prvního cíle souboru pravidel [pseudotarget](pseudotargets.md) vytvoří další cíle. NMAKE používá zadaným /F; soubory pravidel Pokud /F není zadán, použije soubor pravidel soubor v aktuálním adresáři. Pokud není zadán žádný soubor pravidel, používá k sestavení příkazového řádku pravidla odvozování *cíle*.

*Commandfile* textový soubor (nebo soubor odezvy) obsahuje vstupní příkazového řádku. Ostatní vstupy můžete předcházejícím nebo následujícím \@ *commandfile*. Smí obsahovat cestu. V *commandfile*, zalomení řádků jsou považovány za mezery. Pokud obsahují mezery, uzavřete do uvozovek definice maker.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[NMake – možnosti](nmake-options.md)

[Tools.ini a příkaz NMAKE](tools-ini-and-nmake.md)

[Kódy ukončení příkazu NMake](exit-codes-from-nmake.md)

## <a name="see-also"></a>Viz také:

[NMAKE – referenční zdroje](nmake-reference.md)