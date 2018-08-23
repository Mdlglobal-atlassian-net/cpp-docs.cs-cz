---
title: __svm_clgi | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_clgi
dev_langs:
- C++
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54f1a88acef3f3f79a39a8dd68e1beb079f30fec
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464716"
---
# <a name="svmclgi"></a>__svm_clgi
**Specifické pro Microsoft**  
  
 Vymaže příznak globální přerušení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_clgi( void );  
```  
  
## <a name="remarks"></a>Poznámky  
 `__svm_clgi` Funkce je ekvivalentní volání `CLGI` strojové instrukce. Přerušení globální příznak určuje, jestli mikroprocesoru ignoruje, odloží nebo zpracovává přerušení z důvodu události, například dokončení vstupně-výstupních operací, výstraha teploty hardwaru nebo výjimka ladění.  
  
 Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "programátor architektury AMD64 ruční svazek 2: programování v systému," číslo 24593 revize 3.11, v dokumentu [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__svm_clgi`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__svm_stgi](../intrinsics/svm-stgi.md)