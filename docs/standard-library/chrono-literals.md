---
title: "literály typu chrono | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7a470c96670753fd98b97f9b9d5daffbb8c3eba0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="chrono-literals"></a>literály typu chrono
(C ++ 14) \<Typu chrono > záhlaví definuje 12 [uživateli definované literály](../cpp/user-defined-literals-cpp.md) usnadňuje pomocí literály, které představují hodiny, minuty, sekundy, milisekundách, mikrosekundách a nanosekundách. Každé uživatelské literál má integrální hodnotu a s plovoucí desetinnou čárkou přetížení. Literály jsou definovány v oboru názvů vloženého literals::chrono_literals, která je uvedena do oboru automaticky po std::chrono v oboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline namespace literals {  
    inline namespace chrono_literals {  
 // return integral hours  
    constexpr chrono::hours operator"" h(unsigned long long Val);

 // return floating-point hours  
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

 // return integral minutes  
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

 // return floating-point minutes  
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

 // return integral seconds  
    constexpr chrono::seconds operator"" s(unsigned long long Val);

 // return floating-point seconds  
    constexpr chrono::duration<double> operator"" s(long double Val);

 // return integral milliseconds  
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

 // return floating-point milliseconds  
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

 // return integral microseconds      
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

 // return floating-point microseconds  
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

 // return integral nanoseconds  
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

 // return floating-point nanoseconds  
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

 }// inline namespace chrono_literals  
}// inline namespace literals  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Literály, které provést `long long` argument, vrátí hodnotu nebo příslušného typu. Literály, které provést plovoucí bodu argument návratový [doba trvání](../standard-library/duration-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady osev použití literály typu chrono.  
  
```cpp  
constexpr auto day = 24h;  
constexpr auto week = 24h* 7;  
constexpr auto my_duration_unit = 108ms;  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: \<typu chrono >  
  
 **Namespace**: std::literals::chrono_literals  
  
## <a name="see-also"></a>Viz také  
 [\<typu chrono >](../standard-library/chrono.md)
