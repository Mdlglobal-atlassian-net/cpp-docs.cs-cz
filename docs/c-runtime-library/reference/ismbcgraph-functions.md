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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: eb76b6ebdbe4b27ce5a7368ad1b8c2dd8f858d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343243"
---
# <a name="_ismbcgraph-_ismbcgraph_l-_ismbcprint-_ismbcprint_l-_ismbcpunct-_ismbcpunct_l-_ismbcblank-_ismbcblank_l-_ismbcspace-_ismbcspace_l"></a>_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l

Určuje, zda je znak grafický znak, znak zobrazení, interpunkční znak nebo znak mezery.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*C*<br/>
Charakter, který bude určen.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud znak splňuje podmínku testu, nebo 0, pokud tomu tak není. Pokud *c* <= 255 a existuje odpovídající **_ismbb** rutina (například **_ismbcalnum** odpovídá **_ismbbalnum**), výsledkem je vrácená hodnota odpovídající **_ismbb** rutiny.

Verze těchto funkcí jsou identické, s tím rozdílem, že ty, které mají **příponu _l** použít národní prostředí, které je předáno pro jejich chování závislé na národním prostředí, namísto aktuálního národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí testuje daný vícebajtový znak pro danou podmínku.

|Rutina|Zkušební podmínka|Příklad znakové stránky 932|
|-------------|--------------------|---------------------------|
|**_ismbcgraph**|Grafické|Vrátí hodnotu nenulová pouze tehdy a pouze v *případě,* že c představuje jednobajtový znak libovolného tisknutelného znaku ASCII nebo katakana s výjimkou prázdného místa ( ).|
|**_ismbcprint**|Tisknutelné|Vrátí hodnotu nenulová pouze tehdy a pouze v *případě,* že c představuje jednobajtový reprezentaci libovolného tisknutelného znaku ASCII nebo katakana včetně prázdného místa ( ).|
|**_ismbcpunct**|Interpunkční znaménka|Vrátí nenulovou hodnotu pouze v případě, že *c* představuje jednobajtou reprezentaci libovolného interpunkčního znaku ASCII nebo katakana.|
|**_ismbcblank**|Mezera nebo vodorovná karta|Vrátí nenulovou pouze tehdy a pouze v *případě,* že c je znak mezery nebo vodorovné tabulátoru: *c*= 0x20 nebo *c*= 0x09.|
|**_ismbcspace**|Prázdné místo|Vrátí nenulovou hodnotu pouze v případě, že *c* je nefunkční znak: *c*=0x20 nebo 0x09<=*c*<=0x0D.|

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbcgraph**|\<mbstring.h>|
|**_ismbcgraph_l**|\<mbstring.h>|
|**_ismbcprint**|\<mbstring.h>|
|**_ismbcprint_l**|\<mbstring.h>|
|**_ismbcpunct**|\<mbstring.h>|
|**_ismbcpunct_l**|\<mbstring.h>|
|**_ismbcblank**|\<mbstring.h>|
|**_ismbcblank_l**|\<mbstring.h>|
|**_ismbcspace**|\<mbstring.h>|
|**_ismbcspace_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
