---
title: "fclose –, _fcloseall – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fclose
- _fcloseall
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
f1_keywords:
- fclose
- _fcloseall
dev_langs: C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d0cb985b4e2ddeea853ccd40668a3e378834e68a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall
Zavře datového proudu (`fclose`) nebo, zavře všechny otevřené datové proudy (`_fcloseall`).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fclose(   
   FILE *stream   
);  
int _fcloseall( void );  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 `fclose`Vrátí hodnotu 0, pokud datový proud je uzavřen úspěšně. `_fcloseall`Vrátí celkový počet datových proudů uzavřen. Obě funkce vrátí `EOF` indikující chybu.  
  
## <a name="remarks"></a>Poznámky  
 `fclose` Funkce zavře `stream`. Pokud `stream` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `fclose` nastaví `errno` k `EINVAL` a vrátí `EOF`. Dále je doporučeno `stream` ukazatel vždy zaškrtnuto před volání této funkce.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.  
  
 `_fcloseall` Funkce zavře všechny otevřené datové proudy s výjimkou `stdin`, `stdout`, `stderr` (a v MS-DOS, `_stdaux` a `_stdprn`). Také se zavře a odstraní všechny dočasné soubory vytvořené `tmpfile`. V obou funkce jsou před uzavírací Vyprázdněné všechny vyrovnávací paměti přidružené datového proudu. Vyrovnávací paměti přidělené systému vydávají při datový proud je uzavřen. Vyrovnávací paměti přiřazené uživatelem s `setbuf` a `setvbuf` nejsou vydané automaticky.  
  
 **Poznámka:** Pokud tyto funkce používají Zavřít datový proud, podkladové popisovače souborů a operačního systému popisovač souboru (nebo soketu) jsou uzavřeny, a také datového proudu. Proto pokud soubor byl původně otevřen jako soubor zpracování nebo soubor popisovače a se zavřel s `fclose`, ne také provést volání `_close` k zavřete popisovače souborů; Nevolejte funkce Win32 `CloseHandle` zavřít popisovač souboru.  
  
 `fclose`a `_fcloseall` , přidat kód pro ochranu proti rušení jiná vlákna. Bez uzamčení verze nástroje `fclose`, najdete v části `_fclose_nolock`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fclose`|\<stdio.h >|  
|`_fcloseall`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [fopen –](../../c-runtime-library/reference/fopen-wfopen.md).  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_close –](../../c-runtime-library/reference/close.md)   
 [_fdopen –, _wfdopen –](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush –](../../c-runtime-library/reference/fflush.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen –, _wfreopen –](../../c-runtime-library/reference/freopen-wfreopen.md)