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
ms.openlocfilehash: b4d6b9ce4fb66ee545f52946e28e4984d9e4f924
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287544"
---
# <a name="fwrite"></a>fwrite

Zapíše data do datového proudu.

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
Ukazatel na data, která má být proveden zápis.

*Velikost*<br/>
Velikost položky v bajtech.

*Počet*<br/>
Maximální počet položek má být proveden zápis.

*stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

**fwrite –** vrátí číslo úplné aktuálně zapsaných položky, které mohou být menší než *počet* Pokud dojde k chybě. Navíc pokud dojde k chybě, nelze určit Indikátor pozice v souboru. Pokud *stream* nebo *vyrovnávací paměti* je ukazatel s hodnotou null, nebo pokud v režimu Unicode je zadán lichý počet bajtů, které mají být zapsána, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

**Fwrite –** funkce zapíše *počet* položky, z *velikost* délka, z *vyrovnávací paměti* do výstupu *stream*. Ukazatel na soubor přidružený k *stream* (pokud existuje) je zvýšen o počet aktuálně zapsaných bajtů. Pokud *stream* je otevřen v textovém režimu, každý znak odřádkování nahradí návrat na začátek řádku – znak odřádkování pár. Pokud chcete nahrazení nemá žádný vliv na návratovou hodnotu.

Při *stream* je otevřen v režimu Unicode překladu – například pokud *datového proudu* otevření voláním **fopen –** a pomocí režimu parametru, která zahrnuje **ccs = UNICODE**, **ccs = UTF-16LE**, nebo **ccs = UTF-8**, nebo pokud je režim změnit na režim překladu Unicode pomocí **_setmode** a režim parametr, který zahrnuje **_O_WTEXT**, **_O_U16TEXT**, nebo **_O_U8TEXT**–*vyrovnávací paměti* je interpretován jako ukazatel na pole **wchar_t** , který obsahuje data UTF-16. Pokus o zápis lichý počet bajtů v tomto režimu způsobí chybu ověření parametru.

Protože tato funkce uzamkne volajícího vlákna, je bezpečná pro vlákno. Nezamykací verzi naleznete v tématu **_fwrite_nolock –**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fread –](fread.md).

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
