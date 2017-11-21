---
title: "-Zc: rvalueCast (vynucení pravidel převodu typů) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 068d1e0e9061645729728c4d0a3c956e521948cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Vynucení pravidel převodu typů)
Když **/Zc: rvaluecast** je zadána možnost, kompilátor správně identifikuje typ deklarátor odkazu jako výsledek operace cast v souladu s C ++ 11 standardní. Pokud není zadána možnost, kompilátoru chování je stejné jako v sadě Visual Studio 2012. Ve výchozím nastavení **/Zc: rvaluecast** je vypnutý. Shoda a k odstranění chyb s použitím přetypování, doporučujeme použít **/Zc: rvaluecast**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Zc:rvalueCast[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud **/Zc: rvaluecast** je zadán, kompilátor postupuje podle části 5.4 C ++ 11 standardní a vyhodnotí pouze přetypování výrazů, které za následek bez odkazové typy a přetypovat výrazy, jejichž výsledkem rvalue odkazy na typy jiné funkce jako typy rvalue. Ve výchozím nastavení nebo pokud **/Zc:rvalueCast-** je zadán, kompilátor je jiný vyhovující a zpracovává všechny výrazy přetypování, jejichž výsledkem odkazy rvalue jako rvalue.  
  
 Použití **/Zc: rvaluecast** Pokud předáte výraz přetypování jako argument funkce, která přebírá typ deklarátor odkazu. Výchozí chování způsobí, že chyba kompilátoru [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) při kompilátor nesprávně určuje typ výraz cast. Tento příklad ukazuje Chyba kompilátoru v správný kód, pokud není zadán/Zc: rvaluecast:  
  
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
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc: rvaluecast** a potom zvolte **OK**.  
  
## <a name="see-also"></a>Viz také  
 [/Zc (shoda)](../../build/reference/zc-conformance.md)