---
title: Systémová volání
ms.date: 11/04/2016
f1_keywords:
- c.system
helpviewer_keywords:
- Windows [C++], system calls
- system calls
ms.assetid: 0255f2ec-a5a0-487e-8b09-9dad001d81ed
ms.openlocfilehash: 2d86a35718ab6c1aab941149c9707004b1532d24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304525"
---
# <a name="system-calls"></a>Systémová volání

Následující funkce jsou volání operačního systému Windows.

## <a name="system-call-functions"></a>Volání funkce systému

|Funkce|Použití|
|--------------|---------|
|[_findclose](../c-runtime-library/reference/findclose.md)|Uvolnit prostředky z předchozí operace find|
|[_findfirst, _findfirst32, _findfirst64, _findfirsti64, _findfirst32i64, _findfirst64i32, _wfindfirst, _wfindfirst32, _wfindfirst64, _wfindfirsti64, _wfindfirst32i64, _wfindfirst64i32](../c-runtime-library/reference/findfirst-functions.md)|Najít soubor pomocí zadaných atributů|
|[_findnext, _findnext32, _findnext64, _findnexti64, _findnext32i64, _findnext64i32, _wfindnext, _wfindnext32, _wfindnexti64, _wfindnext64, _wfindnexti64](../c-runtime-library/reference/findnext-functions.md)|Najít další soubor pomocí zadaných atributů|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Zpracování souborů](../c-runtime-library/file-handling.md)<br/>
[Ovládací prvek adresáře](../c-runtime-library/directory-control.md)<br/>
[I/O nízké úrovně](../c-runtime-library/low-level-i-o.md)<br/>
