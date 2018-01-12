---
title: set::set (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set::set
dev_langs: C++
helpviewer_keywords: set member [STL/CLR]
ms.assetid: 0cce8501-92ed-431c-b711-14e0b7be7375
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 381473ceebe696bce549732de6a738f733161403
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setset-stlclr"></a>set::set (STL/CLR)
Sestaví objekt kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set();  
explicit set(key_compare^ pred);  
set(set<Key>% right);  
set(set<Key>^ right);  
template<typename InIter>  
    setset(InIter first, InIter last);  
template<typename InIter>  
    set(InIter first, InIter last,  
        key_compare^ pred);  
set(System::Collections::Generic::IEnumerable<GValue>^ right);  
set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 Začátek rozsahu k vložení.  
  
 poslední  
 Konec rozsahu k vložení.  
  
 Před  
 Řazení predikát pro řízené sekvenci.  
  
 vpravo  
 Objekt, nebo rozsah k vložení.  
  
## <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `set();`  
  
 Inicializuje výchozí řazení predikát řízené sekvenci bez prvků `key_compare()`. Se používá k určení prázdný počáteční řízené sekvenci, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `explicit set(key_compare^ pred);`  
  
 Inicializuje řízené sekvenci bez prvků s řazení predikát `pred`. Se používá k určení prázdný počáteční řízené sekvenci, pomocí zadaného predikátu řazení.  
  
 Konstruktor:  
  
 `set(set<Key>% right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right.begin()`, `right.end()`), s výchozí řazení predikátu. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem set `right`, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `set(set<Key>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right->begin()`, `right->end()`), s výchozí řazení predikátu. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem set `right`, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `template<typename InIter> set(InIter first, InIter last);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s výchozí řazení predikátu. Použít k vytvoření řízené sekvenci kopie jiné pořadí, výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s řazení predikát `pred`. Použít k vytvoření kopie jiné pořadí, pomocí zadaného predikátu řazení řízené sekvenci.  
  
 Konstruktor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s výchozí řazení predikátu. Použít k vytvoření kopie jiné pořadí popsaného enumerátor, s výchozí řazení predikát řízené sekvenci.  
  
 Konstruktor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s řazení predikát `pred`. Použít k vytvoření kopie jiné pořadí popsaného enumerátor pomocí zadaného predikátu řazení řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
// construct an empty container   
    Myset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 c b a  
 a b c  
 c b a  
 a b c  
 c b a  
 c b a  
 a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::generic_container (STL/CLR)](../dotnet/set-generic-container-stl-clr.md)   
 [set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)