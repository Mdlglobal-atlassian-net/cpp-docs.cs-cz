---
title: Typ kontroly (CRT) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.types
dev_langs:
- C++
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29cc7366385c187b1324f4d7e6b896a19ac86074
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041269"
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