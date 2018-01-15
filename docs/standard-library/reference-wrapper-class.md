---
title: "reference_wrapper – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::reference_wrapper
- type_traits/std::reference_wrapper
- xrefwrap/std::reference_wrapper
- type_traits/std::reference_wrapper::get
- type_traits/std::reference_wrapper::operator()
- functional/std::reference_wrapper::result_type
- functional/std::reference_wrapper::type
- functional/std::reference_wrapper::get
- functional/std::reference_wrapper::operator()
dev_langs: C++
helpviewer_keywords:
- std::reference_wrapper [C++]
- std::reference_wrapper [C++]
- std::reference_wrapper [C++], result_type
- std::reference_wrapper [C++], type
- std::reference_wrapper [C++], get
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 87608912712f201d4731deac53d7a59fdddf41d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="referencewrapper-class"></a>reference_wrapper – třída
Zabalí odkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Ty>  
class reference_wrapper  
{  
public:  
    typedef Ty type;  
 
    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types> 
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));
 
private:  
    Ty *ptr; // exposition only  
};  
```  
  
## <a name="remarks"></a>Poznámky  
A `reference_wrapper<Ty>` je kopie zkonstruovatelný a kopírování Přiřaditelné obálku kolem odkaz na objekt nebo funkci typu `Ty`a obsahuje ukazatele, který odkazuje na objekt daného typu. A `reference_wrapper` lze použít k ukládání odkazů ve standardní kontejnery a předávání objektů s odkazem na `std::bind`.  
  
Typ `Ty` musí být typu objektu nebo typ funkce nebo statické assert selže v době kompilace.  
  
Podpůrné funkce [std::ref](functional-functions.md#ref) a [std::cref](functional-functions.md#cref) slouží k vytvoření `reference_wrapper` objekty.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[reference_wrapper –](#reference_wrapper)|Vytvoří `reference_wrapper`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[result_type](#result_type)|Slabé výsledný typ zabalené odkaz.|  
|[Typ](#type)|Typ zabalené odkaz.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[get](#get)|Získá odkaz na zabalená.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[reference_wrapper::Operator Ty&amp;](#op_ty_amp)|Získá ukazatel k zabalené odkazu.|  
|[reference_wrapper::Operator()](#op_call)|Volá zabalené odkaz.|  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<funkční >  
  
 **Namespace:** – std  
  
##  <a name="get"></a>reference_wrapper::Get  
 Získá odkaz na zabalená.  
  
```  
Ty& get() const noexcept;
```  
  
### <a name="remarks"></a>Poznámky  
Členská funkce vrátí odkaz na zabalená.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__reference_wrapper_get.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int main() {   
    int i = 1;   
    std::reference_wrapper<int> rwi(i);   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "rwi = " << rwi << std::endl;   
    rwi.get() = -1;   
    std::cout << "i = " << i << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
i = 1  
rwi = 1  
i = -1  
```  
  
##  <a name="op_ty_amp"></a>reference_wrapper::Operator Ty&amp;  
 Získá zabalené odkaz.  
  
```  
operator Ty&() const noexcept;
```  
  
### <a name="remarks"></a>Poznámky  
 Vrací člena operátor `*ptr`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__reference_wrapper_operator_cast.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int main() {   
    int i = 1;   
    std::reference_wrapper<int> rwi(i);   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "(int)rwi = " << (int)rwi << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
i = 1  
(int)rwi = 1  
```  
  
##  <a name="op_call"></a>reference_wrapper::Operator()  
 Volá zabalené odkaz.  
  
```  
template <class... Types>  
auto operator()(Types&&... args);
```  
  
### <a name="parameters"></a>Parametry  
 `Types`  
 Typy seznamu argumentů.  
  
 `args`  
 Seznam argumentů.  
  
### <a name="remarks"></a>Poznámky  
 Šablony členských `operator()` vrátí `std::invoke(get(), std::forward<Types>(args)...)`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__reference_wrapper_operator_call.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val) {   
    return (-val);   
}   
  
int main() {   
    std::reference_wrapper<int (int)> rwi(neg);   
  
    std::cout << "rwi(3) = " << rwi(3) << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
rwi(3) = -3  
```  
  
##  <a name="reference_wrapper"></a>reference_wrapper::reference_wrapper  
 Vytvoří `reference_wrapper`.  
  
```  
reference_wrapper(Ty& val) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ k zalomení.  
  
 `val`  
 Hodnota k zalomení.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor nastaví uložené hodnoty `ptr` k `&val`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__reference_wrapper_reference_wrapper.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val) {   
    return (-val);   
}   
  
int main() {   
    int i = 1;   
    std::reference_wrapper<int> rwi(i);   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "rwi = " << rwi << std::endl;   
    rwi.get() = -1;   
    std::cout << "i = " << i << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
i = 1  
rwi = 1  
i = -1  
```  
  
##  <a name="result_type"></a>reference_wrapper::result_type  
 Slabé výsledný typ zabalené odkaz.  
  
```  
typedef R result_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 `result_type` Typedef je synonymum pro slabé výsledný typ zabalená funkce. Tato typedef má smysl pro typy funkce pouze.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__reference_wrapper_result_type.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val) {   
    return (-val);   
}   
  
int main() {   
    typedef std::reference_wrapper<int (int)> Mywrapper;   
    Mywrapper rwi(neg);   
    Mywrapper::result_type val = rwi(3);   
  
    std::cout << "val = " << val << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
val = -3  
```  
  
##  <a name="type"></a>reference_wrapper::type  
 Typ zabalené odkaz.  
  
```  
typedef Ty type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typedef je synonymum argumentu šablony `Ty`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__reference_wrapper_type.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val) {   
    return (-val);   
}   
  
int main() {   
    int i = 1;   
    typedef std::reference_wrapper<int> Mywrapper;   
    Mywrapper rwi(i);   
    Mywrapper::type val = rwi.get();   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "rwi = " << val << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
i = 1  
rwi = 1  
```  
  
## <a name="see-also"></a>Viz také  
 [cref –](../standard-library/functional-functions.md#cref)   
 [ref](../standard-library/functional-functions.md#ref)

