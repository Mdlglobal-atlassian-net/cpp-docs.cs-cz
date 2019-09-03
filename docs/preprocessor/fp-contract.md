---
title: fp_contract – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: 833d8e7f4b8c9da18901610e52afed619468c5c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218561"
---
# <a name="fp_contract-pragma"></a>fp_contract – direktiva pragma

Určuje, jestli se má vykonat kontrakt s plovoucí desetinnou čárkou. Kontrakt s plovoucí desetinnou čárkou je instrukce, jako je FMA (s vynásobeným přidáním), který kombinuje dva samostatné operace s plovoucí desetinnou čárkou do jediné instrukce. Použití těchto instrukcí může ovlivnit přesnost s plovoucí desetinnou čárkou, protože místo zaokrouhlování po každé operaci může procesor po obou operacích zaokrouhlit jenom jednou.

## <a name="syntax"></a>Syntaxe

> **#pragma fp_contract (** { **on** | **off** } **)**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je fp_contract **zapnutý**. To kompilátoru oznamuje, že pokud je to možné, použijte pokyny pro kontrakt s plovoucí desetinnou čárkou. Nastavte **fp_contract** na **off** pro zachování jednotlivých instrukcí s plovoucí desetinnou čárkou.

Další informace o chování plovoucí desetinné čárky naleznete v tématu [/FP (určení chování s plovoucí](../build/reference/fp-specify-floating-point-behavior.md)desetinnou čárkou).

Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Příklad

Kód vygenerovaný z této ukázky nepoužívá pojistou instrukci pro přidání, i když je k dispozici v cílovém procesoru. Pokud zadáte komentář `#pragma fp_contract (off)`, vygenerovaný kód může použít instrukci s pojistkou, pokud je k dispozici.

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

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
