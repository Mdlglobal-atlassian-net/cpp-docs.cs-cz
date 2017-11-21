---
title: "Návratové hodnoty (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f8ac22790fa6b94dd19ba7d46cf737824e898f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="return-values-c"></a>Návratové hodnoty (C++)
Skalární návratovou hodnotu, která můžete začlenit do 64bitová verze je vráceny prostřednictvím RAX – to zahrnuje __m64 typy. Bez skalárních typů, včetně obtékaných objektů, Double a vektoru typy, jako [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) jsou vráceny v XMM0. Stav Nepoužité bity v hodnotě, vrátí se v RAX nebo XMM0 není definován.  
  
 Uživatelem definované typy mohou být vráceny podle hodnoty z globální funkce a funkce statický člen. Vrátí hodnotu ve RAX, uživatelem definované typy musí mít délku 1, 2, 4, 8, 16, 32 nebo 64bitová verze; žádné uživatelem definované konstruktoru, destruktor nebo operátor přiřazení kopie; žádné datové nestatické soukromé nebo chráněné členy; žádné datové nestatické členy odkaz; žádné základní třídy; žádné virtuální funkce; a žádní členové data, které nesplňují taky tyto požadavky. (To je v podstatě definice 03 C ++ POD typu. Protože definici došlo ke změně v C ++ 11 standardní nedoporučujeme používání `std::is_pod` pro tento test.) Volající, jinak hodnota předpokládá odpovědnost přidělování paměti a předání ukazatele pro vrácenou hodnotu jako první argument. Další argumenty jsou potom zapuštěno jeden argument vpravo. Stejný ukazatel má být vrácen volaného v RAX.  
  
 Tyto příklady ukazují, jak se předávají parametry a návratové hodnoty pro funkce s zadané deklarace:  
  
## <a name="example-of-return-value-1---64-bit-result"></a>Příklad 1 64bitový výsledku návratová hodnota  
  
```Output  
__int64 func1(int a, float b, int c, int d, int e);  
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,  
// callee returns __int64 result in RAX.  
```  
  
## <a name="example-of-return-value-2---128-bit-result"></a>Příklad 2 128bitové výsledku návratová hodnota  
  
```Output  
__m128 func2(float a, double b, int c, __m64 d);   
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,   
// callee returns __m128 result in XMM0.  
```  
  
## <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Příklad návratová hodnota 3 - výsledek typu uživatele ukazatel  
  
```Output  
struct Struct1 {  
   int j, k, l;    // Struct1 exceeds 64 bits.   
};  
Struct1 func3(int a, double b, int c, float d);   
// Caller allocates memory for Struct1 returned and passes pointer in RCX,   
// a in RDX, b in XMM2, c in R9, d pushed on the stack;   
// callee returns pointer to Struct1 result in RAX.  
```  
  
## <a name="example-of-return-value-4---user-type-result-by-value"></a>Příklad návratovou hodnotu 4 - výsledek typu uživatele podle hodnoty  
  
```Output  
struct Struct2 {  
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.  
};  
Struct2 func4(int a, double b, int c, float d);   
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;   
// callee returns Struct2 result by value in RAX.  
```  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)