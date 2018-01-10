---
title: Implementuje strukturu | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Implements
dev_langs: C++
helpviewer_keywords: Implements structure
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63da9ea650c34b7b1ed75d351587c39e52a88098
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="implements-structure"></a>Implementuje strukturu
Implementuje QueryInterface a GetIid pro zadaná rozhraní.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 ID zeroth rozhraní. (Povinné)  
  
 `I1`  
 První rozhraní ID. (Volitelné)  
  
 `I2`  
 Druhý ID rozhraní. (Volitelné)  
  
 `I3`  
 Třetí ID rozhraní. (Volitelné)  
  
 `I4`  
 Čtvrtý ID rozhraní. (Volitelné)  
  
 `I5`  
 Páté ID rozhraní. (Volitelné)  
  
 `I6`  
 Šesté ID rozhraní. (Volitelné)  
  
 `I7`  
 Sedmého ID rozhraní. (Volitelné)  
  
 `I8`  
 ID nakrmeni rozhraní. (Volitelné)  
  
 `I9`  
 Deváté ID rozhraní. (Volitelné)  
  
 `flags`  
 Konfigurace příznaky pro třídu. Jeden nebo více [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) výčty, které jsou určené v [runtimeclassflags –](../windows/runtimeclassflags-structure.md) struktura.  
  
## <a name="remarks"></a>Poznámky  
 Je odvozena ze seznamu zadaný rozhraní a implementuje šablony pomocné rutiny pro QueryInterface a GetIid.  
  
 Každý `I0` prostřednictvím `I9` rozhraní parametr musí být odvozeny od buď IUnknown IInspectable, nebo [chaininterfaces –](../windows/chaininterfaces-structure.md) šablony. `flags` Parametr určuje, zda je podpora vygenerované IUnknown nebo IInspectable.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`ClassFlags`|Synonymum pro `RuntimeClassFlags<WinRt>`.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Implements::CanCastTo – metoda](../windows/implements-cancastto-method.md)|Získá ukazatele k zadanému rozhraní.|  
|[Implements::CastToUnknown – metoda](../windows/implements-casttounknown-method.md)|Získá ukazatel na základní rozhraní IUnknown.|  
|[Implements::FillArrayWithIid – metoda](../windows/implements-fillarraywithiid-method.md)|Vloží zadané parametrem aktuální šablony zeroth do elementu zadané pole ID rozhraní.|  
  
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