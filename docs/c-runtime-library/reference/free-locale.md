---
title: _free_locale
ms.date: 11/04/2016
apiname:
- _free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __free_locale
- free_locale
- _free_locale
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
ms.openlocfilehash: 92dc8cd711087e8e797b484d6c7e3c6c3b031b5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537381"
---
# <a name="freelocale"></a>_free_locale

Uvolní objekt národního prostředí.

## <a name="syntax"></a>Syntaxe

```C
void _free_locale(
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Národní prostředí*<br/>
Objekt národního prostředí pro uvolnění.

## <a name="remarks"></a>Poznámky

**_Free_locale –** funkce slouží k uvolnění objektu národního prostředí získaný z volání **_get_current_locale –** nebo **_create_locale**.

Předchozí název této funkce **__free_locale –** (se dvěma vedoucími podtržítky) je zastaralá.

## <a name="requirements"></a>Požadavky

|**Rutina**|Požadovaný hlavičkový soubor|
|---------------|---------------------|
|**_free_locale**|\<Locale.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
