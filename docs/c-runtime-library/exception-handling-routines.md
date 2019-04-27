---
title: Rutiny zpracování výjimek
ms.date: 11/04/2016
f1_keywords:
- c.exceptions
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
ms.openlocfilehash: 8def356793906074e6fc4b8d7a139ce1915a5f9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344301"
---
# <a name="exception-handling-routines"></a>Rutiny zpracování výjimek

Funkce zpracování výjimek jazyka C++ použijte k zotavení z neočekávaných událostí během provádění programu.

## <a name="exception-handling-functions"></a>Funkce pro zpracování výjimek

|Funkce|Použití|
|--------------|---------|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Win32 zpracování výjimek (strukturované výjimky jazyka C) jako C++ typu výjimky|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Nainstalujte si vlastní rutinu ukončení, které jsou volány **ukončit**|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Nainstalovat vlastní funkci ukončení má být volána **neočekávané**|
|[ukončit](../c-runtime-library/reference/terminate-crt.md)|Volá automaticky za určitých okolností se po vyvolání výjimky. **Ukončit** volání funkce **přerušit** nebo funkce, které zadáte pomocí **set_terminate**|
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|Volání **ukončit** nebo funkce, které zadáte pomocí **set_unexpected**. **Neočekávané** funkce se nepoužívá v aktuální implementaci zpracování výjimek C++ společnosti Microsoft|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
