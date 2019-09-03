---
title: __addgsbyte, __addgsword, __addgsdword, __addgsqword
ms.date: 09/02/2019
f1_keywords:
- __addgsdword
- __addgsqword
- __addgsword_cpp
- __addgsword
- __addgsbyte_cpp
- __addgsqword_cpp
- __addgsbyte
- __addgsdword_cpp
helpviewer_keywords:
- __addgsword intrinsic
- __addgsqword intrinsic
- __addgsdword intrinsic
- __addgsbyte intrinsic
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
ms.openlocfilehash: 5dddd8b4a887dc0e01107f8c1036a399b4e52d2e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221091"
---
# <a name="__addgsbyte-__addgsword-__addgsdword-__addgsqword"></a>__addgsbyte, __addgsword, __addgsdword, __addgsqword

**Specifické pro společnost Microsoft**

Přidejte hodnotu do umístění v paměti určené posunem relativně ke začátku `GS` segmentu.

## <a name="syntax"></a>Syntaxe

```C
void __addgsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __addgsword(
   unsigned long Offset,
   unsigned short Data
);
void __addgsdword(
   unsigned long Offset,
   unsigned long Data
);
void __addgsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Polohy*\
pro Posun od začátku `GS`.

*Údajů*\
pro Hodnota, která se má přidat do umístění v paměti

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__addgsbyte`|x64|
|`__addgsword`|x64|
|`__addgsdword`|x64|
|`__addgsqword`|x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou k dispozici pouze jako vnitřní.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__incgsbyte, \__incgsword, \__incgsdword, \__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)\
[__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
