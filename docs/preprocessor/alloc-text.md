---
title: alloc_text
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 399e8956a511f289b480e66db7f03cac0a6c7c20
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031359"
---
# <a name="alloctext"></a>alloc_text
Pojmenuje oddíl kódu, do kterého mají být umístěny dané definice funkcí. Pro pojmenované funkce se tato direktiva pragma musí vyskytnout mezi deklarátorem funkce a její definicí.

## <a name="syntax"></a>Syntaxe

```
#pragma alloc_text( "
textsection
", function1, ... )
```

## <a name="remarks"></a>Poznámky

**Alloc_text** – Direktiva pragma nezpracovává členských funkcí jazyka C++ a přetížené funkce. Se vztahuje pouze na funkce deklarované s propojení jazyka – to znamená, že funkce deklarované s **extern "C"** specifikace propojení. Při pokusu o použití této direktivy pragma u funkce s propojením jazyka C++ dojde k vygenerování chyby kompilátoru.

Jelikož adresování funkcí pomocí `__based` nepodporuje umístění oddílů zapotřebí použití **alloc_text** direktivy pragma. Název zadaný v *textsection* by měl být uzavřen do dvojitých uvozovek.

**Alloc_text** – Direktiva pragma musí vyskytovat za deklaracemi některý ze zadaných funkcí a před definicemi těchto funkcí.

Funkce odkazované v **alloc_text** – Direktiva pragma musí definovat ve stejném modulu jako direktiva. Pokud tato podmínka není splněna a dojde-li později ke kompilaci nedefinované funkce do jiné textové části, zachycení této chyby není zaručeno. Ačkoli program bude obvykle fungovat správně, nebude funkce přidělena ve správném oddílu.

Další omezení **alloc_text** jsou následující:

- Nelze ji použít uvnitř funkce.

- Musí být použita po deklaraci funkce, ale před její definicí.

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)