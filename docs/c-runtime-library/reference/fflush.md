---
title: fflush
ms.date: 4/2/2020
api_name:
- fflush
- _o_fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: 401f715e99e6304f0726c8b9c96a71d9582dbc1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347171"
---
# <a name="fflush"></a>fflush

Vyprázdní datový proud.

## <a name="syntax"></a>Syntaxe

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

**Fflush** vrátí hodnotu 0, pokud byla vyrovnávací paměť úspěšně vyprázdněna. Hodnota 0 je také vrácena v případech, ve kterých zadaný datový proud nemá žádnou vyrovnávací paměť nebo je otevřen pouze pro čtení. Vrácená hodnota **EOF** označuje chybu.

> [!NOTE]
> Pokud **fflush** vrátí **EOF**, data mohou být ztraceny z důvodu selhání zápisu. Při nastavování obslužné rutiny kritické chyby je nejbezpečnější vypnout ukládání do vyrovnávací paměti pomocí funkce **setvbuf** nebo použít rutiny vstupně-dovodů nižší úrovně, jako jsou **_open**, **_close**a **_write** místo funkcí vstupně-za datových proudů.

## <a name="remarks"></a>Poznámky

Funkce **fflush** vyprázdní *datový proud*. Pokud byl datový proud otevřen v režimu zápisu nebo byl otevřen v režimu aktualizace a poslední operace byla zápis, obsah vyrovnávací paměti datového proudu jsou zapsány do základního souboru nebo zařízení a vyrovnávací paměti je zahozena. Pokud byl datový proud otevřen v režimu čtení nebo pokud datový proud nemá žádnou vyrovnávací paměť, volání **fflush** nemá žádný vliv a všechny vyrovnávací paměti je zachována. Volání **fflush** neguje účinek jakékoli předchozí volání **ungetc** pro datový proud. Datový proud zůstane po volání otevřený.

Pokud *datový proud* je **NULL**, chování je stejný jako volání **fflush** na každém otevřeném datovém proudu. Všechny datové proudy otevřené v režimu zápisu a všechny datové proudy otevřené v režimu aktualizace, kde poslední operace byla zápis jsou vyprázdněny. Volání nemá žádný vliv na jiné datové proudy.

Vyrovnávací paměti jsou obvykle udržovány operačním systémem, který určuje optimální čas pro automatické zápis dat na disk: při zaplnění vyrovnávací paměti, při zavření datového proudu nebo při ukončení programu normálně bez zavření datového proudu. Funkce potvrzení na disk v knihovně za běhu umožňuje zajistit, aby byla důležitá data zapsána přímo na disk, nikoli do vyrovnávacích pamětí operačního systému. Bez přepisování existujícího programu můžete tuto funkci povolit propojením souborů objektů programu s souborem COMMODE.OBJ. Ve výsledném spustitelném souboru volání **_flushall** zapsat obsah všech vyrovnávacích pamětí na disk. Pouze **_flushall** a **fflush** jsou ovlivněny COMMODE.OBJ.

Informace o řízení funkce potvrzení na disk naleznete v [tématu Stream I/O](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md)a [_fdopen](fdopen-wfdopen.md).

Tato funkce uzamkne volající vlákno a je proto bezpečná pro přístup z více vláken. O verzi bez zamykání viz **_fflush_nolock**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fflush.c
// Compile with: cl /W4 crt_fflush.c
// This sample gets a number from the user, then writes it to a file.
// It ensures the write isn't lost on crash by calling fflush.
#include <stdio.h>

int * crash_the_program = 0;

int main(void)
{
    FILE * my_file;
    errno_t err = fopen_s(&my_file, "myfile.txt", "w");
    if (my_file && !err)
    {
        printf("Write a number: ");

        int my_number = 0;
        scanf_s("%d", &my_number);

        fprintf(my_file, "User selected %d\n", my_number);

        // Write data to a file immediately instead of buffering.
        fflush(my_file);

        if (my_number == 5)
        {
            // Without using fflush, no data was written to the file
            // prior to the crash, so the data is lost.
            *crash_the_program = 5;
        }

        // Normally, fflush is not needed as closing the file will write the buffer.
        // Note that files are automatically closed and flushed during normal termination.
        fclose(my_file);
    }
    return 0;
}
```

```Input
5
```

```myfile.txt
User selected 5
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
