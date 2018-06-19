---
title: _findclose – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _findclose
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
- _findclose
- findclose
dev_langs:
- C++
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a25ed42f1a53eb81c834997f42db0154658f376
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395683"
---
# <a name="findclose"></a>_findclose

Zavře popisovač zadaný hledaný a související prostředky.

## <a name="syntax"></a>Syntaxe

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>Parametry

*Popisovač*<br/>
Popisovač hledání vrácené z předchozího volání **_findfirst –**.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného **_findclose –** vrátí hodnotu 0. Jinak vrátí hodnotu -1 a nastaví **errno** k **enoent –**, která udává, že žádné další odpovídající soubory nebyla nalezena.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_findclose**|\<IO.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Systémová volání](../../c-runtime-library/system-calls.md)<br/>
[Funkce hledání názvů souborů](../../c-runtime-library/filename-search-functions.md)<br/>
