---
title: DLL – načítání kódů výjimek (CC++/)
ms.date: 11/19/2019
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
ms.openlocfilehash: f557fe736f45f8c3f5411d076a0be18f1d1b670e
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74243855"
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

K vyvolaným kódům výjimek patří hodnoty Standard VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) a VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). Výjimka předá ukazatel na strukturu **DelayLoadInfo** v hodnotě LPDWORD, kterou lze načíst **GetExceptionInformation** ve struktuře [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) , v poli ExceptionInformation [0].

Kromě toho, pokud jsou v poli grAttrs nastaveny nesprávné bity, je vyvolána výjimka ERROR_INVALID_PARAMETER. Tato výjimka je pro všechny záměry a účely závažná.

Další informace najdete v tématu [Struktura a definice konstant](structure-and-constant-definitions.md) .

## <a name="see-also"></a>Viz také:

[Zpracování chyb a oznámení](error-handling-and-notification.md)
