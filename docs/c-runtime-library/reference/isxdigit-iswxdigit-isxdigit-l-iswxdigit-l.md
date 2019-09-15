---
title: isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l
ms.date: 11/04/2016
api_name:
- _iswxdigit_l
- iswxdigit
- isxdigit
- _isxdigit_l
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswxdigit
- isxdigit
- _istxdigit
helpviewer_keywords:
- isxdigit function
- istxdigit function
- _iswxdigit_l function
- _istxdigit function
- _isxdigit_l function
- iswxdigit_l function
- isxdigit_l function
- hexadecimal characters
- iswxdigit function
ms.assetid: c8bc5146-0b58-4e3f-bee3-f2318dd0f829
ms.openlocfilehash: 18f360e66583dfbf5033f813deed0b56abc71260
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953579"
---
# <a name="isxdigit-iswxdigit-_isxdigit_l-_iswxdigit_l"></a>isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l

Určuje, zda celočíselná hodnota představuje znak, který je šestnáctkovou číslicí.

## <a name="syntax"></a>Syntaxe

```C
int isxdigit(
   int c
);
int iswxdigit(
   wint_t c
);
int _isxdigit_l(
   int c,
   _locale_t locale
);
int _iswxdigit_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo k otestování.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud je *c* konkrétní reprezentace hexadecimální číslice. **isxdigit** vrací nenulovou hodnotu, pokud je *c* šestnáctková číslice (a-F, a-f nebo 0-9). **iswxdigit** vrací nenulovou hodnotu, pokud je *c* je celosvětovým znakem, který odpovídá šestnáctkovému znaku číslice. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje podmínky testu.

V případě národního prostředí "C" funkce **iswxdigit** nepodporuje hexadecimální znaky s plnou šířkou Unicode.

Verze těchto funkcí, které mají příponu **_l** , používají národní prostředí, které je předáno namísto aktuálního národního prostředí pro své chování závislé na národním prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Chování **isxdigit** a **_isxdigit_l** není definováno, pokud *c* není EOF nebo v rozsahu 0 až 0xFF (včetně). Pokud je použita knihovna CRT ladění a *c* není jedna z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istxdigit**|**isxdigit**|**isxdigit**|**iswxdigit**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isxdigit**|\<CType. h >|
|**iswxdigit**|\<CType. h > nebo \<WCHAR. h >|
|**_isxdigit_l**|\<CType. h >|
|**_iswxdigit_l**|\<CType. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
