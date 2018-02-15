---
title: "_Crtsetdbgflag – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fb2af7756db37e3c5021894936d801d11705f0c6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="crtsetdbgflag"></a>_CrtSetDbgFlag
Načte nebo upraví stav **_crtdbgflag –** příznak můžete řídit chování přidělení haldy ladění správce (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int _CrtSetDbgFlag(   
   int newFlag   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `newFlag`  
 Nový stav pro **_crtdbgflag –**.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí předchozí stav **_crtdbgflag –**.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtSetDbgFlag` Funkce umožňuje řídit, jak správce haldy ladění sleduje přidělování paměti změnou bitových polí z aplikaci **_crtdbgflag –** příznak. Nastavením službu bits (zapnout), aplikace můžete určit, aby správce haldy ladění k provedení operace speciální ladění, včetně kontroly pro nevracení paměti při ukončení aplikace a vytváření sestav, pokud nějaké nalezeny, simulaci podmínky nedostatku paměti podle určení, že bloky uvolněné paměti zůstat v odkazovaného seznamu do haldy a ověření integrity halda zkontrolováním každého bloku paměti na každý požadavek na přidělení. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtSetDbgFlag` jsou odebrány při předběžném zpracování.  
  
 Následující tabulka uvádí bitových polí pro **_crtdbgflag –** a popisuje jejich chování. Vzhledem k nastavení bits výsledky v vyšší výstup diagnostiky a rychlost provádění snížené programu, nejsou nastavit tyto služby bits (vypnuté) ve výchozím nastavení. Další informace o těchto bit pole naleznete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details).  
  
|Bitová pole|Výchozí|Popis|  
|---------------|-------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|ON|ON: Povolit přidělení haldy ladění a použití paměti identifikátory typ bloku, například `_CLIENT_BLOCK`. OFF: Přidat nové přidělení haldy odkazovaného seznamu, ale nastavení blokovat typ **_ignore_block –**.<br /><br /> Můžete také kombinovat s žádným z makra Kontrola haldy frekvence.|  
|**_CRTDBG_CHECK_ALWAYS_DF**|VYPNOUT|ON: Volání [_crtcheckmemory –](../../c-runtime-library/reference/crtcheckmemory.md) při každé žádosti o přidělení a zrušení přidělení. OFF: `_CrtCheckMemory` musí být explicitně volána.<br /><br /> Makra Kontrola haldy frekvence nemají žádný vliv, pokud je nastavený tento příznak.|  
|`_CRTDBG_CHECK_CRT_DF`|VYPNOUT|ON: Zahrnout `_CRT_BLOCK` typy v úniku detekce a paměť stavu rozdíl operace. VYPNUTO: Je paměť používaná interně k běhové knihovny ignorován v těchto operací.<br /><br /> Můžete také kombinovat s žádným z makra Kontrola haldy frekvence.|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|VYPNOUT|ON: Zachování uvolněné paměti bloky v haldě je propojená seznamu, přiřaďte jim **_free_block –** zadejte a vyplnit je hodnota bajtu 0xDD. VYPNUTO: Není mějte uvolněné bloky haldy odkazovaného seznamu.<br /><br /> Můžete také kombinovat s žádným z makra Kontrola haldy frekvence.|  
|`_CRTDBG_LEAK_CHECK_DF`|VYPNOUT|ON: Provést automatické úniku kontrola při ukončení programu prostřednictvím volání [_crtdumpmemoryleaks –](../../c-runtime-library/reference/crtdumpmemoryleaks.md) a vygenerovat zprávu o chybách v případě, že aplikace se nezdařilo uvolnit všechny jeho přidělené paměti. VYPNUTÍ: Neprovádět automaticky úniku kontrola při ukončení programu.<br /><br /> Můžete také kombinovat s žádným z makra Kontrola haldy frekvence.|  
  
 **Kontrola haldy frekvence makra**  
  
 Můžete určit, jak často běhové knihovny jazyka C provede ověření haldy ladění (`_CrtCheckMemory`) na základě počtu volání `malloc`, `realloc`, **volné**, a `_msize`.  
  
 `_CrtSetDbgFlag` pak zkontroluje horní 16 bitů `newFlag` parametr pro hodnotu. Zadaná hodnota je počet `malloc`, `realloc`, **volné**, a `_msize` volání mezi `_CrtCheckMemory` volání. Čtyři předdefinovaná makra jsou k dispozici pro tento účel.  
  
|Macro|Počet volání malloc, realloc – volné a _msize – mezi _crtcheckmemory – volání|  
|-----------|------------------------------------------------------------------------------------------|  
|_CRTDBG_CHECK_EVERY_16_DF|16|  
|_CRTDBG_CHECK_EVERY_128_DF|128|  
|_CRTDBG_CHECK_EVERY_1024_DF|1024|  
|_CRTDBG_CHECK_DEFAULT_DF|0 (ve výchozím nastavení žádné kontroly haldy)|  
  
 Ve výchozím nastavení `_CrtCheckMemory` je volána po každých 1 024 časy zavoláte `malloc`, `realloc`, **volné**, a `_msize`.  
  
 Například můžete zadat haldy zkontrolujte každých 16 `malloc`, `realloc`, **volné**, a `_msize` operací s následujícím kódem:  
  
```  
#include <crtdbg.h>  
int main( )  
{  
int tmp;  
  
// Get the current bits  
tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);  
  
// Clear the upper 16 bits and OR in the desired freqency  
tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;  
  
// Set the new bits  
_CrtSetDbgFlag(tmp);  
}  
```  
  
 Horní 16 bitů `newFlag` parametru jsou ignorovány, když je zadané _crtdbg_check_always_df –. V takovém případě `_CrtCheckMemory` je volána při každém volání `malloc`, `realloc`, **volné**, a `_msize`.  
  
 `newFlag` je nový stav pro použití **_crtdbgflag –** a je kombinace hodnot pro každé pole verze.  
  
### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>Změnit jeden nebo více těchto bitových polí a vytvořit nový stav pro příznak  
  
1.  Volání `_CrtSetDbgFlag` s `newFlag` rovna `_CRTDBG_REPORT_FLAG` získat aktuální **_crtdbgflag –** stavu a uložit vrácená hodnota v dočasné proměnné.  
  
2.  Zapnout všechny služby bits pomocí `OR`- ing dočasné proměnné s odpovídající bitovou masku (určená v kódu aplikace pomocí manifestu konstanty).  
  
3.  Vypnout službu bits podle **a**- ing proměnnou pomocí bitové **není** z příslušné bitovou masku.  
  
4.  Volání `_CrtSetDbgFlag` s `newFlag` rovna s hodnotou uloženou v dočasné proměnné pro nastavení nového stavu pro **_crtdbgflag –**.  
  
 Následující kód ukazuje, jak k simulaci nedostatku paměti podmínky udržováním uvolněno bloky paměti v haldě na odkazovaného seznamu a zabránit `_CrtCheckMemory` z volané na každý požadavek na přidělení:  
  
```  
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
  
 Přehled správy paměti a haldy ladění, najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Zakázání příznaku s `_CrtSetDbgFlag` funkce, měli byste **a** proměnnou pomocí bitové hodnotě **není** z bitové masky.  
  
 Pokud `newFlag` není platná hodnota, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí předchozí stav `_crtDbgFlag`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtSetDbgFlag`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_crtsetdflag.c  
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug  
/*  
 * This program concentrates on allocating and freeing memory  
 * blocks to test the functionality of the _crtDbgFlag flag..  
 */  
  
#include <string.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main( )  
{  
        char *p1, *p2;  
        int tmpDbgFlag;  
  
        _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );  
        _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );  
        /*  
         * Set the debug-heap flag to keep freed blocks in the  
         * heap's linked list - This will allow us to catch any  
         * inadvertent use of freed memory  
         */  
        tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);  
        tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;  
        tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;  
        _CrtSetDbgFlag(tmpDbgFlag);  
  
        /*  
         * Allocate 2 memory blocks and store a string in each  
         */  
        p1 = malloc( 34 );  
        p2 = malloc( 38 );  
        strcpy_s( p1, 34, "p1 points to a Normal allocation block" );  
        strcpy_s( p2, 38, "p2 points to a Client allocation block" );  
  
        /*  
         * Free both memory blocks  
         */  
        free( p2 );  
        free( p1 );  
  
        /*  
         * Set the debug-heap flag to no longer keep freed blocks in the  
         * heap's linked list and turn on Debug type allocations (CLIENT)  
         */  
        tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);  
        tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;  
        tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;  
        _CrtSetDbgFlag(tmpDbgFlag);  
  
        /*  
         * Explicitly call _malloc_dbg to obtain the filename and   
         * line number of our allocation request and also so we can   
         * allocate CLIENT type blocks specifically for tracking  
         */  
        p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );  
        p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );  
        strcpy_s( p1, 40, "p1 points to a Normal allocation block" );  
        strcpy_s( p2, 40, "p2 points to a Client allocation block" );  
  
        /*  
         * _free_dbg must be called to free the CLIENT block  
         */  
        _free_dbg( p2, _CLIENT_BLOCK );  
        free( p1 );  
  
        /*  
         * Allocate p1 again and then exit - this will leave unfreed  
         * memory on the heap  
         */  
        p1 = malloc( 10 );  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [_CrtCheckMemory](../../c-runtime-library/reference/crtcheckmemory.md)