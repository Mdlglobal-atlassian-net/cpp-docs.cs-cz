---
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: a518f24973aaddff59b97f104d9d912e4a2bedce
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447153"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char, wchar_t, char16_t, char32_t

Typy **char**, **wchar_t**, **char16_t** a **char32_t** jsou předdefinované typy, které představují alfanumerické znaky, a také nealfanumerické glyfy a netisknutelné znaky.

## <a name="syntax"></a>Syntaxe

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Poznámky

Typ **znaku byl původní typ znaku** v jazyce C a. C++ Znak typu **bez znaménka** se často používá k vyjádření *bajtů*, což není vestavěný typ v C++. Typ **znaku** lze použít k ukládání znaků ze znakové sady ASCII nebo libovolné znakové sady ISO-8859 a jednotlivé bajty vícebajtových znaků, jako je například Shift-JIS nebo kódování UTF-8 znakové sady Unicode. Řetězce typu **char** jsou označovány jako *úzké* řetězce, a to i v případě, že se používají ke kódování vícebajtových znaků. V kompilátoru společnosti Microsoft je **znak** typu 8 bitů.

Typ **wchar_t** je typ znaku definovaný pro implementaci. V kompilátoru společnosti Microsoft představuje 16bitový znak, který se používá k uložení kódování Unicode kódovaného jako UTF-16LE, nativního typu znaku v operačních systémech Windows. Verze rozhraní UCRT (Universal C Runtime) knihovny pro velké znaky používají **wchar_t** a jeho typ ukazatele a pole jako parametry a návratové hodnoty, stejně jako verze v rámci nativního znaku rozhraní API systému Windows.

Typy **char16_t** a **char32_t** reprezentují 16 bitů a 32 znaků v uvedeném pořadí. Kódování Unicode kódované jako UTF-16 může být uloženo v typu **char16_t** a kódování Unicode jako utf-32 lze uložit do **char32_tho** typu. Řetězce těchto typů a **wchar_t** jsou všechny označovány jako *roztažitelné* řetězce, ačkoliv pojem často označuje konkrétně řetězce **wchar_t** typu.

Ve C++ standardní knihovně je typ `basic_string` specializovaný pro zúžené i roztažitelné řetězce. Použijte `std::string`, pokud jsou znaky typu **char**, `std::u16string` Pokud jsou znaky typu **char16_t**, `std::u32string`, pokud jsou znaky typu **char32_t**a `std::wstring`, pokud jsou znaky typu **wchar_t**. Jiné typy, které reprezentují text, včetně `std::stringstream` a `std::cout` mají specializace pro zúžené a širší řetězce.