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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 5da2c128c54fd88bb874b360f5a966f17b14a935
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350009"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Naformátujte časový řetězec.

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

*Maxsize*<br/>
Velikost *strDest* vyrovnávací paměti, měřeno ve znacích **(char** nebo **wchar_t).**

*Formát*<br/>
Řetězec řízení formátu

*timeptr*<br/>
**tm** datové struktury.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strftime** vrátí počet znaků umístěných v *strDest* a **wcsftime** vrátí odpovídající počet širokých znaků.

Pokud je celkový počet znaků, včetně ukončující null, je větší než *maxsize*, **strftime** a **wcsftime** vrátit 0 a obsah *strDest* jsou neurčité.

Počet znaků v *strDest* se rovná počtu literálznaků ve *formátu,* stejně jako všechny znaky, které mohou být přidány do *formátu* pomocí formátovacích kódů. Ukončující null řetězce se nepočítá v vrácené hodnotě.

## <a name="remarks"></a>Poznámky

Funkce **strftime** a **wcsftime** formátují hodnotu **času tm** v *timeptr* podle zadaného *argumentu formátu* a ukládají výsledek do *strDest*vyrovnávací paměti . Maximálně *maxsize* znaky jsou umístěny v řetězci. Popis polí ve struktuře *timeptr* naleznete v tématu [asctime](asctime-wasctime.md). **wcsftime** je širokoznakový ekvivalent **strftime**; jeho argument ukazatel řetězce odkazuje na řetězec s širokým znakem. Tyto funkce se chovají stejně jinak.

Tato funkce ověřuje její parametry. Pokud *strDest*, *format*nebo *timeptr* je nulový ukazatel nebo pokud je datová struktura **tm** adresovaná *timeptr* neplatná (například pokud obsahuje hodnoty mimo rozsah pro čas nebo datum) nebo pokud *formátovací* řetězec obsahuje neplatný formátovací kód, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí 0 a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**Strftime**|**Strftime**|**wcsftime**|

Argument *formátu* se skládá z jednoho nebo více kódů; jako v **printf**, formátovací kódy předchází**%** znaménko procenta ( ). Znaky, které nezačínají, **%** jsou zkopírovány beze změny do *strDest*. Kategorie **LC_TIME** aktuálního národního prostředí ovlivňuje výstupní formátování **strftime**. (Další informace o **LC_TIME**naleznete v [tématu setlocale](setlocale-wsetlocale.md).) Funkce **strftime** a **wcsftime** používají aktuálně nastavené národní prostředí. **Verze _strftime_l** a **_wcsftime_l** těchto funkcí jsou identické s tím rozdílem, že berou národní prostředí jako parametr a používají jej namísto aktuálně nastaveného národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Funkce **strftime** podporují tyto formátovací kódy:

|||
|-|-|
|kód|Náhradní řetězec|
|**%a**|Zkrácený název dne v týdnu v národním prostředí|
|**%A**|Úplný název dne ve všední dny v národním prostředí|
|**%b**|Zkrácený název měsíce v národním prostředí|
|**%B**|Úplný název měsíce v národním prostředí|
|**%c**|Reprezentace data a času vhodná pro národní prostředí|
|**%c**|Rok vydělený 100 a zkrácený na celé číslo jako desítkové číslo (00−99)|
|**%d**|Den v měsíci jako desítkové číslo (01 - 31)|
|**%d**|Odpovídá **%m/%d/%y**|
|**%e**|Den v měsíci jako desítkové číslo (1 - 31), kde jednociferné číslice předchází mezera|
|**%F**|Odpovídá **%Y-%m-%d**|
|**%g**|Poslední 2 číslice roku založeného na týdnu ISO 8601 jako desítkové číslo (00 - 99)|
|**%g**|Týden založený na iso 8601 jako desítkové číslo|
|**%h**|Zkrácený název měsíce (odpovídá **%b**)|
|**%H**|Hodina ve 24hodinovém formátu (00 - 23)|
|**%i**|Hodina ve 12hodinovém formátu (01 - 12)|
|**%j**|Den v roce jako desítkové číslo (001 - 366)|
|**%m**|Měsíc jako desítkové číslo (01 - 12)|
|**%M**|Minuta jako desítkové číslo (00 - 59)|
|**%n**|Znak nového řádku (**\n**)|
|**%p**|Národní prostředí je A.M./P.M. indikátor pro 12hodinové hodiny|
|**%r**|12hodinový čas národního prostředí|
|**%R**|Odpovídá **%H:%M**|
|**%s**|Druhé jako desítkové číslo (00 - 59)|
|**%t**|Vodorovný znak tabulátoru (**\t**)|
|**%T**|Odpovídá **%H:%M:%S**, formátu času ISO 8601|
|**%u**|ISO 8601 ve všední den jako desítkové číslo (1 - 7; Pondělí je 1)|
|**%u**|Číslo týdne roku jako desítkové číslo (00 - 53), kde první neděle je první den v týdnu 1|
|**%V**|Číslo týdne ISO 8601 jako desítkové číslo (00 - 53)|
|**%w**|Den v týdnu jako desítkové číslo (0 - 6; Neděle je 0)|
|**%W**|Číslo týdne roku jako desítkové číslo (00 - 53), kde první pondělí je první den v týdnu 1|
|**%x**|Reprezentace data pro národní prostředí|
|**%X**|Reprezentace času pro národní prostředí|
|**%y**|Rok bez století, jako desetinné číslo (00 - 99)|
|**%Y**|Rok s stoletím jako desítkové číslo|
|**%z**|Posun od UTC ve formátu ISO 8601; žádné znaky, pokud časové pásmo není známo|
|**%Z**|Název časového pásma národního prostředí nebo zkratka časového pásma v závislosti na nastavení registru; žádné znaky, pokud časové pásmo není známo|
|**%%**|Znak procenta|

Stejně jako ve funkci **#** **printf** může příznak předponu jakýkoli kód formátování. V takovém případě se význam formátu kódu změní takto.

|Formátování kódu|Význam|
|-----------------|-------------|
|**%#a**, **%#A**, **%#b #B**, **%#g #B**, **%#B**, **%#G**, **%#h**, **%#n #h**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X**, **%#z**, **%#Z**,**%#%**|**#** příznak je ignorován.|
|**%#c**|Dlouhé reprezentace data a času, vhodné pro národní prostředí. Například: "Úterý, Březen 14, 1995, 12:41:29".|
|**%#x**|Reprezentace dlouhého data, vhodné pro národní prostředí. Například: "Úterý, březen 14, 1995".|
|**%#d**, **%#D**, **%#e**, **%#F**, **%#H**, **%#I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S**, **%#T**, **%#U**, **%#V**, **%#W**, **%#y**, **%#Y**|Odstraňte úvodní nuly nebo mezery (pokud existuje).|

Týden a týden založený na iso 8601 produkovaný **%V**, **%g**a **%G**používá týden, který začíná v pondělí, kde týden 1 je týden, který obsahuje 4. Pokud je první pondělí v roce druhé, třetí nebo čtvrté, jsou předchozí dny součástí posledního týdne předchozího roku. Pro tyto dny je **%V** nahrazeno číslem 53 a **%g** i **%G** jsou nahrazeny číslicemi předchozího roku.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Strftime**|\<time.h>|
|**wcsftime**|\<time.h> \<nebo wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> \<nebo wchar.h>|

Funkce **_strftime_l** a **_wcsftime_l** jsou specifické pro společnost Microsoft. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad [pro čas](time-time32-time64.md).

## <a name="see-also"></a>Viz také

[Národní prostředí](../../c-runtime-library/locale.md) <br/>
[Časová správa](../../c-runtime-library/time-management.md) <br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
