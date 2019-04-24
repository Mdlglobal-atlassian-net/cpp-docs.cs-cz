---
title: __readdr
ms.date: 11/04/2016
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: 9d265fe75abaa7ad3cfd508613766cc3b600ee14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263280"
---
# <a name="readdr"></a>__readdr

Přečte hodnotu do registru zadaného ladění.

## <a name="syntax"></a>Syntaxe

```
unsigned         __readdr(unsigned int DebugRegister);
unsigned __int64 __readdr(unsigned int DebugRegister);
```

#### <a name="parameters"></a>Parametry

*DebugRegister*<br/>
[in] Registrace – konstanta od 0 do 7, který identifikuje ladění.

## <a name="return-value"></a>Návratová hodnota

Hodnota registru zadané ladění.

## <a name="remarks"></a>Poznámky

Tyto vnitřní objekty jsou k dispozici pouze v režimu jádra a rutiny jsou k dispozici pouze jako vnitřní funkce.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__readdr`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__readeflags](../intrinsics/readeflags.md)