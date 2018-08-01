---
title: _aligned_free – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_free
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- aligned_free
- _aligned_free
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51220aaf47056f63d37471c61857f8a128a67179
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402445"
---
# <a name="alignedfree"></a>_aligned_free

Uvolní blok paměti, která byla přidělena pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md).

## <a name="syntax"></a>Syntaxe

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock* ukazatele na blok paměti, která se vrátila `_aligned_malloc` nebo `_aligned_offset_malloc` funkce.

## <a name="remarks"></a>Poznámky

**_aligned_free –** je označen `__declspec(noalias)`, což znamená, že funkce je zaručeno, že neupraví globální proměnné. Další informace najdete v tématu [noalias](../../cpp/noalias.md).

Tuto funkci nelze ověřit svůj parametr, na rozdíl od jiných funkcí CRT _aligned. Pokud *memblock* je ukazatel s hodnotou NULL, tato funkce provede jednoduše žádná akce. Nezmění `errno` a vyvolá obslužnou rutinu neplatného parametru. Pokud dojde k chybě ve funkci kvůli pomocí dříve _aligned funkce přidělení bloku paměti nebo chybné zarovnání paměti dochází kvůli některé nepředvídaných calamity, funkce vygeneruje sestavu ladění z [_RPT, _RPTF, _RPTW, _ Rptfw – makra](rpt-rptf-rptw-rptfw-macros.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také:

[Zarovnání dat](../../c-runtime-library/data-alignment.md)  