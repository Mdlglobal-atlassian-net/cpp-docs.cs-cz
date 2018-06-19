---
title: _unlock_file – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _unlock_file
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _unlock_file
- unlock_file
dev_langs:
- C++
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d000dce4c0009341c787a211ed8ef41d1728b51b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407769"
---
# <a name="unlockfile"></a>_unlock_file

Odemkne soubor, což jiných procesů pro přístup k souboru.

## <a name="syntax"></a>Syntaxe

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>Parametry

*soubor* popisovač souboru.

## <a name="remarks"></a>Poznámky

**_Unlock_file –** funkce odemkne soubor určený touto *soubor*. Odemknutí souboru umožňuje přístup k souboru s jinými procesy. Tuto funkci nelze volat, pokud **_lock_file –** volala dřív na *souboru* ukazatel. Volání metody **_unlock_file –** na soubor, který není uzamčený může vést k zablokování. Příklad, naleznete v části [_lock_file –](lock-file.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
