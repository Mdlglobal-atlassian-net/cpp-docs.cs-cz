---
title: Výjimky (C/C++)
ms.date: 11/04/2016
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
ms.openlocfilehash: 360acba73278902cc40d10fd975011488742a7a2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492921"
---
# <a name="exceptions-cc"></a>Výjimky (C/C++)

Pokud dojde k chybám, lze vyvolat dva kódy výjimek:

- Pro chybu **LoadLibrary**

- Pro chybu **GetProcAddress**

Tady jsou informace o výjimce:

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

Vyvolání kódů výjimek jsou standardní hodnoty VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) a VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). Výjimka předá ukazatel na strukturu **DelayLoadInfo** v hodnotě LPDWORD, kterou lze načíst **GetExceptionInformation** v poli struktury [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) , ExceptionInformation [0].

Kromě toho, pokud jsou nesprávné bity nastaveny v poli grAttrs, je vyvolána výjimka ERROR_INVALID_PARAMETER. Tato výjimka je pro všechny záměry a účely závažná.

Další informace najdete v tématu [Struktura a definice konstant](structure-and-constant-definitions.md) .

## <a name="see-also"></a>Viz také:

[Zpracování chyb a oznámení](error-handling-and-notification.md)
