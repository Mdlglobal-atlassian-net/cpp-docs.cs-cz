---
title: __addgsbyte, __addgsword, __addgsdword, __addgsqword
ms.date: 11/04/2016
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
ms.openlocfilehash: 2439e541332705ec5330a7ee6e703c99712f7e8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667603"
---
# <a name="addgsbyte-addgsword-addgsdword-addgsqword"></a>__addgsbyte, __addgsword, __addgsdword, __addgsqword

**Specifické pro Microsoft**

Přidat hodnotu do umístění v paměti určený posun vzhledem k začátku `GS` segmentu.

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Parametry

*Posun*<br/>
[in] Posun od začátku `GS`.

*Data*<br/>
[in] Hodnota k přidání do umístění v paměti.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__addgsbyte`|x64|
|`__addgsword`|x64|
|`__addgsdword`|x64|
|`__addgsqword`|x64|

## <a name="remarks"></a>Poznámky

Tyto vnitřní objekty jsou k dispozici v pouze v režimu jádra a tyto rutiny jsou dostupné jenom jako vnitřní funkce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[__incgsbyte, \__incgsword, \__incgsdword, \__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)<br/>
[__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)