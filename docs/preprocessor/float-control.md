---
title: float_control
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 8a7829252cebb726363c67c990a94d08b0d6467a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389213"
---
# <a name="floatcontrol"></a>float_control

Určuje chování plovoucí desetinné čárky pro funkci.

## <a name="syntax"></a>Syntaxe

> **#pragma float_control** [ **(** [ *hodnotu* **,** *nastavení* [ **, push** ]] | [ **nabízených** | **pop** ] **)** ]

## <a name="options"></a>Možnosti

*Hodnota*, *nastavení* [, **nabízených**]<br/>
Určuje chování plovoucí desetinné čárky. *Hodnota* může být **přesné**, **striktní**, nebo **s výjimkou**. Další informace najdete v tématu [/fp (určení chování plovoucí desetinné čárky)](../build/reference/fp-specify-floating-point-behavior.md). *Nastavení* může být buď **na** nebo **vypnout**.

Pokud *hodnotu* je **striktní**, nastavení pro obě **striktní** a **s výjimkou** jsou určeny *nastavení* . **s výjimkou** lze nastavit pouze **na** při **přesné** nebo **striktní** je také nastavena na **na**.

Pokud volitelný **nabízených** token se přidá, aktuální nastavení pro *hodnotu* je vloženo do zásobníku vnitřního kompilátoru.

**push**<br/>
Nabízená aktuální **float_control** nastavení do vnitřního zásobníku kompilátoru

**pop**<br/>
Odebere **float_control** nastavení z vrcholu vnitřního zásobníku kompilátoru a, která umožňuje novou **float_control** nastavení.

## <a name="remarks"></a>Poznámky

Nemůžete použít **float_control** Chcete-li **přesné** vypnuté, kdy **s výjimkou** zapnutý. Obdobně **přesné** nelze vypnout, kdy [fenv_access](../preprocessor/fenv-access.md) zapnutý. Přejít od striktní modelu k rychlé modelu s použitím **float_control** – Direktiva pragma, použijte následující kód:

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

Přejít od modelu rychlé striktní modelu s **float_control** – Direktiva pragma, použijte následující kód:

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

Pokud nejsou zadány žádné parametry, **float_control** nemá žádný vliv.

Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zachytit výjimku přetečení s plovoucí desetinnou čárkou pomocí direktivy pragma **float_control**.

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
