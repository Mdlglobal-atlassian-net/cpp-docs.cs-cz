---
title: __writecr3
ms.date: 09/02/2019
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: f2472a21fe42f10dbf0918480ef02f7e48109747
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219275"
---
# <a name="__writecr3"></a>__writecr3

**Specifické pro společnost Microsoft**

Zapíše hodnotu `Data` do cr3 registru.

## <a name="syntax"></a>Syntaxe

```C
void writecr3(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Údajů*\
pro Hodnota, která se má zapsat do registru CR3

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__writecr3`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tato vnitřní funkce je k dispozici pouze v režimu jádra a rutina je k dispozici pouze jako vnitřní.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
