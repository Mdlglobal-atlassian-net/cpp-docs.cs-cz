---
title: _disable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _disable_cpp
- _disable
dev_langs: C++
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f46744ab30fe3139e036aabbd66cb9017f62ce2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="disable"></a>_disable
**Konkrétní Microsoft**  
  
 Zakáže přerušení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _disable(void);  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_disable`|x86 ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `_disable`dá pokyn procesor pro příznaku přerušení. Na x86 systémy, tato funkce generuje Vymazat příznak přerušení (`cli`) instrukcí.  
  
 Tato funkce je dostupný jenom v režimu jádra. Pokud se používá v uživatelském režimu, Privilegovaná instrukce k výjimce v době běhu.  
  
 Na platformách ARM této rutiny je k dispozici pouze jako vnitřní.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)