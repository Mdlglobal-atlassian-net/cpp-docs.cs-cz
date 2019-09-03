---
title: __addfsbyte, __addfsword, __addfsdword
ms.date: 09/02/2019
f1_keywords:
- __addfsbyte_cpp
- __addfsdword
- __addfsword_cpp
- __addfsbyte
- __addfsword
- __addfsdword_cpp
helpviewer_keywords:
- __addfsdword intrinsic
- __addfsword intrinsic
- __addfsbyte intrinsic
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
ms.openlocfilehash: 302e58ed13c144913e7806a0a8b7adc202a67ef6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218519"
---
# <a name="__addfsbyte-__addfsword-__addfsdword"></a>__addfsbyte, __addfsword, __addfsdword

**Specifické pro společnost Microsoft**

Přidejte hodnotu do umístění v paměti určené posunem relativně ke začátku `FS` segmentu.

## <a name="syntax"></a>Syntaxe

```C
void __addfsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __addfsword(
   unsigned long Offset,
   unsigned short Data
);
void __addfsdword(
   unsigned long Offset,
   unsigned long Data
);
```

### <a name="parameters"></a>Parametry

*Polohy*\
pro Posun od začátku `FS`.

*Údajů*\
pro Hodnota, která se má přidat do umístění v paměti

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__addfsbyte`|x86|
|`__addfsword`|x86|
|`__addfsdword`|x86|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou k dispozici pouze jako vnitřní objekty.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__incfsbyte, \__incfsword, \__incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)\
[__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
