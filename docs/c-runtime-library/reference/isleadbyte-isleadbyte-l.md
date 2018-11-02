---
title: isleadbyte, _isleadbyte_l
ms.date: 11/04/2016
apiname:
- _isleadbyte_l
- isleadbyte
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
ms.openlocfilehash: 1a3f427e49e53bb553020da100b0e713350fab3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531886"
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte, _isleadbyte_l

Určuje, zda znak je vedoucí bajt vícebajtového znaku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo k testování.

## <a name="return-value"></a>Návratová hodnota

**isleadbyte –** vrací nenulovou hodnotu, pokud argument splňuje testovací podmínku, nebo 0, pokud tomu tak není. V národním prostředí "C" a jednobajtové znakové sady (SBCS) národní prostředí, **isleadbyte –** vždy vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

**Isleadbyte –** – makro vrací nenulovou hodnotu, pokud je jeho argument první bajt vícebajtového znaku. **isleadbyte –** vytváří smysluplný výsledek pro libovolný celočíselný argument od -1 (**EOF**) k **UCHAR_MAX** (0xFF) včetně.

Očekávaný argument typu **isleadbyte –** je **int**; Pokud je předán znak se znaménkem, kompilátor ho může převést na celé číslo s rozšířením znaménka, což má za následek nepředvídatelné výsledky.

Verze této funkce se **_l** přípona je identická s tím rozdílem, že používá národní prostředí namísto aktuálního národního prostředí pro své chování závislé na národním prostředí.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte –**|Vždy vrátí hodnotu false|**_isleadbyte**|Vždy vrátí hodnotu false|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isleadbyte –**|\<ctype.h >|
|**_isleadbyte_l**|\<ctype.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
