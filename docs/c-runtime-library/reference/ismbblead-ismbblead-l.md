---
title: _ismbblead, _ismbblead_l
ms.date: 11/04/2016
api_name:
- _ismbblead_l
- _ismbblead
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
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: c0f9ec748a86d5d1413cf4f881234d786c2a2d78
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954055"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead, _ismbblead_l

Testuje znak pro určení, zda se jedná o vedoucí bajt vícebajtového znaku.

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
Celé číslo, které se má testovat.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud je celé číslo *c* první bajt vícebajtového znaku.

## <a name="remarks"></a>Poznámky

Vícebajtové znaky se skládají z vedoucího bajtu následovaného koncovým bajtem. Vedoucí bajty jsou odlišeny v určitém rozsahu pro danou znakovou sadu. Například pouze v kódové stránce 932 je v rozsahu od 0x81-0x9F a 0xE0-0xFC.

**_ismbblead** používá aktuální národní prostředí pro chování závislé na národním prostředí. **_ismbblead_l** je totožný s tím rozdílem, že místo toho používá národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Vždycky vrátí hodnotu false.|**_ismbblead**|Vždycky vrátí hodnotu false.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<Mbctype. h > nebo \<Mbstring. h >|\<CType. h >, * \<Limits. h > \<, Stdlib. h >|
|**_ismbblead_l**|\<Mbctype. h > nebo \<Mbstring. h >|\<CType. h >, * \<Limits. h > \<, Stdlib. h >|

\*Pro konstanty manifestu pro podmínky testu.

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
