---
title: "writeonly_texture_view – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
dev_langs:
- C++
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3ab115301a6d7063ba443cf528b382ae955360f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="writeonlytextureview-class"></a>writeonly_texture_view – třída
Poskytuje přístup writeonly k texturou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
class writeonly_texture_view;  
 
template <
    typename value_type,  
    int _Rank  
>  
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementů v textury.  
  
 `_Rank`  
 Pořadí textury.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`scalar_type`||  
|`value_type`|Typ elementů v textury.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[writeonly_texture_view Constructor](#ctor)|Inicializuje novou instanci třídy `writeonly_texture_view` třídy.|  
|[~writeonly_texture_view Destructor](#ctor)|Zničí `writeonly_texture_view` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[set](#set)|Nastaví hodnotu elementu v zadaném indexu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator=](#operator_eq)|Zkopíruje zadaný `writeonly_texture_view` k tomuto objektu.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[pořadí konstanta](#rank)|Získá pořadí `writeonly_texture_view` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_Texture_base`  
  
 `writeonly_texture_view`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp_graphics.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="dtor"></a> ~writeonly_texture_view 

 Zničí `writeonly_texture_view` objektu.  
  
```  
~writeonly_texture_view() restrict(amp,cpu);
```  
  
##  <a name="operator_eq"></a> operátor = 

 Zkopíruje zadaný `writeonly_texture_view` k tomuto objektu.  
  
```  
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `writeonly_texture_view` objekt, který chcete zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `writeonly_texture_view` objektu.  
  
##  <a name="rank"></a> Pořadí 

 Získá pořadí `writeonly_texture_view` objektu.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="set"></a> nastavení 

 Nastaví hodnotu elementu v zadaném indexu.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index elementu.  
  
 `value`  
 Nová hodnota elementu.  
  
##  <a name="ctor"></a> writeonly_texture_view 

 Inicializuje novou instanci třídy `writeonly_texture_view` třídy.  
  
```  
writeonly_texture_view(
    texture<value_type, 
    _Rank>& _Src) restrict(amp);

 
writeonly_texture_view(
    const writeonly_texture_view<value_type,  
    _Rank>& _Src) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí textury.  
  
 `value_type`  
 Typ elementů v textury.  
  
 `_Src`  
 Texture, který se používá k vytvoření `writeonly_texture_view`.  
  
## <a name="see-also"></a>Viz také  
 [Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
