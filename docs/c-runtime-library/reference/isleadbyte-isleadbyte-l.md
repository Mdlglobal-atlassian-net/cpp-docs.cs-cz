---
title: isleadbyte –, _isleadbyte_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _isleadbyte_l
- isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
dev_langs:
- C++
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 682cdde6983c5e590920c43418e510b9c275b34e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte, _isleadbyte_l

Určuje, zda znak je realizace bajt vícebajtových znaků.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo pro testování.

## <a name="return-value"></a>Návratová hodnota

**isleadbyte –** vrátí nenulovou hodnotu, pokud argument splňuje podmínky testu nebo 0, pokud neexistuje. V národního prostředí "C" a jednobajtové znaková sada (SBCS) národní prostředí, **isleadbyte –** vždy vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

**Isleadbyte –** makro vrátí nenulovou hodnotu, pokud jeho argument je první bajt vícebajtových znaků. **isleadbyte –** vytvoří smysluplný výsledek pro některý argument celé číslo od -1 (**EOF**) k **uchar_max –** (0xFF), včetně.

Očekávaný argument typ **isleadbyte –** je **int**; Pokud je předán podepsaný znak, kompilátor může ho převést na celé číslo rozšířením přihlášení je vést k neočekávaným výsledkům.

Verze této funkce se **_l** přípona se shoduje s tím rozdílem, že používá národní prostředí předaná místo aktuální národní prostředí pro své chování závislých na národním prostředí.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte –**|Vždy vrátí hodnotu false|**_isleadbyte**|Vždy vrátí hodnotu false|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isleadbyte –**|\<ctype.h >|
|**_isleadbyte_l**|\<ctype.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
