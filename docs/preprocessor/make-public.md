---
title: make_public | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bdec8afa2088cad5faf700b3946926bb9d85748
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466306"
---
# <a name="makepublic"></a>make_public
Označuje, že nativní typ by měl mít veřejný přístup k sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma make_public(type)  
```  
  
### <a name="parameters"></a>Parametry  
*typ* je název typu, které chcete mít veřejný přístup k sestavení.  
  
## <a name="remarks"></a>Poznámky  

**make_public** oceníte, když je nativní typ, který chcete odkazovat ze souboru .h, jenž nelze změnit. Je-li třeba nativní typ použít v podpisu veřejné funkce v typu s veřejnou viditelností sestavení, musí mít nativní typ také veřejný přístup k sestavení. Pokud toto neplatí, kompilátor vygeneruje upozornění.  
  
**make_public** musí být zadána v globálním oboru a je platná pouze od bodu v němž je deklarována a platí až na konec souboru se zdrojovým kódem.  
  
Nativní typ může být implicitně nebo explicitně soukromý. Zobrazit [viditelnost typů](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) Další informace.  
  
## <a name="examples"></a>Příklady  
Následující příklad je obsah souboru .h, který obsahuje definice dvou nativních struktur.  
  
```cpp  
// make_public_pragma.h  
struct Native_Struct_1 { int i; };  
struct Native_Struct_2 { int i; };  
```  

Následující příklad kódu používá hlavičkový soubor a ukazuje, že pokud je explicitně označit nativních struktur jako veřejné, pomocí **make_public**, kompilátor vygeneruje upozornění při pokusu o použití nativních struktur v podpisu veřejné funkce veřejného spravovaného typu.  
  
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
  
## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)