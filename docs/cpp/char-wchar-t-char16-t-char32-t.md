---
title: Char, wchar_t, char16_t, char32_t | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs: C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4eaccef4253d2b677f01801b680bb94d8a4d3516
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t
Typy char, wchar_t, char16_t a char32_t jsou vestavěné typy, které představují alfanumerické znaky a také jiné než alfanumerické glyfů a netisknutelné znaky. CHAR je osmi bitů velikost, wchar_t a char16_t jsou 16 bitů velikost a char32_t je 32 bitů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
char     ch1{ 'a' };    
wchar_t  ch2{ 'a' }; // or {L'a'}    
char16_t ch3{ L'a' };// or {L'a'}    
char32_t ch4{ L'a' };// or {L'a'}  
```  
  
## <a name="remarks"></a>Poznámky  
 `char` Typ byl původní typy znaků jazyka C a C++. Může sloužit k ukládání znaky znakové sady ASCII nebo žádné z ISO 8859 znakových sad, nebo UTF-8 znaková sada. Typ `unsigned char` se často používá k reprezentování *bajtů* což není předdefinovaný typ v jazyce C++. Znakový typ není vhodný pro text v mnoha jazycích. Obecně platí, moderní programy by měly používat jeden z typů široká znaková představuje text. Je kódování Unicode  
  
 Standardní knihovny C++ se specializuje typ basic_string pro omezený a široké řetězce. Std::string použijte, pokud znaky je znakový typ a std::wstring, pokud jsou znaky z wchar_t typu. Jiné typy, které představují text, včetně std::stringstream a std::cout mít specializací pro omezený a široké řetězce.  
  
