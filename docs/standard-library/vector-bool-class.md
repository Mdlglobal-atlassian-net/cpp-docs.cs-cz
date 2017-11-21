---
title: "vektor&lt;bool&gt; třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vector<bool>
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::pointer
- vector/std::vector::flip
- vector/std::vector::swap
dev_langs: C++
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 718cb52bbc06645ec40fe5e35ba0a8cc55ff1778
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vectorltboolgt-class"></a>vektor&lt;bool&gt; – třída
`vector<bool>` Třída je částečná specializace [vektoru](../standard-library/vector-class.md) pro elementy typu `bool`. Má přidělení pro základní typ, který je používán specializace, která poskytuje optimalizace místa uložením jeden `bool` hodnotu za bit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Allocator = allocator<bool>>  
class vector<bool, Allocator>  
```  
  
## <a name="remarks"></a>Poznámky  
 Specializace šablony Tato třída se chová jako vektoru, s výjimkou rozdíly popsaných v tomto článku.  
  
 Operace, které pracují s `bool` typ odpovídají hodnotám v úložišti kontejneru. `allocator_traits::construct`můžete vytvořit tyto hodnoty se nepoužije.  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[const_pointer –](#const_pointer)|Typedef k `const_iterator` , může sloužit jako ukazatel konstantní logickou prvek `vector<bool>`.|  
|[const_reference –](#const_reference)|Typedef pro `bool`. Po inicializaci nekontroluje aktualizace původní hodnoty.|  
|[ukazatele](#pointer)|Typedef pro `iterator` , může sloužit jako ukazatel na logickou elementu `vector<bool>`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[Překlopit](#flip)|Vrátí zpět všechny bitů `vector<bool>`.|  
|[swap](#swap)|Výměny dva elementy `vector<bool>`s.|  
|[operátor &#91; &#93;](#op_at)|Vrátí simulované odkaz na `vector<bool>` element na zadané pozici.|  
|`at`|Funguje stejně jako unspecialized [vektoru](../standard-library/vector-class.md):: na funkce, s výjimkou toho, které se používá třídu proxy [vektoru\<bool >:: odkaz](#reference_class). Viz také [operátor &#91; &#93;](#op_at).|  
|`front`|Funguje stejně jako unspecialized [vektoru](../standard-library/vector-class.md):: front funkce, s tím rozdílem, že používá třídu proxy [vektoru\<bool >:: odkaz](#reference_class). Viz také [operátor &#91; &#93;](#op_at).|  
|`back`|Funguje stejně jako unspecialized [vektoru](../standard-library/vector-class.md):: zpět funkce, s tím rozdílem, že používá třídu proxy [vektoru\<bool >:: odkaz](#reference_class). Viz také [operátor &#91; &#93;](#op_at).|  
  
### <a name="proxy-class"></a>Třída proxy  
  
|||  
|-|-|  
|[vektor\<bool > odkazovat – třída](#reference_class)|Třídu, která funguje jako proxy pro simulaci `bool&` chování a jejichž objekty může poskytnout odkazy na elementy (jeden bits) v rámci `vector<bool>` objektu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: \<vektoru >  
  
 **Namespace:** – std  
  
##  <a name="const_pointer"></a>vektor\<bool >:: const_pointer –  
 Typ, který popisuje objekt, který může sloužit jako konstantní ukazatel na element Boolean obsažený v pořadí `vector<bool>` objektu.  
  
```  
typedef const_iterator const_pointer;  
```  
  
##  <a name="const_reference"></a>vektor\<bool >:: const_reference –  
 Typ, který popisuje objekt, který může sloužit jako konstantní odkaz na element Boolean obsažený v pořadí `vector<bool>` objektu.  
  
```  
typedef bool const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace a příklady kódu najdete v tématu [vektoru&lt;bool&gt;:: reference::operator =](#reference_operator_eq).  
  
##  <a name="flip"></a>vektor\<bool >:: překlopit  
 Vrátí zpět všechny bitů `vector<bool>`.  
  
```  
void flip();
```  
  
### <a name="example"></a>Příklad  
  
```cpp  
// vector_bool_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha; // format output for subsequent code  
  
    vector<bool> vb = { true, false, false, true, true };  
    cout << "The vector is:" << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vb.flip();  
  
    cout << "The flipped vector is:" << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="op_at"></a>vektor\<bool >:: [] – operátor  
 Vrátí simulované odkaz na `vector<bool>` element na zadané pozici.  
  
```  
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`Pos`|Pozice `vector<bool>` elementu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 A [vektoru\<bool >:: odkaz](#reference_class) nebo [vektoru\<bool >:: const_reference –](#const_reference) objekt, který obsahuje hodnotu indexovaného elementu.  
  
 Pokud je zadaná pozice větší nebo rovna velikosti kontejneru, výsledek je nedefinován.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je kompilovat s `_ITERATOR_DEBUG_LEVEL` nastavit, Chyba spuštění dojde, pokud se pokusíte o přístup k elementu mimo hranice vektoru.  Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Příklad  
  Tento příklad kódu ukazuje správné použití `vector<bool>::operator[]` a dvě běžné chyb, které jsou vloženy do komentáře kódu. Tyto chyby způsobit chyby, protože adresu `vector<bool>::reference` objektu, který `vector<bool>::operator[]` vrátí nelze vytvářet.  
  
```cpp  
// cl.exe /EHsc /nologo /W4 /MTd   
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
    vector<bool> vb;  
  
    vb.push_back(true);  
    vb.push_back(false);  
  
    //    bool* pb = &vb[1]; // conversion error - do not use  
    //    bool& refb = vb[1];   // conversion error - do not use  
    bool hold = vb[1];  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
  
    // Note this doesn't modify hold.  
    vb[1] = true;  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
}  
```  
  
##  <a name="pointer"></a>vektor\<bool >:: ukazatele  
 Typ, který popisuje objekt, který může sloužit jako ukazatel na element Boolean obsažený v pořadí `vector<bool>` objektu.  
  
```  
typedef iterator pointer;  
```  
  
##  <a name="reference_class"></a>vektor\<bool >:: odkazovat – třída  
 `vector<bool>::reference` Třídy je třída proxy poskytované [vektoru\<bool > třída](../standard-library/vector-bool-class.md) k simulaci `bool&`.  
  
### <a name="remarks"></a>Poznámky  
 Simulovaný odkaz je vyžadován, protože jazyk C++ nativně neumožňuje přímé odkazy na bity. `vector<bool>`používá jenom jeden bit na element, který lze odkazovat pomocí této třídy proxy serveru. Simulace odkazu však není kompletní, protože určitá přiřazení nejsou platná. Například protože adresu `vector<bool>::reference` objekt nelze vytvářet, následující kód, který používá [vektoru\<bool >:: operátor &#91; &#93;](#op_at) není správný:  
  
```cpp  
vector<bool> vb;  
//...  
bool* pb = &vb[1]; // conversion error - do not use  
bool& refb = vb[1];   // conversion error - do not use  
```  
  
###  <a name="reference_flip"></a>vektor\<bool >:: Reference::Flip –  
 Invertuje výběr logická hodnota odkazovaný [vektoru\<bool >](../standard-library/vector-bool-class.md) element.  
  
```  
void flip();
```  
  
#### <a name="example"></a>Příklad  
  
```cpp  
// vector_bool_ref_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    cout << "The vector is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vector<bool>::reference vbref = vb.front();  
    vbref.flip();  
  
    cout << "The vector with first element flipped is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
```  
  
```Output  
The vector is:  
    true false false true true  
The vector with first element flipped is:  
    false false false true true  
```  
  
###  <a name="reference_operator_bool"></a>vektor\<bool >:: reference::operator bool  
 Poskytuje implicitní převod z `vector<bool>::reference` k `bool`.  
  
```  
operator bool() const;
```  
  
#### <a name="return-value"></a>Návratová hodnota  
 Logická hodnota elementu vektoru\<bool > objektu.  
  
#### <a name="remarks"></a>Poznámky  
 `vector<bool>` Objektu nelze změnit pomocí tento operátor.  
  
###  <a name="reference_operator_eq"></a>vektor\<bool >:: reference::operator =  
 Přiřadí k bitu logickou hodnotu nebo hodnotu obsaženou referenčním prvkem.  
  
```  
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```  
  
#### <a name="parameters"></a>Parametry  
 `Right`  
 Odkaz prvku, jehož hodnota má být přiřazena k bitu.  
  
 `Val`  
 Logická hodnota, která má být přiřazena k bitu.  
  
#### <a name="example"></a>Příklad  
  
```cpp  
// vector_bool_ref_op_assign.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    print("The vector is: ", vb);  
  
    // Invoke vector<bool>::reference::operator=()  
    vector<bool>::reference refelem1 = vb[0];  
    vector<bool>::reference refelem2 = vb[1];  
    vector<bool>::reference refelem3 = vb[2];  
  
    bool b1 = refelem1;  
    bool b2 = refelem2;  
    bool b3 = refelem3;  
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;  
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;  
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;  
    cout << endl;  
  
    refelem2 = refelem1;  
  
    print("The vector after assigning refelem1 to refelem2 is now: ", vb);  
  
    refelem3 = true;  
  
    print("The vector after assigning false to refelem1 is now: ", vb);  
  
    // The initial values are still stored in the bool variables and remained unchanged  
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;  
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;  
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;  
    cout << endl;  
}  
```  
  
```Output  
The vector is: true false false true true  
The original value of the 1st element stored in a bool: true  
The original value of the 2nd element stored in a bool: false  
The original value of the 3rd element stored in a bool: false  
  
The vector after assigning refelem1 to refelem2 is now: true true false true true  
The vector after assigning false to refelem1 is now: true true true true true  
The original value of the 1st element still stored in a bool: true  
The original value of the 2nd element still stored in a bool: false  
The original value of the 3rd element still stored in a bool: false  
```  
  
##  <a name="swap"></a>vektor\<bool >:: swap  
 Statické členské funkce, která výměny dva elementy Boolean vektorů ( `vector<bool>`) s použitím třídy proxy [vektoru\<bool >:: odkaz](#reference_class).  
  
```  
static void swap(
    reference Left,  
    reference Right);
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Element k výměně s `Right` elementu.  
  
 `Right`  
 Element k výměně s `Left` elementu.  
  
### <a name="remarks"></a>Poznámky  
 Toto přetížení podporuje požadavky dané speciální proxy `vector<bool>`. [vektor](../standard-library/vector-class.md):: swap má stejné funkce jako jeden argument přetížení `vector<bool>::swap()`.  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)

