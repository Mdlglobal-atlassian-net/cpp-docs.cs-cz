---
title: _Cifmod – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _CIfmod
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _CIfmod
- CIfmod
dev_langs:
- C++
helpviewer_keywords:
- CIfmod intrinsic
- _CIfmod intrinsic
ms.assetid: 7c050653-7ec6-4810-b3a7-7a0057ea65ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bde7a170eb499a9b179a909bfb95e75f8fc89518
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386556"
---
# <a name="cifmod"></a>_CIfmod
Vypočítá zbytek nejvyšší dvě hodnoty v zásobníku s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __cdecl _CIfmod();  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato verze `fmod` funkce má specializované konvence volání, která funguje s technologií kompilátoru. Ji urychluje spuštění, protože kopie brání generován a pomáhá s přidělení registru.  
  
 Výsledná hodnota se posune do horní části zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** x86  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmod, fmodf](../c-runtime-library/reference/fmod-fmodf.md)