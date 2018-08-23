---
title: __svm_stgi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_stgi
dev_langs:
- C++
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4717fdc2018788d1fe56c26ae913a71e4f83475f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465761"
---
# <a name="svmstgi"></a>__svm_stgi
**Specifické pro Microsoft**  
  
 Nastaví příznak globální přerušení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_stgi(void);  
```  
  
## <a name="remarks"></a>Poznámky  
 `__svm_stgi` Funkce je ekvivalentní volání `STGI` strojové instrukce. Přerušení globální příznak určuje, jestli mikroprocesoru ignoruje, odloží nebo zpracovává přerušení z důvodu události, například dokončení vstupně-výstupních operací, výstraha teploty hardwaru nebo výjimka ladění.  
  
 Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "programátor architektury AMD64 ruční svazek 2: programování v systému," číslo 24593 revize 3.11, v dokumentu [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__svm_stgi`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__svm_clgi](../intrinsics/svm-clgi.md)