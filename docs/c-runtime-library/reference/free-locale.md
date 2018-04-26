---
title: _free_locale – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 23e1333d7649b6d1ce24ee1bb7840e0389edb908
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
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

*národní prostředí* národní prostředí objektu k uvolnění.

## <a name="remarks"></a>Poznámky

**_Free_locale –** funkce slouží k bezplatným objekt národního prostředí získané z volání **_get_current_locale –** nebo **_create_locale –**.

Předchozí název této funkce **__free_locale –** (se dvěma úvodní podtržítka) je zastaralá.

## <a name="requirements"></a>Požadavky

|**Rutiny**|Požadovaný hlavičkový soubor|
|---------------|---------------------|
|**_free_locale**|\<Locale.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
