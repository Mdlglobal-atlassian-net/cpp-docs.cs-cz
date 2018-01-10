---
title: "_fclose_nolock – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fclose_nolock
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
- fclose_nolock
- _fclose_nolock
dev_langs: C++
helpviewer_keywords:
- streams, closing
- fclose_nolock function
- _fclose_nolock function
ms.assetid: b4af4392-5fc8-49bb-9fe2-ca7293d3ce04
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a993376f1174a86506f5c61d3b403953bedec3f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fclosenolock"></a>_fclose_nolock
Zavře datového proudu bez blokování vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _fclose_nolock(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Ukazatel `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 `fclose`Vrátí hodnotu 0, pokud datový proud je uzavřen úspěšně. Vrátí `EOF` indikující chybu.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je verze bez uzamčení `fclose`. Je identický s tím rozdílem, že není chráněn před narušení další vlákna. Může být rychlejší, protože není nesnižuje režii uzamykání jiná vlákna. Tuto funkci můžete používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fclose_nolock`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_close –](../../c-runtime-library/reference/close.md)   
 [_fdopen –, _wfdopen –](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush –](../../c-runtime-library/reference/fflush.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)