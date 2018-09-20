---
title: __writegsbyte __writegsdword, __writegsqword __writegsword | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
dev_langs:
- C++
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dded14f47c4c0305e4dc145ee2b006c76da9b8f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393552"
---
# <a name="writegsbyte-writegsdword-writegsqword-writegsword"></a>__writegsbyte, __writegsdword, __writegsqword, __writegsword

**Specifické pro Microsoft**

Zápis paměti do umístění určeného proměnnou posun vzhledem k začátku segmentu GS.

## <a name="syntax"></a>Syntaxe

```
void __writegsbyte( 
   unsigned long Offset, 
   unsigned char Data 
);
void __writegsword( 
   unsigned long Offset, 
   unsigned short Data 
);
void __writegsdword( 
   unsigned long Offset, 
   unsigned long Data 
);
void __writegsqword( 
   unsigned long Offset, 
   unsigned __int64 Data 
);
```

#### <a name="parameters"></a>Parametry

*Posun*<br/>
[in] Posun od začátku GS k zápisu.

*Data*<br/>
[in] Hodnota k zápisu.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__writegsbyte`|x64|
|`__writegsdword`|x64|
|`__writegsqword`|x64|
|`__writegsword`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tyto vnitřní objekty jsou k dispozici v pouze v režimu jádra a tyto rutiny jsou dostupné jenom jako vnitřní funkce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)