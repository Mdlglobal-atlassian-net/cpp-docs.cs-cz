---
title: fenv_access – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: c8e66881bde12df28bf24e18230471cb4caca792
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218604"
---
# <a name="fenv_access-pragma"></a>fenv_access – direktiva pragma

Zakáže (**zapnuto**) nebo povolí (**vypnuto**) optimalizace, které by mohly změnit testy příznaků prostředí s plovoucí desetinnou čárkou a změny v režimu.

## <a name="syntax"></a>Syntaxe

> **#pragma fenv_access (** { **on** | **off** } **)**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je fenv_access **vypnutý**. Pokud kompilátor může předpokládat, že váš kód nepřistupuje k prostředí s plovoucí desetinnou čárkou nebo s ním nepracuje, může provést mnoho optimalizace kódu s plovoucí desetinnou čárkou. Nastavte **fenv_access** na **on** pro informování kompilátoru, že váš kód přistupuje k prostředí s plovoucí desetinnou čárkou pro testování příznaků stavu, výjimek nebo nastavení příznaků režimu ovládacího prvku. Kompilátor tyto optimalizace zakáže, aby váš kód mohl konzistentně přistupovat k prostředí s plovoucí desetinnou čárkou.

Další informace o chování plovoucí desetinné čárky naleznete v tématu [/FP (určení chování s plovoucí](../build/reference/fp-specify-floating-point-behavior.md)desetinnou čárkou).

Typy optimalizací, které jsou předmětem **fenv_access** :

- Eliminace globálních běžných dílčích výrazů

- Pohyb kódu

- Konstantní skládání

Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Příklady

Tento příklad nastaví **fenv_access** na **on** pro nastavení registračního registru ovládacího prvku s plovoucí desetinnou čárkou na 24-bitovou přesnost:

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2 /arch:IA32
// processor: x86
#include <stdio.h>
#include <float.h>
#include <errno.h>
#pragma fenv_access (on)

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=9.999999776482582e-03
```

Pokud zadáte komentář `#pragma fenv_access (on)` z předchozí ukázky, Všimněte si, že výstup je jiný, protože kompilátor provádí vyhodnocení v době kompilace, které nepoužívá režim řízení.

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2 /arch:IA32
#include <stdio.h>
#include <float.h>

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=1.000000000000000e-02
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
