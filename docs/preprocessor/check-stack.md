---
title: check_stack
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 49477a3b39db17047f349e341bd05c04954c964c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023370"
---
# <a name="checkstack"></a>check_stack
Instruuje kompilátor, chcete-li vypnout sondy zásobníku, pokud `off` (nebo `-`) je zadán, nebo chcete zapnout sondy zásobníku, pokud `on` (nebo `+`) je zadán.

## <a name="syntax"></a>Syntaxe

```
#pragma check_stack([ {on | off}] )
#pragma check_stack{+ | -}
```

## <a name="remarks"></a>Poznámky

Pokud není uveden žádný argument, jsou považovány sondy zásobníku podle výchozích nastavení. Tato direktiva pragma se projeví v první funkci definovanou po direktivy pragma je zobrazena. Sondy zásobníku se ani jedna část maker ani funkcí, které jsou generované jako vložené.

Pokud není argument **check_stack –** – Direktiva pragma, kontrolou zásobníku se vrátí do chování zadané na příkazovém řádku. Další informace najdete v tématu [kompilátory](../build/reference/compiler-options.md). Interakce `#pragma check_stack` a [/Gs](../build/reference/gs-control-stack-checking-calls.md) možnost je shrnuto v následující tabulce.

### <a name="using-the-checkstack-pragma"></a>Pomocí check_stack – direktiva Pragma

|Syntaxe|Zkompilovaná<br /><br /> /GS – možnost?|Akce|
|------------|------------------------------------|------------|
|`#pragma check_stack( )` or<br /><br /> `#pragma check_stack`|Ano|Vypne kontroly zásobníku pro funkce, které následují|
|`#pragma check_stack( )` or<br /><br /> `#pragma check_stack`|Ne|Zapne kontroly zásobníku pro funkce, které následují|
|`#pragma check_stack(on)`<br /><br /> or `#pragma check_stack +`|Ano nebo Ne|Zapne kontroly zásobníku pro funkce, které následují|
|`#pragma check_stack(off)`<br /><br /> or `#pragma check_stack -`|Ano nebo Ne|Vypne kontroly zásobníku pro funkce, které následují|

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)