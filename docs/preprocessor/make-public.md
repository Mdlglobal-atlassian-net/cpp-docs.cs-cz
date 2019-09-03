---
title: make_public – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: d12fab685e0088993cb43073c3603bda12edd2f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218829"
---
# <a name="make_public-pragma"></a>make_public – direktiva pragma

Označuje, že nativní typ by měl mít veřejný přístup k sestavení.

## <a name="syntax"></a>Syntaxe

> **#pragma make_public (** *typ* **)**

### <a name="parameters"></a>Parametry

*textový*\
Název typu, který má mít veřejné přístupnost sestavení.

## <a name="remarks"></a>Poznámky

**make_public** je užitečná pro, pokud je nativní typ, na který chcete odkazovat, ze souboru hlaviček, který nelze změnit. Pokud chcete použít nativní typ v signatuře veřejné funkce v typu s viditelností veřejného sestavení, musí mít nativní typ také veřejnou přístupnost sestavení, jinak kompilátor vydá upozornění.

**make_public** musí být zadáno v globálním oboru. Je to v platnosti od bodu, ve kterém je deklarována až po konec souboru zdrojového kódu.

Nativní typ může být implicitně nebo explicitně soukromý. Další informace najdete v tématu [viditelnost typů](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).

## <a name="examples"></a>Příklady

Následující ukázka je obsah hlavičkového souboru, který obsahuje definice dvou nativních struktur.

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

Následující ukázka kódu používá hlavičkový soubor. Ukazuje, že pokud neoznačíte nativní struktury jako veřejné pomocí **make_public**, kompilátor vygeneruje upozornění, když se pokusíte použít nativní struktury v signatuře veřejné funkce ve veřejném spravovaném typu.

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
