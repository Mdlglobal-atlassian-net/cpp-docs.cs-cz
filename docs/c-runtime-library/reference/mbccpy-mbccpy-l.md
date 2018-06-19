---
title: _mbccpy –, _mbccpy_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbccpy
- _mbccpy_l
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
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
dev_langs:
- C++
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d79ab8362eaa911b7a4aa936d6351aa29f610fa8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403167"
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy, _mbccpy_l

Zkopíruje vícebajtových znaků z jednoho řetězce k jiným řetězcem. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_mbccpy_s –, _mbccpy_s_l –](mbccpy-s-mbccpy-s-l.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
void _mbccpy(
   unsigned char *dest,
   const unsigned char *src
);
void _mbccpy_l(
   unsigned char *dest,
   const unsigned char *src,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*cíle* cíli kopírování.

*src* vícebajtových znaků pro kopírování.

*národní prostředí* národního prostředí použít.

## <a name="remarks"></a>Poznámky

**_Mbccpy –** funkce zkopíruje jeden vícebajtových znaků z *src* k *cíle*.

Tato funkce ověří jeho parametry. Pokud **_mbccpy –** byla předána ukazatel s hodnotou null pro *cíle* nebo *src*, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –**.

**_mbccpy –** používá aktuální národní prostředí pro chování všech závislých na národním prostředí. **_mbccpy_l –** je stejný jako **_mbccpy –** s tím rozdílem, že **_mbccpy_l –** používá národní prostředí předaná chování všech závislých na národním prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

**Poznámka k zabezpečení** pomocí řetězce ukončené hodnotou null. Řetězce ukončené hodnotou null nesmí překročit velikost cílové vyrovnávací paměti. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795). Přetečení vyrovnávací paměti problémy jsou často metodu systému útoku, výsledkem bude vyplacena neoprávněně zvýšení úrovně oprávnění.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy –**|Mapuje makro nebo vložené funkce|**_mbccpy**|Mapuje makro nebo vložené funkce|
|**_tccpy_l –**|není k dispozici|**_mbccpy_l**|není k dispozici|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbccpy**|\<Mbctype.h >|
|**_mbccpy_l**|\<Mbctype.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
