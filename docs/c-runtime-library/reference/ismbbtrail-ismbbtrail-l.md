---
title: _ismbbtrail, _ismbbtrail_l
ms.date: 11/04/2016
apiname:
- _ismbbtrail
- _ismbbtrail_l
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
ms.openlocfilehash: 5c09884f013e878fca516388f1ad933a2a08b35a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545935"
---
# <a name="ismbbtrail-ismbbtraill"></a>_ismbbtrail, _ismbbtrail_l

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
Celé číslo k testování.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_ismbbtrail** vrací nenulovou hodnotu, pokud celé číslo *c* je druhý bajt vícebajtového znaku. Například v kódu jsou stránky 932 pouze platné rozsahy 0x40 – 0x7E a 0x80 – 0xFC.

## <a name="remarks"></a>Poznámky

**_ismbbtrail** používá aktuální národní prostředí pro závislá chování. **_ismbbtrail_l –** je totožný s tím rozdílem, že používá národní prostředí, které je předáno místo. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_ismbbtrail**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<limits.h >, \<stdlib.h >|
|**_ismbbtrail_l**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<limits.h >, \<stdlib.h >|

\* Pro konstanty manifestu pro zkušební podmínky.

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
