---
title: vlastnosti (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- property_cpp
dev_langs:
- C++
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4673101d41b896ed3fc19aa1998aa9329064b41
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408608"
---
# <a name="property-c"></a>property (C++)
**Specifické pro Microsoft**  
  
 Tento atribut lze použít pro nestatické „virtuální datové členy“ v definici třídy nebo struktury. Kompilátor zpracovává tyto „virtuální datové členy“ jako datové členy změnou jejich odkazů na volání funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
   __declspec( property( get=get_func_name ) ) declarator  
   __declspec( property( put=put_func_name ) ) declarator  
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 Když kompilátor narazí na datový člen deklarovaný pomocí tohoto atributu na pravé straně operátoru výběru členů ("**.**"nebo"**->**"), převede operaci `get` nebo `put` funkce, v závislosti na tom, jestli je takový výraz l hodnotou nebo r-hodnotou. U více komplikovaných kontextů, jako například "`+=`", je provedena revize pomocí `get` a `put`.  
  
 Tento atribut lze použít také v deklaraci prázdného pole v definici třídy nebo struktury. Příklad:  
  
```cpp 
__declspec(property(get=GetX, put=PutX)) int x[];  
```  
  
 Výše uvedený příkaz označuje, že `x[]` lze použít s jedním nebo více indexy pole. V tomto případě bude `i=p->x[a][b]` převeden na `i=p->GetX(a, b)` a `p->x[a][b] = i` bude převeden na `p->PutX(a, b, i);`  
  
 **Specifické pro END Microsoft**  
  
## <a name="example"></a>Příklad  
  
```cpp 
// declspec_property.cpp  
struct S {  
   int i;  
   void putprop(int j) {   
      i = j;  
   }  
  
   int getprop() {  
      return i;  
   }  
  
   __declspec(property(get = getprop, put = putprop)) int the_prop;  
};  
  
int main() {  
   S s;  
   s.the_prop = 5;  
   return s.the_prop;  
}  
```  
  
## <a name="see-also"></a>Viz také:  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)