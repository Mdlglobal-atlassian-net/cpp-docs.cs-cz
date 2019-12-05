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
ms.openlocfilehash: 2353f0861f0f249416d0bb84a7a951b1cb6d64bc
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857330"
---
# <a name="references-c"></a>Odkazy (C++)

Odkaz, jako je ukazatel, ukládá adresu objektu, který je umístěn jinde v paměti. Na rozdíl od ukazatele nemůže být odkaz po inicializaci vytvořen pro odkazování na jiný objekt nebo nastavení na hodnotu null. Existují dva druhy odkazů: odkazy lvalue odkazující na pojmenovanou proměnnou a odkazy rvalue odkazující na [dočasný objekt](../cpp/temporary-objects.md). Operátor & označuje odkaz lvalue a operátor & & označuje buď odkaz rvalue, nebo univerzální odkaz (buď rvalue nebo lvalue) v závislosti na kontextu.

Odkazy mohou být deklarovány pomocí následující syntaxe:

> \[*storage-class-specifiers*] \[*cv-qualifiers*] *type-specifiers* \[*ms-modifier*] *declarator* \[ **=** *expression*] **;**

Může být použit libovolný platný deklarátor určující odkaz. Pokud odkaz není odkazem na typ funkce nebo pole, platí následující zjednodušená syntaxe:

> \[*specifikátory třídy úložiště*] \[*specifikátory* *cv*] \[ **&** nebo **&&** ] \[*kvalifikátory cv*] *identifikátor* **\[=** *výraz*] **;**

Odkazy jsou deklarovány pomocí následujícího pořadí:

1. Specifikátory deklarace:

   - Volitelný specifikátor paměťové třídy.

   - Volitelné kvalifikátory **const** nebo **volatile** .

   - Specifikátor typu: název typu.

1. Deklarátor:

   - Volitelný specifický modifikátor Microsoft. Další informace najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Operátor **&** nebo operátor **&&**

   - Volitelné **const** a/nebo **volatile** kvalifikátorů.

   - Identifikátor.

1. Volitelný inicializátor.

Složitější formuláře deklarátor pro ukazatele na pole a funkce se vztahují také na odkazy na pole a funkce. Další informace najdete v tématu [ukazatelé](../cpp/pointers-cpp.md).

V seznamu odděleném čárkami se může zobrazit několik deklarátory a inicializátorů za jediným specifikátorem deklarace. Příklad:

```cpp
int &i;
int &i, &j;
```

Odkazy, ukazatele a objekty mohou být deklarovány společně:

```cpp
int &ref, *ptr, k;
```

Odkaz uchovává adresu objektu, ale chová syntakticky jako objekt.

V následujícím programu si všimněte, že název objektu, `s`a odkaz na objekt, `SRef`, lze v programech použít stejným způsobem:

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
