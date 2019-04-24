---
title: _ismbblead, _ismbblead_l
ms.date: 11/04/2016
apiname:
- _ismbblead_l
- _ismbblead
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
ms.openlocfilehash: 7bf8e8c88153e2f22cfa08bb35ff8d4ba01a8804
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157208"
---
# <a name="ismbblead-ismbbleadl"></a>_ismbblead, _ismbblead_l

Testuje charakter pro určení, zda jde o vedoucí bajt vícebajtového znaku.

## <a name="syntax"></a>Syntaxe

```C
int _ismbblead(
   unsigned int c
);
int _ismbblead_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo k testování.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud celé číslo *c* je první bajt vícebajtového znaku.

## <a name="remarks"></a>Poznámky

Vícebajtové znaky jsou tvořeny vedoucím bajtem následovaným koncovým bajtem. Vedoucí bajty jsou odlišeny tím, že v určitém rozsahu pro danou znakovou sadu. Například v kódu stránky 932 pouze jsou vedoucí bajty v rozsahu 0x81 – 0x9F a 0xE0 – 0xFC.

**_ismbblead** používá aktuální národní prostředí pro závislá chování. **_ismbblead_l –** je stejná s tím rozdílem, že používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Vždy vrátí hodnotu false|**_ismbblead**|Vždy vrátí hodnotu false|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbblead_l**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Pro konstanty manifestu pro zkušební podmínky.

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
