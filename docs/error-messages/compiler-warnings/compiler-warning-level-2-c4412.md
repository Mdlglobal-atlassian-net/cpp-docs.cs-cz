---
title: Upozornění kompilátoru (úroveň 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 601b99eec4625e9b598ece4cbb74d0039ad04bf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161786"
---
# <a name="compiler-warning-level-2-c4412"></a>Upozornění kompilátoru (úroveň 2) C4412

> '*Function*': signatura funkce obsahuje typ '*Type*'; C++ objekty nejsou bezpečné předávat mezi čistým a smíšeným nebo nativním kódem.

## <a name="remarks"></a>Poznámky

Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017. Pokud máte kód, který musí být čistý, doporučujeme vám ho přenést na C#.

Kompilátor zjistil potenciálně nebezpečnou situaci, která by mohla způsobit chybu za běhu: volání z **/clr: Pure** kompilantu do funkce, která byla importována prostřednictvím dllimport a signatura funkce obsahuje nezabezpečený typ. Typ je nebezpečný, pokud obsahuje členskou funkci nebo má datový člen, který je nebezpečného typu nebo nepřímý odkaz na nezabezpečený typ.

To je nebezpečné kvůli rozdílu ve výchozích konvencích volání mezi čistým a nativním kódem (nebo smíšeným nativním a spravovaným). Při importu (prostřednictvím `dllimport`) funkce do **/clr: Pure** kompilantu zajistěte, aby deklarace každého typu v podpisu byly stejné jako v kompilantu, které tuto funkci vyexportují (obzvláště opatrní na rozdíly v implicitních konvencích volání).

Virtuální členská funkce je obzvláště náchylná k poskytnutí neočekávaných výsledků.  I nevirtuální funkce by však měly být testovány, aby bylo zajištěno, že získáte správné výsledky. Pokud jste si jisti, že se vám zobrazí správné výsledky, můžete toto upozornění ignorovat.

C4412 je ve výchozím nastavení vypnutá. Další informace naleznete v tématu [Upozornění kompilátoru, která jsou vypnuta ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) a [dllexport, dllimport](../../cpp/dllexport-dllimport.md) .

Chcete-li vyřešit toto upozornění, odeberte všechny funkce z typu.

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

Následující ukázka je hlavičkový soubor, který deklaruje dva typy. Typ `Unsafe` je nebezpečný, protože má členskou funkci.

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

Tato ukázka exportuje funkce s typy definovanými v hlavičkovém souboru.

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

Výchozí konvence volání v kompilaci **/clr: Pure** se liší od nativní kompilace.  Pokud je součástí C4412. h, `Test` výchozí nastavení `__clrcall`. Pokud tento program zkompilujete a spustíte (nepoužíváte **/c**), program vyvolá výjimku.

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
