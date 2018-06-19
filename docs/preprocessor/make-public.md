---
title: make_public – | Microsoft Docs
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
ms.openlocfilehash: 27db5ac934973178e2485327090ed70f994becec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849584"
---
# <a name="makepublic"></a>make_public
Označuje, že nativní typ by měl mít veřejný přístup k sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma make_public(type)  
```  
  
### <a name="parameters"></a>Parametry  
 Parametr `type` je název typu, který bude mít veřejný přístup k sestavení.  
  
## <a name="remarks"></a>Poznámky  
Direktiva pragma `make_public` je užitečná, pochází-li nativní typ, na který je odkazováno, ze souboru .h, jenž nelze změnit. Je-li třeba nativní typ použít v podpisu veřejné funkce v typu s veřejnou viditelností sestavení, musí mít nativní typ také veřejný přístup k sestavení. Pokud toto neplatí, kompilátor vygeneruje upozornění.  
  
Direktiva pragma `make_public` musí být zadána v globálním oboru a je platná pouze od okamžiku, v němž je deklarována a platí až po konec souboru zdrojového kódu.  
  
Nativní typ může být implicitně nebo explicitně privátní; v tématu [viditelnost typů](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) Další informace.  
  
## <a name="example"></a>Příklad  
Následující příklad je obsah souboru .h, který obsahuje definice dvou nativních struktur.  
  
```cpp  
// make_public_pragma.h  
struct Native_Struct_1 { int i; };  
struct Native_Struct_2 { int i; };  
```  
  
## <a name="example"></a>Příklad  
Následující příklad kódu používá hlavičkový soubor a ukazuje, že pokud nejsou nativní struktury explicitně označeny pomocí direktivy pragma `make_public` jako veřejné, vygeneruje kompilátor při pokusu o použití nativních struktur v podpisu veřejné funkce veřejného spravovaného typu upozornění.  
  
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