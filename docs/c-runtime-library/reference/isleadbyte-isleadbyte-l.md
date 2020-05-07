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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 078efc2fa5499e23ce7f2fb6f8fc0ffc5123de1e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909542"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

Určuje, zda je znakem vedoucí bajt vícebajtového znaku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parametry

*r*<br/>
Celé číslo k otestování.

## <a name="return-value"></a>Návratová hodnota

**isleadbyte** vrací nenulovou hodnotu, pokud argument splňuje podmínku testu nebo 0, pokud tomu tak není. V národním prostředí "C" a v prostředích s jednou bajtovou znakovou sadou (SBCS) **isleadbyte** vždycky vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Makro **isleadbyte** vrací nenulovou hodnotu, pokud je jeho argument první bajt vícebajtového znaku. **isleadbyte** vytváří smysluplný výsledek pro libovolný celočíselný argument z-1 (**EOF**) do **UCHAR_MAX** (0xFF) včetně.

Očekávaný typ argumentu **isleadbyte** je **int**; Pokud je předán znak se znaménkem, kompilátor jej může převést na celé číslo podle přípony znaménka a vracet nepředvídatelné výsledky.

Verze této funkce s příponou **_l** je shodná s tím rozdílem, že používá předané národní prostředí namísto aktuálního národního prostředí pro své chování závislé na národním prostředí.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Vždycky vrátí hodnotu false.|**_isleadbyte**|Vždycky vrátí hodnotu false.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isleadbyte**|\<CType. h>|
|**_isleadbyte_l**|\<CType. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Rutiny _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
