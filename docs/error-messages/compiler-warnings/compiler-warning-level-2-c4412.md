---
title: Kompilátor upozornění (úroveň 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 2c9d50fc3433321c0ca92366a512892212545754
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665514"
---
# <a name="compiler-warning-level-2-c4412"></a>Kompilátor upozornění (úroveň 2) C4412

> "*funkce*': podpis funkce obsahuje typ"*typ*'; Jsou objekty C++ není bezpečné předávat mezi čistým kódem a kombinovaným nebo nativním kódem.

## <a name="remarks"></a>Poznámky

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017. Pokud máte kód, který má být čistě, doporučujeme port na C#.

Kompilátor zjistil potenciálně nebezpečné situace, které by mohlo způsobit chybu modulu runtime: přišla z **/CLR: pure** kompilantu funkci, která byla importována pomocí příkazů dllimport a signatura funkce obsahuje nezabezpečený typ . Typ nebezpečné, pokud obsahuje členské funkce nebo má datový člen, který je nezabezpečený typ nebo dereferenci nebezpečné typu.

To nebezpečné kvůli rozdílu ve výchozích konvencí mezi čistě a nativního kódu volání (nebo smíšená nativní a spravovaná). Při importu (prostřednictvím `dllimport`) funkce do **/CLR: pure** kompilace, zajistěte, aby byly stejné jako ty v souboru pro kompilaci, která se exportuje – funkce (dbejte na to hlavně o deklarace každého typu v podpisu rozdíly v implicitní konvence volání).

Virtuální členská funkce je zvlášť náchylné k chybám, poskytne neočekávané výsledky.  Ale i nevirtuální funkce by měl být testován zajistit, že dostanete správné výsledky. Pokud jste si jistí, že se zobrazuje správné výsledky, můžete toto upozornění ignorovat.

C4412 je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) a [dllexport, dllimport](../../cpp/dllexport-dllimport.md) Další informace.

Pokud chcete vyřešit toto upozornění, odeberte všechny funkce z typu.

## <a name="example"></a>Příklad

Následující ukázka generuje C4412.

```cpp
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

Následující příklad je soubor hlaviček, který deklaruje dva typy. `Unsafe` Typ nebezpečné, protože obsahuje členské funkce.

```cpp
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

Tento příklad exportuje funkce s typy definované v souboru hlaviček.

```cpp
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

Výchozí konvenci volání **/CLR: pure** kompilace se liší od nativní kompilace.  Když C4412.h je zahrnuta, `Test` výchozí hodnota je `__clrcall`. Pokud kompilace a spuštění tohoto programu (nepoužívejte **/c**), program vyvolá výjimku.

Následující ukázka generuje C4412.

```cpp
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