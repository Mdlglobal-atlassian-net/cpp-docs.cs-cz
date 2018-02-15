---
title: "__min – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- __min
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
apitype: DLLExport
f1_keywords:
- __min
- min
- _min
dev_langs:
- C++
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8e4f282331caaef9b56d1ca0b52ebf7c5e63ab6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="min"></a>__min
Vrátí menší ze dvou hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
type __min(  
   type a,  
   type b   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Všechny číselným datovým typem.  
  
 `a, b`  
 Hodnoty všech číselného typu, který se má porovnat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Menší dva argumenty.  
  
## <a name="remarks"></a>Poznámky  
 `__min` Makro porovná dvě hodnoty a vrátí hodnotu typu menší. Argumenty, které může být jakékoli číselný datový typ, podepsané nebo bez znaménka. Argumenty a návratová hodnota musí být stejného datového typu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`__min`|\<stdlib.h>|  
  
## <a name="example"></a>Příklad  
  
```  
// crt_minmax.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int a = 10;  
   int b = 21;  
  
   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );  
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );  
}  
```  
  
```Output  
The larger of 10 and 21 is 21  
The smaller of 10 and 21 is 10  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [__max](../../c-runtime-library/reference/max.md)