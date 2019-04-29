---
title: __writecr0
ms.date: 11/04/2016
f1_keywords:
- _writecr0
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
ms.openlocfilehash: 24d9ffe0e07269fedf19f90a7c66a07e3c5e7d3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389941"
---
# <a name="writecr0"></a>__writecr0

**Microsoft Specific**

Zapíše hodnotu `Data` CR0 registrace.

## <a name="syntax"></a>Syntaxe

```
void writecr0(
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>Parametry

*Data*<br/>
[in] Hodnota k zápisu do registru CR0.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__writecr0`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní je k dispozici pouze v režimu jádra a rutina je dostupný jenom jako vnitřní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)