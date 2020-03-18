---
title: Zacházení s vyrovnávací pamětí
ms.date: 04/04/2018
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
ms.openlocfilehash: a79bfdb33d2bff5e18c916a2e116ab03251afdf1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443598"
---
# <a name="buffer-manipulation"></a>Zacházení s vyrovnávací pamětí

Pomocí těchto rutin můžete pracovat s oblastmi paměti na základě bajtů.

## <a name="buffer-manipulation-routines"></a>Rutiny manipulace s vyrovnávací pamětí

|Rutina|Použití|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|Kopírovat znaky z jedné vyrovnávací paměti do druhé, dokud daný znak nebo daný počet znaků nebyl zkopírován|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Vrátí ukazatel na první výskyt, který je v zadaném počtu znaků, z daného znaku v bufferu.|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Porovnat zadaný počet znaků ze dvou vyrovnávacích pamětí|
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s, wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Kopírovat zadaný počet znaků z jedné vyrovnávací paměti do druhé|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Porovnat zadaný počet znaků ze dvou vyrovnávacích pamětí bez ohledu na velikost písmen|
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s, wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Kopírovat zadaný počet znaků z jedné vyrovnávací paměti do druhé|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Použijte daný znak k inicializaci zadaného počtu bajtů ve vyrovnávací paměti.|
|[_swab](../c-runtime-library/reference/swab.md)|Prohození bajtů dat a jejich uložení v zadaném umístění|

Když se zdrojové a cílové oblasti překrývají, je zaručeno správné zkopírování úplného zdroje pouze **memmove** .

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)
