---
title: "srand – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: srand
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords: srand
dev_langs: C++
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.assetid: 7bf56dc5-5692-4182-a3c1-18af98d2dd1a
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 99847da3be2e311ac9cb0da301ed4729705ad9fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="srand"></a>srand
Nastaví výchozí počáteční hodnotu pro generátor pseudonáhodných čísel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void srand(  
   unsigned int seed   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `seed`  
 Počáteční hodnota pro generování pseudonáhodných čísel  
  
## <a name="remarks"></a>Poznámky  
 Funkce `srand` nastaví počáteční bod pro generování posloupnosti pseudonáhodných celých čísel v aktuálním vlákně. Chcete-li generátor opětovně inicializovat, aby vytvořil stejnou sekvenci výsledků, zavolejte funkci `srand` a použijte znovu stejný argument `seed`. Jakákoli jiná hodnota parametru `seed` nastaví generátor na jiný výchozí bod v pseudonáhodné posloupnosti. Funkce `rand` načte pseudonáhodná čísla, která jsou generována. Volání funkce `rand` před voláním funkce `srand` vygeneruje stejnou posloupnost jako volání funkce `srand` s hodnotou 1 předanou parametru `seed`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`srand`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [rand –](../../c-runtime-library/reference/rand.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [rand –](../../c-runtime-library/reference/rand.md)