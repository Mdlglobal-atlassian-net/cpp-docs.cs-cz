---
title: property (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: 03f71739698fd20a01fd72567ce5b9babc176327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179299"
---
# <a name="property-c"></a>property (C++)

**Specifické pro společnost Microsoft**

Tento atribut lze použít pro nestatické „virtuální datové členy“ v definici třídy nebo struktury. Kompilátor zpracovává tyto „virtuální datové členy“ jako datové členy změnou jejich odkazů na volání funkce.

## <a name="syntax"></a>Syntaxe

```
   __declspec( property( get=get_func_name ) ) declarator
   __declspec( property( put=put_func_name ) ) declarator
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator
```

## <a name="remarks"></a>Poznámky

Když kompilátor uvidí datový člen deklarovaný pomocí tohoto atributu na pravé straně operátoru výběru členů (" **.** " nebo " **->** "), převede operaci na funkci `get` nebo `put`, a to v závislosti na tom, zda takový výraz je l-hodnota nebo r-hodnota. Ve složitějších kontextech, jako je například "`+=`", je přepisování provedeno pomocí `get` a `put`.

Tento atribut lze použít také v deklaraci prázdného pole v definici třídy nebo struktury. Příklad:

```cpp
__declspec(property(get=GetX, put=PutX)) int x[];
```

Výše uvedený příkaz označuje, že `x[]` lze použít s jedním nebo více indexy pole. V tomto případě bude `i=p->x[a][b]` převeden na `i=p->GetX(a, b)` a `p->x[a][b] = i` bude převeden na `p->PutX(a, b, i);`

**Specifické pro konec Microsoftu**

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

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
