---
title: _tempnam_dbg, _wtempnam_dbg
ms.date: 11/04/2016
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
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
ms.openlocfilehash: 804c8ad1f17c6ee1df563cafc69ee7aef494d1cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596453"
---
# <a name="tempnamdbg-wtempnamdbg"></a>_tempnam_dbg, _wtempnam_dbg

Funkce verze [_tempnam – _wtempnam –, tmpnam – _wtmpnam –](tempnam-wtempnam-tmpnam-wtmpnam.md) , které používají ladicí verze **malloc**, **_malloc_dbg**.

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

*adresář*<br/>
Cesta v názvu souboru používá, pokud neexistuje žádná proměnná prostředí TMP, nebo pokud TMP není platný adresář.

*prefix*<br/>
Řetězec, který bude pre čekajícího na názvy vrácené **_tempnam –**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí ukazatel na název generované nebo **NULL** Pokud dojde k selhání. Selhání může dojít, pokud je neplatný název adresáře zadané v proměnné prostředí TMP a v *dir* parametru.

> [!NOTE]
> **bezplatné** (nebo **free_dbg –**) musí být volána pro ukazatele přidělaná **_tempnam_dbg –** a **_wtempnam_dbg –**.

## <a name="remarks"></a>Poznámky

**_Tempnam_dbg –** a **_wtempnam_dbg –** funkce jsou stejné jako **_tempnam –** a **_wtempnam –** s tím rozdílem, že když **_DEBUG** je definován, tyto funkce používají ladicí verze **malloc** a **_malloc_dbg**, přidělení paměti, pokud **NULL** je předán jako první parametr. Další informace najdete v tématu [_malloc_dbg](malloc-dbg.md).

Chcete-li explicitně volat tyto funkce ve většině případů nepotřebujete. Místo toho můžete definovat příznak **_CRTDBG_MAP_ALLOC**. Když **_CRTDBG_MAP_ALLOC** je definován, jsou volání **_tempnam –** a **_wtempnam –** budou přemapovány na **_tempnam_dbg –** a **_ wtempnam_dbg –**, se *blockType* nastavena na **_NORMAL_BLOCK**. Proto není potřeba explicitně volat tyto funkce, pokud chcete označit jako bloky haldy **_CLIENT_BLOCK**. Další informace najdete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttempnam_dbg**|**_tempnam_dbg**|**_tempnam_dbg**|**_wtempnam_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_tempnam_dbg –**, **_wtempnam_dbg –**|\<crtdbg.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
