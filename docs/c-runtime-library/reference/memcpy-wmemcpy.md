---
title: memcpy, wmemcpy
ms.date: 11/04/2016
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: afdb854bd28b55735cc6b5e26788307e2db0caa6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156587"
---
# <a name="memcpy-wmemcpy"></a>memcpy, wmemcpy

Kopie bajtů mezi vyrovnávací paměti. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [memcpy_s – wmemcpy_s –](memcpy-s-wmemcpy-s.md).

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

*dest*<br/>
Vyrovnávací paměť nového.

*src*<br/>
Zkopírovat z vyrovnávací paměti.

*Počet*<br/>
Počet znaků, které mají kopírovat.

## <a name="return-value"></a>Návratová hodnota

Hodnota *dest*.

## <a name="remarks"></a>Poznámky

**memcpy** kopie *počet* bajtů z *src* k *dest*; **wmemcpy –** kopie *počet* široké znaky (dva bajty). Pokud zdroj a cíl překrývají, chování **memcpy** není definován. Použití **memmove** zpracování překrývající se oblasti.

> [!IMPORTANT]
> Ujistěte se, že cílová vyrovnávací paměť je stejný velké nebo větší než zdrojová vyrovnávací paměť. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

> [!IMPORTANT]
> Protože tolik přetečení vyrovnávací paměti a proto potenciální zneužití zabezpečení, byla trasovali nesprávné použití **memcpy**, tato funkce je uvedena mezi "zakázané" funkce pomocí Security Development Lifecycle (SDL).  Podívat se, že některé třídy knihovny VC ++ nadále používat **memcpy**.  Kromě toho a podívat se, že Optimalizátor kompilátoru VC ++ někdy vydává volání **memcpy**.  Produkt Visual C++ je vytvořena v souladu s procesu SDL a proto používání této zakázané funkce úzce vyhodnocení.  V případě knihovny využít, volání bylo pečlivě kontrolovány zajistit, že přetečení vyrovnávací paměti nebudou povolena, prostřednictvím těchto volání.  V případě kompilátor, někdy určitých vzorů v kódu jsou rozpoznány jako stejný jako vzor **memcpy**a proto se nahradí volání funkce.  V takových případech použití **memcpy** je více nebezpečné než původní pokyny by byl; stačí k volání optimalizace výkonu byly optimalizovány **memcpy** funkce.  Stejně jako použití funkcí CRT "bezpečné" nezaručuje bezpečnosti (se právě snížili šanci, může být potenciálně nebezpečný) použijte "zakázané" funkce nezaručuje nebezpečí (pouze vyžadují větší kontroly k zajištění bezpečnosti).
>
> Protože **memcpy** využití ze strany VC ++ kompilátor a knihovny se pečlivě proto kontrolovány, tato volání jsou povoleny v rámci kódu, který je jinak v souladu s SDL.  **memcpy** volání zavedené ve zdrojovém kódu aplikace jsou kompatibilní s SDL pouze v případě, které používají revidovaný odborníky na zabezpečení.

**Memcpy** a **wmemcpy –** funkce se nepoužívají pouze pokud konstanty **_CRT_SECURE_DEPRECATE_MEMORY** je definovaná před příkazem zahrnutí v pořadí Funkce zastaralé, například v následujícím příkladu:

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
|**memcpy**|\<Memory.h > nebo \<string.h >|
|**wmemcpy**|\<wchar.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Zobrazit [memmove](memmove-wmemmove.md) ukázku toho, jak používat **memcpy**.

## <a name="see-also"></a>Viz také:

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
