---
title: Zacházení s vyrovnávací pamětí
ms.date: 04/04/2018
f1_keywords:
- c.memory
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
ms.openlocfilehash: e8a449cbfa6a52ccc2346e2215ce187c09d677e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590499"
---
# <a name="buffer-manipulation"></a>Zacházení s vyrovnávací pamětí

Pomocí těchto rutin pro práci s oblastí paměti na základě bajt po bajtu.

## <a name="buffer-manipulation-routines"></a>Rutiny zacházení s vyrovnávací pamětí

|Rutina|Použití|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|Kopírování znaků z jedné vyrovnávací paměti do druhého, dokud se daný znak nebo zadaný počet znaků, které se zkopírovala|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Vrátí ukazatel na první výskyt, v rámci zadaný počet znaků, z daný znak ve vyrovnávací paměti|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Porovnání několika určenými znaky ze dvou vyrovnávacích pamětí|
|[memcpy wmemcpy –](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s – wmemcpy_s –](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Kopírování zadaný počet znaků z jedné vyrovnávací paměti do jiného|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Porovnání několika určenými znaky ze dvou vyrovnávacích pamětech bez ohledu na případ|
|[memmove wmemmove –](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s – wmemmove_s –](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Kopírování zadaný počet znaků z jedné vyrovnávací paměti do jiného|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Použijte zadaný znak inicializovat zadaný počet bajtů ve vyrovnávací paměti|
|[_swab](../c-runtime-library/reference/swab.md)|Prohození bajtů dat a jejich uložení v zadaném umístění|

Pokud zdrojové a cílové oblasti překrývají, pouze **memmove** je zaručeno zkopírovat úplné zdrojové správně.

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)
