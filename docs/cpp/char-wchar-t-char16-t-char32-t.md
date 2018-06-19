---
title: Char, wchar_t, char16_t, char32_t | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs:
- C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dc38eb9742459139747578a8227bdfaee8bb8a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413892"
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t
Typy **char**, **wchar_t**, **char16_t** a **char32_t** jsou předdefinované typy, které představují alfanumerické znaky a také jiné než alfanumerické glyfů a netisknutelné znaky.

## <a name="syntax"></a>Syntaxe

```cpp  
char     ch1{ 'a' };  // or { u8'a' }   
wchar_t  ch2{ L'a' };    
char16_t ch3{ u'a' };    
char32_t ch4{ U'a' };  
```  
  
## <a name="remarks"></a>Poznámky

**Char** typ byl původní typy znaků jazyka C a C++. Typ **nepodepsané char** se často používá k reprezentování *bajtů*, což není předdefinovaný typ v jazyce C++. **Char** typ lze použít k uložení znaky znakové sady ASCII nebo některý z ISO 8859 znakových sad a jednotlivé bajtů vícebajtové znaky, jako jsou Shift JIS nebo kódování UTF-8 ve znakové sadě Unicode. Strings **char** typu se označují jako *zúžit* řetězce, i když použitá ke kódování vícebajtové znaky. V kompilátoru Microsoft **char** je typ 8 bitů.

**Wchar_t** typ je typ definované implementací široká znaková. V kompilátoru Microsoft představuje 16bitové široké znak použitý k uložení jako znakové sady UTF-16LE kódování Unicode typy nativní znaků v operačních systémech Windows. Široká znaková verzích použití funkce Universal C Runtime (UCRT) knihovny **wchar_t** a jeho ukazatel a pole typy jako parametry a návratové hodnoty, jako proveďte široká znaková verzích nativní rozhraní API systému Windows.

**Char16_t** a **char32_t** typy představují 16bitové a 32bitové verze široké znaky, v uvedeném pořadí. Kódování UTF-16 může být uložen v Unicode **char16_t** typu a kódování UTF-32 může být uložen v Unicode **char32_t** typu. Řetězce z těchto typů a **wchar_t** jsou všechny odkazované jako *široké* řetězce, i když termín se často vztahuje konkrétně na řetězce z **wchar_t** typu.

Ve standardní knihovně C++ `basic_string` typu se specializuje na úzké a široké řetězce. Použití `std::string` při znaky jsou typu **char**, `std::u16string` při znaky jsou typu **char16_t**, `std::u32string` při znaky jsou typu **char32_t** , a `std::wstring` při znaky jsou typu **wchar_t**. Jiné typy, které představují text, včetně `std::stringstream` a `std::cout` mít specializací pro omezený a široké řetězce.  
  
