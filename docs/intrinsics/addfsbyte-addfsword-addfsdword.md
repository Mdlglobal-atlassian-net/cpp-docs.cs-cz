---
title: __addfsbyte __addfsword, __addfsdword | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __addfsbyte_cpp
- __addfsdword
- __addfsword_cpp
- __addfsbyte
- __addfsword
- __addfsdword_cpp
dev_langs:
- C++
helpviewer_keywords:
- __addfsdword intrinsic
- __addfsword intrinsic
- __addfsbyte intrinsic
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5831d109301fe400cf75110221c3c37204bf5b26
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414963"
---
# <a name="addfsbyte-addfsword-addfsdword"></a>__addfsbyte __addfsword, __addfsdword

**Specifické pro Microsoft**

Přidat hodnotu do umístění v paměti určený posun vzhledem k začátku `FS` segmentu.

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Parametry

*Posun*<br/>
[in] Posun od začátku `FS`.

*Data*<br/>
[in] Hodnota k přidání do umístění v paměti.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__addfsbyte`|x86|
|`__addfsword`|x86|
|`__addfsdword`|x86|

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou k dispozici pouze jako vnitřní funkce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[__incfsbyte, \__incfsword, \__incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)<br/>
[__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)<br/>
[__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)