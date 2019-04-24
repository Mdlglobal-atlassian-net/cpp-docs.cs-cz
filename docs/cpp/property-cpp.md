---
title: property (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: ece1016b7a18873dfa477b0f8b6ae4271a0f8001
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301484"
---
# <a name="property-c"></a>property (C++)

**Microsoft Specific**

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

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)