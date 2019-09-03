---
title: check_stack – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 4c976692ec36cedcb73825ee0cc7093736a3a3dc
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216135"
---
# <a name="check_stack-pragma"></a>check_stack – direktiva pragma

Instruuje kompilátor, aby vypnul sondy zásobníku, Pokud je zadán **-** (nebo), nebo zapněte sondy zásobníku, pokud je zadána na **+** (nebo).

## <a name="syntax"></a>Syntaxe

> **#pragma check_stack (** [{ **on** | **off** }] **)** \
> **#pragma check_stack** { **+**  |  **-** }

## <a name="remarks"></a>Poznámky

Tato direktiva pragma se projeví u první funkce definované po výskytu direktivy pragma. Sondy zásobníku nejsou součástí maker ani funkcí, které jsou vygenerovány jako vložené.

Pokud nezadáte argument pro direktivu pragma **check_stack** , Kontrola zásobníku se vrátí k chování zadanému na příkazovém řádku. Další informace naleznete v tématu [Možnosti kompilátoru](../build/reference/compiler-options.md). Interakce `#pragma check_stack` s možností a [/GS](../build/reference/gs-control-stack-checking-calls.md) je shrnuta v následující tabulce.

### <a name="using-the-check_stack-pragma"></a>Použití direktivy pragma check_stack

|Syntaxe|Kompilováno s<br /><br /> /GS možnost?|Akce|
|------------|------------------------------------|------------|
|`#pragma check_stack( )`ani<br /><br /> `#pragma check_stack`|Ano|Vypne kontrolu zásobníku pro funkce, které následují.|
|`#pragma check_stack( )`ani<br /><br /> `#pragma check_stack`|Ne|Zapne kontrolu zásobníku pro funkce, které následují.|
|`#pragma check_stack(on)`<br /><br /> ani`#pragma check_stack +`|Ano nebo Ne|Zapne kontrolu zásobníku pro funkce, které následují.|
|`#pragma check_stack(off)`<br /><br /> ani`#pragma check_stack -`|Ano nebo Ne|Vypne kontrolu zásobníku pro funkce, které následují.|

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
