---
title: Odkazy (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
ms.openlocfilehash: aafc582299402eabab2736ac7d07b6c4c397413c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616445"
---
# <a name="references-c"></a>Odkazy (C++)

Odkaz, jako je ukazatel, uchovává adresu objektu, který je umístěn kdekoli v paměti. Na rozdíl od ukazatel, odkaz po inicializaci nelze nastavit nebo odkazovat na jiný objekt nebo nastavit na hodnotu null. Existují dva druhy odkazy: odkazy lvalue, které odkazují na pojmenované proměnné a r-hodnoty odkazy, které se vztahují [dočasný objekt](../cpp/temporary-objects.md). & – Operátor označuje, že reference na lvalue a & & – operátor oznamuje odkaz rvalue nebo odkaz univerzální (rvalue nebo l-hodnoty) v závislosti na kontextu.

Odkazy mohou být deklarovány pomocí následující syntaxe:

> \[*specifikátory třídy úložiště*] \[ *kvalifikátory cv*] *specifikátory typu* \[ *ms modifikátor*]  *deklarátor* \[ **=** *výraz*]**;**

Žádné platné deklarátoru určující odkaz může být použit. Není-li odkaz na odkaz na funkci nebo typ pole, platí následující zjednodušenou syntaxi:

> \[*specifikátory třídy úložiště*] \[ *kvalifikátory cv*] *specifikátory typu* \[ **&** nebo **&&**] \[ *kvalifikátory cv*] *identifikátor* \[ **=** *výraz*]**;**

Odkazy jsou deklarovány následujícím způsobem:

1. Specifikátory deklarace:

   - Volitelný specifikátor paměťové třídy.

   - Volitelné **const** a/nebo **volatile** kvalifikátory.

   - Specifikátor typu: název typu.

1. Deklarátor:

   - Volitelný specifický modifikátor Microsoft. Další informace najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).

   - **&** Operátor nebo **&&** operátor.

   - Volitelné **const** a/nebo **volatile** qualifers.

   - Identifikátor.

1. Volitelný inicializátor.

Složitějších deklarátorů formuláře pro ukazatele na pole a funkce platí také pro odkazy na pole a funkce. Další informace najdete v tématu [ukazatele](../cpp/pointers-cpp.md).

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

V následující program, Všimněte si, že název objektu, `s`a odkaz na objekt, `SRef`, můžete použít stejně jako v programech:

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
