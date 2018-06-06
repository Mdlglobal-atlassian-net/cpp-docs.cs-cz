---
title: _open_osfhandle – | Microsoft Docs
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af3783420389dc008e39c818c39406f0b2af8af5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569833"
---
# <a name="openosfhandle"></a>_open_osfhandle

Přidruží popisovač soubor spouští za běhu C popisovač existující soubor operačního systému.

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

*Příznaky*<br/>
Typy operací povolena.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného **_open_osfhandle –** , vrátí se popisovač soubor spouští za běhu C. V opačném případě vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

**_Open_osfhandle –** funkce přiděluje popisovač soubor spouští za běhu C a přidruží ji popisovač souboru operačního systému určený *osfhandle*. Abyste se vyhnuli upozornění kompilátoru, přetypovat *osfhandle* argument z **zpracování** k **intptr_t –**. *Příznaky* argument je použit celočíselný výraz, který je vytvořen z jednoho nebo více manifestu konstanty definované v \<fcntl.h >. Při použití dvou nebo více manifestu konstanty do formuláře *příznaky* argument, konstanty spolu se operátoru bitové operace OR ( **&#124;** ).

Tyto manifestu konstanty jsou definovány v \<fcntl.h >:

|||
|-|-|
**\_O\_PŘIPOJENÍ**|Umisťuje soubor ukazatel na konec souboru před každou operaci zápisu.
**\_O\_RDONLY**|Otevře se soubor jen pro čtení.
**\_O\_TEXT**|Otevře soubor v režimu textových (přeložit).
**\_O\_WTEXT**|Soubor se otevře v režimu Unicode (přeložený UTF-16).

**_Open_osfhandle –** volání přenese vlastnictví popisovač souboru Win32 popisovače souborů. Zavřete soubor otevřít s **_open_osfhandle –**, volání [ \_zavřete](close.md). Základní popisovač souboru je také uzavřený voláním **_close –**, takže není nutné volat funkci Win32 **funkce CloseHandle** na původní popisovač. Pokud je vlastníkem popisovače souborů **soubor &#42;**  datového proudu, pak volání [fclose –](fclose-fcloseall.md) na který **souboru &#42;**  datového proudu také zavře popisovač souboru a základní obslužná rutina. V takovém případě Nevolejte **_close –** na popisovače souborů.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_open_osfhandle**|\<IO.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
