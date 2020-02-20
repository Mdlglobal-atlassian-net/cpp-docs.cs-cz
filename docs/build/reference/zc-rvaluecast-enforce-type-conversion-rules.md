---
title: /Zc:rvalueCast (Vynucení pravidel převodu typů)
ms.date: 02/18/2020
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
ms.openlocfilehash: ac74192cad8a62e4c82b480038e727b114362cdd
ms.sourcegitcommit: b9aaaebe6e7dc5a18fe26f73cc7cf5fce09262c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504570"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Vynucení pravidel převodu typů)

Pokud je zadána možnost **`/Zc:rvalueCast`** , kompilátor správně identifikuje odkazový typ rvalue jako výsledek operace přetypování. Jeho chování odpovídá standardu C++ 11. Není-li parametr zadán, je chování kompilátoru stejné jako v aplikaci Visual Studio 2012.

## <a name="syntax"></a>Syntaxe

> **`/Zc:rvalueCast`**\
> **`/Zc:rvalueCast-`**

## <a name="remarks"></a>Poznámky

Je-li zadán **`/Zc:rvalueCast`** , kompilátor následuje oddíl 5,4 standardu c++ 11 a zpracovává pouze výrazy přetypování, jejichž výsledkem jsou neodkazové typy a výrazy přetypování, jejichž výsledkem jsou odkazy rvalue na typy bez funkce jako rvalue typy. Ve výchozím nastavení, nebo pokud je zadána **`/Zc:rvalueCast-`** , kompilátor nevyhovuje a zpracovává všechny výrazy přetypování, jejichž výsledkem jsou odkazy rvalue jako rvalue. Pro účely shody a odstranění chyb v používání přetypování doporučujeme použít **`/Zc:rvalueCast`** .

Ve výchozím nastavení je **`/Zc:rvalueCast`** vypnuto ( **`/Zc:rvalueCast-`** ). Možnost kompilátoru [/Permissive-](permissive-standards-conformance.md) implicitně nastaví tuto možnost, ale je možné ji přepsat pomocí **`/Zc:rvalueCast-`** .

Použijte **`/Zc:rvalueCast`** , Pokud předáte výraz přetypování jako argument funkci, která přebírá typ odkazu rvalue. Výchozí chování způsobí chybu kompilátoru [Upozornění C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) , když kompilátor nesprávně určí typ výrazu přetypování. Tento příklad ukazuje chybu kompilátoru ve správném kódu, když není zadána **`/Zc:rvalueCast`** :

```cpp
// Test of /Zc:rvalueCast
// compile by using:
// cl /c /Zc:rvalueCast- make_thing.cpp
// cl /c /Zc:rvalueCast make_thing.cpp

#include <utility>

template <typename T>
struct Thing {
   // Construct a Thing by using two rvalue reference parameters
   Thing(T&& t1, T&& t2)
      : thing1(t1), thing2(t2) {}

   T& thing1;
   T& thing2;
};

// Create a Thing, using move semantics if possible
template <typename T>
Thing<T> make_thing(T&& t1, T&& t2)
{
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));
}

struct Test1 {
   long a;
   long b;

   Thing<long> test() {
      // Use identity casts to create rvalues as arguments
      return make_thing(static_cast<long>(a), static_cast<long>(b));
   }
};
```

Výchozí chování kompilátoru nemusí hlásit chybu C2102, pokud je to vhodné. V tomto příkladu kompilátor nehlásí chybu, pokud je převedená adresa rvalue vytvořená přetypováním identity, když je **`/Zc:rvalueCast`** neurčený:

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

Další informace o problémech s kompatibilitou ve vizuálu C++najdete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránce vlastností **jazyka** **CC++ /**  > .

1. Nastavte vlastnost **Vynutilit pravidla konverze typu** na **`/Zc:rvalueCast`** nebo **`/Zc:rvalueCast-`** . Změny uložte kliknutím na **OK** nebo **použít** .

## <a name="see-also"></a>Viz také

[/Zc (shoda)](zc-conformance.md)
