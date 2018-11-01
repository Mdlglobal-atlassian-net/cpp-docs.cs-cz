---
title: _open_osfhandle
ms.date: 05/29/2018
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: e8b7dc097c1af60894c627b8b660c4d9d81361db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519454"
---
# <a name="openosfhandle"></a>_open_osfhandle

Přidruží popisovač souboru za běhu C existující popisovač souboru operačního systému.

## <a name="syntax"></a>Syntaxe

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Parametry

*osfhandle*<br/>
Popisovač souboru operačního systému.

*příznaky*<br/>
Typy operací, které jsou povoleny.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **_open_osfhandle –** vrátí popisovač souboru za běhu C. V opačném případě vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

**_Open_osfhandle –** funkce přidělí popisovač souboru za běhu C a přidruží ji k popisovač souboru operačního systému určený *osfhandle*. Chcete-li zabránit upozornění kompilátoru, přetypujte *osfhandle* argument od **zpracování** k **intptr_t**. *Příznaky* argument je výraz celého čísla, který je vytvořen z jednoho nebo více konstant manifestu definovaných v \<fcntl.h >. Při použití dvou nebo více konstant manifestu do formuláře *příznaky* argument konstanty jsou kombinované pomocí bitového operátoru OR – operátor ( **&#124;** ).

Tyto konstanty manifestu jsou definovány v \<fcntl.h >:

|||
|-|-|
**\_O\_PŘIPOJENÍ**|Umístí ukazatel souboru na konec souboru před každou operaci zápisu.
**\_O\_RDONLY**|Otevře se soubor jen pro čtení.
**\_O\_TEXT**|Otevře soubor v textovém (přeloženém) režimu.
**\_O\_WTEXT**|Otevře soubor v režimu Unicode (přeloženého UTF-16).

**_Open_osfhandle –** volání převede vlastnictví popisovač souboru Win32 do popisovače souboru. Zavřete soubor otevřít s **_open_osfhandle –**, volání [ \_zavřete](close.md). Volání také uzavřel podkladové popisovač souboru operačního systému **_Zavřít**, takže není nutné volat funkci Win32 **CloseHandle** na původní popisovač. Pokud popisovač souboru je vlastněna **souboru &#42;**  datový proud a následným voláním [fclose –](fclose-fcloseall.md) zabývat **souboru &#42;**  stream také uzavře popisovač souboru a základní popisovač. V takovém případě Nevolejte **_Zavřít** na popisovač souboru.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_open_osfhandle**|\<IO.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
