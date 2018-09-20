---
title: __readpmc | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readpmc
dev_langs:
- C++
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4574ac1c5ff1ab45dfdf935e5eba3a14a76b948a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419842"
---
# <a name="readpmc"></a>__readpmc

**Specifické pro Microsoft**

Generuje `rdpmc` instrukce, který čte určené čítače sledování výkonu `counter`.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __readpmc( 
   unsigned long counter 
);
```

#### <a name="parameters"></a>Parametry

*Čítač*<br/>
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

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)