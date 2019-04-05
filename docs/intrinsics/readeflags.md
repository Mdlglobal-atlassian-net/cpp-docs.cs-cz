---
title: __readeflags
ms.date: 11/04/2016
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: 9913fb4287e673faf79b2c352bb42eda7f590fdd
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026367"
---
# <a name="readeflags"></a>__readeflags

Přečte že stav programu a ovládací prvek (EFLAGS) registrovat.

## <a name="syntax"></a>Syntaxe

```
unsigned     int __readeflags(void);
unsigned __int64 __readeflags(void);
```

## <a name="return-value"></a>Návratová hodnota

Hodnota registru EFLAGS. Vrácená hodnota je 32 bitů dlouhý na 32bitové platformě a 64 bitů dlouhý na 64bitové platformě.

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou k dispozici pouze jako vnitřní funkce.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__readeflags`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__writeeflags](../intrinsics/writeeflags.md)