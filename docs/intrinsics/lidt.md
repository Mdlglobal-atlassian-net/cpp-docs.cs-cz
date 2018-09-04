---
title: __lidt | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs:
- C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4b6dcdee1d30274e8cc4baf3de70e4c6cbb611d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692699"
---
# <a name="lidt"></a>__lidt
**Specifické pro Microsoft**  
  
 Načte do přerušení popisovač tabulky registru (IDTR) s hodnotou v zadaném umístění v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[in] `Source`|Hodnota, která má být zkopírován do IDTR ukazatel.|  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__lidt`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `__lidt` Funkce je ekvivalentní volání `LIDT` strojové instrukce a je k dispozici pouze v režimu jádra. Další informace vyhledejte dokument, "ruční architektury Intel softwarový vývojář, svazek 2: odkaz na sadu instrukcí," na [společnosti Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokality.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__sidt](../intrinsics/sidt.md)