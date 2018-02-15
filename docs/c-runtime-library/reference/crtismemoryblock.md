---
title: "_Crtismemoryblock – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
dev_langs:
- C++
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58faccd95e831dd264910abf063529db12701bf6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock
Ověřuje, zda blok zadaný paměti je v lokální haldy a který obsahuje identifikátor typ bloku platný ladění haldy (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _CrtIsMemoryBlock(   
   const void *userData,  
   unsigned int size,  
   long *requestNumber,  
   char **filename,  
   int *linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `userData`  
 Ukazatel na začátku bloku paměti k ověření.  
  
 [in] `size`  
 Velikost zadaný blok (v bajtech).  
  
 [out] `requestNumber`  
 Ukazatel na číslo přidělení bloku nebo `NULL`.  
  
 [out] `filename`  
 Ukazatel na název zdrojového souboru, který požadovaný blok nebo `NULL`.  
  
 [out] `linenumber`  
 Ukazatel na číslo řádku ve zdrojovém souboru nebo `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_CrtIsMemoryBlock` Vrátí `TRUE` Pokud bloku zadaná paměťová se nachází v rámci lokální haldy a má platný ladění haldy bloku typ identifikátor; jinak vrátí `FALSE`.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtIsMemoryBlock` Funkce ověřuje, zda blok zadaná paměťová se nachází v rámci aplikace lokální haldy a že má identifikátor platný blok typem. Tato funkce slouží také k získání objektu přidělení pořadové číslo a číslo zdrojového souboru název nebo čáry kde původně požádal bloku přidělení paměti. Probíhá předání hodnoty NULL `requestNumber`, `filename`, nebo `linenumber` parametry příčiny `_CrtIsMemoryBlock` pro tyto parametry nastavit na hodnoty v hlavičce ladění bloku paměti, pokud najde bloku v haldě místní. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtIsMemoryBlock` jsou odebrány při předběžném zpracování.  
  
 Pokud `_CrtIsMemoryBlock` nezdaří, vrátí `FALSE` a výstupní parametry se inicializovat výchozí hodnoty: `requestNumber` a `lineNumber` jsou nastavena na hodnotu 0 a `filename` je nastaven na `NULL`.  
  
 Protože funkce vrátí hodnotu `TRUE` nebo `FALSE`, mohla být předána do jednoho z [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra pro vytváření jednoduchých ladění chyba mechanismu pro zpracování. V následujícím příkladu způsobí chybu assertion Pokud zadaná adresa není umístěn v lokální haldy:  
  
```  
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,   
&filename, &linenumber ) );  
```  
  
 Další informace o tom, `_CrtIsMemoryBlock` lze použít s další funkce ladění a makra najdete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtIsMemoryBlock`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
 Podívejte se příklad [_crtisvalidheappointer –](../../c-runtime-library/reference/crtisvalidheappointer.md) tématu.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)