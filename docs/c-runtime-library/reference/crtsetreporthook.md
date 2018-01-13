---
title: "_Crtsetreporthook – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
dev_langs: C++
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4c1fb85ab41c02bb9f604f024f86ebb42706eeda
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtsetreporthook"></a>_CrtSetReportHook
Nainstaluje klienta definované funkce vytváření sestav tak, že zapojování do procesu vytváření sestav běhové ladění C (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_CRT_REPORT_HOOK _CrtSetReportHook(   
   _CRT_REPORT_HOOK reportHook   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `reportHook`  
 Nový klient definované generování sestav funkce připojí do běhu C ladění procesu generování sestav.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí předchozí klientský definované funkce vytváření sestav.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtSetReportHook`umožňuje aplikaci používat vlastní funkce vytváření sestav do ladicí běhové knihovny jazyka C reporting procesu. Výsledkem je, vždy, když [_crtdbgreport –](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) je volána k vygenerování sestavy ladění, je reporting funkce je volána nejprve aplikace. Tato funkce umožňuje aplikaci k provedení operací, jako je například filtrování sestavy ladění tak, aby se zaměřit na konkrétní přidělení typy nebo poslat zprávu cíle není k dispozici pomocí `_CrtDbgReport`. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtSetReportHook` jsou odebrány při předběžném zpracování.  
  
 Robustnější verzi `_CrtSetReportHook`, najdete v části [_crtsetreporthook2 –](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md).  
  
 `_CrtSetReportHook` Funkce nainstaluje nový klient definované reporting zadanou ve funkci `reportHook` a vrátí hák předchozí definované klienta. Následující příklad ukazuje, jak by měla být deklaraci háku klient definované sestavy:  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 kde `reportType` je typ sestavy ladění (`_CRT_WARN`, `_CRT_ERROR`, nebo `_CRT_ASSERT`), `message` je zpráva již sestavených ladění uživatele mají být obsažena v sestavě, a `returnValue` je hodnotu zadanou pomocí definované klienta vytváření sestav funkce, která má být vrácen podle `_CrtDbgReport`. Úplný popis typů sestav k dispozici, najdete v článku [_crtsetreportmode –](../../c-runtime-library/reference/crtsetreportmode.md) funkce.  
  
 Pokud funkci generování sestav definované klienta úplně zpracovává zprávy ladění tak, aby další vykazování se nevyžaduje, pak by měla vrátit funkce `TRUE`. Když funkce vrátí hodnotu `FALSE`, `_CrtDbgReport` je volána při generování sestav o ladění pomocí aktuální nastavení pro typ sestavy, režimu a souboru. Kromě toho zadáním `_CrtDbgReport` vrátit hodnotu v `returnValue`, aplikace můžete taky řídit, jestli zalomení ladění. Úplný popis jak nakonfigurovaný a vygenerovat sestavu ladění, najdete v části `_CrtSetReportMode`, [_crtsetreportfile –](../../c-runtime-library/reference/crtsetreportfile.md), a `_CrtDbgReport`.  
  
 Další informace o použití jiných podporující háku běhové funkce a psaní vlastního klienta definované funkce háku najdete v tématu [ladění zápis funkce háku](/visualstudio/debugger/debug-hook-function-writing).  
  
> [!NOTE]
>  Pokud vaše aplikace je kompilovat s `/clr` a vytváření sestav funkce je volána po aplikaci byl ukončen hlavní, modul CLR bude vyvolána výjimka, pokud žádné funkce CRT volá funkci generování sestav.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtSetReportHook`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_CrtGetReportHook](../../c-runtime-library/reference/crtgetreporthook.md)