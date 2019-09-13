---
title: fflush
ms.date: 09/11/2019
api_name:
- fflush
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
ms.openlocfilehash: 966ff5622faaccd2d9e501b39da99b010e841c22
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940948"
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

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

**fflush** vrátí hodnotu 0, pokud byla vyrovnávací paměť úspěšně vyprázdněna. Hodnota 0 se také vrátí v případech, kdy zadaný datový proud nemá vyrovnávací paměť, nebo je otevřen pouze pro čtení. Návratová hodnota **EOF** značí chybu.

> [!NOTE]
> Pokud **fflush** vrátí **EOF**, data mohla být ztracena z důvodu chyby zápisu. Při nastavování kritické obslužné rutiny chyb je nejbezpečnější zapnout vyrovnávací paměť pomocí funkce **setvbuf –** nebo použít rutiny i/o nízké úrovně, jako je **_open**, **_close**a **_Write** namísto funkcí vstupu/výstupu datového proudu.

## <a name="remarks"></a>Poznámky

Funkce **fflush** vyprázdní *datový proud*streamu. Pokud byl datový proud otevřen v režimu zápisu nebo byl otevřen v režimu aktualizace a poslední operace byla zápis, obsah vyrovnávací paměti datového proudu je zapsán do podkladového souboru nebo zařízení a vyrovnávací paměť je zahozena. Pokud byl datový proud otevřen v režimu čtení, nebo pokud datový proud nemá vyrovnávací paměť, volání **fflush** nemá žádný účinek a veškerá vyrovnávací paměť zůstane zachována. Volání **fflush** negace efektu jakéhokoli předchozího volání **ungetc –** pro datový proud. Datový proud zůstane otevřený po volání.

Pokud má *datový proud* **hodnotu null**, chování je stejné jako volání **fflush** v každém otevřeném streamu. Všechny datové proudy otevřené v režimu zápisu a všechny datové proudy otevřené v režimu aktualizace, kde byla poslední operace zápis vyprázdněna. Volání nemá žádný vliv na jiné streamy.

Vyrovnávací paměti jsou obvykle udržovány operačním systémem, který určuje optimální čas pro automatické zápis dat na disk: Pokud je vyrovnávací paměť plná, když je datový proud zavřen nebo když se program ukončí normálně bez zavření datového proudu. Funkce Commit-to-disk v běhové knihovně vám umožní zajistit, aby byla kritická data zapisována přímo na disk, nikoli do vyrovnávací paměti operačního systému. Bez přepisu stávajícího programu můžete tuto funkci povolit propojením souborů objektů programu pomocí COMMODE. OBJ. Ve výsledném spustitelném souboru volání **_flushall** zapisují obsah všech vyrovnávacích pamětí na disk. COMMODE. OBJ má vliv pouze na **_flushall** a **fflush** .

Informace o řízení funkce potvrzení na disk najdete v tématu [streamování I/O](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md)a [_fdopen](fdopen-wfdopen.md).

Tato funkce zamkne volající vlákno a je proto bezpečná pro přístup z více vláken. Neuzamykání verze naleznete v tématu **_fflush_nolock**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
