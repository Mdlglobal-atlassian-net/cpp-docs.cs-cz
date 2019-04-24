---
title: _ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l
ms.date: 11/04/2016
apiname:
- _ismbcl2
- _ismbcl1
- _ismbcl0
- _ismbcl2_l
- _ismbcl1_l
- _ismbcl0_l
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
- ismbcl0
- _ismbcl1_l
- _ismbcl0
- ismbcl1
- ismbcl0_l
- _ismbcl2_l
- ismbcl2
- ismbcl1_l
- _ismbcl1
- _ismbcl0_l
- _ismbcl2
- ismbcl2_l
helpviewer_keywords:
- _ismbcl0_l function
- _ismbcl2 function
- _ismbcl1_l function
- ismbcl2 function
- _ismbcl1 function
- ismbcl0_l function
- ismbcl2_l function
- ismbcl1_l function
- ismbcl0 function
- ismbcl1 function
- _ismbcl2_l function
- _ismbcl0 function
ms.assetid: ee15ebd1-462c-4a43-95f3-6735836d626a
ms.openlocfilehash: b4ea5a165e5fb06229c3fdf69c53cdf82c4f35f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286627"
---
# <a name="ismbcl0-ismbcl0l-ismbcl1-ismbcl1l-ismbcl2-ismbcl2l"></a>_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l

**Kódu stránky 932 specifické funkce**, pomocí aktuálního národního prostředí nebo zadané kategorie stavu převodu LC_CTYPE.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbcl0(
   unsigned int c
);
int _ismbcl0_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcl1(
   unsigned int c
);
int _ismbcl1_l(
   unsigned int c ,
   _locale_t locale
);
int _ismbcl2(
   unsigned int c
);
int _ismbcl2_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak k testování.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud znak splňuje testovací podmínku, nebo 0, pokud tomu tak není. Pokud *c* < = 255 a existuje odpovídající **_ismbb –** rutina (například **_ismbcalnum –** odpovídá **_ismbbalnum –**), Výsledkem je návratová hodnota odpovídající **_ismbb –** rutiny.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí testujte daný vícebajtový znak na danou podmínku.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

|Rutina|Testovací podmínka (pouze znaková stránky 932)|
|-------------|-------------------------------------------|
|**_ismbcl0**|Bez JIS-Kanji: 0x8140<=*c*<=0x889E.|
|**_ismbcl0_l**|Bez JIS-Kanji: 0x8140<=*c*<=0x889E.|
|**_ismbcl1**|Úroveň JIS-1: 0x889F < =*c*< = 0x9872.|
|**_ismbcl1_l**|Úroveň JIS-1: 0x889F < =*c*< = 0x9872.|
|**_ismbcl2**|Úroveň JIS-2: 0x989F<=*c*<=0xEAA4.|
|**_ismbcl2_l**|Úroveň JIS-2: 0x989F<=*c*<=0xEAA4.|

Funkce ověří, zda zadaná hodnota *c* odpovídá zkušebním podmínkám popsaným výše, ale nekontrolují, zda *c* je platný vícebajtový znak. Pokud nižší bajt je v rozsahu 0x00 – 0x3F, 0x7F nebo 0xFD – 0xFF, tyto funkce vrátí nenulovou hodnotu, která udává, že znak splňuje testovací podmínku. Použití [_ismbbtrail](ismbbtrail-ismbbtrail-l.md) k ověření, zda je vícebajtový znak definován.

**End specifické pro kódovou stránku 932**

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbcl0**|\<Mbstring.h >|
|**_ismbcl0_l**|\<Mbstring.h >|
|**_ismbcl1**|\<Mbstring.h >|
|**_ismbcl1_l**|\<Mbstring.h >|
|**_ismbcl2**|\<Mbstring.h >|
|**_ismbcl2_l**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
