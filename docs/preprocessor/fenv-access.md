---
title: fenv_access – direktiva pragma
description: Popisuje využití a účinky direktivy pragma fenv_access. Direktiva fenv_access řídí přístup k prostředí s plovoucí desetinnou čárkou za běhu.
ms.date: 11/19/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: e03eb404f2805a4f7c96509600c063c1b1acf629
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305846"
---
# <a name="fenv_access-pragma"></a>fenv_access – direktiva pragma

Zakáže (**zapnuto**) nebo povolí (**vypnuto**) optimalizace, které by mohly změnit testy příznaků prostředí s plovoucí desetinnou čárkou a změny v režimu.

## <a name="syntax"></a>Syntaxe

> **#pragma fenv_access (** { **on** | **off** } **)**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je fenv_access **vypnuto**. Kompilátor předpokládá, že váš kód nepřistupuje k prostředí s plovoucí desetinnou čárkou nebo s ním nepracuje. Pokud není přístup k prostředí vyžadován, může kompilátor provádět více pro optimalizaci kódu s plovoucí desetinnou čárkou.

Povolte **fenv_access** , pokud váš kód testuje příznaky stavu s plovoucí desetinnou čárkou, výjimky nebo příznaky režimu ovládacího prvku sady. Kompilátor zakáže optimalizace s plovoucí desetinnou čárkou, takže váš kód může konzistentně přistupovat k prostředí s plovoucí desetinnou čárkou.

Možnost příkazového řádku [/FP: Strict] automaticky povolí **fenv_access**. Další informace o tomto a dalším chování plovoucí desetinné čárky najdete v tématu [/FP (určení chování s plovoucí](../build/reference/fp-specify-floating-point-behavior.md)desetinnou čárkou).

Existují omezení způsobů, jak můžete použít direktivu pragma **fenv_access** v kombinaci s dalšími nastaveními s plovoucí desetinnou čárkou:

- Nemůžete povolit **fenv_access** , pokud není povolená Přesná sémantika. Pomocí direktivy pragma [float_control](float-control.md) lze povolit přesné sémantiky nebo pomocí možností kompilátoru [/FP:](../build/reference/fp-specify-floating-point-behavior.md) [Restricted nebo/FP: Strict](../build/reference/fp-specify-floating-point-behavior.md) . Kompilátor je standardně **/FP: přesné** , pokud není zadána jiná možnost příkazového řádku s plovoucí desetinnou čárkou.

- Pokud je nastavená **fenv_access (zapnuto)** , nemůžete použít **float_control** k zakázání přesné sémantiky.

Typy optimalizací, které jsou předmětem **fenv_access** :

- Eliminace globálních běžných dílčích výrazů

- Pohyb kódu

- Konstantní skládání

Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Příklady

Tento příklad nastaví **fenv_access** na **on** pro nastavení registračního registru ovládacího prvku s plovoucí desetinnou čárkou na 24bitové přesnosti:

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

Pokud Odkomentujete `#pragma fenv_access (on)` z předchozí ukázky, výstup se liší. Je to proto, že kompilátor provádí vyhodnocení v době kompilace, což nepoužívá režim řízení.

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
