---
title: __readcr8
ms.date: 11/04/2016
f1_keywords:
- __readcr8
helpviewer_keywords:
- __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
ms.openlocfilehash: d4c0b22d38d725566062d2da98839579c22d571c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396454"
---
# <a name="readcr8"></a>__readcr8

**Microsoft Specific**

Přečte CR8 registr a vrátí jeho hodnotu.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __readcr8(void);
```

## <a name="return-value"></a>Návratová hodnota

Hodnota registru CR8.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__readcr8`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní je k dispozici pouze v režimu jádra a rutina je dostupný jenom jako vnitřní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)