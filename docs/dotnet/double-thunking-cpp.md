---
title: Dvojitý převod adres na jinou bitovou šířku (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
ms.openlocfilehash: 89cca9ef42910d295cbae8bb677fb51927dbcdd2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988534"
---
# <a name="double-thunking-c"></a>Dvojitý převod adres na jinou bitovou šířku (C++)

Dvojitá dvojitýa odkazuje na ztrátu výkonu, ke kterému může dojít, když volání funkce ve spravovaném kontextu volá C++ vizuální spravovanou funkci a kde spuštění programu zavolá nativní vstupní bod funkce, aby mohl volat spravovanou funkci. Toto téma popisuje, kde dochází k dvojitý a jak se můžete vyhnout jeho zvýšení výkonu.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení, při kompilaci s možností **/CLR**, definice spravované funkce způsobí, že kompilátor vygeneruje spravovaný vstupní bod a nativní vstupní bod. To umožňuje, aby se spravovaná funkce volala z nativních a spravovaných webů volání. Pokud však existuje nativní vstupní bod, může být vstupním bodem pro všechna volání funkce. Pokud je volající funkce spravována, nativní vstupní bod pak bude volat spravovaný vstupní bod. V důsledku toho se ke vyvolání funkce vyžadují dvě volání (tedy Double dvojitý). Například virtuální funkce jsou vždy volány prostřednictvím nativního vstupního bodu.

Jedním z řešení je oznámit kompilátoru, aby negeneroval nativní vstupní bod pro spravovanou funkci, že funkce bude volána pouze ze spravovaného kontextu pomocí [__clrcall](../cpp/clrcall.md) konvence volání.

Podobně pokud exportujete ([dllexport, dllimport](../cpp/dllexport-dllimport.md)) spravovanou funkci, je vygenerován nativní vstupní bod a jakákoli funkce, která importuje a volá tuto funkci, bude volat prostřednictvím nativního vstupního bodu. Abyste se vyhnuli dvojnásobné dvojitý v této situaci, nepoužívejte nativní sémantiku exportu/importu; jednoduše odkazujte metadata prostřednictvím `#using` (viz [direktiva #using](../preprocessor/hash-using-directive-cpp.md)).

Kompilátor byl aktualizován, aby snižoval zbytečný dvojitý. Například jakákoli funkce se spravovaným typem v podpisu (včetně návratového typu) bude implicitně označena jako `__clrcall`.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje dvojitou dvojitý. Při kompilování nativní (bez **/CLR**) volání virtuální funkce v `main` generuje jedno volání kopírovacího konstruktoru `T`a jedno volání destruktoru. Podobné chování je dosaženo při deklaraci virtuální funkce s možností **/CLR** a `__clrcall`. Pokud je však pouze zkompilována s možností **/CLR**, volání funkce vygeneruje volání kopírovacího konstruktoru, ale existuje jiné volání kopírovacího konstruktoru z důvodu nativního převodu z nativního na spravovaného kódu.

### <a name="code"></a>Kód

```cpp
// double_thunking.cpp
// compile with: /clr
#include <stdio.h>
struct T {
   T() {
      puts(__FUNCSIG__);
   }

   T(const T&) {
      puts(__FUNCSIG__);
   }

   ~T() {
      puts(__FUNCSIG__);
   }

   T& operator=(const T&) {
      puts(__FUNCSIG__);
      return *this;
   }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;

   printf("calling struct S\n");
   pS->f(t);
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Vzorový výstup

```
__thiscall T::T(void)
calling struct S
__thiscall T::T(const struct T &)
__thiscall T::T(const struct T &)
__thiscall T::~T(void)
__thiscall T::~T(void)
after calling struct S
__thiscall T::~T(void)
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Předchozí ukázka ukázala existenci dvojité dvojitý. Tato ukázka ukazuje svůj efekt. Smyčka `for` volá virtuální funkci a program oznamuje dobu spuštění. Nejpomalejší čas je hlášena při kompilování programu s možností **/CLR**. Nejrychlejší časy jsou hlášeny při kompilaci bez **/CLR** nebo pokud je virtuální funkce deklarována s `__clrcall`.

### <a name="code"></a>Kód

```cpp
// double_thunking_2.cpp
// compile with: /clr
#include <time.h>
#include <stdio.h>

#pragma unmanaged
struct T {
   T() {}
   T(const T&) {}
   ~T() {}
   T& operator=(const T&) { return *this; }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;
   clock_t start, finish;
   double  duration;
   start = clock();

   for ( int i = 0 ; i < 1000000 ; i++ )
      pS->f(t);

   finish = clock();
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);
   printf( "%2.1f seconds\n", duration );
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Vzorový výstup

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>Viz také:

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
