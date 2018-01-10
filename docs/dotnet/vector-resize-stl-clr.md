---
title: Vector::Resize (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::resize
dev_langs: C++
helpviewer_keywords: resize member [STL/CLR]
ms.assetid: a3556fbc-67d9-463a-9ffc-cb43ee15657f
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3b4fbc196f9e4ca14ee8d8e744da380e08ec4d8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vectorresize-stlclr"></a>vector::resize (STL/CLR)
Změní počet elementů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>Parametry  
 new_size  
 Nová velikost řízené sekvenci.  
  
 Val  
 Hodnota odsazení elementu.  
  
## <a name="remarks"></a>Poznámky  
 Členské funkce obou Ujistěte se, že [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()` od nynějška vrátí `new_size`. Pokud je třeba provést řízené sekvenci déle, první členská funkce připojí elementy s hodnotou `value_type()`, zatímco druhý členská funkce připojí elementy s hodnotou `val`. Chcete-li řízené sekvenci kratší, oba členské funkce efektivně vymazat posledním elementem [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size` časy. Můžete použít k zajištění, že řízené sekvenci má velikost `new_size`, ořezávání nebo odsazení aktuální řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / vektoru >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)   
 [Vector::Erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)   
 [vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)