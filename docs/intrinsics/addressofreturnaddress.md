---
title: _AddressOfReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: d705029c30fdbc117c4c6e96923691e43e072e23
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221075"
---
# <a name="_addressofreturnaddress"></a>_AddressOfReturnAddress

**Specifické pro společnost Microsoft**

Poskytuje adresu umístění v paměti, která obsahuje zpáteční adresu aktuální funkce. Tato adresa se nedá použít pro přístup k jiným umístěním v paměti (například argumentům funkce).

## <a name="syntax"></a>Syntaxe

```C
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86, x64, ARM, ARM64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Při `_AddressOfReturnAddress` použití v programu zkompilovaném pomocí [/CLR](../build/reference/clr-common-language-runtime-compilation.md)je funkce obsahující `_AddressOfReturnAddress` volání kompilována jako nativní funkce. Pokud je funkce kompilována jako spravovaná volání do funkce obsahující `_AddressOfReturnAddress`, `_AddressOfReturnAddress` nemusí chovat podle očekávání.

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```cpp
// compiler_intrinsics_AddressOfReturnAddress.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

// This function will print three values:
//   (1) The address retrieved from _AddressOfReturnAdress
//   (2) The return address stored at the location returned in (1)
//   (3) The return address retrieved the _ReturnAddress* intrinsic
// Note that (2) and (3) should be the same address.
__declspec(noinline)
void func() {
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();
   printf_s("%p\n", pvAddressOfReturnAddress);
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));
   printf_s("%p\n", _ReturnAddress());
}

int main() {
   func();
}
```

```Output
0012FF78
00401058
00401058
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
