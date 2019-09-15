---
title: towctrans
ms.date: 11/04/2016
api_name:
- towctrans
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towctrans
helpviewer_keywords:
- towctrans function
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
ms.openlocfilehash: d63fc343647cd0f949f282e2a64d4a0636e62bd7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957429"
---
# <a name="towctrans"></a>towctrans

Transformuje znak.

## <a name="syntax"></a>Syntaxe

```C
wint_t towctrans(
   wint_t c,
   wctrans_t category
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak, který chcete transformovat.

*Kategorie*<br/>
Identifikátor, který obsahuje vrácenou hodnotu [wctrans](wctrans.md).

## <a name="return-value"></a>Návratová hodnota

Znak *c*, po **towctrans** použil pravidlo transformace v *kategorii*.

## <a name="remarks"></a>Poznámky

Hodnota *kategorie* musí být vrácená dřívějším úspěšným voláním metody [wctrans](wctrans.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**towctrans**|\<wctype. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Ukázku, která používá **towctrans**, najdete v tématu **wctrans** .

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
