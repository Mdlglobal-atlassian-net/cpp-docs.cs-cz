---
title: memcpy, wmemcpy
ms.date: 11/04/2016
api_name:
- memcpy
- wmemcpy
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: bf7f12cd00780347f23252764aace449dd6f5722
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303292"
---
# <a name="memcpy-wmemcpy"></a>memcpy, wmemcpy

Kopíruje bajty mezi vyrovnávacími paměťmi. K dispozici jsou bezpečnější verze těchto funkcí; viz [memcpy_s, wmemcpy_s](memcpy-s-wmemcpy-s.md).

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

*propojovací*<br/>
Nová vyrovnávací paměť.

*src*<br/>
Vyrovnávací paměť, ze které se má kopírovat.

*výpočtu*<br/>
Počet znaků, které mají být zkopírovány.

## <a name="return-value"></a>Návratová hodnota

Hodnota *cíl*.

## <a name="remarks"></a>Poznámky

**memcpy** kopíruje *počet* bajtů ze *Src* na *cíl*; **wmemcpy** kopíruje *počet* znaků v šířce (dva bajty). Pokud se zdrojový a cílový překrývají, chování **memcpy** není definováno. Použijte **memmove** k obsluze překrývajících se oblastí.

> [!IMPORTANT]
> Ujistěte se, že cílová vyrovnávací paměť má stejnou velikost nebo je větší než zdrojová vyrovnávací paměť. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!IMPORTANT]
> Vzhledem k tomu, že mnoho přetečení vyrovnávací paměti a tedy potenciální zneužití zabezpečení bylo sledováno pro nesprávné použití **memcpy**, je tato funkce uvedena mezi funkcemi "zakázáno" v rámci rozhraní SDL (Security Development Lifecycle).  Můžete si všimnout, že některé třídy knihovny VC + + dál používají **memcpy**.  Kromě toho můžete všimnout, že Optimalizátor kompilátoru VC + + někdy generuje volání do **memcpy**.  Vizuální C++ produkt je vyvíjen v souladu s procesem SDL, takže využití této zakázané funkce bylo pečlivě vyhodnoceno.  V případě použití knihovny jsou volání pečlivě kontrolována, aby se zajistilo, že přetečení vyrovnávací paměti nebudou prostřednictvím těchto volání povolena.  V případě kompilátoru jsou někdy určité vzory kódu rozpoznány stejně jako vzor **memcpy**a jsou proto nahrazeny voláním funkce.  V takových případech použití **memcpy** není bezpečnější než původní pokyny. byly jednoduše optimalizované pro volání funkce **memcpy** s vyladěným výkonem.  Stejně jako používání "bezpečných" CRT funkcí nezaručuje bezpečnost (jen proto, že by to bylo těžší být nebezpečné), použití zakázaných funkcí nezaručí nebezpečí (k zajištění bezpečnosti stačí jenom lepší kontroly).
>
> Vzhledem k tomu, že **memcpy** využití kompilátorem VC + + a knihovny byly pečlivě kontrolovány, jsou tato volání povolena v rámci kódu, který je jinak kompatibilní s SDL.  volání **memcpy** představená ve zdrojovém kódu aplikace jsou kompatibilní s SDL pouze v případě, že je toto použití přezkoumáno odborníky na zabezpečení.

Funkce **memcpy** a **wmemcpy** budou zastaralé pouze v případě, že je konstanta **_CRT_SECURE_DEPRECATE_MEMORY** definována před příkazem začlenění, aby byly funkce zastaralé, například v následujícím příkladu:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

nebo

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memcpy**|\<Memory. h > nebo \<String. h >|
|**wmemcpy**|\<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Ukázku použití **memcpy**naleznete v tématu [memmove](memmove-wmemmove.md) .

## <a name="see-also"></a>Viz také:

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
