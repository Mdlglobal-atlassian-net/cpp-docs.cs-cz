---
title: _ismbbtrail –, _ismbbtrail_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ismbbtrail_l function
- _ismbbtrail function
- _ismbbtrail_l function
- ismbbtrail function
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e41ad2be1447946570f10028249582225386877
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399748"
---
# <a name="ismbbtrail-ismbbtraill"></a>_ismbbtrail, _ismbbtrail_l

Určuje, zda je bajt koncové bajt vícebajtových znaků.

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
Na celé číslo, které má být testována.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_ismbbtrail –** vrátí nenulovou hodnotu, pokud na celé číslo *c* je druhý bajt vícebajtových znaků. Například v kódu stránka 932 pouze, platné rozsahy jsou 0x40 k 0x7E a 0x80 k 0xFC.

## <a name="remarks"></a>Poznámky

**_ismbbtrail –** používá aktuální národní prostředí pro chování závislých na národním prostředí. **_ismbbtrail_l –** se shoduje s tím rozdílem, že používá národní prostředí, je předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_ismbbtrail –**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<Limits.h – >, \<stdlib.h >|
|**_ismbbtrail_l**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<Limits.h – >, \<stdlib.h >|

\* Pro manifest konstanty podmínky testu.

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
