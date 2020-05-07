---
title: _ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l
ms.date: 4/2/2020
api_name:
- _ismbcpunct_l
- _ismbcblank
- _ismbcprint
- _ismbcgraph_l
- _ismbcblank_l
- _ismbcpunct
- _ismbcprint_l
- _ismbcspace_l
- _ismbcspace
- _ismbcgraph
- _o__ismbcblank
- _o__ismbcblank_l
- _o__ismbcgraph
- _o__ismbcgraph_l
- _o__ismbcprint
- _o__ismbcprint_l
- _o__ismbcpunct
- _o__ismbcpunct_l
- _o__ismbcspace
- _o__ismbcspace_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbcspace
- _ismbcgraph
- _ismbcpunct
- ismbcspace_l
- ismbcgraph
- _ismbcgraph_l
- _ismbcprint
- _ismbcspace_l
- ismbcprint
- ismbcgraph_l
- ismbcspace
- ismbcpunct
helpviewer_keywords:
- ismbcspace_l function
- _ismbcprint_l function
- ismbcspace function
- ismbcpunct function
- _ismbcspace_l function
- _ismbcprint function
- ismbcprint function
- _ismbcgraph function
- ismbcgraph_l function
- _ismbcpunct_l function
- ismbcpunct_l function
- ismbcprint_l function
- _ismbcpunct function
- ismbcgraph function
- _ismbcgraph_l function
- _ismbcspace function
ms.assetid: 8e0a5f47-ba64-4411-92a3-3c525d16e3be
ms.openlocfilehash: 5f2c8b595de323994aa670a8e0fee9e562897e49
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919766"
---
# <a name="_ismbcgraph-_ismbcgraph_l-_ismbcprint-_ismbcprint_l-_ismbcpunct-_ismbcpunct_l-_ismbcblank-_ismbcblank_l-_ismbcspace-_ismbcspace_l"></a>_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l

Určuje, zda je znak grafický znak, znak zobrazení, znak interpunkce nebo znak mezery.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbcgraph(
   unsigned int c
);
int _ismbcgraph_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcprint(
   unsigned int c
);
int _ismbcprint_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcpunct(
   unsigned int c
);
int _ismbcpunct_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcblank(
   unsigned int c
);
int _ismbcblank_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcspace(
   unsigned int c
);
int _ismbcspace_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*r*<br/>
Znak, který má být určen.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrací nenulovou hodnotu, pokud znak splňuje testovací podmínku, nebo 0, pokud tomu tak není. Pokud *c* <= 255 a existuje odpovídající rutina **_ismbb** (například **_ismbcalnum** odpovídá **_ismbbalnum**), výsledkem je návratová hodnota odpovídající **_ismbb** rutiny.

Verze těchto funkcí jsou identické, s tím rozdílem, že ty, které mají příponu **_l** používají národní prostředí, které je předáno pro své chování závislé na národním prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí testuje daný vícebajtový znak pro danou podmínku.

|Rutina|Testovací podmínka|Příklad znakové stránky 932|
|-------------|--------------------|---------------------------|
|**_ismbcgraph**|Objekty|Vrátí nenulovou hodnotu, pokud a pouze v případě, že *c* je jednobajtové znázornění libovolného tisknutelného znaku ASCII nebo katakana s výjimkou mezer ().|
|**_ismbcprint**|Tisknutelný|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtové znázornění libovolného tisknutelného znaku ASCII nebo katakana, včetně mezer ().|
|**_ismbcpunct**|Interpunkční znaménka|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtové znázornění znaku interpunkce ASCII nebo Katakana.|
|**_ismbcblank**|Mezera nebo horizontální tabulátor|Vrátí nenulovou hodnotu pouze v případě, že *c* je mezera nebo horizontální znak tabulátoru: *c*= 0x20 nebo *c*= 0x09.|
|**_ismbcspace**|Prázdné znaky|Vrátí nenulovou hodnotu, pokud je *c* znak prázdné místo: *c*= 0x20 nebo 0x09<=*c*<= 0x0D.|

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbcgraph**|\<Mbstring. h>|
|**_ismbcgraph_l**|\<Mbstring. h>|
|**_ismbcprint**|\<Mbstring. h>|
|**_ismbcprint_l**|\<Mbstring. h>|
|**_ismbcpunct**|\<Mbstring. h>|
|**_ismbcpunct_l**|\<Mbstring. h>|
|**_ismbcblank**|\<Mbstring. h>|
|**_ismbcblank_l**|\<Mbstring. h>|
|**_ismbcspace**|\<Mbstring. h>|
|**_ismbcspace_l**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[je, rutiny ISW](../../c-runtime-library/is-isw-routines.md)<br/>
[Rutiny _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
