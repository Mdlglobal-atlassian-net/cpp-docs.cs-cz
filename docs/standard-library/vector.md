---
title: '&lt;vektor&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <vector>
dev_langs:
- C++
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94038dcbda6c35723fabbaee153902ec48e45c71
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltvectorgt"></a>&lt;vektor&gt;
Definuje vektoru třída šablony kontejneru a několika podpůrné šablony.  
  
 `vector` Je kontejner, který slouží k uspořádání elementy daného typu v lineární pořadí. Umožňuje vysoká rychlost náhodného přístup k žádné elementu a dynamické přidání a odstraňování do a z pořadí. `vector` Je upřednostňovaný kontejner pro pořadí, když výkonu náhodný přístup premium.  
  
 Další informace o třídě `vector`, najdete v části [vector – třída](../standard-library/vector-class.md). Informace o specializace `vector<bool>`, najdete v části [vektoru\<bool > třída](../standard-library/vector-bool-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace std {  
template <class Type, class Allocator>  
class vector;  
template <class Allocator>  
class vector<bool>;  
 
template <class Allocator>  
struct hash<vector<bool, Allocator>>;  
 // TEMPLATE FUNCTIONS  
template <class Type, class Allocator>  
bool operator== (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator!= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator<(
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator> (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator<= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator>= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
void swap (
    vector<Type, Allocator>& left,  
    vector<Type, Allocator>& right);

}  // namespace std  
```  
  
#### <a name="parameters"></a>Parametry  
 Typ  
 Parametr šablony pro typ dat uložených v vektoru.  
  
 Allocator  
 Parametr šablony pro objekt uložená allocator zodpovědná za přidělování paměti a zrušení přidělení.  
  
 `left`  
 První vektoru (levém) v rámci operace porovnání  
  
 `right`  
 Druhý vektoru (napravo) v rámci operace porovnání.  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operator – operátor! =](../standard-library/vector-operators.md#op_neq)|Testy, pokud vektoru objekt na levé straně operátoru není stejný jako vektoru objekt na pravé straně.|  
|[operátor <](../standard-library/vector-operators.md#op_lt)|Testy, pokud vektoru objekt na levé straně operátor je menší než vektoru objekt na pravé straně.|  
|[Operátor\<=](../standard-library/vector-operators.md#op_gt_eq)|Pokud vektoru objekt na levé straně operátoru testů je menší než nebo rovno vektoru objekt na pravé straně.|  
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|Testy, pokud vektoru objekt na levé straně operátoru rovná vektoru objekt na pravé straně.|  
|[operator>](../standard-library/vector-operators.md#op_gt)|Testy, pokud vektoru objekt na levé straně operátoru je větší než vektoru objekt na pravé straně.|  
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Testy, pokud je vektoru objekt na levé straně operátoru větší než nebo rovna hodnotě vektoru objekt na pravé straně.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[vector – třída](../standard-library/vector-class.md)|Šablony třídy kontejnerů pořadí, které umožňuje uspořádat prvky daného typu v lineární uspořádání a povolit vysoká rychlost náhodného přístup k libovolného elementu.|  
  
### <a name="specializations"></a>Specializace  
  
|||  
|-|-|  
|[vektor\<bool > – třída](../standard-library/vector-bool-class.md)|Úplné specializace šablony vektoru třídy pro elementy typu `bool` s přidělení pro základní typ používané specializace.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<vektoru >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)

