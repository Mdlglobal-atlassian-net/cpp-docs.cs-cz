---
title: __writecr4
ms.date: 09/02/2019
f1_keywords:
- _writecr4
helpviewer_keywords:
- _writecr4 intrinsic
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
ms.openlocfilehash: 1afdadcdfdbf1060c87e3865dd5597b0b9a2ea6b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219266"
---
# <a name="__writecr4"></a>__writecr4

**Specifické pro společnost Microsoft**

Zapíše hodnotu `Data` do CR4 registru.

## <a name="syntax"></a>Syntaxe

```C
void writecr4(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Údajů*\
pro Hodnota, která se má zapsat do registru CR4

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__writecr4`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tato vnitřní funkce je k dispozici pouze v režimu jádra a rutina je k dispozici pouze jako vnitřní.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
