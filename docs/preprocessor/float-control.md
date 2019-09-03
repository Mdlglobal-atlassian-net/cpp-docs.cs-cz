---
title: float_control – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: aa8cdc07953405175c1753791ab53214d73ba516
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218576"
---
# <a name="float_control-pragma"></a>float_control – direktiva pragma

Určuje chování plovoucí desetinné čárky pro funkci.

## <a name="syntax"></a>Syntaxe

> **#pragma float_control**\
> **#pragma float_control (** { **přesný** | **Strict** | **Except** } **;** { **on** | **off** } [ **; push** ] **)** \
> **#pragma float_control (** { **push** | **POP** } **)**

## <a name="options"></a>Možnosti

 | přesné, s výjimkou, při vypnutí, nabízení |  | \
Určuje chování s plovoucí desetinnou čárkou, které může být **přesné**, **striktní**nebo **s výjimkou**. Další informace najdete v tématu [/FP (určení chování s plovoucí](../build/reference/fp-specify-floating-point-behavior.md)desetinnou čárkou). Nastavení lze buď **zapnout** , nebo **vypnout**.

Pokud je to **striktní**, nastavení pro **Strict** i **s výjimkou** jsou určena nastavením **zapnuto** nebo **vypnuto** . **s výjimkou** lze nastavit pouze hodnotu **on** , pokud je nastavena možnost **přesné** nebo **striktní** , na hodnotu **on**.

Pokud je přidán volitelný token **push** , aktuální nastavení pro **float_control** je vloženo do vnitřního zásobníku kompilátoru.

**replik**\
Vložení aktuálního nastavení **float_control** do interního zásobníku kompilátoru

**výstrah**\
Odebere nastavení **float_control** z vrcholu vnitřního zásobníku kompilátoru a vytvoří nové nastavení **float_control** .

## <a name="remarks"></a>Poznámky

**Float_control** nelze použít pro **přesné** vypnutí, pokud je to v případě, že je zapnuto. Podobně, **přesný** , nelze vypnout, pokud je zapnutá funkce [fenv_access](../preprocessor/fenv-access.md) . Chcete-li přejít z striktního modelu na rychlý model pomocí direktivy pragma **float_control** , použijte následující kód:

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

Chcete-li přejít z rychlého modelu do striktního modelu pomocí direktivy pragma **float_control** , použijte následující kód:

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

Pokud nejsou zadány žádné možnosti, **float_control** nemá žádný vliv.

Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zachytit výjimku při přetečení plovoucí desetinné čárky pomocí direktivy pragma **float_control**.

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

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
