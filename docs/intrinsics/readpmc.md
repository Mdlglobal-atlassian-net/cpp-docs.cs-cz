---
title: __readpmc
ms.date: 11/04/2016
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: 848c880e76d6d431ee56a0bb30a33b276837ce76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396441"
---
# <a name="readpmc"></a>__readpmc

**Microsoft Specific**

Generuje `rdpmc` instrukce, který čte určené čítače sledování výkonu `counter`.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __readpmc(
   unsigned long counter
);
```

#### <a name="parameters"></a>Parametry

*counter*<br/>
[in] Čítač výkonu ke čtení.

## <a name="return-value"></a>Návratová hodnota

Hodnotu zadaný čítač výkonu.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__readpmc`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní je k dispozici v pouze v režimu jádra a rutina je dostupný jenom jako vnitřní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)