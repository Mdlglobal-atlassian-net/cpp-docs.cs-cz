---
title: __readcr3
ms.date: 11/04/2016
f1_keywords:
- __readcr3
helpviewer_keywords:
- __readcr3 intrinsic
ms.assetid: e24392c3-cad7-4788-8f31-94bf2e9e0053
ms.openlocfilehash: 8b5839d233154b6ddb69d2bbe0b13497c3b66305
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396532"
---
# <a name="readcr3"></a>__readcr3

**Microsoft Specific**

Přečte CR3 registr a vrátí jeho hodnotu.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __readcr3(void);
```

## <a name="return-value"></a>Návratová hodnota

Hodnota registru CR3.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__readcr3`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní je k dispozici pouze v režimu jádra a rutina je dostupný jenom jako vnitřní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)