---
title: Upozornění kompilátoru (úroveň 1 a 3) C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: e7ca3b10e09b0d6818fbc7f5607ebc9c95c7f15c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280539"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Upozornění kompilátoru (úroveň 1 a 3) C4793

> "*funkce*': funkce se zkompilovat jako nativní kód:"*důvod*"

## <a name="remarks"></a>Poznámky

Kompilátor nemůže kompilovat *funkce* do spravovaného kódu, i když [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) je zadána možnost kompilátoru. Místo toho kompilátor vydá upozornění C4793 a vysvětlující pokračování zprávu a pak zkompiluje *funkce* do nativního kódu. Pokračování zpráva obsahuje *důvod* text, který vysvětluje, proč *funkce* nemohou být zkompilovány do `MSIL`.

Toto je upozornění úrovně 1 při zadávání **/CLR: pure** – možnost kompilátoru.  **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

V následující tabulce jsou uvedeny všechny možné pokračování zprávy.

|Důvod zprávy|Poznámky|
|--------------------|-------------|
|Zarovnané datové typy nejsou ve spravovaném kódu podporované.|Modul CLR musí být schopen přidělení dat podle potřeby, což nemusí být možné dat je v souladu s deklaracemi, jako v případě [__m128](../../cpp/m128.md) nebo [zarovnat](../../cpp/align-cpp.md).|
|Funkce, které používají ": __ImageBase" nejsou ve spravovaném kódu podporované.|`__ImageBase` je speciální linkeru symbol, který je obvykle používána pouze nízké úrovně nativní kód pro načtení knihovny DLL.|
|Funkce VarArgs nejsou podporovány "/ clr' – možnost kompilátoru|Nativní funkce nelze volat spravované funkce, které mají [seznamy argumentů proměnných](../../cpp/functions-with-variable-argument-lists-cpp.md) (vararg) vzhledem k tomu, že nemají tyto funkce požadavkům na rozložení jiný zásobník. Ale pokud zadáte **/CLR: pure** – možnost kompilátoru, seznamy jsou podporované, protože sestavení může obsahovat jenom spravované funkce argumentů s proměnnou délkou. Další informace najdete v tématu [prázdná a ověřitelný kód (C++vyhodnocovací)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|
|64bitový modul CLR nepodporuje data deklarovaný s modifikátorem __ptr32|Ukazatel musí mít stejnou velikost jako nativní ukazatel na aktuální platformě. Další informace najdete v tématu [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|32bitová verze CLR nepodporuje data deklarovaný s modifikátorem __ptr64|Ukazatel musí mít stejnou velikost jako nativní ukazatel na aktuální platformě. Další informace najdete v tématu [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|Jeden nebo více vnitřních objektů není ve spravovaném kódu podporované.|Název vnitřní objekt není k dispozici v době, kdy je vygenerován zprávy. Vnitřní objekt, který způsobí, že tato zpráva obvykle však představuje nízké úrovně počítače instrukce.|
|Vložené nativní sestavení (__asm) není ve spravovaném kódu podporované.|[Vložený kód sestavení](../../assembler/inline/asm.md) může obsahovat libovolný nativní kód, který není možné spravovat.|
|Převodní rutina virtuální funkci bez __clrcall musí kompilovat jako nativní.|Non -[__clrcall](../../cpp/clrcall.md) virtuální funkce převodní rutina musí používat adresu nespravované.|
|Funkce pomocí "_setjmp" musí kompilovat jako nativní.|Modul CLR musí být schopni řídit vykonávání programu. Ale [setjmp](../../cpp/using-setjmp-longjmp.md) funkce obchází provádění pravidelných programu pomocí ukládání a obnova nízké úrovně informace, jako je registry a stav provádění.|

## <a name="example"></a>Příklad

Následující ukázka generuje C4793.

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

Následující ukázka generuje C4793.

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```