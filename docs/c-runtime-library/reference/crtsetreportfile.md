---
title: "_Crtsetreportfile – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a97e3f856dae60eeae9b96f3d5b422f8a262c68a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="crtsetreportfile"></a>_CrtSetReportFile
Po použití [_crtsetreportmode –](../../c-runtime-library/reference/crtsetreportmode.md) k určení `_CRTDBG_MODE_FILE`, můžete zadat popisovač souboru přijímat textové zprávy. `_CrtSetReportFile` je také používány [_crtdbgreport –, _crtdbgreportw –](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) k určení cílového textu (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_HFILE _CrtSetReportFile(   
   int reportType,  
   _HFILE reportFile   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `reportType`  
 Typ sestavy: `_CRT_WARN`, `_CRT_ERROR`, a `_CRT_ASSERT`.  
  
 `reportFile`  
 Nový soubor sestavy pro `reportType`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při úspěšném dokončení `_CrtSetReportFile` vrací předchozího souboru sestavy definované pro typ sestavy zadané v `reportType`. Pokud je předána neplatná hodnota `reportType`, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `_CRTDBG_HFILE_ERROR`. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_CrtSetReportFile` se používá s [_crtsetreportmode –](../../c-runtime-library/reference/crtsetreportmode.md) funkce můžete definovat cíl nebo cíle pro konkrétní typ sestavy generované `_CrtDbgReport`. Když `_CrtSetReportMode` byla volána přiřadit `_CRTDBG_MODE_FILE` reporting režim pro konkrétní typ sestavy, `_CrtSetReportFile` by měla být volána poté zadat konkrétní soubor nebo datový proud použít jako cíl. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtSetReportFile` jsou odebrány při předběžném zpracování.  
  
 Následující tabulka uvádí seznam dostupných možností pro `reportFile` a jejich výsledné chování z `_CrtDbgReport`. Tyto možnosti jsou definovány jako bitové příznaky v Crtdbg.h.  
  
 `file handle`  
 Popisovač pro soubor, který bude cíl zprávy. Žádný pokus se uskuteční k ověření platnosti popisovač. Musíte otevřít a zavřít popisovač souboru. Příklad:  
  
```  
HANDLE hLogFile;  
hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,   
   FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,   
   FILE_ATTRIBUTE_NORMAL, NULL);  
_CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_WARN, hLogFile);  
  
_RPT0(_CRT_WARN,"file message\n");  
CloseHandle(hLogFile);  
```  
  
 `_CRTDBG_FILE_STDERR`  
 Zápisy zprávu `stderr`, což může být přesměrován následujícím způsobem:  
  
```  
freopen( "c:\\log2.txt", "w", stderr);  
_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);  
  
_RPT0(_CRT_ERROR,"1st message\n");  
```  
  
 `_CRTDBG_FILE_STDOUT`  
 Zápisy zprávu `stdout`, které může přesměrovat.  
  
 `_CRTDBG_REPORT_FILE`  
 Vrátí aktuální režim sestavy.  
  
 Soubor sestavy používá každý typ sestavy můžete řídit samostatně. Například je možné určit, že `reportType` z `_CRT_ERROR` , se nahlásí `stderr`, zatímco `reportType` z `_CRT_ASSERT` ohlášena popisovač uživatelem definované souboru nebo datový proud.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportFile`|\<crtdbg.h>|\<errno.h>|  
  
 Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce mohli používat v aplikacích pro UPW, musí být přesměrována. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
 **Knihovny:** ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)