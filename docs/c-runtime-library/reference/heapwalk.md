---
title: _heapwalk
ms.date: 11/04/2016
apiname:
- _heapwalk
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- heapwalk
- _heapwalk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
ms.openlocfilehash: cc2a49d9032746cc6c82c9dc401fc96baabbe2e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454896"
---
# <a name="heapwalk"></a>_heapwalk

Projde haldu a vrátí informace o další položce.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime s výjimkou v sestaveních ladění. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _heapwalk( _HEAPINFO *entryinfo );
```

### <a name="parameters"></a>Parametry

*entryinfo*<br/>
Vyrovnávací paměť obsahující informace o haldě.

## <a name="return-value"></a>Návratová hodnota

**_heapwalk** vrátí jednu z následujících konstant manifestu celé číslo definovaných v Malloc.h.

|Návratová hodnota|Význam|
|-|-|
|**_HEAPBADBEGIN –**| Počáteční informace hlavičky jsou neplatné nebo nebyly nalezeny.|
|**_HEAPBADNODE –**| Haldy poškozený nebo nalezený špatný uzel.|
|**_HEAPBADPTR –**| **_Pentry** pole **_heapinfo –** struktury neobsahuje platný ukazatel do haldy nebo *entryinfo* je ukazatel s hodnotou null.|
|**_HEAPEND –**| Úspěšně bylo dosaženo konce haldy.|
|**_HEAPEMPTY –**| Halda neinicializována.|
|**_HEAPOK –**| Zatím; žádné chyby *entryinfo* se aktualizuje informacemi o další položce haldy.|

Kromě toho, pokud dojde k chybě **_heapwalk** nastaví **errno** k **ENOSYS**.

## <a name="remarks"></a>Poznámky

**_Heapwalk** funkce umožňuje ladění problémů souvisejících s haldou v aplikacích. Funkce projde haldu, procházení jednu položku na jedno zavolání a vrátí ukazatel na strukturu typu **_heapinfo –** , který obsahuje informace o další položce haldy. **_Heapinfo –** typ definovaný v souboru Malloc.h, obsahuje následující prvky.

|Pole|Význam|
|-|-|
|`int *_pentry`|Ukazatel vstupu haldy.|
|`size_t _size`|Velikost záznamu haldy.|
|`int _useflag`|Příznak, který označuje, zda je položka haldy používá.|

Volání **_heapwalk** , která vrací **_heapok –** ukládá velikost zadání v **_velikost** pole a nastaví **_useflag** buď pole **_FREEENTRY** nebo **_USEDENTRY** (obojí jsou konstanty definované v Malloc.h). Pro získání těchto informací o první položce v haldě, předejte **_heapwalk** ukazatel **_heapinfo –** strukturu, jejíž **_pentry** člen je **NULL** . Pokud operační systém nepodporuje **_heapwalk**(například Windows 98), funkce vrátí **_heapend –** a nastaví **errno** k **ENOSYS**.

Tato funkce ověřuje svůj parametr. Pokud *entryinfo* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **_heapbadptr –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_heapwalk**|\<malloc.h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
