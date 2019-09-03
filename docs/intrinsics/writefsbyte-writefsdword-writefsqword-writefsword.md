---
title: __writefsbyte, __writefsdword, __writefsqword, __writefsword
ms.date: 09/02/2019
f1_keywords:
- __writefsword
- __writefsbyte
- __writefsqword
- __writefsdword
helpviewer_keywords:
- writefsbyte intrinsic
- __writefsword intrinsic
- writefsqword intrinsic
- writefsdword intrinsic
- __writefsdword intrinsic
- __writefsqword intrinsic
- __writefsbyte intrinsic
- writefsword intrinsic
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
ms.openlocfilehash: c0cb70986fc75d14f23fb70efe89f48e10fb047e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219127"
---
# <a name="__writefsbyte-__writefsdword-__writefsqword-__writefsword"></a>__writefsbyte, __writefsdword, __writefsqword, __writefsword

**Specifické pro společnost Microsoft**

Zapište paměť do umístění určeného posunem relativně vzhledem k začátku segmentu FS.

## <a name="syntax"></a>Syntaxe

```C
void __writefsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writefsword(
   unsigned long Offset,
   unsigned short Data
);
void __writefsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writefsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Polohy*\
pro Posun od začátku FS, do které se má zapisovat

*Údajů*\
pro Hodnota, která má být zapsána.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__writefsbyte`|x86|
|`__writefsword`|x86|
|`__writefsdword`|x86|
|`__writefsqword`|x86|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou k dispozici pouze jako vnitřní objekty.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
