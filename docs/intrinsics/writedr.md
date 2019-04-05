---
title: __writedr
ms.date: 11/04/2016
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: c495e8c80029680512358198ca8fb0ce6e65414d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022478"
---
# <a name="writedr"></a>__writedr

Zadaná hodnota zapíše do registru zadaného ladění.

## <a name="syntax"></a>Syntaxe

```
void __writedr(unsigned DebugRegister, unsigned DebugValue);
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);
```

#### <a name="parameters"></a>Parametry

*DebugRegister*<br/>
[in] Číslo od 0 do 7, který identifikuje ladění registru.

*DebugValue*<br/>
[in] Hodnota k zápisu do dialogu ladit zaregistrovat.

## <a name="remarks"></a>Poznámky

Tyto vnitřní objekty jsou k dispozici pouze v režimu jádra a rutiny jsou k dispozici pouze jako vnitřní funkce.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__writedr`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__readdr](../intrinsics/readdr.md)