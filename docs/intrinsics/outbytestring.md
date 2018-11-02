---
title: __outbytestring
ms.date: 11/04/2016
f1_keywords:
- __outbytestring
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
ms.openlocfilehash: 89d2964fbc3e0d7858ec662fb55511c090036ad8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530921"
---
# <a name="outbytestring"></a>__outbytestring

**Specifické pro Microsoft**

Generuje `rep outsb` instrukce, která odesílá první `Count` bajtů dat, na které odkazuje `Buffer` na port určený `Port`.

## <a name="syntax"></a>Syntaxe

```
void __outbytestring( 
   unsigned short Port, 
   unsigned char* Buffer, 
   unsigned long Count 
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port pro odesílání dat na.

*Vyrovnávací paměti*<br/>
[in] Data, která mají být odeslány zadaný port.

*Počet*<br/>
[in] Počet bajtů dat k odeslání.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__outbytestring`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)