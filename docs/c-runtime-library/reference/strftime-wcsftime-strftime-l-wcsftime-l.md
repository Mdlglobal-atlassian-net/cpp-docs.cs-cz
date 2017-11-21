---
title: "STRFTIME –, wcsftime –, _strftime_l –, _wcsftime_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ec9c46f1a6d52a8769e5db454d44baf9ec9d8a8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
#### <a name="parameters"></a>Parametry  
 `strDest`  
 Výstupní řetězec.  
  
 `maxsize`  
 Velikost `strDest` vyrovnávací paměť, měřená v znaků (`char` nebo `wchart_t`).  
  
 `format`  
 Řetězec řízení formátu  
  
 `timeptr`  
 `tm`Datová struktura.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 `strftime`Vrátí počet znaků, které jsou umístěny v `strDest` a `wcsftime` vrátí odpovídající počet široké znaky.  
  
 Celkový počet znaků, včetně ukončující null, je-li více než `maxsize`, oba `strftime` a `wcsftime` vrátit 0 a obsah `strDest` jsou neurčitou.  
  
 Počet znaků v `strDest` se rovná počet literálu znaků v `format` a také znaky, které mohou být přidány do `format` prostřednictvím formátování kódy. Ukončující null řetězce nepočítá v návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `strftime` a `wcsftime` funkce formát `tm` čas hodnota v `timeptr` podle zadaných `format` argument a uložit výsledek ve vyrovnávací paměti `strDest`. Maximálně `maxsize` znaky jsou umístěny v řetězci. Popis polí v `timeptr` struktury najdete v tématu [asctime –](../../c-runtime-library/reference/asctime-wasctime.md). `wcsftime`je ekvivalentem široká charakterová `strftime`; její argument řetězec ukazatel odkazuje na řetězec znaků celou. Tyto funkce chovají stejně jako jinak.  
  
> [!NOTE]
>  Ve verzi před Visual C++ 2005 popsané v dokumentaci `format` parametr `wcsftime` tak, že má datový typ `const wchar_t *`, ale skutečný implementace `format` datový typ byla `const char *`. Implementace `format` datový typ je aktualizovaná tak, aby odrážela předchozí a aktuální dokumentaci, který je `const wchar_t *`.  
  
 Tato funkce ověří jeho parametry. Pokud `strDest`, `format`, nebo `timeptr` je ukazatel s hodnotou null, nebo pokud `tm` datová struktura řešené pomocí `timeptr` je neplatný (například pokud obsahuje mimo rozsah hodnoty pro čas nebo datum), nebo pokud `format` řetězec obsahuje neplatný kód formátování, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu 0 a nastaví je povoleno spuštění `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsftime`|`strftime`|`strftime`|`wcsftime`|  
  
 `format` Argument se skládá z jednoho nebo více kódů; protože v `printf`, formátování kódy jsou uvozená znakem procent (`%`). Znaky, které nemají na začátku `%` se zkopírují do beze změny `strDest`. `LC_TIME` Kategorie aktuální národní prostředí má vliv na výstupní formátování `strftime`. (Další informace o `LC_TIME`, najdete v části [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).) Funkce bez `_l` používat příponu aktuálně nastavené národní prostředí. Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že trvat národní prostředí jako parametr a použijte místo aktuálně nastavené národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Formátování kódy pro `strftime` jsou uvedeny níže:  
  
 `%a`  
 Zkrácený název dne  
  
 `%A`  
 Úplný název dne  
  
 `%b`  
 Zkrácený název měsíce  
  
 `%B`  
 Úplný název měsíce  
  
 `%c`  
 Datum a čas reprezentace vhodné pro národní prostředí  
  
 `%d`  
 Den v měsíci jako desetinné číslo (01-31)  
  
 `%H`  
 Hodiny ve 24hodinovém formátu (00 - 23)  
  
 `%I`  
 Hodiny ve formátu 12 hodin (01-12)  
  
 `%j`  
 Den roku jako desetinné číslo (001-366)  
  
 `%m`  
 Měsíc jako desetinné číslo (01-12)  
  
 `%M`  
 Minutu jako desetinné číslo (00 - 59)  
  
 `%p`  
 12hodinovém aktuální národní prostředí. Indikátor pro 12 hodin  
  
 `%S`  
 Druhý jako desetinné číslo (00 - 59)  
  
 `%U`  
 Týden roku jako desetinné číslo, přičemž použije neděli jako první den v týdnu (00 - 53)  
  
 `%w`  
 Den v týdnu jako desetinné číslo (0 - 6; Neděle je 0)  
  
 `%W`  
 Týden roku jako desítkové číslo s pondělí jako první den v týdnu (00 - 53)  
  
 `%x`  
 Reprezentace datum pro aktuální národní prostředí  
  
 `%X`  
 Čas vyjádřený aktuální národní prostředí  
  
 `%y`  
 Rok bez století jako desetinné číslo (00 - 99)  
  
 `%Y`  
 Rok s století jako desetinné číslo  
  
 `%z, %Z`  
 Název časového pásma nebo zkratka časové pásmo, v závislosti na nastavení registru; žádné znaky, pokud se časové pásmo neznámý  
  
 `%%`  
 Znak procenta  
  
 Jako v `printf` funkce, `#` příznak může předpony žádné formátování kódu. V takovém případě se následujícím způsobem změnit význam formátovat kód.  
  
|Formátovat kód|Význam|  
|-----------------|-------------|  
|`%#a, %#A, %#b, %#B, %#p, %#X, %#z, %#Z, %#%`|`#`příznaku je ignorována.|  
|`%#c`|Dlouhé datum a čas reprezentace vhodné pro aktuální národní prostředí. Například: "Úterý, 14 března 1995, 12:41:29".|  
|`%#x`|Reprezentace dlouhého data, vhodné pro aktuální národní prostředí. Například: "Úterý, 14 března 1995".|  
|`%#d, %#H, %#I, %#j, %#m, %#M, %#S, %#U, %#w, %#W, %#y, %#Y`|Odebere úvodní nuly (pokud existuje).|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strftime`|\<Time.h >|  
|`wcsftime`|\<Time.h > nebo \<wchar.h >|  
|`_strftime_l`|\<Time.h >|  
|`_wcsftime_l`|\<Time.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [čas](../../c-runtime-library/reference/time-time32-time64.md).  
  
## <a name="see-also"></a>Viz také  
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Správa času](../../c-runtime-library/time-management.md)   
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [localeconv –](../../c-runtime-library/reference/localeconv.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll – funkce](../../c-runtime-library/strcoll-functions.md)   
 [strxfrm –, wcsxfrm –, _strxfrm_l –, _wcsxfrm_l –](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)