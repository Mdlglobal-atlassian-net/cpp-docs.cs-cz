---
title: __readcr2
ms.date: 11/04/2016
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: e26ccbb3db1dfc113f84210314379b06dae93542
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396547"
---
# <a name="readcr2"></a>__readcr2

**Microsoft Specific**

Čtení registru CR2 a vrátí jeho hodnotu.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>Návratová hodnota

Hodnota registru CR2.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__readcr2`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní je k dispozici pouze v režimu jádra a rutina je dostupný jenom jako vnitřní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)