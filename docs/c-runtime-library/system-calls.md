---
title: Systémová volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.system
dev_langs:
- C++
helpviewer_keywords:
- Windows [C++], system calls
- system calls
ms.assetid: 0255f2ec-a5a0-487e-8b09-9dad001d81ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 648b0e1addd509652ba67e09d32dbdd060f29e87
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074419"
---
# <a name="system-calls"></a>Systémová volání

Následující funkce jsou volání operačního systému Windows.

## <a name="system-call-functions"></a>Volání funkce systému

|Funkce|Použití|
|--------------|---------|
|[_findclose](../c-runtime-library/reference/findclose.md)|Uvolnit prostředky z předchozí operace find|
|[_findfirst, _findfirst32 –, _findfirst64 –, _findfirsti64 –, _findfirst32i64 –, _findfirst64i32 –, _wfindfirst –, _wfindfirst32 –, _wfindfirst64 –, _wfindfirsti64 –, _wfindfirst32i64 –, _wfindfirst64i32 –](../c-runtime-library/reference/findfirst-functions.md)|Najít soubor pomocí zadaných atributů|
|[_findnext, _findnext32 –, _findnext64 –, _findnexti64 –, _findnext32i64 –, _findnext64i32 –, _wfindnext –, _wfindnext32 –, _wfindnexti64 –, _wfindnext64 –, _wfindnexti64 –](../c-runtime-library/reference/findnext-functions.md)|Najít další soubor pomocí zadaných atributů|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Zpracování souborů](../c-runtime-library/file-handling.md)<br/>
[Ovládací prvek adresáře](../c-runtime-library/directory-control.md)<br/>
[I/O nízké úrovně](../c-runtime-library/low-level-i-o.md)<br/>
