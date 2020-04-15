---
title: _open_osfhandle
ms.date: 4/2/2020
api_name:
- _open_osfhandle
- _o__open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 16966bedd80dc90eaa89ee46e6b633a9cf7af74f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338548"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

Přidruží popisovač souboru c run-time s existujícím popisovačem souboru operačního systému.

## <a name="syntax"></a>Syntaxe

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Parametry

*osfhandle*<br/>
Popisovač souborů operačního systému.

*příznaky*<br/>
Typy operací jsou povoleny.

## <a name="return-value"></a>Návratová hodnota

Pokud **je** _open_osfhandle úspěšný, vrátí popisovač souboru za běhu jazyka C. V opačném případě vrátí -1.

## <a name="remarks"></a>Poznámky

Funkce **_open_osfhandle** přiděluje popisovač souboru c run-time. Přidruží tento popisovač souboru k popisovači souborů operačního systému určenému *popisovačem osfhandle*. Chcete-li se vyhnout upozornění kompilátoru, přetypujte argument *osfhandle* z **popisovače** na **intptr_t**. Argument *flags* je celé číslo výraz utvářený z jedné nebo \<více konstant manifestu definovaných v souboru fcntl.h>. Pomocí operátoru bitové nebo ( **&#124;** ) můžete zkombinovat dvě nebo více konstant manifestu a vytvořit argument *příznaků.*

Tyto konstanty manifestu \<jsou definovány v souboru fcntl.h>:

|||
|-|-|
| **\_O\_APPEND** | Umístí ukazatel souboru na konec souboru před každou operací zápisu. |
| **\_O\_RDONLY** | Otevře soubor pouze pro čtení. |
| **\_O\_TEXT** | Otevře soubor v textovém (přeloženém) režimu. |
| **\_O\_WTEXT** | Otevře soubor v režimu Unicode (přeloženo UTF-16). |

Volání **_open_osfhandle** přenese vlastnictví popisovače souboru Win32 do popisovače souboru. Chcete-li soubor otevřít pomocí **_open_osfhandle**, volání [ \_zavřít](close.md). Základní popisovač souboru operačního systému je také uzavřen voláním **_close**. Nevolejte win32 funkce **CloseHandle** na původní popisovač. Pokud je popisovač souboru vlastněn **datovým proudem &#42;SOUBOR,** volání [k zavření zavře](fclose-fcloseall.md) deskriptor souboru i základní popisovač. V takovém případě nevolejte **_close** na popisovač souboru nebo **CloseHandle** na původní popisovač.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
