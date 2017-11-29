---
title: "&lt;nové&gt; funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
caps.latest.revision: "10"
manager: ghogen
ms.openlocfilehash: 6ce4e11a41f199d4ec82a593b53c2f0b7f1c47e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltnewgt-functions"></a>&lt;nové&gt; funkce
|||  
|-|-|  
|[nothrow](#nothrow)|[set_new_handler –](#set_new_handler)|  
  
##  <a name="nothrow"></a>nothrow  
 Poskytuje objekt, který se má použít jako argument `nothrow` verze **nové** a **odstranit**.  
  
```  
extern const std::nothrow_t nothrow;  
```  
  
### <a name="remarks"></a>Poznámky  
 Objekt se používá jako argument funkce tak, aby odpovídaly typu parametru [std::nothrow_t](../standard-library/nothrow-t-structure.md).  
  
### <a name="example"></a>Příklad  
  V tématu [new – operátor](../standard-library/new-operators.md#op_new) a [new – operátor &#91; &#93;](../standard-library/new-operators.md#op_new_arr) příklady `std::nothrow_t` slouží jako parametr funkce.  
  
##  <a name="set_new_handler"></a>set_new_handler –  
 Nainstaluje funkci uživatele, která má být voláno, když `operator new` selže při jeho pokusu o přidělení paměti.  
  
```  
new_handler set_new_handler(new_handler Pnew) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `Pnew`  
 New_handler k instalaci.  
  
### <a name="return-value"></a>Návratová hodnota  
 0 na prvním volání a předchozí `new_handler` na následující volání.  
  
### <a name="remarks"></a>Poznámky  
 Funkce úložiště `Pnew` v statického [novou obslužnou rutinu](../standard-library/new-typedefs.md#new_handler) ukazatele, který udržuje, vrátí hodnotu, dříve uloženou v ukazatele. Obslužná rutina nové používá [new – operátor](../standard-library/new-operators.md#op_new)( **size_t –**).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// new_set_new_handler.cpp  
// compile with: /EHsc  
#include<new>  
#include<iostream>  
  
using namespace std;  
void __cdecl newhandler( )  
{  
   cout << "The new_handler is called:" << endl;  
   throw bad_alloc( );  
   return;  
}  
  
int main( )   
{  
   set_new_handler (newhandler);  
   try  
   {  
      while ( 1 )   
      {  
         new int[5000000];  
         cout << "Allocating 5000000 ints." << endl;  
      }  
   }  
   catch ( exception e )  
   {  
      cout << e.what( ) << endl;  
   }  
}  
```  
  
```Output  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
The new_handler is called:  
bad allocation  
```  
  
## <a name="see-also"></a>Viz také  
 [\<Nový >](../standard-library/new.md)
