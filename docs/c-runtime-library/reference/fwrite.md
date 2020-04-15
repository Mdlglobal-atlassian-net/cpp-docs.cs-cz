---
title: fwrite
ms.date: 4/2/2020
api_name:
- fwrite
- _o_fwrite
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: a5bd6da3c8d16189f7ff0db744901e03513acc21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345394"
---
# <a name="fwrite"></a>fwrite

Zapisuje data do datového proudu.

## <a name="syntax"></a>Syntaxe

```C
size_t fwrite(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Ukazatel na data, která mají být zapsána.

*Velikost*<br/>
Velikost položky v bajtech.

*Počet*<br/>
Maximální počet položek, které mají být zapsány.

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

**fwrite** vrátí počet zcela zapsaných položek, které mohou být menší než *počet,* pokud dojde k chybě. Také pokud dojde k chybě, indikátor pozice souboru nelze určit. Pokud je *datový proud* nebo *vyrovnávací paměť* ukazatelem null nebo pokud je v režimu Unicode zadán lichý počet bajtů, který má být zapsán, funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí 0.

## <a name="remarks"></a>Poznámky

Funkce **fwrite** zapisuje do *počtu* položek, *o velikosti* délky, z *vyrovnávací paměti* do výstupního *datového proudu*. Ukazatel souboru přidružený k *datovému proudu* (pokud existuje) se zintáží o počet skutečně zapsaných bajtů. Pokud je *datový proud* otevřen v textovém režimu, každý řádek je nahrazen dvojicí datového kanálu vozíku. Nahrazení nemá žádný vliv na vrácenou hodnotu.

Při otevření *datového proudu* v režimu překladu Unicode – například pokud je *datový proud* otevřen voláním **fopen** a pomocí parametru režimu, který zahrnuje **ccs=UNICODE**, **ccs=UTF-16LE**nebo **ccs=UTF-8**, nebo pokud je režim změněn na režim překladu Unicode pomocí **_setmode** a parametru režimu, který zahrnuje **_O_WTEXT**, **_O_U16TEXT**nebo **_O_U8TEXT**–*vyrovnávací paměť* je interpretována jako ukazatel na pole **wchar_t,** které obsahuje data UTF-16. Pokus o zápis lichého počtu bajtů v tomto režimu způsobí chybu ověření parametru.

Protože tato funkce uzamkne volající vlákno, je bezpečné pro přístup z více vláken. Neblokovací verze viz **_fwrite_nolock**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [fread](fread.md).

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
