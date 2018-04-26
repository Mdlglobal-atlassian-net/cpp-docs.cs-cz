---
title: memcpy wmemcpy – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- memcpy
- wmemcpy
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
apitype: DLLExport
f1_keywords:
- wmemcpy
- memcpy
dev_langs:
- C++
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a31ada40bfab599b6da41da268bf79792f8ebf20
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="memcpy-wmemcpy"></a>memcpy, wmemcpy

Počet bajtů kopie mezi vyrovnávací paměti. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [memcpy_s –, wmemcpy_s –](memcpy-s-wmemcpy-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *memcpy(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemcpy(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*Cíle*<br/>
Vyrovnávací paměť nového.

*src*<br/>
Zkopírovat z vyrovnávací paměti.

*Počet*<br/>
Počet znaků pro kopírování.

## <a name="return-value"></a>Návratová hodnota

Hodnota *cíle*.

## <a name="remarks"></a>Poznámky

**memcpy –** kopie *počet* bajtů z *src* k *cíle*; **wmemcpy –** kopie *počet* široké znaky (dva bajty). Pokud zdrojové a cílové překrývají, chování **memcpy** není definován. Použití **memmove –** pro zpracování překrývající se oblasti.

> [!IMPORTANT]
> Ujistěte se, že cílová vyrovnávací paměť je stejný velké nebo větší než zdrojová vyrovnávací paměť. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

> [!IMPORTANT]
> Protože mnoho přetečení vyrovnávací paměti a proto potenciální zneužití zabezpečení, byla trasovali nesprávné využití od **memcpy**, tato funkce je uveden mezi "zakázaného" funkce pomocí životního cyklu SDL (Security Development).  Můžete pozorovat, že některé třídy knihovny VC ++ nadále používat **memcpy**.  Kromě toho může zjistíte, že optimalizace kompilátoru VC ++ někdy vysílá volání **memcpy**.  Produkt Visual C++ vyvinutý v souladu s v rámci procesu SDL, a proto využití této funkce zakázaného úzce vyhodnocení.  V případě knihovny pomocí jeho, volání byl pečlivě kontrolovány zajistit, že přetečení vyrovnávací paměti nebudou povolena, prostřednictvím těchto volání.  V případě kompilátoru, někdy určité vzorce kódu jsou rozpoznána jako identické vzor **memcpy**a proto jsou nahrazeny volání funkce.  V takových případech použití **memcpy** není žádné další bezpečné než původní pokyny by byl; jednoduše k volání optimalizaci výkonu byly optimalizovány **memcpy** funkce.  Stejně jako použití "bezpečnou" funkcí CRT nezaručuje zabezpečení (se právě znesnadňuje nebezpečnou) použití "zakázaného" funkce nezaručuje nebezpečí (vyžadují jenom větší kontroly k zajištění bezpečnosti).
>
> Protože **memcpy** využití podle VC ++ kompilátoru a knihovny má proto pečlivě kontrolovány, tyto volání jsou povolena v rámci kód, který je kompatibilní s SDL jinak.  **memcpy –** volání zavedená ve zdrojovém kódu aplikace jsou kompatibilní s procesu SDL, pouze pokud byl revidován využívající odborníky na zabezpečení.

**Memcpy** a **wmemcpy –** funkce pouze přestanou Pokud konstanta **_CRT_SECURE_DEPRECATE_MEMORY** je definovaná před příkazem zahrnutí v pořadí funkce jako zastaralé, například v následujícím příkladu:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

or

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memcpy –**|\<Memory.h > nebo \<string.h >|
|**wmemcpy**|\<wchar.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

V tématu [memmove –](memmove-wmemmove.md) pro ukázkové použití **memcpy**.

## <a name="see-also"></a>Viz také

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
