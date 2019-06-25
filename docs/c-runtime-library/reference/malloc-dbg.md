---
title: _malloc_dbg
ms.date: 11/04/2016
apiname:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
ms.openlocfilehash: b126678a9aecf6ae4041764576e8d06d1557dcc1
ms.sourcegitcommit: fc6bdffcf7d5521609da629621cc8459b200b004
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67351786"
---
# <a name="mallocdbg"></a>_malloc_dbg

Přiděluje blok paměti v haldě s další místo pro ladění záhlaví a přepsat vyrovnávací paměti (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Požadovaná velikost bloku paměti (v bajtech).

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*linenumber*<br/>
Číslo řádku ve zdrojovém souboru, ve kterém se požadovaná operace rozdělení nebo **NULL**.

*Filename* a *linenumber* parametry jsou k dispozici pouze při **_malloc_dbg** explicitně volána nebo [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)byla definována konstanta preprocesoru.

## <a name="return-value"></a>Návratová hodnota

Při úspěšném dokončení, tato funkce vrací ukazatel na část uživatele bloku paměti přidělené, volá funkci novou obslužnou rutinu nebo vrátí **NULL**. Úplný popis návratový chování najdete v části poznámky. Další informace o tom, jak použít nové funkce obslužné rutiny najdete v tématu [malloc](malloc.md) funkce.

## <a name="remarks"></a>Poznámky

**_malloc_dbg** je ladicí verzi [malloc](malloc.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_malloc_dbg** je omezená na volání **malloc**. Obě **malloc** a **_malloc_dbg** přidělení bloku paměti v haldě základní, ale **_malloc_dbg** nabízí některé funkce pro ladění: vyrovnávací paměť po obou stranách uživatele část bloku pro testování nevracení, parametr typu blok pro sledování konkrétní přidělení typů a *filename*/*linenumber* informací pro určení původu požadavky na přidělení.

**_malloc_dbg** přiděluje blok paměti se trochu více místa požadovaného *velikost*. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Při přidělení bloku část uživatele bloku je vyplněny hodnotou 0xCD a každý z vyrovnávací paměti přepsání jsou vyplněny 0xFD.

**_malloc_dbg** nastaví **errno** k **ENOMEM** Pokud selhání přidělení paměti nebo pokud přesahuje velikost potřebné paměti (včetně režie již bylo zmíněno dříve) **_HEAP_ MAXREQ**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat **_malloc_dbg**, naleznete v tématu [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
