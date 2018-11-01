---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 03/22/2018
apiname:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 932a7827ef61a5e111f86f8bc44291827843b76e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505661"
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Formátovací řetězec času.

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

*Parametr MaxSize*<br/>
Velikost *strDest* vyrovnávací paměti, měřeno v znaků (**char** nebo **wchar_t**).

*Formát*<br/>
Řetězec řízení formátu

*timeptr*<br/>
**TM** datové struktury.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**STRFTIME** vrátí počet znaků, které jsou umístěny v *strDest* a **wcsftime** vrátí odpovídající počet širokých znaků.

Celkový počet znaků, včetně ukončujícího znaku null, je-li více než *maxsize*, obě **strftime** a **wcsftime** vrátí 0 a obsah  *strDest* jsou neurčité.

Počet znaků v *strDest* je rovna počtu literálními znaky ve *formátu* a také všechny znaky, které mohou být přidány do *formátu* prostřednictvím formátování kódů. Ukončující znak null řetězce se nepočítá ve vrácené hodnotě.

## <a name="remarks"></a>Poznámky

**Strftime** a **wcsftime** funkce formátu **tm** časové hodnoty ve *timeptr* podle zadané  *Formát* argument a uloží výsledek do vyrovnávací paměti *strDest*. Maximálně *maxsize* znaky jsou umístěny v řetězci. Popis pole *timeptr* struktury, přečtěte si téma [asctime –](asctime-wasctime.md). **wcsftime** je ekvivalentem širokého znaku **strftime**; její argument ukazatele na řetězec odkazuje na řetězec širokých znaků. Tyto funkce chovají identicky jinak.

Tato funkce ověřuje své parametry. Pokud *strDest*, *formátu*, nebo *timeptr* je ukazatel s hodnotou null, nebo pokud **tm** řešený datová struktura *timeptr* je neplatná (například, pokud obsahuje mimo rozsah hodnot pro času nebo data), nebo pokud *formátu* řetězec obsahuje neplatný kód formátování, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, funkce vrátí hodnotu 0 a nastaví **errno** k **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime –**|**STRFTIME**|**STRFTIME**|**wcsftime**|

*Formátu* argument se skládá z jednoho nebo více kódů; protože v **printf**, formátování kódy jsou uvozená znakem procent (**%**). Znaky, které nezačínají **%** zkopírují beze změny do *strDest*. **LC_TIME** kategorie aktuálního národního prostředí má vliv na výstupní formátování **strftime**. (Další informace o **LC_TIME**, naleznete v tématu [setlocale](setlocale-wsetlocale.md).) **Strftime** a **wcsftime** aktuálně nastavené pomocí funkce národního prostředí. **_Strftime_l –** a **_wcsftime_l –** verze těchto funkcí jsou identické, s tím rozdílem, že trvat národního prostředí jako parametr a použít namísto v současné době nastavené národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**Strftime** funkce podporují tyto formátovací kódy:

|||
|-|-|
|Kód|Řetězci pro nahrazení|
|**%a**|Zkrácený název dne v národním prostředí|
|**%A**|Úplný název dne v národním prostředí|
|**%b**|Zkrácený název měsíce v národním prostředí|
|**%B**|Úplný název měsíce v národním prostředí|
|**%c**|Datum a čas reprezentace vhodné pro národní prostředí|
|**%C**|Rok, vydělí se číslem 100 a zkrácen na celočíselnou hodnotu jako desetinné číslo (00−99)|
|**%d**|Den v měsíci jako desetinné číslo (01-31)|
|**%D**|Ekvivalentní **%m/%d/%y**|
|**%e**|Den v měsíci jako desetinné číslo (1-31), kde jeden číslic předchází mezeru|
|**%F**|Ekvivalentní **%Y - min %– %d**|
|**%g**|Poslední 2 číslice rok týden podle ISO 8601 jako desítkové číslo (00 - 99)|
|**%G**|Rok týden podle ISO 8601 jako desítkové číslo|
|**%h**|Zkrácený název měsíce (ekvivalentní **%b**)|
|**%H**|Hodiny ve 24hodinovém formátu (00 - 23)|
|**%I**|Hodiny ve 12hodinovém formátu (01-12)|
|**%j**|Den v roce jako desetinné číslo (001-366)|
|**%m**|Měsíce jako desetinné číslo (01-12)|
|**%M**|Minuty jako desetinné číslo (00 - 59)|
|**%n**|Znak nového řádku (**\n**)|
|**%p**|12hodinovém národního prostředí. Indikátor pro 12hodinový formát|
|**%r**|Národního prostředí 12hodinový formát času|
|**%R**|Ekvivalentní **% H: %M**|
|**%S**|Druhý jako desetinné číslo (00 - 59)|
|**%t**|Znak horizontálního tabulátoru (**\t**)|
|**%T**|Ekvivalentní **% H: % M: %S**, formát času ISO 8601|
|**%u**|ISO 8601 den v týdnu jako desetinné číslo (1-7; Pondělí je 1)|
|**%U**|Číslo týdne v roce jako desetinné číslo (00 - 53), kde První neděle je první den v týdnu 1|
|**%V**|ISO 8601. číslo týdne jako desítkové číslo (00 - 53)|
|**%w**|Den v týdnu jako desetinné číslo (0 – 6; 0 je neděle)|
|**%W**|Číslo týdne v roce jako desetinné číslo (00 - 53), kde první pondělí je první den v týdnu 1|
|**%x**|Datum reprezentaci pro národní prostředí|
|**%X**|Čas reprezentace pro národní prostředí|
|**%y**|Rok bez století, jako desetinné číslo (00 - 99)|
|**%Y**|Rok se stoletím jako desetinné číslo|
|**%z**|Posun od času UTC ve formátu ISO 8601. žádné znaky, pokud se časové pásmo neznámý|
|**%Z**|Časové pásmo název národního prostředí nebo zkratku časové pásmo, v závislosti na nastavení registru. žádné znaky, pokud se časové pásmo neznámý|
|**%%**|Znak procent|

Stejně jako **printf** funkce, **#** příznak může předpony žádné formátování kódu. V takovém případě význam formátovat kód je změněno následovně.

|Formátování kódu|Význam|
|-----------------|-------------|
|**% #**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X** , **%#z**, **%#Z**, **%#%**|**#** Příznak se ignoruje.|
|**%#c**|Dlouhé datum a čas reprezentace, vhodné pro národní prostředí. Příklad: "Úterý, 14 dne 1995, 12:41:29".|
|**%#x**|Datum (dlouhé) reprezentaci, vhodné pro národní prostředí. Příklad: "Úterý, 14 dne 1995".|
|**%#d**, **%#D**, **%#e**, **%#F**, **%#H**, **% #I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S**, **%#T** , **%#U**, **%#V**, **%#W**, **%#y**, **%#Y**|Odeberte počátečních nul nebo mezery (pokud existuje).|

ISO 8601-týden a na základě týden roku vytvářených **%V**, **%g**, a **%G**, používá týden, který začíná v pondělí, kde je v týdnu, který obsahuje od 4, což je první 1 týden týden, který obsahuje alespoň čtyři dny v roce. Pokud první pondělí rok 2, 3 nebo 4, předchozí dny jsou součástí minulý týden v předchozím roce. U těchto dnů **%V** nahrazuje 53 a oba **%g** a **%G** nahrazují číslic v předchozím roce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**STRFTIME**|\<Time.h >|
|**wcsftime**|\<Time.h > nebo \<wchar.h >|
|**_strftime_l**|\<Time.h >|
|**_wcsftime_l**|\<Time.h > nebo \<wchar.h >|

**_Strftime_l –** a **_wcsftime_l –** funkce jsou specifické pro společnost Microsoft. Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [čas](time-time32-time64.md).

## <a name="see-also"></a>Viz také:

[Národní prostředí](../../c-runtime-library/locale.md) <br/>
[Správa času](../../c-runtime-library/time-management.md) <br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
