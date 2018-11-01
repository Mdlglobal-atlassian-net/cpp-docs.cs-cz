---
title: fp_contract
ms.date: 03/12/2018
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: 14c3ac60d4fc0f45fcf0ece6c3f73153e5de4271
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476502"
---
# <a name="fpcontract"></a>fp_contract

Určuje, zda provede s plovoucí desetinnou čárkou zkracování. S plovoucí desetinnou čárkou zkracování je instrukce, jako je například FMA (taveného-vynásobit-přidat), který kombinuje dvě samostatné operace s plovoucí desetinnou do jediná instrukce. Použijte tyto pokyny může ovlivnit přesnost s plovoucí desetinnou čárkou, protože namísto zaokrouhlení po každé operaci, může pouze jednou zaokrouhlit procesoru po operace.

## <a name="syntax"></a>Syntaxe

> **#pragma fp_contract (** { **na** | **vypnout** } **)**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **fp_contract** je **na**. Říká kompilátoru, aby použil pokyny s plovoucí desetinnou čárkou zmenšení, kde je to možné. Nastavte **fp_contract** k **vypnout** zachovat jednotlivých instrukcí s plovoucí desetinnou čárkou.

Další informace o chování plovoucí desetinné čárky, naleznete v tématu [/fp (určení chování plovoucí desetinné čárky)](../build/reference/fp-specify-floating-point-behavior.md).

Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Příklad

Kód generovaný z tohoto příkladu nepoužívá instrukci sloučeného vícenásobného sčítání, i když je k dispozici na cílový procesor. Pokud jste zakomentovali `#pragma fp_contract (off)`, generovaný kód může použít instrukci sloučeného vícenásobného sčítání, pokud je k dispozici.

```cpp
// pragma_directive_fp_contract.cpp
// on x86 and x64 compile with: /O2 /fp:fast /arch:AVX2
// other platforms compile with: /O2

#include <stdio.h>

// remove the following line to enable FP contractions
#pragma fp_contract (off)

int main() {
   double z, b, t;

   for (int i = 0; i < 10; i++) {
      b = i * 5.5;
      t = i * 56.025;

      z = t * i + b;
      printf("out = %.15e\n", z);
   }
}
```

```Output
out = 0.000000000000000e+00
out = 6.152500000000000e+01
out = 2.351000000000000e+02
out = 5.207249999999999e+02
out = 9.184000000000000e+02
out = 1.428125000000000e+03
out = 2.049900000000000e+03
out = 2.783725000000000e+03
out = 3.629600000000000e+03
out = 4.587525000000000e+03
```

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
