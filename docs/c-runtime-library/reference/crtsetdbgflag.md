---
title: _CrtSetDbgFlag
ms.date: 11/04/2016
api_name:
- _CrtSetDbgFlag
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CRTDBG_REPORT_FLAG
- _CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_EVERY_128_DF
- CRTDBG_CHECK_EVERY_1024_DF
- _CRTDBG_CHECK_EVERY_128_DF
- CrtSetDbgFlag
- CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_EVERY_1024_DF
- _CrtSetDbgFlag
- CRTDBG_REPORT_FLAG
helpviewer_keywords:
- _CRTDBG_CHECK_EVERY_16_DF macro
- CRTDBG_CHECK_EVERY_16_DF macro
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_ALLOC_MEM_DF macro
- CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_ALLOC_MEM_DF macro
- _CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_1024_DF macro
- CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_CHECK_EVERY_1024_DF macro
- _CrtSetDbgFlag function
- CrtSetDbgFlag function
- _CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: b5657ffb-6178-4cbf-9886-1af904ede94c
ms.openlocfilehash: 8506b593a579c8dd1791e56c320bd9d8e2ee9ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938618"
---
# <a name="_crtsetdbgflag"></a>_CrtSetDbgFlag

Načte nebo upraví stav příznaku **_crtDbgFlag** pro řízení chování přidělení Správce haldy ladění (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtSetDbgFlag(
   int newFlag
);
```

### <a name="parameters"></a>Parametry

*newFlag*<br/>
Nový stav pro **_crtDbgFlag**.

## <a name="return-value"></a>Návratová hodnota

Vrátí předchozí stav **_crtDbgFlag**.

## <a name="remarks"></a>Poznámky

Funkce **_CrtSetDbgFlag** umožňuje aplikaci řídit způsob, jakým Správce haldy ladění sleduje přidělení paměti úpravou bitových polí příznaku **_crtDbgFlag** . Nastavením bitů (zapnutí) může aplikace dát správci haldy ladění, aby provedl speciální operace ladění, včetně kontroly nevracení paměti při ukončení aplikace a vytváření sestav, pokud se nějaká najde, a simuluje podmínky nízké paměti určení, že uvolněné paměťové bloky by měly zůstat v propojeném seznamu haldy a ověřit integritu haldy kontrolou každého bloku paměti při každé žádosti o přidělení. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtSetDbgFlag** se během předběžného zpracování odeberou.

Následující tabulka uvádí bitová pole pro **_crtDbgFlag** a popisuje jejich chování. Vzhledem k tomu, že nastavení bitů vede ke zvýšení výstupu diagnostiky a snížení rychlosti provádění programu, tyto bity nejsou ve výchozím nastavení nastavené (vypnuté). Další informace o těchto bitových polích naleznete v tématu [funkce vytváření sestav o stavu haldy](/visualstudio/debugger/crt-debug-heap-details).

|Bitové pole|Výchozí|Popis|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|PNETE|PNETE Povolte přidělení haldy ladění a použití identifikátorů typu blok paměti, jako je **_CLIENT_BLOCK**. ZAOKROUHL Přidejte nové přidělení do propojeného seznamu haldy, ale nastavte typ bloku na **_IGNORE_BLOCK**.<br /><br /> Lze také kombinovat s libovolnými makry kontroly frekvence haldy.|
|**_CRTDBG_CHECK_ALWAYS_DF**|OFF|PNETE Zavolejte [_CrtCheckMemory](crtcheckmemory.md) při každé žádosti o přidělení a zrušení přidělení. OFF: **_CrtCheckMemory** se musí volat explicitně.<br /><br /> V případě, že je tento příznak nastaven, nejsou makra kontroly frekvence haldy nijak ovlivněna.|
|**_CRTDBG_CHECK_CRT_DF**|OFF|PNETE Zahrňte typy **_CRT_BLOCK** do operací detekce nevracení a rozdíl stavu paměti. ZAOKROUHL Tato operace ignoruje paměť používaná interně knihovnou run-time.<br /><br /> Lze také kombinovat s libovolnými makry kontroly frekvence haldy.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|OFF|PNETE Zachovejte uvolněné paměťové bloky v propojeném seznamu haldy, přiřaďte jim typ **_FREE_BLOCK** a vyplňte je hodnotou bajtu 0xDD. ZAOKROUHL Neuchovávat uvolněné bloky v propojeném seznamu haldy.<br /><br /> Lze také kombinovat s libovolnými makry kontroly frekvence haldy.|
|**_CRTDBG_LEAK_CHECK_DF**|OFF|PNETE Provede automatickou kontrolu nevracení při ukončení programu prostřednictvím volání [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) a vygeneruje zprávu o chybách, pokud aplikace nemůže uvolnit veškerou paměť, kterou přidělenu má. ZAOKROUHL Neprovádějte automatickou kontrolu nevracení při ukončení programu.<br /><br /> Lze také kombinovat s libovolnými makry kontroly frekvence haldy.|

**Halda – kontrolní makra frekvence**

Můžete určit, jak často knihovna run-time jazyka C provede ověření haldy ladění ( **_CrtCheckMemory**) na základě počtu **volání,** **realokace**, **Free**a **_msize**.

**_CrtSetDbgFlag** pak zkontroluje horní 16 bitů parametru *newFlag* pro hodnotu. Zadaná hodnota je počet volání **pro_msize** , **realokace** **,** **Free**a mezi voláními **_CrtCheckMemory** . Pro tento účel jsou k dispozici čtyři Předdefinovaná makra.

|– Makro|Počet volání pro_msize, realokace, Free a mezi voláními _CrtCheckMemory|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0 (ve výchozím nastavení nekontrolují haldy)|

Ve výchozím nastavení se _CrtCheckMemory volá jednou za každých 1 024 časů, které **zavoláte**do **za** , **realokace**, **Free**a **_msize**.

Můžete například zadat kontrolu haldy **každých 16,** **realokace**, **bezplatné**a **_msize** operace s následujícím kódem:

```C
#include <crtdbg.h>
int main( )
{
    int tmp;

    // Get the current bits
    tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);

    // Clear the upper 16 bits and OR in the desired frequency
    tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;

    // Set the new bits
    _CrtSetDbgFlag(tmp);
}
```

Horní 16 bitů parametru *newFlag* se při zadání _CRTDBG_CHECK_ALWAYS_DF ignoruje. V tomto případě se **_CrtCheckMemory** volá pokaždé **, když**zavoláte metodu, **realokace**, **Free**a **_msize**.

*newFlag* je nový stav, který se má použít pro **_crtDbgFlag** a je kombinací hodnot pro každé z bitových polí.

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>Změna jednoho nebo více těchto bitových polí a vytvoření nového stavu pro příznak

1. Zavolejte **_CrtSetDbgFlag** s *NewFlag* rovno **_CRTDBG_REPORT_FLAG** pro získání aktuálního stavu **_crtDbgFlag** a uložte vrácenou hodnotu do dočasné proměnné.

1. Zapněte jakékoli bity pomocí bitové **nebo** dočasné proměnné s odpovídajícím vyčíslení (reprezentovaným v kódu aplikace pomocí konstant manifestu).

1. Vypněte ostatní bity na základě **a**proměnnou s bitovým operátorem **Not** příslušného vyčíslení.

1. Pokud chcete nastavit nový stav pro **_crtDbgFlag**, zavolejte **_CrtSetDbgFlag** s *newFlag* rovným hodnotě uložené v dočasné proměnné.

Následující kód ukazuje, jak simulovat podmínky nízké paměti tím, že zachováte volné bloky paměti v propojeném seznamu haldy a zabráníte volání **_CrtCheckMemory** při každém požadavku na přidělení:

```C
// Get the current state of the flag
// and store it in a temporary variable
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn On (OR) - Keep freed memory blocks in the
// heap's linked list and mark them as freed
tmpFlag |= _CRTDBG_DELAY_FREE_MEM_DF;

// Turn Off (AND) - prevent _CrtCheckMemory from
// being called at every allocation request
tmpFlag &= ~_CRTDBG_CHECK_ALWAYS_DF;

// Set the new state for the flag
_CrtSetDbgFlag( tmpFlag );
```

Přehled správy paměti a haldy ladění najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Chcete-li zakázat příznak s funkcí **_CrtSetDbgFlag** , měli byste **a** proměnnou s bitovým operátorem **Not** bitové masky.

Pokud *newFlag* není platná hodnota, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí předchozí stav **_crtDbgFlag**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

```C
// crt_crtsetdflag.c
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug

// This program concentrates on allocating and freeing memory
// blocks to test the functionality of the _crtDbgFlag flag.

#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main( )
{
    char *p1, *p2;
    int tmpDbgFlag;

    _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );
    _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );

    // Set the debug-heap flag to keep freed blocks in the
    // heap's linked list - This will allow us to catch any
    // inadvertent use of freed memory
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;
    tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Allocate 2 memory blocks and store a string in each
    p1 = malloc( 34 );
    p2 = malloc( 38 );
    strcpy_s( p1, 34, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 38, "p2 points to a Client allocation block" );

    // Free both memory blocks
    free( p2 );
    free( p1 );

    // Set the debug-heap flag to no longer keep freed blocks in the
    // heap's linked list and turn on Debug type allocations (CLIENT)
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;
    tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Explicitly call _malloc_dbg to obtain the filename and
    // line number of our allocation request and also so we can
    // allocate CLIENT type blocks specifically for tracking
    p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );
    p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );
    strcpy_s( p1, 40, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 40, "p2 points to a Client allocation block" );

    // _free_dbg must be called to free the CLIENT block
    _free_dbg( p2, _CLIENT_BLOCK );
    free( p1 );

    // Allocate p1 again and then exit - this will leave unfreed
    // memory on the heap
    p1 = malloc( 10 );
}
```

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtCheckMemory](crtcheckmemory.md)<br/>
