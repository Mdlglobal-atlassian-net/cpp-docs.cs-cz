---
title: _aligned_offset_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
ms.openlocfilehash: 4fbacb170fd1ae1ce92de4a11ea85ff42b3942a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939774"
---
# <a name="_aligned_offset_malloc_dbg"></a>_aligned_offset_malloc_dbg

Přidělí paměť v zadané hranici zarovnání (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Velikost požadované alokace paměti

*bod*<br/>
Hodnota zarovnání, která musí být celočíselnou mocninou 2.

*polohy*<br/>
Posun k přidělení paměti pro vynucení zarovnání.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci přidělení, nebo **hodnotu null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení, nebo **hodnota null**.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na blok paměti, který byl přidělen nebo **null** v případě, že operace se nezdařila.

## <a name="remarks"></a>Poznámky

**_aligned_offset_malloc_dbg** je ladicí verze funkce [_aligned_offset_malloc](aligned-offset-malloc.md) . Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_aligned_offset_malloc_dbg** je sníženo na volání **_aligned_offset_malloc**. **_Aligned_offset_malloc** i **_aligned_offset_malloc_dbg** přidělují blok paměti v základní haldě, ale **_aligned_offset_malloc_dbg** nabízí několik funkcí pro ladění: vyrovnávací paměti na obou stranách bloku uživatele na Otestujte nevracení a*číslo řádku* informace o *názvu souboru*/, abyste zjistili původ požadavků na přidělení. Sledování specifických typů přidělení s parametrem typu bloku není podporovanou funkcí ladění pro zarovnávání přidělení. Zarovnaná přidělení se zobrazí jako typ bloku _NORMAL_BLOCK.

**_aligned_offset_malloc_dbg** přiděluje blok paměti o něco více místa, než je požadovaná *Velikost*. Dodatečné místo se používá správcem haldy ladění k propojení bloků paměti ladění a k poskytnutí aplikace s informacemi hlavičky ladění a přepsat vyrovnávací paměti. Po přidělení bloku je uživatelská část bloku vyplněna hodnotou 0xCD a každá z vyrovnávací paměti přepsání je vyplněna 0xFD.

**_aligned_offset_malloc_dbg** je užitečné v situacích, kdy je nutné zarovnat na vnořeném prvku. Například pokud bylo zarovnání nutné pro vnořenou třídu.

_aligned_offset_malloc_dbg je založen na **za** . Další informace najdete [v tématu.](malloc.md)

Tato funkce nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovedlo nebo pokud je požadovaná velikost větší než **_HEAP_MAXREQ**. Další informace o **errno**najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). **_Aligned_offset_malloc** také ověří své parametry. Pokud *Zarovnání* není mocninou 2 nebo pokud je *posun* větší nebo roven *velikosti* a nenulové hodnotě, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrátí **hodnotu null** a nastaví **errno** na **EINVAL**.

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
