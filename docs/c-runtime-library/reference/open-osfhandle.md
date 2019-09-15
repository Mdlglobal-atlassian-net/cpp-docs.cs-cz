---
title: _open_osfhandle
ms.date: 05/21/2019
api_name:
- _open_osfhandle
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
ms.openlocfilehash: 2fa2d8190082967d14dd780aa9be7286996b1f9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951208"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

Přidruží popisovač souboru jazyka C za běhu k existujícímu popisovači souborů operačního systému.

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

*Flag*<br/>
Typy operací povoleny.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí **_open_osfhandle** popisovač souboru jazyka C run-time. V opačném případě vrátí hodnotu-1.

## <a name="remarks"></a>Poznámky

Funkce **_open_osfhandle** přiděluje popisovač souboru runtime jazyka C. Tento popisovač souboru přidružuje k popisovači souborů operačního systému určenému parametrem *osfhandle*. Chcete-li se vyhnout upozornění kompilátoru, přetypujte argument *osfhandle* z **popisovače** na **intptr_t**. Argument *Flags* je celočíselný výraz tvořený jednou nebo více konstantami manifestu, které jsou definovány \<v fcntl. h >. Můžete použít bitový operátor OR ( **&#124;** ) pro kombinování dvou nebo více konstant manifestu pro vytvoření argumentu *Flags* .

Tyto konstanty manifestu jsou definovány \<v fcntl. h >:

|||
|-|-|
| **\_O\_PŘIPOJENÍ** | Umístí ukazatel na soubor na konec souboru před každou operací zápisu. |
| **\_O\_RDONLY** | Otevře soubor pouze pro čtení. |
| **\_O\_TEXT** | Otevře soubor v textovém (přeloženém) režimu. |
| **\_O\_WTEXT** | Otevře soubor v režimu Unicode (přeložené UTF-16). |

Volání **_open_osfhandle** přenáší vlastnictví popisovače souboru Win32 do popisovače souboru. Pokud chcete zavřít soubor otevřený pomocí **_open_osfhandle**, zavolejte [ \_zavřít](close.md). Základní popisovač souboru operačního systému je také uzavřen voláním **_close**. Nevolejte funkci Win32 **CloseHandle** na původním popisovači. Pokud je popisovač souboru vlastněn datovým proudem **souborů &#42;**  , pak volání [fclose](fclose-fcloseall.md) zavře popisovač souboru i podkladový popisovač. V takovém případě Nevolejte **_close** na popisovač souboru ani na **CloseHandle** na původním popisovači.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
