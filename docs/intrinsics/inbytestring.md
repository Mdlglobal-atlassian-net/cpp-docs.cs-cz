---
title: __inbytestring
ms.date: 11/04/2016
f1_keywords:
- __inbytestring
- __inbytestring_cpp
helpviewer_keywords:
- rep insb instruction
- __inbytestring intrinsic
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
ms.openlocfilehash: e515c6452d18ca022707fa2f9e36e2045523ccd5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348949"
---
# <a name="inbytestring"></a>__inbytestring

**Microsoft Specific**

Čte data z pomocí zadaný port `rep insb` instrukce.

## <a name="syntax"></a>Syntaxe

```
void __inbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port, který se má číst z.

*Vyrovnávací paměti*<br/>
[out] Tady je zapsána data načtená z portu.

*Počet*<br/>
[in] Počet bajtů ke čtení.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__inbytestring`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)