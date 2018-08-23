---
title: __svm_skinit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_skinit
dev_langs:
- C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0912b7a1ff41bf7a21da198268dbd4b8dc920a9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465772"
---
# <a name="svmskinit"></a>__svm_skinit
**Specifické pro Microsoft**  
  
 Iniciuje načítání ověřitelně zabezpečeného softwaru, jako je monitorování virtuálního počítače.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`SLB`|Fyzická adresa 32-bit bajtu 64 kB blok zabezpečení zavaděč (SLB).|  
  
## <a name="remarks"></a>Poznámky  
 `__svm_skinit` Funkce je ekvivalentní volání `SKINIT` strojové instrukce. Tato funkce je součástí zabezpečení systému, který používá procesor a modul pro důvěryhodného Platform (TPM) k ověření a načtení důvěryhodný software volá zabezpečení jádra (SK). Monitorování virtuálního počítače je příkladem zabezpečení jádra. Systém zabezpečení ověří součástí programu načteny během procesu inicializace a chrání součásti v manipulaci přerušení, přístup k zařízení nebo jiný program, pokud je počítač procesory.  
  
 `SLB` Parametr určuje fyzickou adresu 64 kB blok paměti volá *zabezpečení Block zavaděč* (SLB). Nástroj SLB obsahuje program s názvem zabezpečené zavaděč, který vytvoří prostředí operačního systému počítač a následně načte zabezpečení jádra.  
  
 Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "programátor architektury AMD64 ruční svazek 2: programování v systému," číslo 24593 revize 3.11, v dokumentu [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__svm_skinit`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)