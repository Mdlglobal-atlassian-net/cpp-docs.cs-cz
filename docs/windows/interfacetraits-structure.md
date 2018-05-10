---
title: Interfacetraits – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4203fbb639b06e7e421809f9d901c70933d586d1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="interfacetraits-structure"></a>InterfaceTraits – struktura
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
template<typename CloakedType>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 Název rozhraní.  
  
 `CloakedType`  
 Pro RuntimeClass, implementuje a chaininterfaces – rozhraní, které nebudou v seznamu podporovaných ID rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Implementuje běžné vlastnosti rozhraní.  
  
 Druhá šablona je specializaci pro skrytá rozhraní. Třetí šablona je specializace parametrů nulovou hodnotu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`Base`|Jedná o synonymum `I0` parametr šablony.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[InterfaceTraits::CanCastTo – metoda](../windows/interfacetraits-cancastto-method.md)|Určuje, zda je zadaný ukazatel lze převést na ukazatel na `Base`.|  
|[InterfaceTraits::CastToBase – metoda](../windows/interfacetraits-casttobase-method.md)|Vrhá zadaný ukazatel na ukazatel na `Base`.|  
|[InterfaceTraits::CastToUnknown – metoda](../windows/interfacetraits-casttounknown-method.md)|Vrhá zadaný ukazatel na ukazatel IUnknown.|  
|[InterfaceTraits::FillArrayWithIid – metoda](../windows/interfacetraits-fillarraywithiid-method.md)|Přiřadí ID rozhraní `Base` na element pole určený argumentem index.|  
|[InterfaceTraits::Verify – metoda](../windows/interfacetraits-verify-method.md)|Ověřuje, že je správně odvozený Base.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[InterfaceTraits::IidCount – konstanta](../windows/interfacetraits-iidcount-constant.md)|Obsahuje počet rozhraní, které ID přidružené k aktuálnímu objektu interfacetraits –.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `InterfaceTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)