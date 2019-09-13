---
title: _cgets_s, _cgetws_s
ms.date: 11/04/2016
api_name:
- _cgetws_s
- _cgets_s
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
ms.openlocfilehash: 2039fc32cecb768c3c3fbc239446abedeb48f188
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939268"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s, _cgetws_s

Získá řetězec znaků z konzoly. Tyto verze [_cgets a _cgetws](../../c-runtime-library/cgets-cgetws.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*vyrovnávací paměti*<br/>
Umístění úložiště pro data

*numberOfElements*<br/>
Velikost vyrovnávací paměti v jednobajtových nebo velkých znacích, což je také maximální počet znaků, které mají být čteny.

*pSizeRead*<br/>
Počet znaků, které jsou ve skutečnosti čteny.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota je v případě úspěchu nulová. v opačném případě kód chyby, pokud dojde k selhání.

### <a name="error-conditions"></a>Chybové stavy

|*vyrovnávací paměti*|*numberOfElements*|*pSizeRead*|vrátit|Obsah *vyrovnávací paměti*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|Jakýmikoli|Jakýmikoli|**EINVAL**|není k dispozici|
|Není **null**|nula|Jakýmikoli|**EINVAL**|Neupraveno|
|Není **null**|Jakýmikoli|**NULL**|**EINVAL**|řetězec s nulovou délkou|

## <a name="remarks"></a>Poznámky

**_cgets_s** a **_cgetws_s** čtou z konzoly řetězec a do *vyrovnávací paměti*kopíruje řetězec (s ukončovacím znakem null). **_cgetws_s** je verze funkce s velkým znakem. Kromě velikosti znaku je chování těchto dvou funkcí stejné. Maximální velikost řetězce, který se má načíst, se předává jako parametr *numberOfElements* . Tato velikost by měla obsahovat znak navíc pro ukončující hodnotu null. Skutečný počet čtených znaků je umístěný v *pSizeRead*.

Pokud během operace nebo při ověřování parametrů dojde k chybě, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a vrátí **EINVAL** .

V C++nástroji je použití těchto funkcí zjednodušeno pomocí přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky, čímž eliminují nutnost zadat argument velikosti a můžou automaticky nahradit starší a méně zabezpečené funkce jejich novějšími, bezpečnějšími protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cgets_s**|\<CONIO. h >|
|**_cgetws_s**|\<CONIO. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
