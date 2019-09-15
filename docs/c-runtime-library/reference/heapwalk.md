---
title: _heapwalk
ms.date: 11/04/2016
api_name:
- _heapwalk
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapwalk
- _heapwalk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
ms.openlocfilehash: 8dc7ee9335f227bde93a414748ff70b165c44f8d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954779"
---
# <a name="_heapwalk"></a>_heapwalk

Projde haldu a vrátí informace o další položce.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime s výjimkou sestavení ladění. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _heapwalk( _HEAPINFO *entryinfo );
```

### <a name="parameters"></a>Parametry

*entryinfo*<br/>
Vyrovnávací paměť obsahující informace o haldě.

## <a name="return-value"></a>Návratová hodnota

**_heapwalk** vrátí jednu z následujících celočíselných konstant manifestu definovaných ve typu. h.

|Návratová hodnota|Význam|
|-|-|
|**_HEAPBADBEGIN**| Informace počáteční hlavičky jsou neplatné nebo se nenašly.|
|**_HEAPBADNODE**| Byl nalezen poškozený nebo chybný uzel haldy.|
|**_HEAPBADPTR**| Pole **_pentry** struktury **_HEAPINFO** neobsahuje platný ukazatel na haldu nebo *entryinfo* je ukazatel s hodnotou null.|
|**_HEAPEND**| Konec haldy byl úspěšně dosažen.|
|**_HEAPEMPTY**| Halda není inicializovaná.|
|**_HEAPOK**| Zatím žádné chyby; *entryinfo* se aktualizuje o informace o další položce haldy.|

Kromě toho, pokud dojde k chybě, **_heapwalk** nastaví **errno** na **ENOSYS**.

## <a name="remarks"></a>Poznámky

Funkce **_heapwalk** pomáhá ladit problémy související s haldou v programech. Funkce projde haldou, projde jednu položku pro každé volání a vrátí ukazatel na strukturu typu **_HEAPINFO** , která obsahuje informace o další položce haldy. Typ **_HEAPINFO** definovaný v typu. h obsahuje následující prvky.

|Pole|Význam|
|-|-|
|`int *_pentry`|Ukazatel na položku haldy.|
|`size_t _size`|Velikost položky haldy.|
|`int _useflag`|Příznak, který označuje, zda je položka haldy používána.|

Volání **_heapwalk** , které vrací **_HEAPOK** , ukládá velikost položky v poli **_Size** a nastaví pole **_useflag** na **_FREEENTRY** nebo **_USEDENTRY** (obě jsou konstanty definované v systému. h). Chcete-li získat tyto informace o první položce v haldě, předejte **_heapwalk** ukazatel na strukturu **_HEAPINFO** , jejíž člen **_pentry** je **null**. Pokud operační systém nepodporuje **_heapwalk**(například Windows 98), funkce vrátí **_HEAPEND** a nastaví **errno** na **ENOSYS**.

Tato funkce ověří svůj parametr. Pokud je *entryinfo* ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **_HEAPBADPTR**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_heapwalk**|\<. h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_heapwalk.c

// This program "walks" the heap, starting
// at the beginning (_pentry = NULL). It prints out each
// heap entry's use, location, and size. It also prints
// out information about the overall state of the heap as
// soon as _heapwalk returns a value other than _HEAPOK
// or if the loop has iterated 100 times.

#include <stdio.h>
#include <malloc.h>

void heapdump(void);

int main(void)
{
    char *buffer;

    heapdump();
    if((buffer = (char *)malloc(59)) != NULL)
    {
        heapdump();
        free(buffer);
    }
    heapdump();
}

void heapdump(void)
{
    _HEAPINFO hinfo;
    int heapstatus;
    int numLoops;
    hinfo._pentry = NULL;
    numLoops = 0;
    while((heapstatus = _heapwalk(&hinfo)) == _HEAPOK &&
          numLoops < 100)
    {
        printf("%8s block at %Fp of size %4.4X\n",
               (hinfo._useflag == _USEDENTRY ? "USED" : "FREE"),
               hinfo._pentry, hinfo._size);
        numLoops++;
    }

    switch(heapstatus)
    {
    case _HEAPEMPTY:
        printf("OK - empty heap\n");
        break;
    case _HEAPEND:
        printf("OK - end of heap\n");
        break;
    case _HEAPBADPTR:
        printf("ERROR - bad pointer to heap\n");
        break;
    case _HEAPBADBEGIN:
        printf("ERROR - bad start of heap\n");
        break;
    case _HEAPBADNODE:
        printf("ERROR - bad node in heap\n");
        break;
    }
}
```

```Output
    USED block at 00310650 of size 0100
    USED block at 00310758 of size 0800
    USED block at 00310F60 of size 0080
    FREE block at 00310FF0 of size 0398
    USED block at 00311390 of size 000D
    USED block at 003113A8 of size 00B4
    USED block at 00311468 of size 0034
    USED block at 003114A8 of size 0039
...
    USED block at 00312228 of size 0010
    USED block at 00312240 of size 1000
    FREE block at 00313250 of size 1DB0
OK - end of heap
```

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapchk](heapchk.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
