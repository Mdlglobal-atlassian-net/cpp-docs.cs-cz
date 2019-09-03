---
title: __readcr2
ms.date: 09/02/2019
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: 482f4548a692d6aa3b65fbc42caabda29bb393c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217105"
---
# <a name="__readcr2"></a>__readcr2

**Specifické pro společnost Microsoft**

Přečte CR2 registr a vrátí jeho hodnotu.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>Návratová hodnota

Hodnota v registru CR2

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__readcr2`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Vnitřní funkce je k dispozici pouze v režimu jádra a rutina je k dispozici pouze jako vnitřní.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
