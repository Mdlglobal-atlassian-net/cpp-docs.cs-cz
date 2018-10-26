---
title: fenv_access | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c06556d47bf0c471aa7e4fab610971e2b7ad11e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081466"
---
# <a name="fenvaccess"></a>fenv_access
Zakáže (**na**) nebo povolí (**vypnout**) příznak optimalizace, které by mohly změnit prostředí s plovoucí desetinnou čárkou, testy a změně režimu.

## <a name="syntax"></a>Syntaxe

> **#pragma fenv_access (** { **na** | **vypnout** } **)**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **fenv_access** je **vypnout**. Pokud kompilátor můžete předpokládat, že váš kód získat přístup nebo manipulaci s plovoucí desetinnou čárkou prostředí a potom ho můžete provádět mnoho optimalizace plovoucí desetinné čárky kód. Nastavte **fenv_access** k **na** k informuje kompilátor, že váš kód přistupuje k s plovoucí desetinnou čárkou prostředí pro testování stavu příznaky, výjimky, nebo nastavení příznaků režim ovládacího prvku. Kompilátor zakáže tyto optimalizace tak, aby váš kód může přistupovat k prostředí s plovoucí desetinnou čárkou konzistentně.

Další informace o chování plovoucí desetinné čárky, naleznete v tématu [/fp (určení chování plovoucí desetinné čárky)](../build/reference/fp-specify-floating-point-behavior.md).

Typy optimalizace, které platí pro ně **fenv_access** jsou:

- Globální eliminace společných dílčích

- Kód pohybu

- Konstantní skládání

Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Příklady

Tento příklad nastaví **fenv_access** k **na** nastavení registru ovládacího prvku s plovoucí desetinnou čárkou 24 bitů přesnosti:

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2
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
out=9.999999776482582e-003
```

Pokud jste zakomentovali `#pragma fenv_access (on)` od předchozího vzorku, mějte na paměti, že výstup se liší, protože kompilátor provádí vyhodnocení za kompilace, která nevyužívá režim ovládacího prvku.

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2
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
out=1.000000000000000e-002
```

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
