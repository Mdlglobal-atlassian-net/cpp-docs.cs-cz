---
title: "fsetpos – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fsetpos
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
f1_keywords: fsetpos
dev_langs: C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71dbbf3c56f81b4987fcadb3db98be8d82e70fb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fsetpos"></a>fsetpos
Nastaví datový proud pozice indikátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fsetpos(   
   FILE *stream,  
   const fpos_t *pos   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
 `pos`  
 Označení pozice úložiště.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `fsetpos` vrátí hodnotu 0. Funkce vrátí nenulovou hodnotu, při selhání a nastaví `errno` na jednu z následujících manifest konstanty (definovanou v kód chyby. H): `EBADF`, což znamená, že soubor není dostupný nebo objekt, `stream` body není platný soubor struktura; nebo `EINVAL`, což znamená neplatnou hodnotu pro `stream` nebo `pos` byl předán. Pokud není předán neplatný parametr v těchto funkcí vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratové kódy.  
  
## <a name="remarks"></a>Poznámky  
 `fsetpos` Funkce nastaví indikátor pozice souboru pro `stream` na hodnotu `pos`, který byl získán v předchozí volání `fgetpos` proti `stream`. Funkce vymaže indikátoru end souboru a vrátí zpět důsledky [ungetc –](../../c-runtime-library/reference/ungetc-ungetwc.md) na `stream`. Po volání `fsetpos`, další operace na `stream` může být buď vstup nebo výstup.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fsetpos`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [fgetpos –](../../c-runtime-library/reference/fgetpos.md).  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)