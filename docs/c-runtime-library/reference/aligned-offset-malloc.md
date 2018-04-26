---
title: _aligned_offset_malloc – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
dev_langs:
- C++
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62ddae2faf8139b58e43f889c46771647b254b10
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc

Přidělí paměť na hranici zadané zarovnání.

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Velikost velikost paměti požadované přidělení.

*Zarovnání*<br/>
Zarovnání hodnota, která musí být celé číslo mocninou 2.

*Posun*<br/>
Posun do přidělení paměti vynutit zarovnání.

## <a name="return-value"></a>Návratová hodnota

Ukazatele na blok paměti, který byl přidělen nebo **NULL** Pokud operace se nezdařila.

## <a name="remarks"></a>Poznámky

**_aligned_offset_malloc –** je užitečné v situacích, kde je potřeba zarovnání vnořený elementu; například, pokud byl na vnořené třídy potřeba zarovnání.

**_aligned_offset_malloc –** je založena na **malloc –**; Další informace najdete v tématu [malloc –](malloc.md).

**_aligned_offset_malloc –** je označena `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce záruku, že nechcete upravit globální proměnné a že má ukazatel vrátí není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

Tato funkce nastaví **errno** k **enomem –** Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost **_heap_maxreq –**. Další informace o **errno**, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc **_aligned_offset_malloc –** ověří jeho parametry. Pokud *zarovnání* není mocninou 2 nebo, pokud *posun* je větší než nebo rovno *velikost* a nenulové hodnoty, tato funkce volá neplatný parametr obslužnou rutinu, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu **NULL** a nastaví **errno** k **einval –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc –](aligned-malloc.md).

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
