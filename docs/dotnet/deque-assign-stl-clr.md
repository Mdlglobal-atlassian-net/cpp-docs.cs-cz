---
title: deque::Assign (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::assign
dev_langs:
- C++
helpviewer_keywords:
- assign member [STL/CLR]
ms.assetid: 03fafdbb-6b10-4464-b3dc-0cc5cb8ac980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e53bb976b854716799ced11367cf799f7ccb5cce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="dequeassign-stlclr"></a>deque::assign (STL/CLR)
Nahradí všechny elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Počet elementů k vložení.  
  
 `first`  
 Začátek rozsahu k vložení.  
  
 `last`  
 Konec rozsahu k vložení.  
  
 `right`  
 Výčet k vložení.  
  
 `val`  
 Hodnota elementu, který chcete vložit.  
  
## <a name="remarks"></a>Poznámky  
 První člen funkce nahradí řízené sekvenci opakování `count` elementy hodnoty `val`. Použijete jej vyplníte kontejneru elementů všechny má stejnou hodnotu.  
  
 Pokud `InIt` je celočíselného typu, druhý členská funkce se chová stejně jako `assign((size_type)first, (value_type)last)`. Jinak nahradí řízené sekvenci s pořadím [`first`, `last`). Použijete jej aby řízené pořadí kopii jiného pořadí.  
  
 Třetí členská funkce nahradí řízené sekvenci pořadí určených enumerátor `right`. Můžete použít k vytvoření kopie pořadí popsaného enumerátor řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cliext_deque_assign.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / deque >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)