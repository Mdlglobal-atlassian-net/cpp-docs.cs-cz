---
title: -HIGHENTROPYVA | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fec9314be9d69e2cb0af2a98884bd78de1ff679
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211688"
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
