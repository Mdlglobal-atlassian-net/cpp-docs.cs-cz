---
title: __invlpg
ms.date: 09/02/2019
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: ba8bd81498f805992336b0dc4163fe18fa157a2c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221893"
---
# <a name="__invlpg"></a>__invlpg

**Specifické pro společnost Microsoft**

Vygeneruje instrukci x86 `invlpg` , která pro stránku přidruženou k paměti, na kterou ukazuje *adresa*, neověřuje TLB vyrovnávací paměť (TLB) překladu.

## <a name="syntax"></a>Syntaxe

```C
void __invlpg(
   void* Address
);
```

### <a name="parameters"></a>Parametry

*Adresáře*\
pro 64-bitová adresa.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__invlpg`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Vnitřní `__invlpg` vygeneruje privilegovanou instrukci, která je k dispozici pouze v režimu jádra s úrovní oprávnění (CPL) 0.

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
