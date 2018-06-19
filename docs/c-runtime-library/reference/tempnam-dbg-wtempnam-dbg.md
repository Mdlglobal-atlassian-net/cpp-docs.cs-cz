---
title: _tempnam_dbg –, _wtempnam_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wtempnam_dbg
- _tempnam_dbg
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
- wtempnam_dbg
- tempnam_dbg
- _tempnam_dbg
- _wtempnam_dbg
dev_langs:
- C++
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8509d9f4b8be5771abc7dfb3d4deacc9ae61494
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412046"
---
# <a name="tempnamdbg-wtempnamdbg"></a>_tempnam_dbg, _wtempnam_dbg

Funkce verze [_tempnam –, _wtempnam –, tmpnam –, _wtmpnam –](tempnam-wtempnam-tmpnam-wtmpnam.md) , použijte ladicí verzi **malloc –**, **_malloc_dbg –**.

## <a name="syntax"></a>Syntaxe

```C
char *_tempnam_dbg(
   const char *dir,
   const char *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wtempnam_dbg(
   const wchar_t *dir,
   const wchar_t *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Dir*<br/>
Cesty použité v názvu souboru, pokud neexistuje žádná proměnná prostředí TMP, nebo pokud TMP není platný adresář.

*prefix*<br/>
Řetězec, který bude pre čekajícího na názvy vrácený **_tempnam –**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_client_block –** nebo **_normal_block –**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Jednotlivé funkce vrací ukazatel na název vygenerovaný nebo **NULL** Pokud dojde k selhání. Selhání může dojít, pokud je zadán neplatný adresář název proměnné prostředí TMP a v *dir* parametr.

> [!NOTE]
> **volné** (nebo **free_dbg –**) potřebuje volat pro ukazatele přidělené **_tempnam_dbg –** a **_wtempnam_dbg –**.

## <a name="remarks"></a>Poznámky

**_Tempnam_dbg –** a **_wtempnam_dbg –** funkce jsou stejné jako **_tempnam –** a **_wtempnam –** s tím rozdílem, že když **_DEBUG –** je definován, tyto funkce používají verzi ladění **malloc –** a **_malloc_dbg –**, přidělit paměť, pokud **NULL** je předat jako první parametr. Další informace najdete v tématu [_malloc_dbg –](malloc-dbg.md).

Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat příznak **_crtdbg_map_alloc –**. Když **_crtdbg_map_alloc –** je definován, volání **_tempnam –** a **_wtempnam –** jsou mapovány na **_tempnam_dbg –** a **_ wtempnam_dbg –**, s *blockType* nastavena na **_normal_block –**. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako **_client_block –**. Další informace najdete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttempnam_dbg**|**_tempnam_dbg**|**_tempnam_dbg**|**_wtempnam_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_tempnam_dbg –**, **_wtempnam_dbg –**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
