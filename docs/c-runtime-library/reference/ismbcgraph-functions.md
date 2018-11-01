---
title: _ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l
ms.date: 11/04/2016
apiname:
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
ms.openlocfilehash: 05946def8c4d832751554a1653afa98c9965fee9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626210"
---
# <a name="ismbcgraph-ismbcgraphl-ismbcprint-ismbcprintl-ismbcpunct-ismbcpunctl-ismbcblank-ismbcblankl-ismbcspace-ismbcspacel"></a>_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l

Určuje, zda je znak grafický znak, znak zobrazení, znak interpunkce nebo znak mezery.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*c*<br/>
Znak k určení.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud znak splňuje testovací podmínku, nebo 0, pokud tomu tak není. Pokud *c* < = 255 a existuje odpovídající **_ismbb –** rutina (například **_ismbcalnum –** odpovídá **_ismbbalnum –**), Výsledkem je návratová hodnota odpovídající **_ismbb –** rutiny.

Verze těchto funkcí jsou identické, s tím rozdílem, že ty, které mají **_l** přípona používají národní prostředí předané pro své chování závislé na národním prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí testujte daný vícebajtový znak na danou podmínku.

|Rutina|Testovací podmínka|Příklad znakové stránky 932|
|-------------|--------------------|---------------------------|
|**_ismbcgraph**|Obrázek|Vrátí nenulovou hodnotu právě tehdy *c* je jednobajtové znázornění libovolného ASCII nebo písma katakana tisknutelného znaku kromě mezery ().|
|**_ismbcprint**|Tisknutelný|Vrátí nenulovou hodnotu právě tehdy *c* je jednobajtové znázornění jakékoli ASCII nebo písma katakana tisknutelný znak včetně mezery ().|
|**_ismbcpunct**|Interpunkční znaménka|Vrátí nenulovou hodnotu právě tehdy *c* je jednobajtové znázornění libovolného znaku ASCII nebo písma katakana interpunkce.|
|**_ismbcblank**|Mezera nebo horizontální tabelátor|Vrátí nenulovou hodnotu právě tehdy *c* je znak mezery nebo znak horizontálního tabulátoru: *c*= 0x20 nebo *c*= 0x09.|
|**_ismbcspace**|Prázdné znaky|Vrátí nenulovou hodnotu právě tehdy *c* je prázdný znak: *c*= 0x20 nebo 0x09 < =*c*< = 0x0D.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbcgraph**|\<Mbstring.h >|
|**_ismbcgraph_l**|\<Mbstring.h >|
|**_ismbcprint**|\<Mbstring.h >|
|**_ismbcprint_l**|\<Mbstring.h >|
|**_ismbcpunct**|\<Mbstring.h >|
|**_ismbcpunct_l**|\<Mbstring.h >|
|**_ismbcblank**|\<Mbstring.h >|
|**_ismbcblank_l**|\<Mbstring.h >|
|**_ismbcspace**|\<Mbstring.h >|
|**_ismbcspace_l**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
