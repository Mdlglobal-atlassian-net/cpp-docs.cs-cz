---
title: /Zc:rvalueCast (Vynucení pravidel převodu typů)
ms.date: 03/06/2018
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
ms.openlocfilehash: e5a6abd3b85136b05ae58ebc8750aa9120cabc33
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810429"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Vynucení pravidel převodu typů)

Když **/Zc: rvaluecast** je zadána možnost, kompilátor správně identifikuje referenční typ rvalue jako výsledku operace přetypování v souladu s standardu C ++ 11. Pokud není zadán parametr, chování kompilátoru je stejné jako v sadě Visual Studio 2012.

## <a name="syntax"></a>Syntaxe

> **/Zc:rvalueCast**[**-**]

## <a name="remarks"></a>Poznámky

Pokud **/Zc: rvaluecast** není zadán, kompilátor následuje oddíl 5.4 standardu C ++ 11 a zpracuje pouze výrazy přetypování, které vedou mimo referenční typy a výrazy přetypování, jejichž výsledkem jsou odkazy na typy funkcí jiné než jako typy r-hodnoty. Ve výchozím nastavení nebo pokud **/Zc:rvalueCast-** není zadán, kompilátor nesplňuje podmínky shody a zpracovává všechny výrazy cast, jejichž výsledkem odkazy rvalue jako rvalues. Pro přizpůsobení a odstranění chyb v užívání přetypování, doporučujeme použít **/Zc: rvaluecast**.

Ve výchozím nastavení **/Zc: rvaluecast** je vypnuto (**/Zc:rvalueCast-**). [/ Permissive-](permissive-standards-conformance.md) – možnost kompilátoru implicitně nastaví tuto možnost, ale lze přepsat pomocí **/Zc:rvalueCast-**.

Použití **/Zc: rvaluecast** Pokud předáte výraz přetypování jako argument funkci, která přebírá typ odkazu rvalue. Výchozí chování způsobí chybu kompilátoru [upozornění C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) Pokud kompilátor nesprávně určí typ výrazu přetypování. Tento příklad ukazuje chybu kompilátoru ve správném kódu, kdy **/Zc: rvaluecast** nezadáte:

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

Výchozí chování kompilátoru nemusí hlásit chybu C2102. V tomto příkladu kompilátor nehlásí chybu Pokud adresa rvalue vytvořená pomocí přetypování identita se používá při **/Zc: rvaluecast** nezadáte:

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc: rvaluecast** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)<br/>
