---
title: '/ Zc: rvaluecast (vynucení pravidel převodu typů) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d730563d01a3b59d4f2ac6bbadc980ca51112203
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Vynucení pravidel převodu typů)

Když **/Zc: rvaluecast** je zadána možnost, kompilátor správně identifikuje typ deklarátor odkazu jako výsledek operace cast v souladu s C ++ 11 standardní. Pokud není zadána možnost, kompilátoru chování je stejné jako v sadě Visual Studio 2012.

## <a name="syntax"></a>Syntaxe

> **/Zc:rvalueCast**[**-**]

## <a name="remarks"></a>Poznámky

Pokud **/Zc: rvaluecast** je zadán, kompilátor postupuje podle části 5.4 C ++ 11 standardní a vyhodnotí pouze přetypování výrazů, které za následek bez odkazové typy a přetypovat výrazy, jejichž výsledkem rvalue odkazy na typy jiné funkce jako typy rvalue. Ve výchozím nastavení nebo pokud **/Zc:rvalueCast-** je zadán, kompilátor je jiný vyhovující a zpracovává všechny výrazy přetypování, jejichž výsledkem odkazy rvalue jako rvalue. Shoda a k odstranění chyb s použitím přetypování, doporučujeme použít **/Zc: rvaluecast**.

Ve výchozím nastavení **/Zc: rvaluecast** je vypnutý (**/Zc:rvalueCast-**). [/ Projektovou-](permissive-standards-conformance.md) – možnost kompilátoru implicitně nastaví tato možnost, ale můžete přepsat pomocí **/Zc:rvalueCast-**.

Použití **/Zc: rvaluecast** Pokud předáte výraz přetypování jako argument funkce, která přebírá typ deklarátor odkazu. Výchozí chování způsobí, že chyba kompilátoru [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) při kompilátor nesprávně určuje typ výraz cast. Tento příklad ukazuje Chyba kompilátoru v správný kód při **/Zc: rvaluecast** není zadán:

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

Výchozí chování kompilátoru nemusí ohlaste chybu C2102 v případě nutnosti. V tomto příkladu kompilátor nenahlásí chybu Pokud nedojde k adresu rvalue vytvořené identity přetypovat při **/Zc: rvaluecast** není zadán:

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue 
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc: rvaluecast** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
