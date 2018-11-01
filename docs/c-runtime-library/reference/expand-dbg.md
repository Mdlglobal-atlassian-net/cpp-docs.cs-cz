---
title: _expand_dbg
ms.date: 11/04/2016
apiname:
- _expand_dbg
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
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: cc3aa2b7e39b52eb71ac10a9b5c4a221ba6fb70c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663798"
---
# <a name="expanddbg"></a>_expand_dbg

Změní velikost zadaný blok paměti v haldě rozbalením nebo smluvní bloku (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void *_expand_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Ukazatele na blok paměti dříve přidělené.

*newSize*<br/>
Požaduje novou velikost bloku (v bajtech).

*blockType*<br/>
Požadovaný typ změněnou velikostí bloku: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který vyžadují rozbalte operace nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadovaná operace rozbalení nebo **NULL**.

*Filename* a *linenumber* parametry jsou k dispozici pouze při **_expand_dbg –** explicitně volána nebo [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)byla definována konstanta preprocesoru.

## <a name="return-value"></a>Návratová hodnota

Při úspěšném dokončení **_expand_dbg –** vrací ukazatel na blok paměti změněnou velikostí. Vzhledem k tomu, že paměť není přesunut, adresa je stejné jako userData. Pokud došlo k chybě nebo blok nelze rozbalit požadovaná velikost, vrátí hodnotu **NULL**. Pokud dojde k selhání, **errno** je s informacemi o operačním systému o povaze chyby. Další informace o **errno**, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Expand_dbg –** funkce je ladicí verze _[rozbalte](expand.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_expand_dbg –** je omezená na volání **_expand**. Obě **_expand** a **_expand_dbg –** změnit velikost bloku paměti v haldě základní, ale **_expand_dbg –** obsáhne některé funkce pro ladění: vyrovnávací paměť po obou stranách uživatele část bloku pro testování nevracení, parametr typu blok pro sledování konkrétní přidělení typů a *filename*/*linenumber* informací pro určení původu požadavky na přidělení.

**_expand_dbg –** změní zadaná paměťová blok s mírně více místa, než požadovaná velikost *newSize*. *newSize* může být větší nebo menší než velikost bloku původně přidělené paměti. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Změnu velikosti provádí rozbalení nebo smluvní původního bloku paměti. **_expand_dbg –** nepřesouvá bloku paměti, stejně jako [_realloc_dbg –](realloc-dbg.md) funkce.

Když *newSize* je větší než původní blok je rozbalená velikost bloku paměti. Během rozbalování, pokud blok paměti nelze rozšířit tak, aby vyhovovaly požadovaná velikost **NULL** je vrácena. Když *newSize* je menší než původní blok velikost bloku paměti je zakázku, dokud není dosaženo novou velikost.

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Tato funkce ověřuje své parametry. Pokud *memblock* je ukazatel s hodnotou null, nebo pokud je větší než velikost **_heap_maxreq –**, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **NULL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

```C
// crt_expand_dbg.c
//
// This program allocates a block of memory using _malloc_dbg
// and then calls _msize_dbg to display the size of that block.
// Next, it uses _expand_dbg to expand the amount of
// memory used by the buffer and then calls _msize_dbg again to
// display the new amount of memory allocated to the buffer.
//

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   long *buffer;
   size_t size;

   // Call _malloc_dbg to include the filename and line number
   // of our allocation request in the header
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );
   if( buffer == NULL )
      exit( 1 );

   // Get the size of the buffer by calling _msize_dbg
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

   // Expand the buffer using _expand_dbg and show the new size
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );

   if( buffer == NULL )
      exit( 1 );
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",
           size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _expand_dbg of 1 more long: 164
```

## <a name="comment"></a>Komentář

Výstup tohoto programu závisí na počítače umožňuje rozšířit všechny oddíly. Pokud všechny oddíly jsou rozbaleny, výstup se projeví v části výstupu.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
