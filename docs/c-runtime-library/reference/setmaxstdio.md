---
title: _setmaxstdio
ms.date: 05/21/2019
apiname:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 94b768d920ffd86a5bd762f8994244dda67fb15f
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174821"
---
# <a name="setmaxstdio"></a>_setmaxstdio

Nastaví maximální počet souběžně otevřených souborů na vstupně-výstupní datový proud úroveň.

## <a name="syntax"></a>Syntaxe

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>Parametry

*new_max*<br/>
Nové maximální počet současně otevírat soubory na datový proud úroveň vstupně-výstupních operací.

## <a name="return-value"></a>Návratová hodnota

Vrátí *new_max* v případě úspěchu; jinak -1.

Pokud *new_max* je menší než **_IOB_ENTRIES**, nebo větší než maximální počet zpracovává v operačních systémech, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce vrátí hodnotu -1 a nastaví **errno** k **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Setmaxstdio –** funkce změní hodnotu maximální počet souborů, které může být otevřeno současně úroveň vstupně-výstupních operací datového proudu.

C run-time vstupně-výstupní operace nyní podporuje až do 8 192 souborů současně otevřít v [s nízkou úrovní vstupně-výstupních operací](../../c-runtime-library/low-level-i-o.md). Tato úroveň zahrnuje soubory otevřít a získat přístup pomocí **_Otevřít**, **_read**, a **_write** řady funkcí vstupně-výstupních operací. Ve výchozím nastavení, může být až 512 soubory otevřené současně [úroveň vstupně-výstupní datový proud stream](../../c-runtime-library/stream-i-o.md). Tato úroveň zahrnuje soubory otevřít a získat přístup pomocí **fopen**, **fgetc –**, a **fputc** řady funkcí. Limit 512 otevřených souborů na úrovni datového proudu vstupně-výstupních operací je možné zvýšit na maximálně 8192 pomocí **_setmaxstdio –** funkce.

Vzhledem k tomu, že datový proud můžu/vstupně-úroveň funkce, jako **fopen –**, jsou postavené na nízkou můžu/vstupně-úroveň funkce, je maximálně 8192 pevná horní hranice pro počet souběžně otevřených souborů prostřednictvím knihovny run-time jazyka C.

> [!NOTE]
> Toto horní omezení může být rámec toho, co je podporováno konkrétní platformy Win32 a konfigurací.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Zobrazit [_getmaxstdio –](getmaxstdio.md) pro příklad použití **_setmaxstdio –**.

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
