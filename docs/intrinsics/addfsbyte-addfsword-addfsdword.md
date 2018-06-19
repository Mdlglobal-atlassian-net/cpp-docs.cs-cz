---
title: __addfsbyte, __addfsword, __addfsdword | Microsoft Docs
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
ms.openlocfilehash: f4c2b4a9e185f709ff829a3b88ea9cb67741fa1c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330243"
---
# <a name="addfsbyte-addfsword-addfsdword"></a>__addfsbyte, __addfsword, __addfsdword
**Konkrétní Microsoft**  
  
 Přidejte hodnotu do umístění v paměti určeného posun vzhledem k začátku `FS` segmentu.  
  
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
 [v] `Offset`  
 Posun od začátku `FS`.  
  
 [v] `Data`  
 Hodnota k přidání do umístění v paměti.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__addfsbyte`|x86|  
|`__addfsword`|x86|  
|`__addfsdword`|x86|  
  
## <a name="remarks"></a>Poznámky  
 Tyto rutiny jsou k dispozici pouze jako vnitřní funkce.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__incfsbyte, \__incfsword, \__incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)   
 [__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)