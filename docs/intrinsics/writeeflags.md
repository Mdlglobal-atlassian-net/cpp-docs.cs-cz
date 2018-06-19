---
title: __writeeflags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writeeflags
dev_langs:
- C++
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a2885f2ea103ad43535b11c526b96ed42de45fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340525"
---
# <a name="writeeflags"></a>__writeeflags
Zapíše zadaná hodnota programu stav a řízení (EFLAGS) zaregistrovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __writeeflags(unsigned Value);  
void __writeeflags(unsigned __int64 Value);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `Value`|Hodnota určená k zápisu do registru EFLAGS. `Value` Parametr je 32 bity dlouho pro 32bitovou platformu a 64bitová verze dlouho pro 64bitovou platformu.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto rutiny jsou k dispozici pouze jako vnitřní funkce.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__writeeflags`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)