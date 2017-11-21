---
title: __faststorefence | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __faststorefence_cpp
- __faststorefence
dev_langs: C++
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a3b023109e247ff81658a1eae2cc2b771f001f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="faststorefence"></a>__faststorefence
**Konkrétní Microsoft**  
  
 Zaručuje, že každý předchozí odkaz paměti, včetně i zatížení a ukládání odkazů na paměti, je globálně viditelné před všechny odkazy na další paměť.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __faststorefence();  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__faststorefence`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Generuje pořadí instrukce úplné paměti bariéry, že záruky spouštění a ukládání operace vydané před Tento vnitřní jsou globálně viditelné před spuštěním bude pokračovat. Efekt je srovnatelná ale rychlejší než `_mm_mfence` vnitřní na všechny x64 platformy.  
  
 Na platformě AMD64 Tato rutina generuje instrukci, který je rychlejší ochranná úložiště, než `sfence` instrukcí. Kód kritický pro čas, použijte tuto vnitřní místo `_mm_sfence` pouze na platformách AMD64. Na platformách Intel x64 `_mm_sfence` instrukce je rychlejší.  
  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)