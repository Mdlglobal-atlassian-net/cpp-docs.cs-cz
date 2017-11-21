---
title: vyvolat | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: raise
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords: Raise
dev_langs: C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.assetid: a3ccd3ad-f68f-4a7b-a005-c3ebfb217e8b
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 703f82f5c91cfecd65cb7ca7cf875729d9967f62
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="raise"></a>raise
Odešle signál k provádění programu.  
  
> [!NOTE]
>  Nepoužívejte tuto metodu vypnout [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace, kromě testování nebo ladění scénáře. Zavřete způsoby programový nebo uživatelského rozhraní [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace nejsou povolené podle části 3.6 z [požadavky na certifikaci aplikace systému Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Další informace najdete v tématu [životního cyklu aplikací (aplikace pro Windows Store)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int raise(  
int sig   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *SIG*  
 Signál má být aktivována.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného **vyvolat** vrátí hodnotu 0. Jinak vrátí nenulovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 **Vyvolat** funkce zasílá *sig* provádění programu. Pokud předchozí volání **signál** má nainstalovanou funkci pro zpracování signál *sig*, **vyvolat** spustí této funkce. Pokud byla nainstalována žádná funkce obslužných rutin, výchozí akce asociovaná s hodnotou signál *sig* se provede následujícím způsobem.  
  
|Signál|Význam|Výchozí|  
|------------|-------------|-------------|  
|`SIGABRT`|Abnormální ukončení|Ukončí volací program s ukončovacím kódem 3|  
|`SIGFPE`|Chyba s plovoucí desetinnou čárkou|Ukončí volací program|  
|`SIGILL`|Neplatná instrukce|Ukončí volací program|  
|`SIGINT`|CTRL + C přerušení|Ukončí volací program|  
|`SIGSEGV`|Přístup k úložišti neplatný|Ukončí volací program|  
|`SIGTERM`|Ukončení požadavek odeslaný programu|Ignoruje signál|  
  
 Pokud argument není platný signál, jak je uvedeno výše, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud nebyla zpracována, nastaví funkci `errno` k `EINVAL` a vrátí nenulovou hodnotu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|**vyvolat**|\<Signal.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [signál](../../c-runtime-library/reference/signal.md)