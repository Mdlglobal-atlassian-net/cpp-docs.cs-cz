---
title: deque::deque (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::deque
dev_langs:
- C++
helpviewer_keywords:
- deque member [STL/CLR]
ms.assetid: e5bc9511-619e-469c-b50a-e06858e7fce7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 433b6ff053db0c642c2a81a5765755c9f42e1a0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="dequedeque-stlclr"></a>deque::deque (STL/CLR)
Sestaví objekt kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Počet elementů k vložení.  
  
 `first`  
 Začátek rozsahu k vložení.  
  
 `last`  
 Konec rozsahu k vložení.  
  
 `right`  
 Objekt, nebo rozsah k vložení.  
  
 `val`  
 Hodnota elementu, který chcete vložit.  
  
## <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `deque();`  
  
 Inicializuje řízené sekvenci s žádné elementy. Se používá k určení prázdný počáteční řízené sekvenci.  
  
 Konstruktor:  
  
 `deque(deque<Value>% right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right.begin()`, `right.end()`). Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem deque `right`. Další informace o iterátory najdete v tématu [deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md) a [deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md).  
  
 Konstruktor:  
  
 `deque(deque<Value>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right->begin()`, `right->end()`). Se používá k určení počáteční řízené sekvenci, který je kopií pořadí řízené deque objekt, jehož popisovač `right`.  
  
 Konstruktor:  
  
 `explicit deque(size_type count);`  
  
 Inicializuje řízené sekvenci s `count` elementy s hodnotou `value_type()`. Použijete jej vyplníte kontejneru elementů všechny má výchozí hodnotu.  
  
 Konstruktor:  
  
 `deque(size_type count, value_type val);`  
  
 Inicializuje řízené sekvenci s `count` elementy s hodnotou `val`. Použijete jej vyplníte kontejneru elementů všechny má stejnou hodnotu.  
  
 Konstruktor:  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`). Použít k vytvoření kopie jiné pořadí řízené sekvenci.  
  
 Konstruktor:  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`. Použít k vytvoření kopie jiné pořadí popsaného enumerátor řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / deque >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::Assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)   
 [deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)   
 [operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)