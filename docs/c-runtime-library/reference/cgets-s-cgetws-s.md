---
title: _cgets_s, _cgetws_s
ms.date: 11/04/2016
apiname:
- _cgetws_s
- _cgets_s
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 8341b775df3b9cbaececdfaa1f17e075d7c7416c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340582"
---
# <a name="cgetss-cgetwss"></a>_cgets_s, _cgetws_s

Získá znak řetězce z konzoly. Tyto verze [_cgets a _cgetws –](../../c-runtime-library/cgets-cgetws.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Velikost vyrovnávací paměti v jednobajtové nebo široké znaky, které je taky maximální počet znaků pro čtení.

*pSizeRead*<br/>
Počet znaků, které skutečně číst.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je nula v případě úspěchu; v opačném případě chybu kódu, pokud dojde k chybě.

### <a name="error-conditions"></a>Chybové podmínky

|*Vyrovnávací paměti*|*numberOfElements*|*pSizeRead*|Vrátí|Obsah *vyrovnávací paměti*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|Všechny|Všechny|**EINVAL**|není k dispozici|
|Není **NULL**|nula|Všechny|**EINVAL**|Nezměněno|
|Není **NULL**|Všechny|**NULL**|**EINVAL**|řetězec nulové délky|

## <a name="remarks"></a>Poznámky

**_cgets_s** a **_cgetws_s –** čtení řetězce z konzoly a zkopírujte řetězec (s ukončovací znak null) do *vyrovnávací paměti*. **_cgetws_s –** je verze širokého znaku funkce; jiné, než je stejný jako znak velikost, chování tyto dvě funkce. Maximální velikost řetězce ke čtení je předán jako *numberOfElements* parametru. Tato velikost by měla obsahovat znak navíc pro ukončující znak null. Skutečný počet znaků, přečtěte si je umístěn v *pSizeRead*.

Pokud dojde k chybě během operace nebo při ověřování parametrů, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a **EINVAL** je vrácena.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky, a tím eliminuje nutnost zadat argument velikosti a dokážou automaticky nahradit starší, méně zabezpečené funkce jejími novějšími, bezpečnějšími protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
