---
title: alloc_text | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
dev_langs:
- C++
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d131cee2194ba139fdb99d9c0fa7ae2c922fe84d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073810"
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

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)