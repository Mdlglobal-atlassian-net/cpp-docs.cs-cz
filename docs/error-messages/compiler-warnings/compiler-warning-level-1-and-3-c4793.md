---
title: Upozornění (úroveň 1 a 3) C4793 kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4793
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3942d09e823fc6bd2f370a8c8ee72b8d00e9a98
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704929"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Upozornění kompilátoru (úroveň 1 a 3) C4793

> '*funkce*': funkce kompiluje v nativním kódu: '*důvod*.

## <a name="remarks"></a>Poznámky

Kompilátor nelze kompilovat *funkce* do spravovaného kódu, i když [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) je zadána možnost kompilátoru. Místo toho kompilátor vydá upozornění C4793 a vysvětlující pokračování zprávu a pak zkompiluje *funkce* do nativního kódu. Pokračování zpráva obsahuje *důvod* text, který vysvětluje, proč *funkce* nelze kompilovat, k `MSIL`.

Toto je upozornění úrovně 1 při zadávání **/CLR: pure** – možnost kompilátoru.  **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Následující tabulka uvádí všechny možné pokračování zprávy.

|Důvod zpráv|Poznámky|
|--------------------|-------------|
|Zarovnaný datové typy nejsou podporovány ve spravovaném kódu|Modul CLR musí být schopen přidělit data podle potřeby, která nemusí být možné v případě, že data je zarovnáno s deklaracemi, jako [__m128](../../cpp/m128.md) nebo [zarovnat](../../cpp/align-cpp.md).|
|Funkce, které používají '__ImageBase' nejsou podporovány ve spravovaném kódu|`__ImageBase` je speciální linkeru symbol, který se obvykle používá pouze pomocí nízké úrovně nativní kód pro načtení knihovny DLL.|
|vararg nejsou podporovány ' / clr' – možnost kompilátoru|Nativní funkce nelze volat spravované funkce, které mají [seznam argumentů s proměnnou délkou](../../cpp/functions-with-variable-argument-lists-cpp.md) (vararg) vzhledem k tomu, že funkce mají různé zásobníku rozložení požadavky. Ale pokud zadáte **/CLR: pure** – možnost kompilátoru, seznamy jsou podporována, protože sestavení může obsahovat jenom spravované funkce argumentů proměnných. Další informace najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|
|64bitová verze CLR nepodporuje data deklarovat s __ptr32 – modifikátor|Ukazatel musí mít stejnou velikost jako nativní ukazatel na aktuální platformě. Další informace najdete v tématu [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|32bitová verze CLR nepodporuje data deklarovat s __ptr64 – modifikátor|Ukazatel musí mít stejnou velikost jako nativní ukazatel na aktuální platformě. Další informace najdete v tématu [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|Jeden nebo více vnitřní funkce není podporována ve spravovaném kódu|Název vnitřní není k dispozici v době, kdy jsou vydávány zprávy. Vnitřní, které obvykle způsobí, že tato zpráva však představuje instrukce nízké úrovně počítače.|
|Nativní vloženého sestavení (__asm) není podporována ve spravovaném kódu|[Kód vnořeného sestavení](../../assembler/inline/asm.md) může obsahovat libovolný nativní kód, který se nedá spravovat.|
|Virtuální funkce převodu bez __clrcall musí být zkompilovány jako nativní|Jinou hodnotu než[__clrcall](../../cpp/clrcall.md) virtuální funkce převodu musí používat adresu nespravované.|
|Funkce pomocí '_setjmp' musí být zkompilovány jako nativní|Modul CLR musí být schopné řídit spuštění programu. Ale [setjmp](../../cpp/using-setjmp-longjmp.md) funkce obchází provádění pravidelných programu ukládání a obnovení nízké úrovně informace, jako je stav spuštění a zaregistruje.|

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