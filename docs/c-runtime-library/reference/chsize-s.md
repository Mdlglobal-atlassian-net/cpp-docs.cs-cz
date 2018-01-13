---
title: "_chsize_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _chsize_s
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
- chsize_s
- _chsize_s
dev_langs: C++
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b00b0afdf9ba2daac8b4a64a8527d3b73e3c0cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="chsizes"></a>_chsize_s
Změní velikost souboru. Toto je verze [_chsize –](../../c-runtime-library/reference/chsize.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _chsize_s(   
   int fd,  
   __int64 size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Odkaz na soubor otevřený popisovač souboru.  
  
 `size`  
 Nové délka souboru v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_chsize_s`Vrátí hodnotu 0, pokud velikost souboru je úspěšně změnit. Vrácená nenulová hodnota označuje chybu: Vrácená hodnota je `EACCES` zadaný soubor uzamčen před přístupem, `EBADF` Pokud zadaný soubor je jen pro čtení nebo je neplatná, popisovač `ENOSPC` Pokud již není místo na zařízení, nebo `EINVAL` Pokud velikost je menší než nula. `errno`je nastavena na stejnou hodnotu.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_chsize_s` Funkce rozšiřuje nebo zkrátí soubor přidružený k `fd` na délku určeného `size`. Soubor musí být otevřený v režimu, která umožňuje zápis. Znaky Null (\0) jsou připojeny, pokud je soubor rozšířeno. Soubor se zkrátí, dojde ke ztrátě všech dat od konce souboru zkrácená na původní délku souboru.  
  
 `_chsize_s`vezme 64bitové celé číslo jako velikost souboru a proto dokáže zpracovat velikost souboru je větší než 4 GB. `_chsize`je omezený na velikosti souborů 32-bit.  
  
 Tato funkce ověří jeho parametry. Pokud `fd` není platný soubor popisovače nebo velikost je menší než nula, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_chsize_s`|\<IO.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [_chsize –](../../c-runtime-library/reference/chsize.md)   
 [_close –](../../c-runtime-library/reference/close.md)   
 [_creat –, _wcreat –](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)