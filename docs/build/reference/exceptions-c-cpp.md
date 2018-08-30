---
title: Výjimky (C/C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
dev_langs:
- C++
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40a3a9e1cf1384603d6b7d95fa5960e951f932ef
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216880"
---
# <a name="exceptions-cc"></a>Výjimky (C/C++)
Dva kódy výjimek může být vyvolána, pokud nedojde k selhání:  
  
-   Pro **LoadLibrary** selhání  
  
-   Pro **GetProcAddress** selhání  
  
 Tady je informace o výjimce:  
  
```  
//  
// Exception information  
//  
#define FACILITY_VISUALCPP  ((LONG)0x6d)  
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)  
```  
  
 Kódy výjimek vyvolána jsou standardní VcppException (error_severity_error –, error_mod_not_found –) a hodnoty VcppException (error_severity_error –, ERROR_PROC_NOT_FOUND). Předává ukazatel na výjimku **DelayLoadInfo** struktury v LPDWORD hodnotu, která je možné načíst podle **GetExceptionInformation** v [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record) Struktura, ExceptionInformation [0] pole.  
  
 Kromě toho pokud jsou v poli grAttrs nesprávné bity, ERROR_INVALID_PARAMETER je vyvolána výjimka. Tato výjimka je pro veškeré záměry a úmysly, závažná.  
  
 Zobrazit [struktura a definice konstant](../../build/reference/structure-and-constant-definitions.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb a oznámení](../../build/reference/error-handling-and-notification.md)