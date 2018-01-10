---
title: "_Crtsetreportmode – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
dev_langs: C++
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 75d71ae4df727df1dd82ff88a793dc4e9c462b76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtsetreportmode"></a>_CrtSetReportMode
Určuje cílový nebo cíle pro konkrétní typ sestavy generované `_CrtDbgReport` a všechny makra, které volají [_crtdbgreport –, _crtdbgreportw –](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md), jako například [_ASSERT, _asserte –, _ASSERT_EXPR makra](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [_ASSERT, _asserte –, _ASSERT_EXPR makra](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _rptfw – makra](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md), a [_RPT, _RPTF, _RPTW, _rptfw – makra](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _CrtSetReportMode(   
   int reportType,  
   int reportMode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `reportType`  
 Typ sestavy: `_CRT_WARN`, `_CRT_ERROR`, a `_CRT_ASSERT`.  
  
 `reportMode`  
 Nový režim sestavy nebo režimy `reportType`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při úspěšném dokončení `_CrtSetReportMode` vrací předchozí sestavy režim nebo režim pro zadaný typ sestavy v `reportType`. Pokud je předána neplatná hodnota jako `reportType` nebo je zadaný neplatný režim pro `reportMode`, `_CrtSetReportMode` volá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí hodnotu -1. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_CrtSetReportMode`Určuje cíl výstupu `_CrtDbgReport`. Protože makra `_ASSERT`, `_ASSERTE`, `_RPT`, a `_RPTF` volání `_CrtDbgReport`, `_CrtSetReportMode` Určuje cíl výstupu textu zadaným těchto makra.  
  
 Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtSetReportMode` jsou odebrány při předběžném zpracování.  
  
 Pokud není volána `_CrtSetReportMode` definovat cíl výstupu zpráv, pak tyto výchozí hodnoty jsou platné:  
  
-   Selhání vyhodnocení a chyb jsou směrované okno zprávy ladění.  
  
-   Upozornění z aplikací systému Windows se odesílají do okna výstupu ladicího programu.  
  
-   Upozornění z konzole aplikace nebudou zobrazeny.  
  
 Následující tabulka uvádí typy sestav, které jsou definované v Crtdbg.h.  
  
|Typ sestavy|Popis|  
|-----------------|-----------------|  
|`_CRT_WARN`|Upozornění, zprávy a informace, které nemusí okamžitou pozornost.|  
|`_CRT_ERROR`|Chyby, neopravitelné problémy a problémy, které vyžadují okamžitou pozornost.|  
|`_CRT_ASSERT`|Selhání vyhodnocení (prohlašovanou výrazů, která se vyhodnotí jako `FALSE`).|  
  
 `_CrtSetReportMode` Funkce přiřadí nový režim sestavy zadané v `reportMode` na typ sestavy, zadaný v `reportType` a vrátí hodnotu režimu dříve definovaném sestavy pro `reportType`. V následující tabulce jsou uvedeny dostupné možnosti pro `reportMode` a jejich výsledné chování z `_CrtDbgReport`. Tyto možnosti jsou definovány jako bitové příznaky v Crtdbg.h.  
  
|Sestava režimu|_Crtdbgreport – chování|  
|-----------------|-----------------------------|  
|`_CRTDBG_MODE_DEBUG`|Zapíše zprávu do okna výstupu ladicího programu.|  
|`_CRTDBG_MODE_FILE`|Zapíše do popisovače souboru uživatelem zadané zprávy. [_Crtsetreportfile –](../../c-runtime-library/reference/crtsetreportfile.md) by měla být volána k definování konkrétní soubor nebo datový proud použít jako cíl.|  
|`_CRTDBG_MODE_WNDW`|Vytvoří okno se zprávou k zobrazení zprávy spolu s `Abort`, `Retry`, a `Ignore` tlačítka.|  
|`_CRTDBG_REPORT_MODE`|Vrátí `reportMode` pro zadaný `reportType`:<br /><br /> 1   `_CRTDBG_MODE_FILE`<br /><br /> 2   `_CRTDBG_MODE_DEBUG`<br /><br /> 4   `_CRTDBG_MODE_WNDW`|  
  
 Každý typ sestavy mohou být oznámeny vůbec pomocí jednu, dvě nebo tři režimy nebo žádný. Proto je možné, že více než jeden cílový definované pro typ jednu sestavu. Například následující fragment kódu způsobí selhání vyhodnocení se mají odeslat do obou okna zpráv ladění a do `stderr`:  
  
```  
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );  
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );  
```  
  
 Kromě toho vytváření sestav režim nebo režim pro každý typ sestavy lze samostatně řídit. Například je možné určit, že `reportType` z `_CRT_WARN` se odesílá do řetězec výstup ladění, při `_CRT_ASSERT` se zobrazí pomocí okno zprávy ladění a odesílají do `stderr`, jako dříve ilustrované.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportMode`|\<crtdbg.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
 **Knihovny:** ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)