---
title: Odkazy (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9bd01cf5c153fcd31bae1a73fead87fe480cdd2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030417"
---
# <a name="references-c"></a>Odkazy (C++)

Odkaz, jako je ukazatel, uchovává adresu objektu, který je umístěn kdekoli v paměti. Na rozdíl od ukazatel, odkaz po inicializaci nelze nastavit nebo odkazovat na jiný objekt nebo nastavit na hodnotu null. Existují dva druhy odkazy: odkazy lvalue, které odkazují na pojmenované proměnné a r-hodnoty odkazy, které se vztahují [dočasný objekt](../cpp/temporary-objects.md). & – Operátor označuje, že reference na lvalue a & & – operátor oznamuje odkaz rvalue nebo odkaz univerzální (rvalue nebo l-hodnoty) v závislosti na kontextu.

Odkazy mohou být deklarovány pomocí následující syntaxe:

```
[storage-class-specifiers] [cv-qualifiers] type-specifiers 
[ms-modifier] declarator [= expression];
```

Žádné platné deklarátoru určující odkaz může být použit. Není-li odkaz na odkaz na funkci nebo typ pole, platí následující zjednodušenou syntaxi:

```
[storage-class-specifiers] [cv-qualifiers] type-specifiers [& or &&] 
[cv-qualifiers] identifier [= expression];
```

Odkazy jsou deklarovány následujícím způsobem:

1. Specifikátory deklarace:

- Volitelný specifikátor paměťové třídy.

- Volitelné **const** a/nebo **volatile** kvalifikátory.

- Specifikátor typu: název typu.

- 2. Deklarátor:

- Volitelný specifický modifikátor Microsoft. Další informace najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).

- & – Operátor nebo & & – operátor.

- Volitelné **const** a/nebo **volatile** qualifers.

- Identifikátor.

3. Volitelný inicializátor.

Složitější forms deklarátoru ukazatele na pole a funkce platí také pro odkazy na pole a funkce, najdete v části [ukazatele](../cpp/pointers-cpp.md).

Více inicializátory a deklarátory mohou zobrazit v čárkami oddělený seznam po jedné deklaraci specifikátor. Příklad:

```cpp
int &i;
int &i, &j;
```

Odkazy, ukazatele a objekty mohou být deklarovány společně:

```cpp
int &ref, *ptr, k;
```

Odkaz na uchovává adresu objektu, ale chová se syntakticky stejně jako objekt.

V následující program, Všimněte si, že název objektu, `Today`a odkaz na objekt, `TodayRef`, můžete použít stejně jako v programech:

## <a name="example"></a>Příklad

```cpp
// references.cpp
#include <stdio.h>
struct S {
   short i;
};

int main() {
   S  s;   // Declare the object.
   S& SRef = s;   // Declare the reference.
   s.i = 3;

   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);

   SRef.i = 4;
   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);
}
```

```Output
3
3
4
4
```

## <a name="see-also"></a>Viz také:

[Argumenty funkce typu odkazu](../cpp/reference-type-function-arguments.md)<br/>
[Funkce vracející typ odkazu](../cpp/reference-type-function-returns.md)<br/>
[Odkazy na ukazatele](../cpp/references-to-pointers.md)

