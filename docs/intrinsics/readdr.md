---
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: 646330ca92af08903485fd4583eb2c217fe3e023
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216684"
---
# <a name="__readdr"></a>__readdr

Přečte hodnotu zadaného registru ladění.

## <a name="syntax"></a>Syntaxe

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>Parametry

*DebugRegister*\
pro Konstanta od 0 do 7, která identifikuje registr ladění.

## <a name="return-value"></a>Návratová hodnota

Hodnota zadaného registru pro ladění.

## <a name="remarks"></a>Poznámky

Tyto vnitřní objekty jsou k dispozici pouze v režimu jádra a rutiny jsou k dispozici pouze jako vnitřní.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__readdr`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
