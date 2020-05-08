---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 4/2/2020
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
- _o__strftime_l
- _o__wcsftime_l
- _o_strftime
- _o_wcsftime
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: 9d262371369681cbbd5975a733950d6c4150fd88
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920025"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Formátování času řetězce.

## <a name="syntax"></a>Syntaxe

```C
size_t strftime(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr
);
size_t _strftime_l(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr,
   _locale_t locale
);
size_t wcsftime(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr
);
size_t _wcsftime_l(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strDest*<br/>
Výstupní řetězec.

*MaxSize*<br/>
Velikost vyrovnávací paměti *strDest* měřená v znacích (**char** nebo **wchar_t**).

*formátovat*<br/>
Řetězec řízení formátu

*timeptr*<br/>
datová struktura **TM**

*locale*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strftime** vrátí počet znaků umístěných v *strDest* a **wcsftime** vrátí odpovídající počet velkých znaků.

Pokud celkový počet znaků, včetně ukončující hodnoty null, je větší než *MaxSize*, **strftime** a **wcsftime** vrátí 0 a obsah *strDest* jsou neurčitelné.

Počet znaků v *strDest* se rovná počtu literálních znaků ve *formátu* a znaků, které mohou být přidány do *formátu* prostřednictvím kódů formátování. Ukončující hodnota null řetězce se nepočítá v návratové hodnotě.

## <a name="remarks"></a>Poznámky

Funkce **strftime** a **wcsftime** naformátují hodnotu času **TM** v *timeptr* podle zadaného argumentu *formátu* a výsledek uloží do vyrovnávací paměti *strDest*. Do řetězce se nanejvýš vloží znaky *MaxSize* . Popis polí ve struktuře *timeptr* naleznete v tématu [asctime](asctime-wasctime.md). **wcsftime** je ekvivalentem **strftime**; Argument ukazatele na řetězec odkazuje na řetězec s velkým znakem. Tyto funkce se chovají identicky jinak.

Tato funkce ověří své parametry. Pokud je *strDest*, *Format*nebo *timeptr* ukazatel s hodnotou null, nebo pokud je struktura dat **TM** adresovaná v *timeptr* neplatná (například pokud obsahuje mimo rozsah hodnot pro čas nebo datum) nebo pokud *formátovací* řetězec obsahuje neplatný kód formátování, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce hodnotu 0 a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

Argument *Format* se skládá z jednoho nebo více kódů; Jak je uvedeno v **printf**, před kódy formátování předchází znak procenta (**%**). Znaky, které nejsou začínat **%** , se zkopírují beze změny do *strDest*. Kategorie **LC_TIME** aktuálního národního prostředí má vliv na formátování výstupu **strftime**. (Další informace o **LC_TIME**najdete v tématu [setlocale](setlocale-wsetlocale.md).) Funkce **strftime** a **wcsftime** používají aktuálně nastavené národní prostředí. **_Strftime_l** a **_wcsftime_l** verze těchto funkcí jsou identické, s tím rozdílem, že přebírají národní prostředí jako parametr a používají jej namísto aktuálně nastaveného národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Funkce **strftime** podporují tyto kódy formátování:

|||
|-|-|
|kód|Řetězec pro nahrazení|
|**% a**|Zkrácený název dne v týdnu v národním prostředí|
|**% A**|Úplný název dne v týdnu v národním prostředí|
|**% b**|Zkrácený název měsíce v národním prostředí|
|**% B**|Úplný název měsíce v národním prostředí|
|**% c**|Reprezentace data a času, která je vhodná pro národní prostředí|
|**% C**|Rok dělený 100 a zkrácený na celé číslo, jako desetinné číslo (00 − 99)|
|**% d**|Den v měsíci jako desetinné číslo (01-31)|
|**% D**|Ekvivalent k **% m/% d/% y**|
|**% e**|Den v měsíci jako desetinné číslo (1-31), kde před sebou následují číslice|
|**% F**|Ekvivalent **% Y-% m-% d**|
|**% g**|Poslední 2 číslice roku založeného na standardu ISO 8601 jako desetinné číslo (00-99)|
|**% G**|Rok založený na týdnu ISO 8601 jako desetinné číslo|
|**% h**|Zkrácený název měsíce (ekvivalent **% b**)|
|**% H**|Hodiny ve 24hodinovém formátu (00-23)|
|**% I**|Hodiny ve 12hodinovém formátu (01-12)|
|**% j**|Den v roce jako desetinné číslo (001-366)|
|**% m**|Měsíc jako desetinné číslo (01-12)|
|**% M**|Minuta jako desetinné číslo (00-59)|
|**% n**|Znak nového řádku (**\n**)|
|**% p**|/P.M. národního prostředí indikátor pro 12 hodin|
|**% r**|12 hodinový čas národního prostředí|
|**% R**|Ekvivalent **% H:%M**|
|**% S**|Sekunda jako desetinné číslo (00-59)|
|**% t**|Znak horizontálního tabulátoru (**\t**)|
|**% T**|Ekvivalent **% H:%M:% S**, formát času ISO 8601|
|**% u**|ISO 8601 Weekday jako desetinné číslo (1-7; Pondělí je 1)|
|**% U**|Číslo týdne v roce jako desetinné číslo (00-53), kde první neděle je první den v týdnu 1|
|**% V**|Číslo ISO 8601 týdnů jako desetinné číslo (00-53)|
|**% w**|Weekday v týdnu jako desetinné číslo (0-6; Neděle je 0)|
|**% W**|Číslo týdne v roce jako desetinné číslo (00-53), kde první pondělí je první den v týdnu 1|
|**% x**|Reprezentace data pro národní prostředí|
|**% X**|Časová reprezentace národního prostředí|
|**% y**|Rok bez století, jako desetinné číslo (00-99)|
|**% Y**|Rok s století, jako desetinné číslo|
|**% z**|Posun od času UTC ve formátu ISO 8601; žádné znaky, pokud je časové pásmo neznámé|
|**% Z**|Název časového pásma národního prostředí nebo zkratka časového pásma, v závislosti na nastavení registru; žádné znaky, pokud je časové pásmo neznámé|
|**%%**|Symbol procenta|

Stejně jako ve funkci **printf** může **#** příznak označovat libovolný formátovací kód. V takovém případě je význam formátu kódu změněn následujícím způsobem.

|Formátování kódu|Význam|
|-----------------|-------------|
|**% #a**, **% #A**, **% #b**, **% #B**, **% #g**, **%**#G **,%** **#h,%**#n, **% #p**, **% #t**, **% #u,%** **#w**, **% #X,**% **#z,%** **#Z,****%#%**|**#** příznak je ignorován.|
|**% #c**|Dlouhé reprezentace data a času, která je vhodná pro národní prostředí. Například: "úterý, 14. března, 1995, 12:41:29".|
|**% #x**|Dlouhé reprezentace data, která je vhodná pro národní prostředí. Například: "úterý, 14. března 1995".|
|**% #d**, **% #D**, **% #e**, **% #F**, **% #H**, **%**#I,% **#j,%** **#m,**% **#M**,% **#r**, **% #R,**% **#S,%** **#T**, **% #U**,% **#V,%** **#W,**% #y, **%#Y** % **#Y,%**|Odebrat úvodní nuly nebo mezery (pokud existují).|

ISO 8601 týden a týden založený na týdnu vytvořil **% V**, **% g**a **% g**používá týden, který začíná v pondělí, kde týden 1 je týden, který obsahuje 4. ledna, což je první týden, který obsahuje nejméně čtyři dny v roce. Pokud je první pondělí roku v roce 2., 3. nebo 4., jsou předchozí dny součástí posledního týdne předchozího roku. V těchto dnech je **% V** nahrazeno 53, přičemž **% g** i **% g** jsou nahrazeny číslicemi předchozího roku.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strftime**|\<Time. h>|
|**wcsftime**|\<Time. h> nebo \<WCHAR. h>|
|**_strftime_l**|\<Time. h>|
|**_wcsftime_l**|\<Time. h> nebo \<WCHAR. h>|

Funkce **_strftime_l** a **_wcsftime_l** jsou specifické pro společnost Microsoft. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [čas](time-time32-time64.md).

## <a name="see-also"></a>Viz také

[Jazyka](../../c-runtime-library/locale.md) <br/>
[Časová správa](../../c-runtime-library/time-management.md) <br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
