---
title: __invlpg | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __invlpg
- __invlpg_cpp
dev_langs:
- C++
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5a25e16439673f367cfe0bfe208dbc21a621b81
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465576"
---
# <a name="invlpg"></a>__invlpg
**Specifické pro Microsoft**  
  
 Generuje x86 `invlpg` instrukce, což způsobí neplatnost vyrovnávací paměti Page Table Entry překladu (vyrovnávací paměti TLB) pro stránku související s pamětí, na které odkazuje `Address`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __invlpg(  
   void* Address  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]  `Address`  
 64-bit adresa.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__invlpg`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Vnitřní objekt `__invlpg` vysílá Privilegovaná instrukce a je dostupná pouze v režimu jádra s úrovní oprávnění (PANELU) 0.  
  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)