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
ms.openlocfilehash: bb5aecc2b47aa8e88666f42d8022395bf99fd85e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747680"
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

## <a name="see-also"></a>Viz také:

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
