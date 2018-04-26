---
title: fwrite – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b91ad6efe0573bc469e0752ed27978b12018ee7
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
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
Maximální počet položek, které mají být zapsána.

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

**fwrite –** vrátí počet úplné položek ve skutečnosti zapisovat, což může být menší než *počet* Pokud dojde k chybě. Navíc pokud dojde k chybě, nelze určit indikátoru pozice souboru. Pokud má jedna *datového proudu* nebo *vyrovnávací paměti* je ukazatel s hodnotou null, nebo pokud je v režimu Unicode je zadán lichý počet bajtů, které mají být zapsána, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

**Fwrite –** funkce zapíše až *počet* položek, z *velikost* délka, z *vyrovnávací paměti* k výstupu *datového proudu*. Ukazatele souboru přidružené *datového proudu* (pokud existuje) se zvýší o počet skutečně zapsaných bajtů. Pokud *datového proudu* je otevřen v režimu textových každý konce řádku nahradí znak-konce - pár konce řádku. Pokud chcete nahrazení nemá žádný vliv na návratovou hodnotu.

Když *datového proudu* je otevřen v režimu převodu znakové sady Unicode – například pokud *datového proudu* je otevřen voláním **fopen –** a použití režimu parametr, který zahrnuje **ccs = Znakové sady UNICODE**, **ccs = UTF-16LE**, nebo **ccs = UTF-8**, nebo pokud změnit režim do režimu převodu znakové sady Unicode pomocí **_setmode –** a režim parametr, který zahrnuje **_O_WTEXT**, **_O_U16TEXT**, nebo **_O_U8TEXT**–*vyrovnávací paměti* interpretována jako ukazatel na pole **wchar_t** obsahující data ve formátu UTF-16. Pokus o zápis lichý počet bajtů v tomto režimu způsobí, že chyba ověření parametru.

Tato funkce zamkne volající vlákno, proto je bezpečné pro přístup z více vláken. Bez uzamčení verze, najdete v části **_fwrite_nolock –**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fread –](fread.md).

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
