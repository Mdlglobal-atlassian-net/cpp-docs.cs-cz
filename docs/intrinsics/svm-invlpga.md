---
title: __svm_invlpga | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_invlpga
dev_langs:
- C++
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e48fc39fd972387ee9fbbe587dc53bf61f2ae59
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330392"
---
# <a name="svminvlpga"></a>__svm_invlpga
**Konkrétní Microsoft**  
  
 Zruší platnost položku mapování adres ve vyrovnávací paměti vzhled vyhraďte překlad počítače. Parametry zadejte virtuální adresu a adresu místa identifikátor stránce zneplatní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `Va`|Virtuální adresa stránce zneplatní.|  
|[v] `ASID`|Adresa místa identifikátor (ASID) stránky zneplatní.|  
  
## <a name="remarks"></a>Poznámky  
 `__svm_invlpga` Funkce je ekvivalentní volání `INVLPGA` počítač instrukcí. Tato funkce podporuje interakci monitorování virtuální počítač na hostitele s hostovaného operačního systému a jeho aplikace. Další informace naleznete v dokumentu "programátory architektura AMD64 ruční svazku 2: programování systému" číslo 24593, revize 3.11, dokumentu v [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__svm_invlpga`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)