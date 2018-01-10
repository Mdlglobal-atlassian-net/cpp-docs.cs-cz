---
title: hash_multimap::hash_multimap (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multimap::hash_multimap
dev_langs: C++
helpviewer_keywords: hash_multimap member [STL/CLR]
ms.assetid: a1d576a7-5dc7-4ad9-abef-ee7a13caaec3
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cff49bfad9143663e8fe5d895c885918bff4a7a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultimaphashmultimap-stlclr"></a>hash_multimap::hash_multimap (STL/CLR)
Sestaví objekt kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
hash_multimap();  
explicit hash_multimap(key_compare^ pred);  
hash_multimap(key_compare^ pred, hasher^ hashfn);  
hash_multimap(hash_multimap<Key, Mapped>% right);  
hash_multimap(hash_multimap<Key, Mapped>^ right);  
template<typename InIter>  
    hash_multimaphash_multimap(InIter first, InIter last);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `hash_multimap();`  
  
 Inicializuje výchozí řazení predikát řízené sekvenci bez prvků `key_compare()`a pomocí funkce výchozí hodnoty hash. Se používá k určení prázdný počáteční řízené sekvenci, s výchozí řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `explicit hash_multimap(key_compare^ pred);`  
  
 Inicializuje řízené sekvenci bez prvků s řazení predikát `pred`a pomocí funkce výchozí hodnoty hash. Se používá k určení prázdný počáteční řízené sekvenci, pomocí zadaného predikátu řazení a výchozí funkce hash.  
  
 Konstruktor:  
  
 `hash_multimap(key_compare^ pred, hasher^ hashfn);`  
  
 Inicializuje řízené sekvenci bez prvků s řazení predikát `pred`a pomocí funkce hash `hashfn`. Se používá k určení prázdný počáteční řízené sekvenci, pomocí zadané řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `hash_multimap(hash_multimap<Key, Mapped>% right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right.begin()`, `right.end()`), s výchozí řazení predikátu a pomocí funkce výchozí hodnoty hash. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem hash_multimap `right`, s výchozí řazení predikát a funkce hash.  
  
 Konstruktor:  
  
 `hash_multimap(hash_multimap<Key, Mapped>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right->begin()`, `right->end()`), s výchozí řazení predikátu a pomocí funkce výchozí hodnoty hash. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem hash_multimap `right`, s výchozí řazení predikát a funkce hash.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_multimap(InIter first, InIter last);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s výchozí řazení predikátu a pomocí funkce výchozí hodnoty hash. Použít k vytvoření řízené sekvenci kopie jiné pořadí, výchozí řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_multimap(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s řazení predikát `pred`a pomocí funkce výchozí hodnoty hash. Použít k vytvoření řízené sekvenci kopie jiné pořadí, pomocí zadaného predikátu řazení a výchozí funkce hash.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_multimap(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s řazení predikát `pred`a pomocí funkce hash `hashfn`. Použít k vytvoření řízené sekvenci kopie jiné pořadí, pomocí zadané řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s výchozí řazení predikátu a pomocí funkce výchozí hodnoty hash. Použít k vytvoření řízené sekvenci kopie jiné pořadí popsaného enumerátor, s výchozí řazení funkce predikátu a hodnoty hash.  
  
 Konstruktor:  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s řazení predikát `pred`a pomocí funkce výchozí hodnoty hash. Použít k vytvoření řízené sekvenci kopie jiné pořadí popsaného enumerátor s zadaný řazení predikát a výchozí funkce hash.  
  
 Konstruktor:  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s řazení predikát `pred`a pomocí funkce hash `hashfn`. Použít k vytvoření řízené sekvenci kopie jiné pořadí popsaného enumerátor pomocí zadané řazení funkce predikátu a hodnoty hash.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
// construct an empty container   
    Myhash_multimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multimap c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multimap c3(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multimap c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c4h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3);   
    for each (Myhash_multimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multimap c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c6h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multimap c7(c4);   
    for each (Myhash_multimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Myhash_multimap c8(%c3);   
    for each (Myhash_multimap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap::generic_container (STL/CLR)](../dotnet/hash-multimap-generic-container-stl-clr.md)   
 [hash_multimap::operator= (STL/CLR)](../dotnet/hash-multimap-operator-assign-stl-clr.md)