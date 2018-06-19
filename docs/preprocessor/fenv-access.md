---
title: fenv_access – | Microsoft Docs
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
ms.openlocfilehash: f74f20b1dcb20c1449d21e91181f8bfb17075b7e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912963"
---
# <a name="fenvaccess"></a>fenv_access

Zakáže (**na**) nebo umožňuje (**vypnout*) optimalizace, které by se mohly změnit s plovoucí desetinnou čárkou prostředí příznak testy a změny v režimu.

## <a name="syntax"></a>Syntaxe

> **fenv_access – #pragma (** { **na** | **vypnout** } **)**  

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **fenv_access –** je **vypnout**. Pokud kompilátor můžete předpokládat, že váš kód přístup nebo manipulaci s plovoucí desetinnou čárkou prostředí a potom ji můžete provádět mnoho optimalizace kódu s plovoucí desetinnou čárkou. Nastavit **fenv_access –** k **na** k informování kompilátor váš kód přistupuje k s plovoucí desetinnou čárkou prostředí pro testování příznaky stavu, výjimky, nebo o nastavení ovládacího prvku příznaky režimu. Kompilátor zakáže tyto optimalizace, aby váš kód konzistentní přístup s plovoucí desetinnou čárkou prostředí. 

Další informace o s plovoucí desetinnou čárkou chování najdete v tématu [/fp (zadejte Floating-Point chování)](../build/reference/fp-specify-floating-point-behavior.md).

Druhy optimalizace, které podléhají **fenv_access –** jsou:

- Globální eliminace společných dílčích výrazů

- Kód pohybu

- Konstantní skládání

Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Příklady

Tento příklad nastaví **fenv_access –** k **na** nastavit s plovoucí desetinnou čárkou řízení registrace pro 24bitový přesnost:

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

Pokud jste komentář `#pragma fenv_access (on)` od předchozího vzorku, Všimněte si, že výstup různých kvůli kompilátor vyhodnocení kompilaci, který nepoužívá režim ovládacího prvku.

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

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
