---
title: _AddressOfReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: 678128c4b09b083b4afe3a86c9b2315eb3c87b1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584480"
---
# <a name="addressofreturnaddress"></a>_AddressOfReturnAddress

**Specifické pro Microsoft**

Poskytuje adresu umístění v paměti, která obsahuje zpáteční adresu aktuální funkce. Tato adresa nemusí být pro přístup k jiné umístění v paměti (například argumenty funkce).

## <a name="syntax"></a>Syntaxe

```
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Když `_AddressOfReturnAddress` se používá v programu kompilovaného s [/CLR](../build/reference/clr-common-language-runtime-compilation.md), funkce obsahující `_AddressOfReturnAddress` volání je zkompilovat jako nativní funkce. Když funkci zkompilovat jako spravovaná volání do funkce obsahující `_AddressOfReturnAddress`, `_AddressOfReturnAddress` nemusí chovat dle očekávání.

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```
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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)