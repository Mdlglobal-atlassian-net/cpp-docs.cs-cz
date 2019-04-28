---
title: _CrtSetDbgFlag
ms.date: 11/04/2016
apiname:
- _CrtSetDbgFlag
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
apitype: DLLExport
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
ms.openlocfilehash: dcb8e37090e4c15ba849e76ca1cb1cc646a7bcc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348182"
---
# <a name="crtsetdbgflag"></a>_CrtSetDbgFlag

Načte nebo změní stav **_crtDbgFlag** příznak, který řídí chování přidělení správce hald ladění (pouze ladicí verze).

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

**_CrtSetDbgFlag** funkce umožňuje, aby aplikace k řízení, jak správce hald ladění sleduje přidělování paměti tak, že upravíte bitového pole **_crtDbgFlag** příznak. Nastavením bity (zapnout), aplikace můžete dát pokyn k provedení speciální operace ladění, včetně kontroly pro nevracení paměti při ukončení aplikace a vytváření sestav, pokud nějaké najde, správce hald ladění budete jen Simulovat podmínky nedostatku paměti podle určení, že uvolněné bloky paměti by měla zůstat v propojeném seznamu haldy a ověření integrity haldy zkontrolováním každý blok paměti na každý požadavek na přidělení. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtSetDbgFlag** odstraněna během předběžného zpracování.

V následující tabulce jsou uvedeny bitových polí pro **_crtDbgFlag** a popisuje jejich chování. Protože nastavení bits výsledky v zvýšenou výstup diagnostiky a rychlost provádění sníženou programu, nejsou nastaveny tyto bity (vypnuté) ve výchozím nastavení. Další informace o těchto bitových polí naleznete v tématu [funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details).

|Bitové pole.|Výchozí|Popis|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|DÁLE|ON: Povolit přidělení haldy ladění a použití identifikátorů typ bloku paměti, jako například **_CLIENT_BLOCK**. OFF: Přidat nové přidělení propojeném seznamu haldy, ale nastavit typ do bloku **_IGNORE_BLOCK**.<br /><br /> Můžete také kombinovat s žádným z makra haldy frekvence kontroly.|
|**_CRTDBG_CHECK_ALWAYS_DF**|OFF|ON: Volání [_CrtCheckMemory](crtcheckmemory.md) při každé žádosti o přidělování a navracení zpět. VYPNUTO: **_CrtCheckMemory** musí být explicitně volána.<br /><br /> Haldy frekvence kontroly makra nemají žádný vliv, pokud je tento příznak nastaven.|
|**_CRTDBG_CHECK_CRT_DF**|OFF|ON: Zahrnout **_CRT_BLOCK** typy ve stavu přetečení zjišťování a paměti rozdíl operace. OFF: Paměť používaná interně knihovnou run-time je ignorována pomocí těchto operací.<br /><br /> Můžete také kombinovat s žádným z makra haldy frekvence kontroly.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|OFF|ON: Zachovat uvolněné bloky paměti v propojeném seznamu haldy, přiřazovat je **_FREE_BLOCK** zadejte a vyplnit hodnota bajtu 0xDD. OFF: Nezachovat uvolněné bloky v propojeném seznamu haldy.<br /><br /> Můžete také kombinovat s žádným z makra haldy frekvence kontroly.|
|**_CRTDBG_LEAK_CHECK_DF**|OFF|ON: Proveďte automatické nevracení při ukončení programu prostřednictvím volání na kontrolu [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) a vygenerovat zprávu o chybách v případě, že aplikace se nezdařilo uvolnit všechny přidělené paměti. OFF: Neprovádějte automaticky nevracení kontrolu při ukončení programu.<br /><br /> Můžete také kombinovat s žádným z makra haldy frekvence kontroly.|

**Kontrola haldy frekvence makra**

Můžete určit, jak často knihovny run-time C provede ověření haldy ladění (**_CrtCheckMemory**) na základě počtu volání **malloc**, **realloc**, **bezplatné**, a **_msize –**.

**_CrtSetDbgFlag** pak zkontroluje horní 16 bitů *newFlag* parametr pro hodnotu. Zadaná hodnota je počet **malloc**, **realloc**, **bezplatné**, a **_msize –** volání mezi **_CrtCheckMemory**  volání. Čtyři předdefinovaná makra jsou k dispozici pro tento účel.

|– Makro|Počet volání malloc, realloc, bezplatná a _msize – mezi voláními _CrtCheckMemory|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0 (ve výchozím nastavení žádné kontroly haldy)|

Ve výchozím nastavení **_CrtCheckMemory** se volá jednou každých 1 024 časy volání **malloc**, **realloc**, **bezplatné**, a **_ msize –**.

Například můžete zadat haldu kontrolovat každých 16 **malloc**, **realloc**, **bezplatné**, a **_msize –** operací s následujícím kódem:

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

Horní 16 bitů *newFlag* parametru jsou ignorovány, pokud je zadán _CRTDBG_CHECK_ALWAYS_DF. V takovém případě **_CrtCheckMemory** je volána pokaždé, když voláte **malloc**, **realloc**, **bezplatné**, a **_msize –**.

*newFlag* je nový stav vyrovnat **_crtDbgFlag** a je kombinace hodnot pro každou z bitových polí.

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>Chcete-li změnit jedno nebo více těchto bitových polí a vytvoření nového stavu pro příznak

1. Volání **_CrtSetDbgFlag** s *newFlag* rovna **_CRTDBG_REPORT_FLAG** pro získání aktuálního **_crtDbgFlag** stavu a uložit Vrácená hodnota v dočasné proměnné.

1. Zapněte všechny bity pomocí logické bitové **nebo** dočasné proměnné s odpovídajícími bitovými maskami (představovanými v kódu aplikace konstantami manifestu).

1. Vypnout podle bity **a**- ing proměnnou logickou bitovou hodnotou **není** z příslušné bitovými maskami.

1. Volání **_CrtSetDbgFlag** s *newFlag* rovna hodnotu uloženou v dočasné proměnné, chcete-li nastavit nový stav pro **_crtDbgFlag**.

Následující kód ukazuje, jak simulovat nedostatku paměti podmínky udržováním uvolnění paměťových bloků v propojeném seznamu haldy a zabránit **_CrtCheckMemory** byla volána na každý požadavek na přidělení:

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

Přehled správy paměti a halda ladění, naleznete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Zakázat pomocí příznaku **_CrtSetDbgFlag** funkce, měli byste **a** proměnnou bitový **není** z bitové masky.

Pokud *newFlag* není platnou hodnotu, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí do předchozího stavu **_crtDbgFlag**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

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
