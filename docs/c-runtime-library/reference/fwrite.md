---
title: fwrite
ms.date: 11/04/2016
apiname:
- fwrite
apilocation:
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
apitype: DLLExport
f1_keywords:
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: f05e39390f3a2d0ad41627f6aed1aecd77b57cca
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376060"
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

*vyrovnávací paměti*<br/>
Ukazatel na data, která mají být zapsána.

*hodnota*<br/>
Velikost položky (v bajtech)

*výpočtu*<br/>
Maximální počet položek, které mají být zapsány.

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

**fwrite** vrátí počet úplných položek, které jsou skutečně napsány, což může být menší než *počet* , pokud dojde k chybě. Také, pokud dojde k chybě, nelze určit ukazatel pozice souboru. Pokud je buď *datový proud* nebo *vyrovnávací paměť* ukazatel s hodnotou null, nebo pokud je v režimu Unicode uveden lichý počet bajtů k zápisu, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Funkce **fwrite** zapisuje do výstupního *datového proudu*až do *počtu* položek, jejichž délka je *Velikost* z *vyrovnávací paměti* . Ukazatel na soubor přidružený ke *streamu* (pokud existuje) se zvýší o počet skutečně zapsaných bajtů. Pokud je *datový proud* otevřený v textovém režimu, jednotlivé řádkové kanály se nahradí dvojicí kanálů návratového řádku. Náhrada nemá na vrácenou hodnotu žádný vliv.

Když je *datový proud* otevřen v režimu překladu Unicode – například pokud je *datový proud* otevřen pomocí volání **fopen** a pomocí parametru režimu, který zahrnuje **CCS = Unicode**, **CCS = UTF-16LE**nebo **CCS = UTF-8**, nebo pokud je režim změněno na režim překladu Unicode pomocí **_setmode** a parametr režimu, který obsahuje **_O_WTEXT**, **_O_U16TEXT**nebo **_O_U8TEXT**–*vyrovnávací paměť* je interpretována jako ukazatel na pole **wchar_t** , který obsahuje Data UTF-16. Pokus o zápis lichého počtu bajtů v tomto režimu způsobí chybu ověření parametru.

Vzhledem k tomu, že tato funkce zamkne volající vlákno, je bezpečný pro přístup z více vláken. Neuzamykání verze naleznete v tématu **_fwrite_nolock**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fread](fread.md).

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
