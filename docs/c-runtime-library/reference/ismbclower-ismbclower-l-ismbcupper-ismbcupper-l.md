---
title: _ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l
ms.date: 11/04/2016
api_name:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbcupper
- _ismbclower
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
ms.openlocfilehash: 6a64a0d9be83733fa5482eee84ce6576dd32c221
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953783"
---
# <a name="_ismbclower-_ismbclower_l-_ismbcupper-_ismbcupper_l"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l

Kontroluje, zda je vícebajtový znak malý nebo malý.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbclower(
   unsigned int c
);
int _ismbclower_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcupper(
   unsigned int c
);
int _ismbcupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Testovaný znak.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrací nenulovou hodnotu, pokud znak splňuje testovací podmínku, nebo 0, pokud tomu tak není. Pokud *c*< = 255 a existuje odpovídající rutina **_ismbb** (například **_ismbcalnum** odpovídá **_ismbbalnum**), výsledkem je návratová hodnota odpovídající rutiny **_ismbb** .

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí testuje daný vícebajtový znak pro danou podmínku.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předané národní prostředí namísto aktuálního národního prostředí pro své chování závislé na národním prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

|Rutina|Testovací podmínka|Příklad znakové stránky 932|
|-------------|--------------------|---------------------------|
|**_ismbclower**|Malá písmena|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtové znázornění písmene anglické abecedy ASCII: 0x61 < =*c*< = 0x7A.|
|**_ismbclower_l**|Malá písmena|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtové znázornění písmene anglické abecedy ASCII: 0x61 < =*c*< = 0x7A.|
|**_ismbcupper**|Velká písmena abecedy|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtové znázornění písmena anglické abecedy ASCII: 0x41 < =*c*< = 0x5A.|
|**_ismbcupper_l**|Velká písmena abecedy|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtové znázornění písmena anglické abecedy ASCII: 0x41 < =*c*< = 0x5A.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbclower**|\<Mbstring. h >|
|**_ismbclower_l**|\<Mbstring. h >|
|**_ismbcupper**|\<Mbstring. h >|
|**_ismbcupper_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
