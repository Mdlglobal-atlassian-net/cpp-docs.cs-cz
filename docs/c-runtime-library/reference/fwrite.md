---
title: "fwrite – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fwrite
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords: fwrite
dev_langs: C++
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b830dfd7b0a9dace46336f8f02da14fc268daf6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fwrite"></a>fwrite
Zapíše data do datového proudu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t fwrite(  
   const void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Ukazatel na data, která má být proveden zápis.  
  
 `size`  
 Velikost položky v bajtech.  
  
 `count`  
 Maximální počet položek, které mají být zapsána.  
  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 `fwrite`Vrátí počet úplné položek ve skutečnosti zapisovat, což může být menší než `count` Pokud dojde k chybě. Navíc pokud dojde k chybě, nelze určit indikátoru pozice souboru. Pokud má jedna `stream` nebo `buffer` je ukazatel s hodnotou null, nebo pokud je v režimu Unicode je zadán lichý počet bajtů, které mají být zapsána, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí hodnotu 0.  
  
## <a name="remarks"></a>Poznámky  
 `fwrite` Funkce zapíše až `count` položek, z `size` délka, z `buffer` k výstupu `stream`. Ukazatele souboru přidružené `stream` (pokud existuje) se zvýší o počet skutečně zapsaných bajtů. Pokud `stream` je otevřen v režimu textových každý konce řádku nahradí znak-konce - pár konce řádku. Pokud chcete nahrazení nemá žádný vliv na návratovou hodnotu.  
  
 Když `stream` je otevřen v režimu převodu znakové sady Unicode – například pokud `stream` je otevřen voláním `fopen` a použití režimu parametr, který zahrnuje `ccs=UNICODE`, `ccs=UTF-16LE`, nebo `ccs=UTF-8`, nebo pokud je režim ke změně typu Unicode režim překladu pomocí `_setmode` a režimu parametr, který zahrnuje `_O_WTEXT`, `_O_U16TEXT`, nebo `_O_U8TEXT`–`buffer` interpretována jako ukazatel na pole `wchar_t` obsahující data ve formátu UTF-16. Pokus o zápis lichý počet bajtů v tomto režimu způsobí, že chyba ověření parametru.  
  
 Tato funkce zamkne volající vlákno, proto je bezpečné pro přístup z více vláken. Bez uzamčení verze, najdete v části `_fwrite_nolock`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fwrite`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [fread –](../../c-runtime-library/reference/fread.md).  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_setmode –](../../c-runtime-library/reference/setmode.md)   
 [fread –](../../c-runtime-library/reference/fread.md)   
 [_fwrite_nolock –](../../c-runtime-library/reference/fwrite-nolock.md)   
 [_write](../../c-runtime-library/reference/write.md)