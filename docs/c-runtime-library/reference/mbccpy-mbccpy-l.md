---
title: _mbccpy _mbccpy_l – | Dokumentace Microsoftu
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
ms.openlocfilehash: 8fca6772c00715722acecd810595a42c60f77d86
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201384"
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy, _mbccpy_l

Zkopíruje vícebajtový znak z jednoho řetězce do jiného řetězce. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_mbccpy_s – _mbccpy_s_l –](mbccpy-s-mbccpy-s-l.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*DEST* cílovou složku kopírování.

*src* vícebajtový znak pro kopírování.

*národní prostředí* národní prostředí.

## <a name="remarks"></a>Poznámky

**_Mbccpy** funkce kopíruje jeden vícebajtový znak *src* k *dest*.

Tato funkce ověřuje své parametry. Pokud **_mbccpy** je předán ukazatel s hodnotou null *dest* nebo *src*, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL**.

**_mbccpy** používá aktuální národní prostředí pro všechna závislá chování. **_mbccpy_l –** je stejný jako **_mbccpy** s tím rozdílem, že **_mbccpy_l –** používá pro všechna chování závislé na národním prostředí předané národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**Poznámka k zabezpečení** použijte řetězec zakončený hodnotou null. Řetězec zakončený hodnotou null nesmí překročit velikost cílové vyrovnávací paměti. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns). Problémů přetečení vyrovnávací paměti jsou častou metodou útoku na systém. Výsledkem je negarantované zvýšení úrovně oprávnění.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy –**|Mapuje se na makro nebo vloženou funkci|**_mbccpy**|Mapuje se na makro nebo vloženou funkci|
|**_tccpy_l –**|není k dispozici|**_mbccpy_l**|není k dispozici|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbccpy**|\<Mbctype.h >|
|**_mbccpy_l**|\<Mbctype.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
