---
title: vlastnosti (C++) | Microsoft Docs
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
ms.openlocfilehash: a791615f7fd91a7ccfcda45b23fc524ebd9b6400
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="property-c"></a>property (C++)
**Konkrétní Microsoft**  
  
 Tento atribut lze použít pro nestatické „virtuální datové členy“ v definici třídy nebo struktury. Kompilátor zpracovává tyto „virtuální datové členy“ jako datové členy změnou jejich odkazů na volání funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   __declspec( property( get=get_func_name ) ) declarator  
   __declspec( property( put=put_func_name ) ) declarator  
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 Když kompilátor uvidí datový člen deklarovat s Tento atribut na pravé straně operátoru výběru členů ("**.**"nebo"**->**"), převede ji na operace **získat** nebo **put** funkci, v závislosti na tom, jestli je takový výraz hodnotou l nebo r-value. V další komplikovanější kontextů, jako například "`+=`", přepište provádí provádění obou **získat** a **put**.  
  
 Tento atribut lze použít také v deklaraci prázdného pole v definici třídy nebo struktury. Příklad:  
  
```  
__declspec(property(get=GetX, put=PutX)) int x[];  
```  
  
 Výše uvedený příkaz označuje, že `x[]` lze použít s jedním nebo více indexy pole. V tomto případě bude `i=p->x[a][b]` převeden na `i=p->GetX(a, b)` a `p->x[a][b] = i` bude převeden na `p->PutX(a, b, i);`  
  
 **Konkrétní Microsoft END**  
  
## <a name="example"></a>Příklad  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)