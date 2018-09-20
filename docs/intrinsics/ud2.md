---
title: __ud2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ud2
dev_langs:
- C++
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 078fcbfd42c64a0ec5d90a41e8ec3e4ae392f57d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433937"
---
# <a name="ud2"></a>__ud2

**Specifické pro Microsoft**

Generuje instrukce nedefinovaný.

## <a name="syntax"></a>Syntaxe

```
void __ud2();
```

## <a name="remarks"></a>Poznámky

Procesor vyvolá výjimku neplatný operační kód, pokud spustí nedefinované instrukce.

`__ud2` Funkce je ekvivalentní volání `UD2` strojové instrukce a je k dispozici pouze v režimu jádra. Další informace vyhledejte dokument, "ruční architektury Intel softwarový vývojář, svazek 2: odkaz na sadu instrukcí," na [společnosti Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__ud2`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="example"></a>Příklad

Následující příklad spustí nedefinované instrukce, která vyvolává výjimku. Obslužná rutina výjimky poté změní návratový kód od nuly do jednoho.

```
// __ud2_intrinsic.cpp
#include <stdio.h>
#include <intrin.h>
#include <excpt.h>
// compile with /EHa

int main() {

// Initialize the return code to 0.
int ret = 0;

// Attempt to execute an undefined instruction.
  printf("Before __ud2(). Return code = %d.\n", ret);
  __try {
  __ud2();
  }

// Catch any exceptions and set the return code to 1.
  __except(EXCEPTION_EXECUTE_HANDLER){
  printf("  In the exception handler.\n");
  ret = 1;
  }

// Report the value of the return code.
  printf("After __ud2().  Return code = %d.\n", ret);
  return ret;
}
```

```Output
Before __ud2(). Return code = 0.
  In the exception handler.
After __ud2().  Return code = 1.
```

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)