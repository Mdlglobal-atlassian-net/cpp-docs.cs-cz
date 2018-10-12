---
title: __sptr __uptr | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/10/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __uptr_cpp
- __sptr_cpp
- __uptr
- __sptr
- _uptr
- _sptr
dev_langs:
- C++
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa67c815fdfeac0f5728ecd671aaa8f04a59ef89
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163475"
---
# <a name="sptr-uptr"></a>__sptr, __uptr

**Specifické pro Microsoft**

Použití **__sptr** nebo **__uptr** modifikátor deklarace 32bitový ukazatel k určení, jak má kompilátor převést 32bitový ukazatel na 64bitový ukazatel. 32bitový ukazatel je například převeden při přiřazení k proměnné 64bitového ukazatele, nebo pokud je k němu přistupováno přes ukazatel na 64bitovou platformu.

Dokumentace společnosti Microsoft pro podporu 64bitových platforem někdy odkazuje na nejvýznamnější bit 32bitového ukazatele jako na bit znaménka. Ve výchozím nastavení používá kompilátor pro převod z 32bitového ukazatele na 64bitový ukazatel příponu znaménka. To znamená, že 32 nejméně významných bitů 64bitového ukazatele je nastaveno na hodnotu 32bitového ukazatele a nejvýznamnějších 32 bitů je nastaveno na bit znaménka 32bitového ukazatele. Tento převod poskytuje správné výsledky, pokud je bit znaménka 0, ale ne v případě, že je bit znaménka 1. Například 32bitová adresa 0x7FFFFFFF dává rovnocennou 64bitovou adresu 0x000000007FFFFFFF, ale 32bitová adresa 0x80000000 je nesprávně změněna na 0xFFFFFFFF80000000.

**__Sptr**, neboli podepsaný ukazatel, modifikátor Určuje, že převod ukazatele nastavuje nejvýznamnější bity 64bitového ukazatele na bit znaménka 32bitového ukazatele. **__Uptr**, nebo ukazatele bez znaménka, modifikátor Určuje, že převod nejvýznamnější bity na nulu. Následující deklarace zobrazují **__sptr** a **__uptr** modifikátory použít s dvěma nekvalifikovanými ukazateli, dvěma kvalifikovanými ukazateli s [__ptr32](../cpp/ptr32-ptr64.md) typu a funkce parametr.

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

Použití **__sptr** a **__uptr** modifikátory s deklaracemi ukazatelů. Modifikátory je třeba použít v pozici [kvalifikátoru typu ukazatele](../c-language/pointer-declarations.md), což znamená, že modifikátor musí následovat po hvězdičce. Nejde použít modifikátory s [ukazatelů na členy](../cpp/pointers-to-members.md). Modifikátory nemají vliv na deklarace neobsahující ukazatele.

Z důvodu kompatibility s předchozími verzemi **_sptr** a **_uptr** jsou synonyma pro **__sptr** a **__uptr** Pokud –možnostkompilátoru[/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) určena.

## <a name="example"></a>Příklad

Následující příklad deklaruje 32bitové ukazatele, které používají **__sptr** a **__uptr** modifikátory, přiřadí každý 32bitový ukazatel k proměnné 64bitového ukazatele a následně zobrazí šestnáctkovou hodnotu každého 64 - ukazatel na bit. Příklad je zkompilován nativním 64bitovým kompilátorem a je spuštěn na 64bitové platformě.

```cpp
// sptr_uptr.cpp
// processor: x64
#include "stdio.h"

int main()
{
    void *        __ptr64 p64;
    void *        __ptr32 p32d; //default signed pointer
    void * __sptr __ptr32 p32s; //explicit signed pointer
    void * __uptr __ptr32 p32u; //explicit unsigned pointer

// Set the 32-bit pointers to a value whose sign bit is 1.
    p32d = reinterpret_cast<void *>(0x87654321);
    p32s = p32d;
    p32u = p32d;

// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated
// to the __sptr and __uptr modifiers.
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");
    printf("p32d:       %p\n", p32d);
    printf("p32s:       %p\n", p32s);
    printf("p32u:       %p\n", p32u);

    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");
    p64 = p32d;
    printf("p32d: p64 = %p\n", p64);
    p64 = p32s;
    printf("p32s: p64 = %p\n", p64);
    p64 = p32u;
    printf("p32u: p64 = %p\n", p64);
    return 0;
}
```

```Output
Display each 32-bit pointer (as an unsigned 64-bit pointer):
p32d:       0000000087654321
p32s:       0000000087654321
p32u:       0000000087654321

Display the 64-bit pointer created from each 32-bit pointer:
p32d: p64 = FFFFFFFF87654321
p32s: p64 = FFFFFFFF87654321
p32u: p64 = 0000000087654321
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md)