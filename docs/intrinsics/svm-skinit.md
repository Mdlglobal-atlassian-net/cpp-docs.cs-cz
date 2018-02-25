---
title: __svm_skinit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_skinit
dev_langs:
- C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 918bd300e11c52b7b4139cfc80b12a5de2b828a4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="svmskinit"></a>__svm_skinit
**Microsoft Specific**  
  
 Zahájí načítání zajišťující bezpečnost zabezpečení softwaru, jako je monitorování virtuálního počítače.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`SLB`|32-bit fyzickou adresu bajt 64 tisíc zabezpečení Block zavaděče (SLB).|  
  
## <a name="remarks"></a>Poznámky  
 `__svm_skinit` Funkce je ekvivalentní volání `SKINIT` počítač instrukcí. Tato funkce je součástí systému zabezpečení, který používá procesoru a důvěryhodné (Trusted Platform Module) k ověření a načtení důvěryhodné softwaru názvem zabezpečení jádra (SK). Monitorování virtuálních počítačů je příkladem zabezpečení jádra. Zabezpečení systému ověřuje součástí programu načtené během procesu inicializace a chrání součásti v manipulaci přerušení, přístup k zařízení nebo jiný program, pokud je počítač procesory.  
  
 `SLB` Parametr určuje fyzickou adresu blok 64 kB paměti volat *zabezpečení Block zavaděč* (SLB). SLB obsahuje program s názvem zabezpečené zavaděč, který vytváří prostředí operačního systému počítače a následně načte zabezpečení jádra.  
  
 Tato funkce podporuje interakci monitorování virtuální počítač na hostitele s hostovaného operačního systému a jeho aplikace. Další informace naleznete v dokumentu "programátory architektura AMD64 ruční svazku 2: programování systému" číslo 24593, revize 3.11, dokumentu v [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__svm_skinit`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)