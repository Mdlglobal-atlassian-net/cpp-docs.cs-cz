---
title: priority_queue::priority_queue (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::priority_queue::priority_queue
dev_langs: C++
helpviewer_keywords: priority_queue member [STL/CLR]
ms.assetid: aab423d7-959e-48fd-9028-e9f45f43cb8a
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 03d0054f3c755c3dd6e4bd653c972a0f7aa6735d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="priorityqueuepriorityqueue-stlclr"></a>priority_queue::priority_queue (STL/CLR)
Vytvoří objekt kontejneru adaptéru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
priority_queue();  
priority_queue(priority_queue<Value, Container> right);  
priority_queue(priority_queue<Value, Container> right);  
explicit priority_queue(value_compare^ pred);  
priority_queue(value_compare^ pred, container_type% cont);  
template<typename InIt>  
    priority_queue(InIt first, InIt last);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred, container_type% cont);  
```  
  
#### <a name="parameters"></a>Parametry  
 potřeba  
 Kontejner pro kopírování.  
  
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
  
 `priority_queue();`  
  
 prázdný zabalené kontejner, vytvoří se výchozí řazení predikátu. Se používá k určení prázdný počáteční řízené sekvenci, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 Vytvoří zabalené kontejner, který je kopií `right.get_container()`, s řazení predikát `right.value_comp()`. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí řízené objekt fronty `right`, s stejné řazení predikátu.  
  
 Konstruktor:  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 Vytvoří zabalené kontejner, který je kopií `right->get_container()`, s řazení predikát `right->value_comp()`. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí řízené objekt fronty `*right`, s stejné řazení predikátu.  
  
 Konstruktor:  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 Vytvoří prázdný zabalené kontejner, s řazení predikát `pred`. Se používá k určení prázdný počáteční řízené sekvenci, pomocí zadaného predikátu řazení.  
  
 Konstruktor:  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 Vytvoří prázdný zabalené kontejner, s řazení predikát `pred`, pak předá všechny elementy `cont` se používá k určení počáteční řízené sekvenci z existující kontejner, pomocí zadaného predikátu řazení.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last);`  
  
 Vytvoří prázdný zabalené kontejner, s výchozí řazení predikát a pak doručí sekvenci [`first`, `last`). Se používá k určení počáteční řízené sekvenci ze zadaného eqeuence, pomocí zadaného predikátu řazení.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`  
  
 Vytvoří prázdný zabalené kontejner, s řazení predikát `pred`, pak předá sekvenci [`first`, `last`). Se používá k určení počáteční řízené sekvenci ze zadaného seqeuence, pomocí zadaného predikátu řazení.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`  
  
 Vytvoří prázdný zabalené kontejner, s řazení predikát `pred`, pak předá všechny elementy `cont` plus sekvenci [`first`, `last`). Se používá k určení počáteční řízené sekvenci z existující kontejner a zadaný seqeuence, pomocí zadaného predikátu řazení.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cliext_priority_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/deque>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
typedef cliext::deque<wchar_t> Mydeque;   
int main()   
    {   
// construct an empty container   
    Mypriority_queue c1;   
    Mypriority_queue::container_type^ wc1 = c1.get_container();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 c a b  
size() = 0  
 a c b  
 a c b  
 c a b  
 a c b  
 a a b c c b  
 c a b  
 c a b  
 a c b  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / fronty >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::Assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)   
 [priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)   
 [priority_queue::operator= (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)