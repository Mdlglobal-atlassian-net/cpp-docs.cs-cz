---
title: "_open_osfhandle – | Microsoft Docs"
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _open_osfhandle
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
dev_langs: C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff05c99180ff8933316e1db9366da3b985c10305
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

*osfhandle*  
Popisovač souboru operačního systému.

*příznaky*  
Typy operací povolena.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného `_open_osfhandle` , vrátí se popisovač soubor spouští za běhu C. V opačném případě vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

`_open_osfhandle` Funkce přiděluje popisovač soubor spouští za běhu C a přidruží ji popisovač souboru operačního systému určený *osfhandle*. *Příznaky* argument je vytvořen z jedné nebo více manifestu konstanty definované v Fcntl.h výraz celé číslo. Při použití dvou nebo více manifestu konstanty do formuláře *příznaky* argument, konstanty spolu se operátoru bitové operace OR ( **&#124;** ).

Fcntl.h definuje následující konstanty manifestu:

**\_O\_PŘIPOJENÍ**  
Umisťuje soubor ukazatel na konec souboru před každou operaci zápisu.

**\_O\_RDONLY**  
Otevře se soubor jen pro čtení.

**\_O\_TEXTU**  
Otevře soubor v režimu textových (přeložit).

**\_O\_WTEXT**  
Soubor se otevře v režimu Unicode (přeložený UTF-16).

Zavřete soubor otevřít s `_open_osfhandle`, volání [ \_zavřete](../../c-runtime-library/reference/close.md). Základní popisovač souboru je také uzavřený voláním `_close`, takže není nutné volat funkci Win32 `CloseHandle` na původní popisovač. Pokud je vlastníkem popisovače souborů `FILE *` datového proudu, pak volání [fclose –](../../c-runtime-library/reference/fclose-fcloseall.md) na který `FILE *` datový proud se zavře také popisovače souborů a základní popisovač. V takovém případě Nevolejte `_close` na popisovače souborů.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_open_osfhandle`|\<IO.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)  
