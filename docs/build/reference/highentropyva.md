---
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: 90d3c868eaab85e3b1a2a416c9aa14b0e27ec8f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603980"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Určuje, zda spustitelné bitové kopie podporují náhodného generování rozložení prostoru adres 64-bit vysokou mírou entropie (technologie ASLR).

## <a name="syntax"></a>Syntaxe

> **/ HIGHENTROPYVA**[**: NO**]

## <a name="remarks"></a>Poznámky

Tato možnost změní záhlaví *spustitelné bitové kopie*, soubor .dll nebo .exe souboru, označuje, zda je podporována 64-bit ASLR. Pokud tato možnost je nastavena na spustitelný soubor a všechny moduly, na kterých závisí, operační systém, který podporuje 64bitové technologie ASLR základ segmentů spustitelné bitové kopie v okamžiku načtení pomocí náhodných adres v 64bitové virtuální adresní prostor. Tento rozsáhlý adresní prostor ztěžuje útočníkovi možnost uhádnout umístění konkrétní paměťové oblasti.

Ve výchozím nastavení, linker umožňuje **/highentropyva** pro 64bitové spustitelné bitové kopie. Tato možnost vyžaduje [/LARGEADDRESSAWARE](largeaddressaware.md), je také povolená ve výchozím nastavení pro 64bitové obrazy. **/ HIGHENTROPYVA** neplatí pro 32bitové spustitelné bitové kopie, pokud tato možnost je ignorována. Chcete-li explicitně zakázat tuto možnost, použijte **/HIGHENTROPYVA:NO**. Pro tuto možnost mají nějaký efekt [možnost/DynamicBase](dynamicbase.md) možnost musí být také nastavena.

## <a name="see-also"></a>Viz také:

- [EDITBIN – možnosti](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Obrana zabezpečení ISV softwaru Windows](https://msdn.microsoft.com/library/bb430720.aspx)
