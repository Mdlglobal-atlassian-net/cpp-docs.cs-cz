---
title: _aligned_offset_recalloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_recalloc_dbg
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
- aligned_offset_recalloc_dbg
- _aligned_offset_recalloc_dbg
helpviewer_keywords:
- aligned_offset_recalloc_dbg function
- _aligned_offset_recalloc_dbg function
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
ms.openlocfilehash: e363a1cb104db9973f5f9e9c67a5d40693d405ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939752"
---
# <a name="_aligned_offset_recalloc_dbg"></a>_aligned_offset_recalloc_dbg

Změní velikost bloku paměti, který byl přidělen pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc](aligned-offset-malloc.md) a inicializuje paměť na hodnotu 0 (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_recalloc_dbg(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Aktuální ukazatel bloku paměti.

*Automatické*<br/>
Počet elementů.

*hodnota*<br/>
Délka v bajtech každého elementu.

*bod*<br/>
Hodnota zarovnání, která musí být celočíselnou mocninou 2.

*polohy*<br/>
Posun k přidělení paměti pro vynucení zarovnání.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci realokace nebo **null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace realokace nebo **hodnota null**.

## <a name="return-value"></a>Návratová hodnota

**_aligned_offset_recalloc_dbg** vrátí ukazatel void na blok paměti realokováno (a případně přesunuto). Návratová hodnota má **hodnotu null** , pokud je velikost nulová a argument buffer nemá **hodnotu null**, nebo pokud není k dispozici dostatek paměti pro rozšíření bloku na danou velikost. V prvním případě je původní blok uvolněn. V druhém případě se původní blok nezměnil. Vrácená hodnota odkazuje na prostor úložiště, který je zaručen vhodným způsobem pro uložení libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než void, použijte přetypování typu u vrácené hodnoty.

## <a name="remarks"></a>Poznámky

**_aligned_offset_realloc_dbg** je ladicí verze funkce [_aligned_offset_recalloc](aligned-offset-recalloc.md) . Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_aligned_offset_recalloc_dbg** je sníženo na volání **_aligned_offset_recalloc**. **_Aligned_offset_recalloc** i **_aligned_offset_recalloc_dbg** znovu přidělí blok paměti v základní haldě, ale **_aligned_offset_recalloc_dbg** nabízí několik funkcí ladění: vyrovnávací paměti na obou stranách uživatelské části. bloku pro otestování nevracení a*číslo řádku* informace o *názvu souboru*/k určení původu žádostí o přidělení. Sledování specifických typů přidělení s parametrem typu bloku není podporovanou funkcí ladění pro zarovnávání přidělení. Zarovnaná přidělení se zobrazí jako typ bloku _NORMAL_BLOCK.

**_aligned_offset_realloc_dbg** znovu přidělí zadaný blok paměti o více místa, než je požadovaný *NewSize*. *NewSize* může být větší nebo menší než velikost původně přiděleného bloku paměti. Dodatečné místo se používá správcem haldy ladění k propojení bloků paměti ladění a k poskytnutí aplikace s informacemi hlavičky ladění a přepsat vyrovnávací paměti. Přerozdělení může mít za následek přesunutí původního bloku paměti na jiné místo v haldě a změnu velikosti bloku paměti. Pokud se blok paměti přesune, obsah původního bloku se přepíše.

Tato funkce nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovedlo nebo pokud požadovaná velikost (*Číselná* * *Velikost*) byla větší než **_HEAP_MAXREQ**. Další informace o **errno**najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). **_Aligned_offset_recalloc_dbg** také ověří své parametry. Pokud *Zarovnání* není mocninou 2 nebo pokud je *posun* větší nebo roven požadované velikosti a nenulové hodnotě, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrátí **hodnotu null** a nastaví **errno** na **EINVAL**.

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy a její ladicí verzí v sestavení ladění aplikace najdete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_recalloc_dbg**|\<. h >|

## <a name="see-also"></a>Viz také:

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
