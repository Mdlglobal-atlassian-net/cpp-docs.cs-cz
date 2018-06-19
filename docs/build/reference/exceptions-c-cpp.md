---
title: Výjimky (C/C++) | Microsoft Docs
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
ms.openlocfilehash: 819f9424b2439cc49517afe54d62a8ed4f06d22d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373384"
---
# <a name="exceptions-cc"></a>Výjimky (C/C++)
Dva kódy výjimek můžete vyvolá, když došlo k selhání:  
  
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
  
 Kódy výjimek vyvolána jsou standardní VcppException (error_severity_error –, error_mod_not_found –) a hodnoty VcppException (error_severity_error –, ERROR_PROC_NOT_FOUND). Ukazatel na předá výjimku **DelayLoadInfo** struktury LPDWORD hodnotu, která může načíst **GetExceptionInformation** v [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) Struktura pole ExceptionInformation [0].  
  
 Kromě toho pokud jsou v poli grAttrs nesprávný bits, ERROR_INVALID_PARAMETER je vyvolána výjimka. Tato výjimka se pro všechny úmyslům a účelům závažná.  
  
 V tématu [struktura a definice konstant](../../build/reference/structure-and-constant-definitions.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb a oznámení](../../build/reference/error-handling-and-notification.md)