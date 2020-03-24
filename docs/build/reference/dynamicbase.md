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
ms.openlocfilehash: ab7682c8344d6fc36ded03e7ef885c83d2f19ab7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169042"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Určuje, jestli se má generovat spustitelná image, která se dá náhodně využít při načítání, pomocí funkce ASLR (Address Space layouting Layout) systému Windows, která byla poprvé dostupná v systému Windows Vista.

## <a name="syntax"></a>Syntaxe

> **/DYNAMICBASE**[ **: No**]

## <a name="remarks"></a>Poznámky

Možnost **/DYNAMICBASE** upraví hlavičku *spustitelné bitové kopie*, soubor. dll nebo. exe, aby označovala, zda by měla být aplikace náhodně založena během načítání, a umožňuje náhodné vyřazení virtuálních adres, což ovlivňuje umístění virtuálních paměti hald, zásobníků a dalších přidělení operačního systému. Možnost **/DYNAMICBASE** se vztahuje na 32 bitové i 64 bitové kopie. ASLR je podporován v systému Windows Vista a novějších operačních systémech. Možnost ignoruje starší operační systémy.

Ve výchozím nastavení je povolená možnost **/DYNAMICBASE** . Pokud chcete tuto možnost zakázat, použijte **/DYNAMICBASE: No**. Možnost **/DYNAMICBASE** je vyžadována, pokud má možnost [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) efekt.

## <a name="see-also"></a>Viz také

- [EDITBIN – možnosti](editbin-options.md)
- [Obrana zabezpečení softwaru Windows ISV](https://msdn.microsoft.com/library/bb430720.aspx)
