---
title: float_control – direktiva pragma
description: Popisuje využití a účinky direktivy pragma float_control. Direktiva float_control řídí stav přesné sémantiky s plovoucí desetinnou čárkou a sémantika výjimky za běhu.
ms.date: 11/18/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 0c9caea5ba35a55a53f7b9340cf9bfd2cce80561
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305509"
---
# <a name="float_control-pragma"></a>float_control – direktiva pragma

Určuje chování plovoucí desetinné čárky pro funkci.

## <a name="syntax"></a>Syntaxe

> **#pragma float_control**\
> **#pragma float_control (přesné,** { **on** | **off** } [ **; push** ] **)** \
> **#pragma float_control (s výjimkou** { **on** | **off** } [ **, push** ] **)** \
> **#pragma float_control (** { **push** | **POP** } **)**

## <a name="options"></a>Možnosti

**přesné**, **on** | **off**, **push**\
Určuje, jestli se má povolit (**zapnuto**) nebo zakázat (**vypnuto**) přesné sémantiky plovoucí desetinné čárky. Informace o tom, jak se tato možnost liší od možnosti podobně pojmenované **/FP: přesný** kompilátor, najdete v části poznámky. Volitelný token **push** instruuje kompilátor, aby vyhrál aktuální nastavení pro **float_control** v interním zásobníku kompilátoru.

**s výjimkou**, **při** | **vypnuto**, **nabízení**\
Určuje, zda se má povolit (**zapnuto**) nebo zakázat (**vypnuto**) sémantika výjimky s plovoucí desetinnou čárkou. Informace o tom, jak se tato možnost liší od podobně pojmenovaného možnosti kompilátoru **/FP: except** , naleznete v části poznámky. Volitelný token **push** instruuje kompilátor, aby vyhrál aktuální nastavení pro **float_control** v interním zásobníku kompilátoru.

**s výjimkou** lze nastavit pouze na hodnotu **zapnuto** , je-li nastavena **přesnost** **na hodnotu on**.

\ **nabízených oznámení**
Posune aktuální **float_control** nastavení do vnitřního zásobníku kompilátoru.

\ **POP**
Odebere nastavení **float_control** v horní části interního zásobníku kompilátoru a vytvoří nové nastavení **float_control** .

## <a name="remarks"></a>Poznámky

**Přesné** a **kromě** možností nemají přesně stejné chování jako možnosti kompilátoru [/FP](../build/reference/fp-specify-floating-point-behavior.md) se stejnými názvy. Direktiva pragma **float_control** se řídí pouze částí chování s plovoucí desetinnou čárkou. Je nutné jej kombinovat s [fp_contract](../preprocessor/fp-contract.md) a [fenv_access](../preprocessor/fenv-access.md) direktivy pragma pro opětovné vytvoření možností kompilátoru **/FP** . Následující tabulka ukazuje ekvivalentní nastavení direktiv pragma pro jednotlivé možnosti kompilátoru:

| | float_control (přesné \*) | float_control (s výjimkou \*) | fp_contract (\*) | fenv_access (\*) |
|-|-|-|-|-|
| /FP: Strict             | na  | na  | vypnuto | na  |
| /FP: Strict/FP: s výjimkou | na  | vypnuto | vypnuto | na  |
| /FP: přesný            | na  | vypnuto | na  | vypnuto |
| /FP: přesný/FP: s výjimkou | na  | na  | na  | vypnuto |
| /FP: Fast               | vypnuto | vypnuto | na  | vypnuto |

Jinými slovy, je nutné použít několik direktiv pragma v kombinaci k emulaci **/FP: Fast**, **/FP:** **Restricted,/FP: Strict**a **/FP: s výjimkou** možností příkazového řádku.

Existují omezení způsobů použití **float_control** a **fenv_access** direktivy pragma s plovoucí desetinnou čárkou v kombinaci:

- **V** případě, že jsou povoleny přesné sémantiky, lze použít pouze **float_control** k nastavení **s výjimkou** na. Pomocí direktivy pragma **float_control** lze povolit přesné sémantiky nebo pomocí možností kompilátoru **/FP:** **Restricted nebo/FP: Strict** .

- Nemůžete použít **float_control** k **zapínání** v případě, že je povolená sémantika výjimky, bez ohledu na možnost kompilátoru **float_control** pragma nebo **/FP: except** .

- **Fenv_access** není možné povolit, pokud není povolená Přesná sémantika, ať už je to **float_control** direktivou pragma nebo parametrem kompilátoru.

- Pokud je povolená **fenv_access** , nemůžete použít **float_control** k jejich **přesnému** vypnutí.

Toto omezení znamená, že pořadí některých direktiv pragma s plovoucí desetinnou čárkou je významné. Chcete-li přejít z rychlého modelu do striktního modelu pomocí **float_control** a souvisejících direktiv pragma, použijte následující kód:

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

Chcete-li přejít z striktního modelu na rychlý model pomocí direktivy pragma **float_control** , použijte následující kód:

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // ensable contractions
```

Pokud nejsou zadány žádné možnosti, **float_control** nemá žádný vliv.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zachytit výjimku pro přetečení plovoucí desetinné čárky pomocí direktivy pragma **float_control**.

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

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[fenv_access](../preprocessor/fenv-access.md)\
[fp_contract](../preprocessor/fp-contract.md)
