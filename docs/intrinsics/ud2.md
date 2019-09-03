---
title: __ud2
ms.date: 09/02/2019
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: b5aa20804099af4d75dcc62a5e62ccc0d4a09566
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219755"
---
# <a name="__ud2"></a>__ud2

**Specifické pro společnost Microsoft**

Vygeneruje nedefinovanou instrukci.

## <a name="syntax"></a>Syntaxe

```C
void __ud2();
```

## <a name="remarks"></a>Poznámky

Procesor vyvolá neplatnou výjimku opcode, pokud spustíte nedefinovanou instrukci.

Funkce je ekvivalentní `UD2` instrukci počítače a je k dispozici pouze v režimu jádra. `__ud2` Pokud chcete získat další informace, vyhledejte dokument "Intel Architecture Software Developer 's Manual, Volume 2: Odkaz na sadu instrukcí "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__ud2`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="example"></a>Příklad

Následující příklad provede nedefinovanou instrukci, která vyvolá výjimku. Obslužná rutina výjimky pak změní návratový kód od nuly na jeden.

```cpp
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

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
