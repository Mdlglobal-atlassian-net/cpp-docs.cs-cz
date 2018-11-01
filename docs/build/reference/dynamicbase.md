---
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: fb8bfd4f4b11d14dbbc605f4366cf1cd5446a319
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430785"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Určuje, jestli se má generovat spustitelnou bitovou kopii, která lze náhodně změnit základ v okamžiku načtení pomocí funkce adresu místo rozložení náhodné (technologie ASLR) z Windows, která byla poprvé dostupná ve Windows Vista.

## <a name="syntax"></a>Syntaxe

> **/ DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>Poznámky

**Možnost/DynamicBase** možnost změní záhlaví *spustitelné bitové kopie*, soubor .dll nebo .exe, označuje, zda by měl být náhodně změnit základ v okamžiku načtení aplikace a umožňuje virtuální adresa náhodné přidělování, který má vliv na umístění virtuální paměti haldy, zásobníků a další přidělení operačního systému. **Možnost/DynamicBase** možnost se vztahuje na 32bitové i 64bitové obrazy. Technologie ASLR je podporován v systémech Windows Vista a novějších operačních systémech. Tato možnost je ignorována ve starších operačních systémech.

Ve výchozím nastavení **možnost/DynamicBase** je povolená. Chcete-li tuto možnost zakázat, použijte **kopii**. **Možnost/DynamicBase** možnost je vyžadována pro [/highentropyva](highentropyva-support-64-bit-aslr.md) možnost mají nějaký efekt.

## <a name="see-also"></a>Viz také:

- [EDITBIN – možnosti](../../build/reference/editbin-options.md)
- [Obrana zabezpečení ISV softwaru Windows](https://msdn.microsoft.com/library/bb430720.aspx)