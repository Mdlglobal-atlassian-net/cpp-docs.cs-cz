---
title: "is_default_constructible třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_default_constructible
dev_langs: C++
helpviewer_keywords: is_default_constructible
ms.assetid: dd8f1c44-dae5-4258-891f-c5e048d94092
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 031eaf0a1de86f354b89152c0ea48b2852de3f86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="isdefaultconstructible-class"></a>is_default_constructible – třída
Testy, pokud typ má výchozí konstruktor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Ty>  
struct is_default_constructible;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je typu třídy, která má výchozí konstruktor, jinak má hodnotu false. Jde o ekvivalent predikát `is_constructible<T>`. Typ `T` musí být typu dokončení `void`, nebo pole neznámé hranice.  
  
## <a name="example"></a>Příklad  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
struct Simple  
{  
    Simple() : val(0) {}  
    int val;  
};  
  
struct Simple2  
{  
    Simple2(int v) : val(v) {}  
    int val;  
};  
  
int main()  
{  
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha  
        << std::is_default_constructible<Simple>::value << std::endl;  
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha  
        << std::is_default_constructible<Simple2>::value << std::endl;  
  
    return (0);  
}  
  
```  
  
```Output  
is_default_constructible<Simple> == true  
is_default_constructible<Simple2> == false  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)

