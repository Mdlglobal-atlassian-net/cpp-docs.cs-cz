---
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 542751cdbd5bb21bb70467163c823e2669373e24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331165"
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t

Typy **char**, **wchar_t**, **char16_t** a **char32_t** jsou předdefinované typy, které představují alfanumerické znaky a jednak jiné než alfanumerické glyfy a netisknutelné znaky.

## <a name="syntax"></a>Syntaxe

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Poznámky

**Char** typ byl původní typ znaku v jazyce C a C++. Typ **unsigned char** se často používá k reprezentování *bajtů*, které není vestavěný typ v jazyce C++. **Char** typ lze použít k ukládání znaky ze znakové sady ASCII nebo některý z ISO-8859 znakových sad a jednotlivých bajtech vícebajtové znaky, jako je například Shift-JIS nebo kódování znakové sady Unicode UTF-8. Řetězce **char** typu jsou označovány jako *zúžit* řetězce, i když použít ke kódování znaků. V kompilátoru Microsoft **char** je 8 bitů typu.

**Wchar_t** typ je typ definovaných implementací širokých znaků. V kompilátoru Microsoft představuje 16bitové širokého znaku, používá k ukládání Unicode s kódováním UTF-16LE, typ nativní znaku v operačních systémech Windows. Verze širokého znaku pomocí funkce Universal C Runtime (UCRT) knihovny **wchar_t** a jeho ukazatele a pole typů jako parametrů a vrácených hodnot, jako verze širokého znaku nativní rozhraní API Windows.

**Char16_t** a **char32_t** typy představují 16bitová a 32bitová verze širokých znaků, v uvedeném pořadí. Kódování UTF-16 může být uložen v kódování Unicode **char16_t** typu a kódování UTF-32 může být uložen v Unicode **char32_t** typu. Řetězce z těchto typů a **wchar_t** jsou všechny uvedené jako *široké* řetězce, přestože termín se často platí konkrétně pro řetězce **wchar_t** typu.

Ve standardní knihovně C++ `basic_string` typu jsou specializované pro úzké a široké řetězce. Použití `std::string` při znaky jsou typu **char**, `std::u16string` při znaky jsou typu **char16_t**, `std::u32string` při znaky jsou typu **char32_t** , a `std::wstring` při znaky jsou typu **wchar_t**. Jiné typy, které představují text, včetně `std::stringstream` a `std::cout` mít specializace pro úzké a široké řetězce.