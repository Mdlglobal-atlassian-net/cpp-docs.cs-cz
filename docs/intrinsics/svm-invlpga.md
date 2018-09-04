---
title: __svm_invlpga | Dokumentace Microsoftu
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
ms.openlocfilehash: 77ada66d0478996eac30c8218793d962e8fcf7ca
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680085"
---
# <a name="svminvlpga"></a>__svm_invlpga
**Specifické pro Microsoft**  
  
 Zruší platnost položky mapování adresy ve vyrovnávací paměti počítače překlad doplňování vzhled. Parametry zadejte virtuální adresu a adresu místo identifikátor stránky zrušit platnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[in] `Va`|Virtuální adresa stránky zrušit platnost.|  
|[in] `ASID`|Adresa místa identifikátor (ASID) na stránce zrušit platnost.|  
  
## <a name="remarks"></a>Poznámky  
 `__svm_invlpga` Funkce je ekvivalentní volání `INVLPGA` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "programátor architektury AMD64 ruční svazek 2: programování v systému," číslo 24593 revize 3.11, v dokumentu [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__svm_invlpga`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)