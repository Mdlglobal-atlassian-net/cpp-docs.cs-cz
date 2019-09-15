---
title: _ismbbtrail, _ismbbtrail_l
ms.date: 11/04/2016
api_name:
- _ismbbtrail
- _ismbbtrail_l
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
- _ismbbtrail
- ismbbtrail
- _ismbbtrail_l
- ismbbtrail_l
helpviewer_keywords:
- ismbbtrail_l function
- _ismbbtrail function
- _ismbbtrail_l function
- ismbbtrail function
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
ms.openlocfilehash: e445de41b05ac4829bdf108d1c98113cd5240ec0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953976"
---
# <a name="_ismbbtrail-_ismbbtrail_l"></a>_ismbbtrail, _ismbbtrail_l

Určuje, zda bajt je koncovým bajtem vícebajtového znaku.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbtrail(
   unsigned int c
);
int _ismbbtrail_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo, které má být testováno.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_ismbbtrail** vrací nenulovou hodnotu, pokud je celé číslo *c* druhým bajtem vícebajtového znaku. Například v kódové stránce 932 jsou platné rozsahy 0x40 pro 0x7E a 0x80 až 0xFC.

## <a name="remarks"></a>Poznámky

**_ismbbtrail** používá aktuální národní prostředí pro chování závislé na národním prostředí. **_ismbbtrail_l** je totožný s tím rozdílem, že místo toho používá národní prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_ismbbtrail**|\<Mbctype. h > nebo \<Mbstring. h >|\<CType. h >, * \<Limits. h > \<, Stdlib. h >|
|**_ismbbtrail_l**|\<Mbctype. h > nebo \<Mbstring. h >|\<CType. h >, * \<Limits. h > \<, Stdlib. h >|

\*Pro konstanty manifestu pro podmínky testu.

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
