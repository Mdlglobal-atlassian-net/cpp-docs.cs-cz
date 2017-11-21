---
title: "Kompilátoru (úroveň 2) upozornění C4412 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4412
dev_langs: C++
helpviewer_keywords: C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2cac6336997ee7ff7a72264ad8449b7d6190255e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-2-c4412"></a>C4412 kompilátoru upozornění (úroveň 2)
'function': podpis funkce obsahuje typu "typ"; Objekty C++ jsou unsafe předat mezi čistý kód a smíšený nebo nativní.  
  
 **/CLR: pure** – možnost kompilátoru je zastaralá ve Visual Studiu 2015.  
  
 Kompilátor zjistil potenciálně nebezpečného situaci, která by mohla vést k chybě běhového prostředí: Probíhá Přišla žádost o z **/CLR: čistý** kompilace funkce, která byla importována pomocí příkazů dllimport a podpis funkce obsahuje typ nezabezpečený . Typ nebezpečné, pokud obsahuje členské funkce nebo má data člena, který je typ nezabezpečený nebo dereference na typ unsafe.  
  
 To nebezpečné kvůli rozdílu ve výchozí mezi čistý a nativní kód konvence volání (nebo ve smíšeném nativní a spravovaná). Při importu (prostřednictvím `dllimport`) funkce do **/CLR: pure** kompilace, zajistěte, aby byly stejné jako v kompilace, který exportuje funkce (dbejte na to hlavně o deklarace každého typu v podpisu rozdíly v implicitní konvence volání).  
  
 Virtuální členské funkce je obzvláště náchylné k neočekávaným výsledkům.  Ale i bez virtuální funkce by měla být testována zajistit, že dostanete správné výsledky. Pokud jste si jistí, že jste správné výsledky, můžete toto upozornění ignorovat.  
  
 Další informace o **/CLR: čistý**, najdete v části [postupy: přechod na/CLR: pure (C + +/ rozhraní příkazového řádku)](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md).  
  
 C4412 je ve výchozím nastavení vypnuté. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) a [dllexport, dllimport](../../cpp/dllexport-dllimport.md) Další informace.  
  
 Toto upozornění vyřešit, odeberte všechny funkce z typu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4412.  
  
```  
// C4412.cpp  
// compile with: /c /W2 /clr:pure  
#pragma warning (default : 4412)  
  
struct Unsafe {  
   virtual void __cdecl Test();  
};  
  
struct Safe {  
   int i;  
};  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   Unsafe *pUnsafe = func();   // C4412  
   // pUnsafe->Test();  
  
   Safe *pSafe = func2();   // OK  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad je soubor hlaviček, který deklaruje dva typy. `Unsafe` Typ není bezpečné, protože obsahuje členské funkce.  
  
```  
// C4412.h  
struct Unsafe {  
   // will be __clrcall if #included in pure compilation  
   // defaults to __cdecl in native or mixed mode compilation  
   virtual void Test(int * pi);  
  
   // try the following line instead  
   // virtual void __cdecl Test(int * pi);  
};  
  
struct Safe {  
   int i;  
};  
```  
  
## <a name="example"></a>Příklad  
 Tato ukázka exportuje funkce s typy definované v záhlaví souboru.  
  
```  
// C4412_2.cpp  
// compile with: /LD  
#include "C4412.h"  
  
void Unsafe::Test(int * pi) {  
   *pi++;  
}  
  
__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }  
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }  
```  
  
## <a name="example"></a>Příklad  
 Výchozí konvencí volání **/CLR: pure** kompilace se liší od nativní kompilace.  Pokud je C4412.h zahrnuta, `Test` výchozí `__clrcall`. Pokud zkompilování a spuštění tohoto programu (nepoužívejte **/c**), programu vyvolá výjimku.  
  
 Následující ukázka generuje C4412.  
  
```  
// C4412_3.cpp  
// compile with: /W2 /clr:pure /c /link C4412_2.lib  
#pragma warning (default : 4412)  
#include "C4412.h"  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   int n = 7;  
   Unsafe *pUnsafe = func();   // C4412  
   pUnsafe->Test(&n);  
  
   Safe *pSafe = func2();   // OK  
}  
```