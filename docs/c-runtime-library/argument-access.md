---
title: Přístup k argumentu | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
f1_keywords:
- c.arguments
dev_langs:
- C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afef1300637f7a31755eb9408f9d33d9504475a1
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="argument-access"></a>Přístup k argumentu

**Va_arg –**, **va_end –**, a **va_start –** makra poskytnout přístup k argumenty funkce, pokud počet argumentů je proměnná. Tyto makra jsou definovány v \<stdarg.h > pro C na ANSI/ISO kompatibility a v \<varargs.h > pro kompatibilitu s V systému UNIX.

## <a name="argument-access-macros"></a>Přístup k argumentu makra

|– Makro|Použití|
|-----------|-------------------------------|
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Načtení argument ze seznamu|
|[va_end –](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Resetování ukazatele|
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Nastavit ukazatel na začátku seznamu argumentů|

## <a name="see-also"></a>Viz také

[Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)
