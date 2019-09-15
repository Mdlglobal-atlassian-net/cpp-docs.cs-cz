---
title: _setmaxstdio
ms.date: 05/21/2019
api_name:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 620213b4df9ea555189a1403b3c9e83b55cad6c6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948224"
---
# <a name="_setmaxstdio"></a>_setmaxstdio

Nastaví maximální počet současně otevřených souborů na úrovni vstupu a výstupu datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>Parametry

*new_max*<br/>
Nové maximum pro počet současně otevřených souborů na úrovni I/O datového proudu.

## <a name="return-value"></a>Návratová hodnota

Vrátí *new_max* , pokud bylo úspěšné. -1 v opačném případě.

Pokud *new_max* je menší než **_IOB_ENTRIES**nebo je větší než maximální počet popisovačů dostupných v operačním systému, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tato funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_setmaxstdio** změní maximální hodnotu počtu souborů, které mohou být otevřeny současně na úrovni I/O datového proudu.

Vstupně-výstupní operace C teď podporuje až 8 192 souborů otevřených současně na [úrovni nízkého I/v](../../c-runtime-library/low-level-i-o.md). Tato úroveň zahrnuje soubory otevřené a dostupné pomocí řady **_open**, **_read**a **_Write** funkcí v/v. Ve výchozím nastavení je možné otevřít až 512 souborů najednou na [úrovni vstupu a výstupu streamu](../../c-runtime-library/stream-i-o.md). Tato úroveň zahrnuje soubory otevřené a dostupné pomocí rodiny funkcí **fopen**, **fgetc**a **fputc** . Omezení 512 otevřených souborů na úrovni vstupu a výstupu datového proudu lze zvýšit na maximum 8 192 pomocí funkce **_setmaxstdio** .

Vzhledem k tomu, že funkce streamování vstupně-výstupních operací, jako je například **fopen**, jsou postaveny na funkci nízkého počtu vstupně-výstupních operací, maximální hodnota 8 192 je pevný horní limit počtu současně otevřených souborů, ke kterým přistupovala prostřednictvím knihovny run-time jazyka C.

> [!NOTE]
> Tento horní limit může být nad rámec toho, co je podporováno konkrétní platformou Win32 a konfigurací.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Příklad použití **_setmaxstdio**naleznete v tématu [_getmaxstdio](getmaxstdio.md) .

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
