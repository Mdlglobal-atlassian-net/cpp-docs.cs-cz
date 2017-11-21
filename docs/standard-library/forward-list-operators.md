---
title: "&lt;forward_list –&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
dev_langs: C++
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
caps.latest.revision: "11"
manager: ghogen
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: c00c7d1e506e60a0a8612601835ef4a91b98ea99
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list –&gt; operátory
||||  
|-|-|-|  
|[Operator! =](#op_neq)|[operátor&gt;](#op_gt)|[operátor&gt;=](#op_gt_eq)|  
|[operátor&lt;](#op_lt)|[operátor&lt;=](#op_lt_eq)|[Operator ==](#op_eq_eq)|  
  
##  <a name="op_eq_eq"></a>Operator ==  
 Testy, pokud se objekt dopředného seznamu na levé straně operátoru rovná objektu dopředného seznamu na pravé straně.  
  
```
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`left`|Objekt typu `forward_list`.|  
|`right`|Objekt typu `forward_list`.|  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce šablony přetížení `operator==` k porovnání dvou objektů třídy šablony `forward_list`. Funkce vrátí hodnotu `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.  
  
##  <a name="op_neq"></a>Operator! =  
 Testy, pokud není objekt dopředného seznamu na levé straně operátoru rovná objektu dopředného seznamu na pravé straně.  
  
```
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`left`|Objekt typu `forward_list`.|  
|`right`|Objekt typu `forward_list`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud seznamy není stejný; **false** Pokud seznamy jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Šablona funkce vrátí hodnotu `!(left == right)`.  
  
##  <a name="op_lt"></a>operátor&lt;  
 Testy, pokud objekt dopředného seznamu na levé straně operátoru je menší než dopředného list objekt na pravé straně.  
  
```
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`left`|Objekt typu `forward_list`.|  
|`right`|Objekt typu `forward_list`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud v seznamu na levé straně operátor je menší než, ale není rovno v seznamu na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce šablony přetížení `operator<` k porovnání dvou objektů třídy šablony `forward_list`. Funkce vrátí hodnotu `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.  
  
##  <a name="op_lt_eq"></a>operátor&lt;=  
 Pokud seznamu dopředného objekt na levé straně operátoru testů je menší než nebo rovna hodnotě dopředného list objekt na pravé straně.  
  
```
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`left`|Objekt typu `forward_list`.|  
|`right`|Objekt typu `forward_list`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud v seznamu na levé straně operátor je menší než nebo rovna v seznamu na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Šablona funkce vrátí hodnotu `!(right < left)`.  
  
##  <a name="op_gt"></a>operátor&gt;  
 Testy, pokud objekt dopředného seznamu na levé straně operátoru je větší než dopředného list objekt na pravé straně.  
  
```
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`left`|Objekt typu `forward_list`.|  
|`right`|Objekt typu `forward_list`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud v seznamu na levé straně operátor je větší než v seznamu na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Šablona funkce vrátí hodnotu `right < left`.  
  
##  <a name="op_gt_eq"></a>operátor&gt;=  
 Testy, pokud objekt dopředného seznamu na levé straně operátoru je větší než nebo rovna hodnotě dopředného list objekt na pravé straně.  
  
```
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`left`|Objekt typu `forward_list`.|  
|`right`|Objekt typu `forward_list`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud dopředného seznamu na levé straně operátoru je větší než nebo rovno dopředného seznamu na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí `!(left < right)`.  
  
## <a name="see-also"></a>Viz také  
 [< forward_list – >](../standard-library/forward-list.md)



