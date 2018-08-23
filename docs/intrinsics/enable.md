---
title: _povolit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _enable
- _enable_cpp
dev_langs:
- C++
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ca265bc8a6adc3da747e94ca67cd57749687f21
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465574"
---
# <a name="enable"></a>_enable
**Specifické pro Microsoft**  
  
 Umožňuje přerušení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _enable(void);  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`_enable`|x86, ARM, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `_enable` dává pokyn k nastavení příznaku přerušení procesoru. Na x86 systémy, tato funkce generuje nastavit příznak přerušení (`sti`) instrukce.  
  
 Tato funkce je pouze k dispozici v režimu jádra. Pokud se použije v uživatelském režimu, je vyvolána výjimka Privilegovaná instrukce.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)