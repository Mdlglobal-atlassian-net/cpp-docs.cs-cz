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
ms.openlocfilehash: de6f514d8e3ad8e7715c9cd13a695e3398fffc8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164804"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Upozornění kompilátoru (úroveň 1 a 3) C4793

> '*Function*': funkce je kompilována jako nativní kód: '*důvod*'

## <a name="remarks"></a>Poznámky

Kompilátor nemůže kompilovat *funkci* do spravovaného kódu, a to i v případě, že je zadána možnost kompilátoru [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) . Místo toho kompilátor vygeneruje upozornění C4793 a vysvětlující zprávu o pokračování a potom zkompiluje *funkci* do nativního kódu. Zpráva o pokračování obsahuje text *důvodu* , který vysvětluje, proč nelze *funkci* zkompilovat do `MSIL`.

Toto je upozornění úrovně 1 při zadání možnosti **/clr: Pure** Compiler.  Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

V následující tabulce jsou uvedeny všechny možné zprávy o pokračování.

|Zpráva důvodu|Poznámky|
|--------------------|-------------|
|Zarovnané datové typy nejsou ve spravovaném kódu podporované.|CLR musí být schopný přidělit data podle potřeby, což může být možné, pokud jsou data zarovnána s deklaracemi, jako je například [__m128](../../cpp/m128.md) nebo [align](../../cpp/align-cpp.md).|
|Funkce, které používají __ImageBase, nejsou ve spravovaném kódu podporované.|`__ImageBase` je speciální symbol linkeru, který se obvykle používá pouze nativním kódem nízké úrovně k načtení knihovny DLL.|
|možnost kompilátoru/CLR nepodporuje VarArgs.|Nativní funkce nemohou volat spravované funkce, které mají [seznamy argumentů proměnných](../../cpp/functions-with-variable-argument-lists-cpp.md) (varargs), protože tyto funkce mají jiné požadavky na rozložení zásobníku. Pokud však zadáte možnost kompilátoru **/clr: Pure** , seznamy argumentů proměnných jsou podporovány, protože sestavení může obsahovat pouze spravované funkce. Další informace najdete v tématu [čistý a ověřitelný kódC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|
|64-bit CLR nepodporuje data deklarovaná pomocí modifikátoru __ptr32.|Ukazatel musí mít stejnou velikost jako nativní ukazatel na aktuální platformě. Další informace najdete v tématu [__ptr32 \__ptr64](../../cpp/ptr32-ptr64.md).|
|32-bit CLR nepodporuje data deklarovaná pomocí modifikátoru __ptr64.|Ukazatel musí mít stejnou velikost jako nativní ukazatel na aktuální platformě. Další informace najdete v tématu [__ptr32 \__ptr64](../../cpp/ptr32-ptr64.md).|
|Jeden nebo více vnitřních objektů není ve spravovaném kódu podporováno.|Název vnitřní není v okamžiku generování zprávy k dispozici. Vnitřní objekt, který způsobí, že tato zpráva obvykle představuje instrukci počítače nízké úrovně.|
|Vložené nativní sestavení (__asm) není ve spravovaném kódu podporované.|[Kód vloženého sestavení](../../assembler/inline/asm.md) může obsahovat libovolný nativní kód, který nelze spravovat.|
|Virtuální funkce, která není __clrcall, musí být zkompilována jako nativní.|Virtuální funkce, která není[__clrcall](../../cpp/clrcall.md) , musí používat nespravovanou adresu.|
|Funkce používající _setjmp musí být kompilována jako nativní.|Modul CLR musí být schopný řídit provádění programu. Funkce [setjmp](../../cpp/using-setjmp-longjmp.md) však obchází běžné spuštění programu uložením a obnovením informací nízké úrovně, jako jsou například registry a stav provádění.|

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
