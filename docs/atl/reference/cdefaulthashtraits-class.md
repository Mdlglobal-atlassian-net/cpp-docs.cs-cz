---
title: Třída CDefaultHashTraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85cf9e27211763559617715a6c025055b25379fa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361509"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits – třída
Tato třída poskytuje statické funkce pro výpočet hodnoty hash.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>  
class CDefaultHashTraits
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v kolekci.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDefaultHashTraits::Hash](#hash)|(Statické) Volání této funkce Vypočítat hodnotu hash pro daného elementu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída obsahuje jednu statickou funkci, která vrátí hodnotu hash pro daný element. Tato třída je využíváno [CDefaultElementTraits třída](../../atl/reference/cdefaultelementtraits-class.md).  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="hash"></a>  CDefaultHashTraits::Hash  
 Volání této funkce Vypočítat hodnotu hash pro daného elementu.  
  
```
static ULONG Hash(const T& element) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Element.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu hash.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí algoritmus hash je velmi jednoduchý: Vrácená hodnota je číslo elementu. Funkci přepište, pokud se vyžaduje složitější algoritmus.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
