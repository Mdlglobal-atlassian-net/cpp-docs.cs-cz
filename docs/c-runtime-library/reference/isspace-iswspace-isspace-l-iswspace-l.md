---
title: isspace –, iswspace –, _isspace_l –, _iswspace_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswspace
- _istspace
- isspace
dev_langs:
- C++
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1da229dbb93e657b01d6f69e2d9b201ed72a7aad
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="isspace-iswspace-isspacel-iswspacel"></a>isspace, iswspace, _isspace_l, _iswspace_l

Určuje, zda celé představuje znak mezery.

## <a name="syntax"></a>Syntaxe

```C
int isspace(
   int c
);
int iswspace(
   wint_t c
);
int _isspace_l(
   int c,
   _locale_t locale
);
int _iswspace_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo pro testování.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Všechny tyto rutiny vrátí nenulové hodnoty, pokud *c* je konkrétní reprezentace mezerou. **isspace –** vrátí nenulovou hodnotu, pokud *c* je prázdný znak (0x09-0x0D nebo 0x20). Výsledek testu podmínky pro **isspace –** funkce závisí na **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce, které nemají **_l** příponu využívání aktuální národní prostředí pro chování všech závislých na národním prostředí, verze, které mají **_l** příponu jsou shodné s tím rozdílem, že se používají národní prostředí, který se předává v místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

**iswspace –** vrátí nenulovou hodnotu, pokud *c* je široké znak, který odpovídá standardní prázdný znak.

Chování **isspace –** a **_isspace_l –** není definován, pokud *c* není EOF nebo v rozsahu 0 až 0xFF (včetně). V případě použití knihovny ladění CRT a *c* není jednou z těchto hodnot, funkce raise kontrolní výrazy.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istspace –**|**isspace –**|[_ismbcspace](ismbcgraph-functions.md)|**iswspace –**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isspace –**|\<ctype.h >|
|**iswspace –**|\<ctype.h > nebo \<wchar.h >|
|**_isspace_l**|\<ctype.h >|
|**_iswspace_l**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
