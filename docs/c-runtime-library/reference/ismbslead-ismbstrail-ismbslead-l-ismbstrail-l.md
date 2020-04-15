---
title: _ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l
ms.date: 4/2/2020
api_name:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
- _o__ismbslead
- _o__ismbslead_l
- _o__ismbstrail
- _o__ismbstrail_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbslead
- ismbs
- ismbslead_l
- _ismbs
- ismbstrail_l
- ismbslead
- _ismbstrail
- _ismbstrail_l
- ismbstrail
- _ismbslead_l
helpviewer_keywords:
- ismbstrail function
- _ismbslead function
- ismbslead function
- ismbslead_l function
- _ismbstrail function
- _ismbslead_l function
- ismbstrail_l function
- _ismbstrail_l function
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
ms.openlocfilehash: d4c9bfcec1deab8c00eb490dc044e62a6124aba3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342920"
---
# <a name="_ismbslead-_ismbstrail-_ismbslead_l-_ismbstrail_l"></a>_ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l

Provádí kontextové testy pro vícebajtové znakové úhlavní bajty a bajty stop a určuje, zda daný ukazatel podřetězce odkazuje na úvodní bajt nebo bajt stopy.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbslead(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbstrail(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbslead_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
int _ismbstrail_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Ukazatel na začátek řetězce nebo předchozí známý úvodní bajt.

*aktuální*<br/>
Ukazatel na pozici v řetězci, který má být testován.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_ismbslead** vrátí hodnotu -1, pokud je znak úvodní bajt a **_ismbstrail** vrátí hodnotu -1, pokud je znakem bajt stopy. Pokud jsou vstupní řetězce platné, ale nejsou úvodní bajt nebo bajt stopy, tyto funkce vrátí nulu. Pokud je některý z argumentů **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce vrátí **null** a nastavit **errno** **eINVAL**.

## <a name="remarks"></a>Poznámky

**_ismbslead** a **_ismbstrail** jsou pomalejší než **verze _ismbblead** a **_ismbbtrail,** protože berou v úvahu kontext řetězce.

Verze těchto funkcí, které mají **_l** příponu jsou identické s tím rozdílem, že pro jejich chování závislé na národním prostředí používají národní prostředí, které je předáno namísto aktuálního národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_ismbslead**|\<mbctype.h> \<nebo mbstring.h>|\<ctype.h>,* \<limits.h \<>, stdlib.h>|
|**_ismbstrail**|\<mbctype.h> \<nebo mbstring.h>|\<ctype.h>,* \<limits.h \<>, stdlib.h>|
|**_ismbslead_l**|\<mbctype.h> \<nebo mbstring.h>|\<ctype.h>,* \<limits.h \<>, stdlib.h>|
|**_ismbstrail_l**|\<mbctype.h> \<nebo mbstring.h>|\<ctype.h>,* \<limits.h \<>, stdlib.h>|

\*Pro manifestové konstanty pro zkušební podmínky.

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
