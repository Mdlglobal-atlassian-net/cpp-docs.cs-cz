---
title: "binary_delegate_noreturn – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::binary_delegate_noreturn
dev_langs: C++
helpviewer_keywords: binary_delegate_noreturn function [STL/CLR]
ms.assetid: 055c7e9d-e5c3-48fe-9327-3f6316e8a51e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ee1ac1ddbd78bba8a6d01f29d45f94e63644dc5a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="binarydelegatenoreturn-stlclr"></a>binary_delegate_noreturn (STL/CLR)
Třída genereic popisuje dva argument delegáta, který vrátí `void`. Můžete ji použít zadejte delegáta z hlediska jeho argumentem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
generic<typename Arg1,  
    typename Arg2>  
    delegate void binary_delegate(Arg1, Arg2);  
```  
  
#### <a name="parameters"></a>Parametry  
 arg1  
 Typ prvního argumentu.  
  
 arg2  
 Typ druhý argument.  
  
## <a name="remarks"></a>Poznámky  
 Delegát genereic popisuje dva argument funkci vracející `void`.  
  
 Všimněte si, že pro:  
  
 `binary_delegate_noreturn<int, int> Fun1;`  
  
 `binary_delegate_noreturn<int, int> Fun2;`  
  
 typy `Fun1` a `Fun2` jsou synonyma, při pro:  
  
 `delegate void Fun1(int, int);`  
  
 `delegate void Fun2(int, int);`  
  
 nejsou stejného typu.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_binary_delegate_noreturn.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
void key_compare(wchar_t left, wchar_t right)   
    {   
    System::Console::WriteLine("compare({0}, {1}) = {2}",   
        left, right, left < right);   
    }   
  
typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    kcomp(L'a', L'a');   
    kcomp(L'a', L'b');   
    kcomp(L'b', L'a');   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(a, a) = False  
compare(a, b) = True  
compare(b, a) = False  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / funkční >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)   
 [unary_delegate (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)   
 [unary_delegate_noreturn – (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)