---
title: hash_set::hash_set (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_set::hash_set
dev_langs: C++
helpviewer_keywords: hash_set member [STL/CLR]
ms.assetid: 006414ed-db5a-4c08-ac81-4a8ae57d0aad
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4e4a7e2975402183c0cabf46ce786bf3877fe6d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hashsethashset-stlclr"></a>hash_set::hash_set (STL/CLR)
Sestaví objekt kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
hash_set();  
explicit hash_set(key_compare^ pred);  
hash_set(key_compare^ pred, hasher^ hashfn);  
hash_set(hash_set<Key>% right);  
hash_set(hash_set<Key>^ right);  
template<typename InIter>  
    hash_sethash_set(InIter first, InIter last);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 Začátek rozsahu k vložení.  
  
 hashfn  
 Hash – funkce pro mapování klíče intervalů.  
  
 poslední  
 Konec rozsahu k vložení.  
  
 Před  
 Řazení predikát pro řízené sekvenci.  
  
 vpravo  
 Objekt, nebo rozsah k vložení.  
  
## <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `hash_set();`  
  
 Inicializuje výchozí řazení predikát řízené sekvenci bez prvků `key_compare()`a pomocí funkce výchozí hodnoty hash. Se používá k určení prázdný počáteční řízené sekvenci, s výchozí řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `explicit hash_set(key_compare^ pred);`  
  
 Inicializuje řízené sekvenci bez prvků s řazení predikát `pred`a pomocí funkce výchozí hodnoty hash. Se používá k určení prázdný počáteční řízené sekvenci, pomocí zadaného predikátu řazení a výchozí funkce hash.  
  
 Konstruktor:  
  
 `hash_set(key_compare^ pred, hasher^ hashfn);`  
  
 Inicializuje řízené sekvenci bez prvků s řazení predikát `pred`a pomocí funkce hash `hashfn`. Se používá k určení prázdný počáteční řízené sekvenci, pomocí zadané řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `hash_set(hash_set<Key>% right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right.begin()`, `right.end()`), s výchozí řazení predikátu a pomocí funkce výchozí hodnoty hash. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem hash_set `right`, s výchozí řazení predikát a funkce hash.  
  
 Konstruktor:  
  
 `hash_set(hash_set<Key>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right->begin()`, `right->end()`), s výchozí řazení predikátu a pomocí funkce výchozí hodnoty hash. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem hash_set `right`, s výchozí řazení predikát a funkce hash.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_set(InIter first, InIter last);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s výchozí řazení predikátu a pomocí funkce výchozí hodnoty hash. Použít k vytvoření řízené sekvenci kopie jiné pořadí, výchozí řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s řazení predikát `pred`a pomocí funkce výchozí hodnoty hash. Použít k vytvoření řízené sekvenci kopie jiné pořadí, pomocí zadaného predikátu řazení a výchozí funkce hash.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s řazení predikát `pred`a pomocí funkce hash `hashfn`. Použít k vytvoření řízené sekvenci kopie jiné pořadí, pomocí zadané řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s výchozí řazení predikátu a pomocí funkce výchozí hodnoty hash. Použít k vytvoření řízené sekvenci kopie jiné pořadí popsaného enumerátor, s výchozí řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s řazení predikát `pred`a pomocí funkce výchozí hodnoty hash. Použít k vytvoření řízené sekvenci kopie jiné pořadí popsaného enumerátor s zadaný řazení predikát a výchozí funkce hash.  
  
 Konstruktor:  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s řazení predikát `pred`a pomocí funkce hash `hashfn`. Použít k vytvoření řízené sekvenci kopie jiné pořadí popsaného enumerátor pomocí zadané řazení funkce predikátu a hodnoty hash.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_set_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
// construct an empty container   
    Myhash_set c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_set c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_set c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_set c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_set c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_set c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_set c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_set c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_set c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_set c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_set c8(%c3);   
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
 a b c  
size() = 0  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_set >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::generic_container (STL/CLR)](../dotnet/hash-set-generic-container-stl-clr.md)   
 [hash_set::Operator = (STL/CLR)](../dotnet/hash-set-operator-assign-stl-clr.md)