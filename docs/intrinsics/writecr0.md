---
title: __writecr0
ms.date: 09/02/2019
f1_keywords:
- _writecr0
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
ms.openlocfilehash: 1f00796242ae352d32935c2551d50f2d93d734ec
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219303"
---
# <a name="__writecr0"></a>__writecr0

**Specifické pro společnost Microsoft**

Zapíše hodnotu `Data` do cr0 registru.

## <a name="syntax"></a>Syntaxe

```C
void writecr0(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Údajů*\
pro Hodnota, která se má zapsat do registru CR0

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__writecr0`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tato vnitřní funkce je k dispozici pouze v režimu jádra a rutina je k dispozici pouze jako vnitřní.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
