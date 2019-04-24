---
title: __indwordstring
ms.date: 11/04/2016
f1_keywords:
- __indwordstring
- __indwordstring_cpp
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
ms.openlocfilehash: 6f50aed8e6efe3b0b0a6e7eaebef5719475463ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263786"
---
# <a name="indwordstring"></a>__indwordstring

**Microsoft Specific**

Čte data z pomocí zadaný port `rep insd` instrukce.

## <a name="syntax"></a>Syntaxe

```
void __indwordstring(
   unsigned short Port,
   unsigned long* Buffer,
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
|`__indwordstring`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)