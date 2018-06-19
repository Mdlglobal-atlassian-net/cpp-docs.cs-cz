---
title: _ismbclegal –, _ismbclegal_l –, _ismbcsymbol –, _ismbcsymbol_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbclegal_l
- _ismbclegal
- _ismbcsymbol
- _ismbcsymbol_l
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
- ismbcsymbol_l
- _ismbcsymbol_l
- _ismbcsymbol
- _ismbclegal_l
- _ismbclegal
- ismbclegal_l
- ismbcsymbol
- ismbclegal
dev_langs:
- C++
helpviewer_keywords:
- ismbcsymbol function
- ismbclegal_l function
- _istlegal_l function
- istlegal function
- _istlegal function
- _ismbcsymbol function
- _ismbclegal_l function
- ismbclegal function
- ismbcsymbol_l function
- _ismbclegal function
- _ismbcsymbol_l function
- istlegal_l function
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d2bd03eb230d85a1f93038d50566b8ccae468a5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402592"
---
# <a name="ismbclegal-ismbclegall-ismbcsymbol-ismbcsymboll"></a>_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l

Zkontroluje, jestli vícebajtových znaků právních nebo znak symbolu.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbclegal(
   unsigned int c
);
int _ismbclegal_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcsymbol(
   unsigned int c
);
int _ismbcsymbol_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak, který má být testována.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Všechny tyto rutiny vrátí nenulovou hodnotu, pokud znak splňuje podmínky testu nebo 0, pokud neexistuje. Pokud *c*< = 255 a existuje odpovídající **_ismbb –** rutiny (například **_ismbcalnum –** odpovídá **_ismbbalnum –**), Výsledkem je vrácenou hodnotu odpovídající **_ismbb –** rutiny.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí testuje dané vícebajtových znaků pro danou podmínku.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají národní prostředí předaná místo aktuální národní prostředí pro jejich chování závislých na národním prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

|Rutina|Test stavu|Příklad kódu stránka 932|
|-------------|--------------------|---------------------------|
|**_ismbclegal**|Platný vícebajtových|Vrátí první bajt nenulové hodnoty v případě a pouze v případě *c* je v rámci rozsahy 0x81-0x9F nebo 0xE0 - 0xFC, zatímco druhý bajt je v rámci rozsahy 0x40-0x7E nebo 0x80 - FC.|
|**_ismbcsymbol**|Více-bajtové – symbol|Vrátí nenulové hodnoty v případě a pouze v případě 0x8141 < =*c*< = 0x81AC.|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlegal –**|Vždy vrátí hodnotu false|**_ismbclegal**|Vždy vrátí hodnotu false.|
|**_istlegal_l –**|Vždy vrátí hodnotu false|**_ismbclegal_l**|Vždy vrátí hodnotu false.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbclegal –**, **_ismbclegal_l –**|\<Mbstring.h >|
|**_ismbcsymbol –**, **_ismbcsymbol_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
