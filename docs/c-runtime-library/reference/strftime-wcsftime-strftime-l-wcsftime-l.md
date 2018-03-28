---
title: STRFTIME –, wcsftime –, _strftime_l –, _wcsftime_l – | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc71dc09b6634e01b1ba78621344dfb5c589c8d5
ms.sourcegitcommit: 604907f77eb6c5b1899194a9877726f3e8c2dabc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Čas řetězec formátu.

## <a name="syntax"></a>Syntaxe

```
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

*maxsize*<br/>
Velikost *strDest* vyrovnávací paměť, měřená v znaků (**char** nebo **wchar_t**).

*Formát*<br/>
Řetězec řízení formátu

*timeptr*<br/>
**TM** datové struktury.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

`strftime` Vrátí počet znaků, které jsou umístěny v *strDest* a `wcsftime` vrátí odpovídající počet široké znaky.

Celkový počet znaků, včetně ukončující null, je-li více než *maxsize*, oba `strftime` a `wcsftime` vrátit 0 a obsah *strDest* jsou neurčitou.

Počet znaků v *strDest* se rovná počet literálu znaků v *formátu* a také znaky, které mohou být přidány do *formát* prostřednictvím formátování kódy. Ukončující null řetězce nepočítá v návratovou hodnotu.

## <a name="remarks"></a>Poznámky

`strftime` a `wcsftime` funkce formát **tm** čas hodnota v *timeptr* podle zadaných *formátu* argument a uložit výsledek v vyrovnávací paměť *strDest*. Maximálně *maxsize* znaky jsou umístěny v řetězci. Popis polí v *timeptr* struktury najdete v tématu [asctime –](../../c-runtime-library/reference/asctime-wasctime.md). `wcsftime` je ekvivalentem široká charakterová `strftime`; její argument řetězec ukazatel odkazuje na řetězec znaků celou. Tyto funkce chovají stejně jako jinak.

> [!NOTE]
>  Ve verzi před Visual C++ 2005 popsané v dokumentaci *formátu* parametr `wcsftime` tak, že má datový typ `const wchar_t *`, ale skutečný implementace *formát* dat typ byl `const char *`. Implementace *formátu* datový typ je aktualizovaná tak, aby odrážela předchozí a aktuální dokumentaci, který je `const wchar_t *`.

Tato funkce ověří jeho parametry. Pokud *strDest*, *formátu*, nebo *timeptr* je ukazatel s hodnotou null, nebo pokud **tm** datová struktura používala *timeptr* je neplatný (například pokud obsahuje mimo rozsah hodnoty pro čas nebo datum), nebo pokud *formát* řetězec obsahuje neplatný kód formátování, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu 0 a nastaví je povoleno spuštění **errno** k **einval –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsftime`|`strftime`|`strftime`|`wcsftime`|

*Formátu* argument se skládá z jednoho nebo více kódů; protože v `printf`, formátování kódy jsou uvozená znakem procent (**%**). Znaky, které nemají na začátku **%** se zkopírují do beze změny `strDest`. **Lc_time –** kategorie aktuální národní prostředí má vliv na výstupní formátování `strftime`. (Další informace o **lc_time –**, najdete v části [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).) `strftime` a `wcsftime` funkce používat aktuálně nastavené národní prostředí. `_strftime_l` a `_wcsftime_l` verze tyto funkce jsou identické s tím rozdílem, že trvat národní prostředí jako parametr a použijte místo aktuálně nastavené národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

`strftime` Funkce podporovat formátování kódy:

|||
|-|-|
|Kód|Náhradní řetězec|
|`%a`|Zkrácený název dne v národním prostředí|
|`%A`|Úplný název dne v národním prostředí|
|`%b`|Zkrácený název měsíce v národním prostředí|
|`%B`|Úplný název měsíce v národním prostředí|
|`%c`|Datum a čas reprezentace vhodné pro národní prostředí|
|`%C`|V roce dělený 100 a zkrácen na celé číslo jako desetinné číslo (00−99)|
|`%d`|Den v měsíci jako desetinné číslo (01-31)|
|`%D`|Ekvivalent hodnoty `%m/%d/%y`|
|`%e`|Den v měsíci jako desetinné číslo (1-31), kde jeden číslic předchází mezery|
|`%F`|Ekvivalent hodnoty `%Y-%m-%d`|
|`%g`|Poslední 2 číslic ISO 8601 na základě týden roku jako desetinné číslo (00 - 99)|
|`%G`|ISO 8601 na základě týden roku jako s desetinným číslem|
|`%h`|Zkrácený název měsíce (ekvivalentní `%b`)|
|`%H`|Hodiny ve 24hodinovém formátu (00 - 23)|
|`%I`|Hodiny ve formátu 12 hodin (01-12)|
|`%j`|Den v roce jako desetinné číslo (001-366)|
|`%m`|Měsíc jako desetinné číslo (01-12)|
|`%M`|Jako s desetinným číslem minut (00 - 59)|
|`%n`|Znak nového řádku (**\n**)|
|`%p`|12hodinovém jako národní prostředí. Indikátor pro 12 hodin|
|`%r`|Čas 12 hodin jako národní prostředí|
|`%R`|Ekvivalent hodnoty `%H:%M`|
|`%S`|Druhý jako desetinné číslo (00 - 59)|
|`%t`|Horizontální tabulátor (**\t**)|
|`%T`|Ekvivalentní `%H:%M:%S`, formát času toho formátu ISO 8601.|
|`%u`|Den v týdnu ISO 8601 jako desetinné číslo (1-7; Pondělí je 1).|
|`%U`|Číslo týdne v roce jako desetinné číslo (00 - 53), kde je první neděle první den v týdnu 1|
|`%V`|Číslo týdne ISO 8601 jako desetinné číslo (00 - 53)|
|`%w`|Den v týdnu jako desetinné číslo (0 - 6; Neděle je 0)|
|`%W`|Číslo týdne v roce jako desetinné číslo (00 - 53), kde je první pondělí první den v týdnu 1|
|`%x`|Reprezentace datum pro národní prostředí|
|`%X`|Čas vyjádřený jako národní prostředí|
|`%y`|Rok bez století jako desetinné číslo (00 - 99)|
|`%Y`|Rok s století jako desetinné číslo|
|`%z`|Posun od času UTC ve formátu ISO 8601. žádné znaky, pokud se časové pásmo neznámý|
|`%Z`|Buď jako národní prostředí název časového pásma nebo zkratka časové pásmo, v závislosti na nastavení registru; žádné znaky, pokud se časové pásmo neznámý|
|`%%`|Znak procenta|

Jako v `printf` funkce, `#` příznak může předpony žádné formátování kódu. V takovém případě se následujícím způsobem změnit význam formátovat kód.

|Formátovat kód|Význam|
|-----------------|-------------|
|`%#a`, `%#A`, `%#b`, `%#B`, `%#g`, `%#G`, `%#h`, `%#n`, `%#p`, `%#t`, `%#u`, `%#w`, `%#X`, `%#z`, `%#Z`, `%#%`|`#` příznaku je ignorována.|
|`%#c`|Dlouhé datum a čas reprezentace vhodné pro národní prostředí. Například: "Úterý, 14 března 1995, 12:41:29".|
|`%#x`|Reprezentace dlouhého data, vhodné pro národní prostředí. Například: "Úterý, 14 března 1995".|
|`%#d`, `%#D`, `%#e`, `%#F`, `%#H`, `%#I`, `%#j`, `%#m`, `%#M`, `%#r`, `%#R`, `%#S`, `%#T`, `%#U`, `%#V`, `%#W`, `%#y`, `%#Y`|Odeberte úvodní nuly nebo mezer (pokud existuje).|

ISO 8601-týden a na základě týden roku vyprodukované `%V`, `%g`, a `%G`, používá týden, který začíná v pondělí, u kterých je týden 1 týden, který obsahuje leden 4., což je první týden, která obsahuje alespoň čtyři dnů roku. Pokud první pondělí roku 2., 3. nebo 4., předchozích dnů jsou součástí poslední týden předchozího roku. Tyto dní `%V` je nahrazena 53 a obě `%g` a `%G` jsou nahrazovány číslic předchozího roku.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`strftime`|\<time.h>|
|`wcsftime`|\<Time.h > nebo \<wchar.h >|
|`_strftime_l`|\<time.h>|
|`_wcsftime_l`|\<Time.h > nebo \<wchar.h >|

`_strftime_l` a `_wcsftime_l` funkce jsou specifické pro společnost Microsoft. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [čas](../../c-runtime-library/reference/time-time32-time64.md).

## <a name="see-also"></a>Viz také

[Národní prostředí](../../c-runtime-library/locale.md) <br/>
[Správa času](../../c-runtime-library/time-management.md) <br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](../../c-runtime-library/reference/localeconv.md) <br/>
[setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) <br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
