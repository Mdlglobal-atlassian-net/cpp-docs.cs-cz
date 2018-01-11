---
title: "is_pod – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_pod
dev_langs: C++
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f6410ca3f8a011cce3673eec28b616bfb4a96aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ispod-class"></a>is_pod – třída
Testy, pokud je typ POD.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
struct is_pod;
```  
  
#### <a name="parameters"></a>Parametry  
*T*  
Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
`is_pod<T>::value`je `true` Pokud typ *T* je prostý staré dat (POD). V opačném případě je `false`.  
  
Aritmetické typy, výčtové typy, typy ukazatelů a ukazatel na typy členů jsou POD.  
  
Odchylka nákladů kvalifikovaný verzi POD typu samotné je typ POD.  
  
Pole POD se POD.  
  
Struktura nebo union, jsou všechny obsahující data nestatické POD, je sám POD Pokud má:  
  
-   Žádné uživatele deklarovaný konstruktory.  
  
-   Žádné datové nestatické soukromé nebo chráněné členy.  
  
-   Žádné základní třídy.  
  
-   Žádné virtuální funkce.  
  
-   Žádné datové nestatické členy odkazového typu.  
  
-   Operátor přiřazení žádné uživatelem definované kopírování.  
  
-   Žádné – destruktor definovaný uživatelem.  
  
Proto můžete rekurzivně sestavení POD struktury a pole, které obsahují POD struktury a pole.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// std__type_traits__is_pod.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial {   
    int val;   
};   
  
struct throws {   
    throws() {}  // User-declared ctor, so not POD
  
    int val;   
};   
  
int main() {   
    std::cout << "is_pod<trivial> == " << std::boolalpha   
        << std::is_pod<trivial>::value << std::endl;   
    std::cout << "is_pod<int> == " << std::boolalpha   
        << std::is_pod<int>::value << std::endl;   
    std::cout << "is_pod<throws> == " << std::boolalpha   
        << std::is_pod<throws>::value << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
is_pod<trivial> == true  
is_pod<int> == true  
is_pod<throws> == false  
```  
  
## <a name="requirements"></a>Požadavky  
**Záhlaví:** \<type_traits >  
  
**Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
[<type_traits>](../standard-library/type-traits.md)



