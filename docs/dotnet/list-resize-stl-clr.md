---
title: list::Resize (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::resize
dev_langs: C++
helpviewer_keywords: resize member [STL/CLR]
ms.assetid: c4b8d41f-a62b-4dbc-8568-0e0a9da24016
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1bded7710d15aba5a87f763d530cc2054d8fdbc4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listresize-stlclr"></a>list::resize (STL/CLR)
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
 Členské funkce obou Ujistěte se, že [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()` od nynějška vrátí `new_size`. Pokud je třeba provést řízené sekvenci déle, první členská funkce připojí elementy s hodnotou `value_type()`, zatímco druhý členská funkce připojí elementy s hodnotou `val`. Chcete-li řízené sekvenci kratší, oba členské funkce efektivně vymazat posledním elementem [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size` časy. Můžete použít k zajištění, že řízené sekvenci má velikost `new_size`, ořezávání nebo odsazení aktuální řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
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
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)   
 [list::Erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)   
 [list::Insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)