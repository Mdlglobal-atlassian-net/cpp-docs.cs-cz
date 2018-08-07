---
title: Implementuje strukturu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
dev_langs:
- C++
helpviewer_keywords:
- Implements structure
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0dc23a9c90fc2112d67180ceae86ebde0e057b06
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607803"
---
# <a name="implements-structure"></a>Implementuje strukturu
Implementuje `QueryInterface` a `GetIid` pro zadaných rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct __declspec(novtable) Implements : Details::ImplementsHelper<RuntimeClassFlags<WinRt>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT>, Details::ImplementsBase;  
template <  
   int flags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
struct __declspec(novtable) Implements<RuntimeClassFlags<flags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : Details::ImplementsHelper<RuntimeClassFlags<flags>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT>, Details::ImplementsBase;  
```  
  
### <a name="parameters"></a>Parametry  
 *I0*  
 ID nultého rozhraní. (Povinné)  
  
 *I1*  
 ID prvního rozhraní. (Volitelné)  
  
 *I2*  
 Druhé ID rozhraní. (Volitelné)  
  
 *I3*  
 ID třetího rozhraní. (Volitelné)  
  
 *TYP I4*  
 ID čtvrtého rozhraní. (Volitelné)  
  
 *I5*  
 ID pátého rozhraní. (Volitelné)  
  
 *I6*  
 ID šestého rozhraní. (Volitelné)  
  
 *I7*  
 ID sedmého rozhraní. (Volitelné)  
  
 *I8*  
 ID osmého rozhraní. (Volitelné)  
  
 *I9*  
 ID devátého rozhraní. (Volitelné)  
  
 *příznaky*  
 Konfigurace příznaky pro třídu. Jeden nebo více [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) výčty, které jsou určené v [runtimeclassflags –](../windows/runtimeclassflags-structure.md) struktury.  
  
## <a name="remarks"></a>Poznámky  
 Je odvozen ze seznamu zadaných rozhraní a implementuje šablony pomocné rutiny pro `QueryInterface` a `GetIid`.  
  
 Každý *I0* prostřednictvím *I9* rozhraní parametr musí být odvozen z rozhraní `IUnknown`, `IInspectable`, nebo [chaininterfaces –](../windows/chaininterfaces-structure.md) šablony. *Příznaky* parametr určuje, zda podpory je vygenerován pro `IUnknown` nebo `IInspectable`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`ClassFlags`|Synonymum pro `RuntimeClassFlags<WinRt>`.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Implements::CanCastTo – metoda](../windows/implements-cancastto-method.md)|Získá ukazatel na rozhraní zadané.|  
|[Implements::CastToUnknown – metoda](../windows/implements-casttounknown-method.md)|Získá ukazatel na základní `IUnknown` rozhraní.|  
|[Implements::FillArrayWithIid – metoda](../windows/implements-fillarraywithiid-method.md)|Vloží ID rozhraní určené parametrem aktuální ID nultého šablona do určeného pole elementu.|  
  
### <a name="protected-constants"></a>Chráněné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[Implements::IidCount – konstanta](../windows/implements-iidcount-constant.md)|Obsahuje počet implementovaných rozhraní ID.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `ImplementsBase`  
  
 `ImplementsHelper`  
  
 `Implements`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)