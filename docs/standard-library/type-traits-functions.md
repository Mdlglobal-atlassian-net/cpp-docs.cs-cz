---
title: '&lt;type_traits&gt; funkce | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_assignable
- type_traits/std::is_copy_assignable
- type_traits/std::is_copy_constructible
- type_traits/std::is_default_constructible
- type_traits/std::is_move_assignable
- type_traits/std::is_move_constructible
- type_traits/std::is_nothrow_move_assignable
- type_traits/std::is_trivially_copy_assignable
- type_traits/std::is_trivially_move_assignable
- type_traits/std::is_trivially_move_constructible
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
caps.latest.revision: "13"
manager: ghogen
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: 668ef9fb5f1786c3830d1ad143348c26060218ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="lttypetraitsgt-functions"></a>&lt;type_traits&gt; funkce
||||  
|-|-|-|  
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|  
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|  
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|[is_trivially_move_assignable](#is_trivially_move_assignable)|  
|[is_trivially_move_constructible](#is_trivially_move_constructible)|  
  
##  <a name="is_assignable"></a>is_assignable  
 Kontroluje, zda hodnota `From` typ lze přiřadit k `To` typu.  
  
```  
template <class To, class From>  
struct is_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 Chcete-li  
 Typ objektu, který obdrží přiřazení.  
  
 From  
 Typ objektu, který obsahuje hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Unevaluated výraz `declval<To>() = declval<From>()` musí být ve správném formátu. Obě `From` a `To` musí být úplný typy `void`, nebo pole neznámé hranice.  
  
##  <a name="is_copy_assignable"></a>is_copy_assignable  
 Testy, zda má typ lze zkopírovat na přiřazení.  
  
```  
template <class Ty>  
struct is_copy_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
### <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má kopírování operátor přiřazení, jinak má hodnotu false. Ekvivalentní is_assignable\<Ty & const Ty & >.  
  
##  <a name="is_copy_constructible"></a>is_copy_constructible  
 Testy, pokud má typ kopírovacího konstruktoru.  
  
```  
template <class Ty>  
struct is_copy_constructible;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
### <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má kopírovacího konstruktoru, jinak má hodnotu false.  
  
### <a name="example"></a>Příklad  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
struct Copyable  
{  
    int val;  
};  
  
struct NotCopyable  
{  
   NotCopyable(const NotCopyable&) = delete;  
   int val;  
  
};  
  
int main()  
{  
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha  
        << std::is_copy_constructible<Copyable>::value << std::endl;  
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha  
        << std::is_copy_constructible<NotCopyable>::value << std::endl;  
  
    return (0);  
}  
  
```  
  
```Output  
is_copy_constructible<Copyable> == true  
is_copy_constructible<NotCopyable > == false  
```  
  
##  <a name="is_default_constructible"></a>is_default_constructible  
 Testy, pokud typ má výchozí konstruktor.  
  
```  
template <class Ty>  
struct is_default_constructible;  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
### <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je typu třídy, která má výchozí konstruktor, jinak má hodnotu false. Jde o ekvivalent predikát `is_constructible<T>`. Typ `T` musí být typu dokončení `void`, nebo pole neznámé hranice.  
  
### <a name="example"></a>Příklad  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
struct Simple  
{  
    Simple() : val(0) {}  
    int val;  
};  
  
struct Simple2  
{  
    Simple2(int v) : val(v) {}  
    int val;  
};  
  
int main()  
{  
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha  
        << std::is_default_constructible<Simple>::value << std::endl;  
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha  
        << std::is_default_constructible<Simple2>::value << std::endl;  
  
    return (0);  
}  
  
```  
  
```Output  
is_default_constructible<Simple> == true  
is_default_constructible<Simple2> == false  
```  
  
##  <a name="is_move_assignable"></a>is_move_assignable  
 Testy, pokud typ lze přesunout přiřazené.  
  
```  
template <class T>  
struct is_move_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
### <a name="remarks"></a>Poznámky  
 Typ je přesunout přiřadit, pokud lze přiřadit deklarátor odkazu na typ odkaz na typ. Je ekvivalentní predikátem typu `is_assignable<T&, T&&>`. Přesuňte typy Přiřaditelné obsahují kde Skalární typy a typy tříd, které mají generované kompilátorem nebo uživatelsky definovaných přesunout operátory přiřazení.  
  
##  <a name="is_move_constructible"></a>is_move_constructible  
 Ověřuje, zda má tento typ konstruktor move.  
  
```  
template <class T>  
struct is_move_constructible;  
```  
  
### <a name="parameters"></a>Parametry  
 T  
 Typ, který se má vyhodnotit  
  
### <a name="remarks"></a>Poznámky  
 Predikát typ, který se vyhodnotí na hodnotu true, pokud typ `T` lze sestavit pomocí operace přesunu. Tento predikát je ekvivalentní `is_constructible<T, T&&>`.  
  
##  <a name="is_nothrow_move_assignable"></a>is_nothrow_move_assignable  
 Kontroluje, zda má typ **nothrow** operátor move assignment.  
  
```  
template <class Ty>  
struct is_nothrow_move_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
### <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` má nothrow přesunutí operátor přiřazení, jinak má hodnotu false.  
  
##  <a name="is_trivially_copy_assignable"></a>is_trivially_copy_assignable  
 Ověřuje, zda má tento typ operátor přiřazení trivial kopírování.  
  
```  
template <class Ty>  
struct is_trivially_copy_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
### <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je třída, která má trivial kopie operátor přiřazení, jinak má hodnotu false.  
  
 Přiřazení konstruktor pro třídu `T` je jednoduchá, pokud je implicitně poskytována, třída `T` nemá žádné virtuální funkce třídy `T` nemá žádné virtuální základů, mít trivial třídy všechny členy nestatické datového typu třídy operátory přiřazení a třídy všechny členy nestatické datové pole typu třídy mají operátory trivial přiřazení.  
  
##  <a name="is_trivially_move_assignable"></a>is_trivially_move_assignable  
 Ověřuje, zda má tento typ operátor přiřazení přesunutí trivial.  
  
```  
template <class Ty>  
struct is_trivially_move_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
### <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má trivial přesunutí operátor přiřazení, jinak má hodnotu false.  
  
 Operátor přiřazení přesunutí pro třídu `Ty` je jednoduchá pokud:  
  
 implicitně je poskytována  
  
 Třída `Ty` nemá žádné virtuální funkce  
  
 Třída `Ty` nemá žádné virtuální základny  
  
 operátory přiřazení pro přesunutí trivial mít třídy všechny členy nestatické datového typu třídy  
  
 operátory přiřazení pro přesunutí trivial mít třídy všechny členy nestatické datové pole typu třídy  
  
##  <a name="is_trivially_move_constructible"></a>is_trivially_move_constructible  
 Testy, pokud má typ trivial přesunout konstruktor.  
  
```  
template <class Ty>  
struct is_trivially_move_constructible;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
### <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má trivial konstruktor move, jinak má hodnotu false.  
  
 Konstruktor move pro třídu `Ty` je jednoduchá pokud:  
  
 implicitně je deklarovaná  
  
 jeho typy parametrů jsou rovnocenná implicitní deklarace  
  
 Třída `Ty` nemá žádné virtuální funkce  
  
 Třída `Ty` nemá žádné virtuální základny  
  
 Třída nemá žádné volatile nestatické datové členy  
  
 všechny přímo základny třídy `Ty` mít konstruktory trivial přesunutí  
  
 třídy všechny členy nestatické datového typu třídy mít konstruktory trivial přesunutí  
  
 třídy všechny členy nestatické datové pole typu třídy mít konstruktory trivial přesunutí  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)
