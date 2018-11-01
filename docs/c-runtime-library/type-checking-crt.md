---
title: Kontrola typu (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.types
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
ms.openlocfilehash: fd892426bb7301acad7ce2a93430e52f25e7c9b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626088"
---
# <a name="type-checking-crt"></a>Kontrola typu (CRT)

Kompilátor provádí omezený typ kontroly na funkce, které můžete provést proměnný počet argumentů, následujícím způsobem:

|Volání funkce|Argumenty typu zaškrtnuto|
|-------------------|-----------------------------|
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|První argument (formátovací řetězec)|
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|První dva argumenty (soubor nebo vyrovnávací paměti a formát řetězce)|
|`_snprintf_s`|První tři argumenty (soubor nebo vyrovnávací paměti, počtu a formátovací řetězec)|
|`_open`|První dva argumenty (cesta a `_open` příznak)|
|`_sopen_s`|První tři argumenty (cesta, `_open` příznak a režim sdílení)|
|`_execl`, `_execle`, `_execlp`, `_execlpe`|První dva argumenty (cestu a první argument ukazatele)|
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|První tři argumenty (příznak režimu, cestu a první argument ukazatele)|

Kompilátor provádí stejný typ omezenou kontrolu širokého znaku protějšky těchto funkcí.

## <a name="see-also"></a>Viz také

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)