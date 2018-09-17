---
title: Spuštění příkazu NMAKE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdc9d89dbc0e77a8002cc34e5d010ee49d761da4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706690"
---
# <a name="running-nmake"></a>Spuštění příkazu NMAKE

## <a name="syntax"></a>Syntaxe

> **NMAKE** [*možnost* ...] [*makra* ...] [*cíle* ...] [**\@**<em>commandfile</em> ...]

## <a name="remarks"></a>Poznámky

Zadat jenom sestavení NMAKE *cíle* nebo, pokud není zadaný žádný, první cíl v souboru pravidel. Může být prvního cíle souboru pravidel [pseudotarget](../build/pseudotargets.md) vytvoří další cíle. NMAKE používá zadaným /F; soubory pravidel Pokud /F není zadán, použije soubor pravidel soubor v aktuálním adresáři. Pokud není zadán žádný soubor pravidel, používá k sestavení příkazového řádku pravidla odvozování *cíle*.

*Commandfile* textový soubor (nebo soubor odezvy) obsahuje vstupní příkazového řádku. Ostatní vstupy můžete předcházejícím nebo následujícím \@ *commandfile*. Smí obsahovat cestu. V *commandfile*, zalomení řádků jsou považovány za mezery. Pokud obsahují mezery, uzavřete do uvozovek definice maker.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[NMake – možnosti](../build/nmake-options.md)

[Tools.ini a příkaz NMAKE](../build/tools-ini-and-nmake.md)

[Kódy ukončení příkazu NMake](../build/exit-codes-from-nmake.md)

## <a name="see-also"></a>Viz také

[NMAKE – referenční zdroje](../build/nmake-reference.md)