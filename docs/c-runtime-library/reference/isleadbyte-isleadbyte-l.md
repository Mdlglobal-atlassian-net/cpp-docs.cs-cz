---
title: isleadbyte, _isleadbyte_l
ms.date: 4/2/2020
api_name:
- _isleadbyte_l
- isleadbyte
- _o__isleadbyte_l
- _o_isleadbyte
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: dddf1d669f77805df8e00f506b6427603ac8fd9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343843"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

Určuje, zda je znak úvodním bajtem vícebajtového znaku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parametry

*C*<br/>
Celé číslo k testování.

## <a name="return-value"></a>Návratová hodnota

**isleadbyte** vrátí nenulovou hodnotu, pokud argument splňuje podmínku testu, nebo 0, pokud tomu tak není. V národním prostředí "C" a v jednobajtové znakové sady (SBCS) národní prostředí **isleadbyte** vždy vrátí 0.

## <a name="remarks"></a>Poznámky

Makro **isleadbyte** vrátí nenulovou hodnotu, pokud je jeho argument prvním bajtem vícebajtového znaku. **isleadbyte** vytváří smysluplný výsledek pro všechny celé číslo argument od -1 (**EOF**) do **UCHAR_MAX** (0xFF), včetně.

Očekávaný typ argumentu **isleadbyte** je **int**; Pokud je předán podepsaný znak, kompilátor jej může převést na celé číslo rozšířením znaménka, což přináší nepředvídatelné výsledky.

Verze této funkce s **příponou _l** je identická s tím rozdílem, že používá národní prostředí předané místo aktuálního národního prostředí pro chování závislé na národním prostředí.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Vždy vrátí false|**_isleadbyte**|Vždy vrátí false|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_ismbb rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
