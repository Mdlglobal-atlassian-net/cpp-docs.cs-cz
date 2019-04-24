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
ms.openlocfilehash: 13987b4ba9c25db0f5417da562ff86f4230937d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271824"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Určuje, jestli se má generovat spustitelnou bitovou kopii, která lze náhodně změnit základ v okamžiku načtení pomocí funkce adresu místo rozložení náhodné (technologie ASLR) z Windows, která byla poprvé dostupná ve Windows Vista.

## <a name="syntax"></a>Syntaxe

> **/ DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>Poznámky

**Možnost/DynamicBase** možnost změní záhlaví *spustitelné bitové kopie*, soubor .dll nebo .exe, označuje, zda by měl být náhodně změnit základ v okamžiku načtení aplikace a umožňuje virtuální adresa náhodné přidělování, který má vliv na umístění virtuální paměti haldy, zásobníků a další přidělení operačního systému. **Možnost/DynamicBase** možnost se vztahuje na 32bitové i 64bitové obrazy. Technologie ASLR je podporován v systémech Windows Vista a novějších operačních systémech. Tato možnost je ignorována ve starších operačních systémech.

Ve výchozím nastavení **možnost/DynamicBase** je povolená. Chcete-li tuto možnost zakázat, použijte **kopii**. **Možnost/DynamicBase** možnost je vyžadována pro [/highentropyva](highentropyva-support-64-bit-aslr.md) možnost mají nějaký efekt.

## <a name="see-also"></a>Viz také:

- [EDITBIN – možnosti](editbin-options.md)
- [Obrana zabezpečení ISV softwaru Windows](https://msdn.microsoft.com/library/bb430720.aspx)