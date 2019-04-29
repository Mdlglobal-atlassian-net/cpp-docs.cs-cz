---
title: __writecr8
ms.date: 11/04/2016
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: 44b009e68f3dd7825bc064e5f9f4ee8d03d7fb4a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389902"
---
# <a name="writecr8"></a>__writecr8

**Microsoft Specific**

Zapíše hodnotu `Data` CR8 registrace.

## <a name="syntax"></a>Syntaxe

```
void writecr8(
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>Parametry

*Data*<br/>
[in] Hodnota k zápisu do registru CR8.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__writecr8`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní je k dispozici pouze v režimu jádra a rutina je dostupný jenom jako vnitřní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)