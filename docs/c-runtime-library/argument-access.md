---
title: Přístup k argumentu
ms.date: 04/04/2018
f1_keywords:
- c.arguments
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
ms.openlocfilehash: 8107cffa6a2da41c38b116b2e3fe36adf6ac945f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470405"
---
# <a name="argument-access"></a>Přístup k argumentu

**Va_arg**, **va_end**, a **va_start** makra poskytují přístup k argumenty funkce, pokud počet argumentů proměnné. Tato makra jsou definována v \<stdarg.h > z důvodu kompatibility ANSI/ISO C a v \<souboru varargs.h > z důvodu kompatibility s V systému UNIX.

## <a name="argument-access-macros"></a>Přístup k argumentu makra

|– Makro|Použití|
|-----------|-------------------------------|
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Načíst ze seznamu argumentů|
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Resetujte ukazatel|
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Nastavte ukazatel na začátku seznamu argumentů|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)
