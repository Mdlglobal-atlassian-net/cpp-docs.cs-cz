---
title: fp_contract – | Microsoft Docs
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 514b4708129d625ea7880e4c61be22c4b1ac2db5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="fpcontract"></a>fp_contract

Určuje, zda s plovoucí desetinnou čárkou zmenšení probíhá. S plovoucí desetinnou čárkou zmenšení je instrukce například FMA (taveného-násobení-přidat), který kombinuje dvě samostatné operace s plovoucí desetinnou do jednoho instrukcí. Použijte tyto pokyny může ovlivnit s plovoucí desetinnou čárkou přesnost, protože místo zaokrouhlení po každé operaci, může jenom jednou zaokrouhlit procesor po obou operacích.

## <a name="syntax"></a>Syntaxe

> **fp_contract – #pragma (** { **na** | **vypnout** } **)**  

## <a name="remarks"></a>Poznámky  

Ve výchozím nastavení **fp_contract –** je **na**. Tato hodnota informuje kompilátoru pro použití s plovoucí desetinnou čárkou zmenšení pokyny, kde je to možné. Nastavit **fp_contract –** k **vypnout** zachovat jednotlivých pokyny s plovoucí desetinnou čárkou.

Další informace o s plovoucí desetinnou čárkou chování najdete v tématu [/fp (zadejte Floating-Point chování)](../build/reference/fp-specify-floating-point-behavior.md).

Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Příklad

Kód, který vygenerovala od této ukázky nepoužívá instrukci začleněny násobení přidat, i když je k dispozici na cílový procesor. Pokud jste komentář `#pragma fp_contract (off)`, generovaný kód mohou používat jako instrukci začleněny násobení přidat, pokud je k dispozici.  
  
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

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
