---
title: _cgets_s, _cgetws_s
ms.date: 4/2/2020
api_name:
- _cgetws_s
- _cgets_s
- _o__cgets_s
- _o__cgetws_s
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
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
ms.openlocfilehash: b4871ff2c362e2c6cbe37be6a31bde4e6e258709
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333550"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s, _cgetws_s

Získá řetězec znaku z konzoly. Tyto verze [_cgets a _cgetws](../../c-runtime-library/cgets-cgetws.md) mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _cgets_s(
   char *buffer,
   size_t numberOfElements,
   size_t *pSizeRead
);
errno_t _cgetws_s(
   wchar_t *buffer
   size_t numberOfElements,
   size_t *pSizeRead
);
template <size_t size>
errno_t _cgets_s(
   char (&buffer)[size],
   size_t *pSizeRead
); // C++ only
template <size_t size>
errno_t _cgetws_s(
   wchar_t (&buffer)[size],
   size_t *pSizeRead
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro data.

*numberOfElements*<br/>
Velikost vyrovnávací paměti v jednobajtové nebo široké znaky, což je také maximální počet znaků, které mají být přečteny.

*pSizeRead*<br/>
Počet znaků skutečně číst.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je nula, pokud je úspěšná; v opačném případě kód chyby, pokud dojde k chybě.

### <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*numberOfElements*|*pSizeRead*|Vrátit|Obsah *vyrovnávací paměti*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**Null**|jakékoli|jakékoli|**EINVAL**|neuvedeno|
|není **null**|nula|jakékoli|**EINVAL**|nezměněno|
|není **null**|jakékoli|**Null**|**EINVAL**|řetězec nulové délky|

## <a name="remarks"></a>Poznámky

**_cgets_s** a **_cgetws_s** číst řetězec z konzoly a zkopírujte řetězec (s zakončením null) do *vyrovnávací paměti*. **_cgetws_s** je široká znaková verze funkce; velikost i velikost i znaku, chování těchto dvou funkcí je identické. Maximální velikost řetězce, který má být přečten, je předána jako parametr *numberOfElements.* Tato velikost by měla obsahovat další znak pro ukončující null. Skutečný počet přečtených znaků je umístěn v *pSizeRead*.

Pokud dojde k chybě během operace nebo při ověřování parametrů, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno provádění pokračovat, **errno** je nastavena na **EINVAL** a **EINVAL** je vrácena.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky, čímž se eliminuje potřeba zadat argument velikost a mohou automaticky nahradit starší, méně zabezpečené funkce s jejich novější, bezpečnější protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze knihovny těchto funkcí nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
