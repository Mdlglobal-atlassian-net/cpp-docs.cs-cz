---
title: "Chaininterfaces – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces
dev_langs: C++
helpviewer_keywords: ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d48aac7e14092c8406db28910263e7048c17bee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces – struktura
Určuje ověření a Inicializace funkce, které mohou být použity pro sadu rozhraní ID.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I0,  
   typename I1,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct ChainInterfaces : I0;  
template <  
   typename DerivedType,  
   typename BaseType,  
   bool hasImplements,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8,  
   typename I9  
>  
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 (Povinné) Rozhraní ID 0.  
  
 `I1`  
 (Povinné) Rozhraní s ID 1.  
  
 `I2`  
 (Volitelné) ID rozhraní 2.  
  
 `I3`  
 (Volitelné) ID rozhraní 3.  
  
 `I4`  
 (Volitelné) ID rozhraní 4.  
  
 `I5`  
 (Volitelné) ID rozhraní 5.  
  
 `I6`  
 (Volitelné) ID rozhraní 6.  
  
 `I7`  
 (Volitelné) Rozhraní ID 7.  
  
 `I8`  
 (Volitelné) ID rozhraní 8.  
  
 `I9`  
 (Volitelné) ID rozhraní 9.  
  
 `DerivedType`  
 Odvozený typ.  
  
 `BaseType`  
 Základní typ odvozeného typu.  
  
 `hasImplements`  
 Logická hodnota. hodnota, že pokud `true`, znamená nelze použít [MixIn](../windows/mixin-structure.md) struktura s třídu, která není odvozena od [implementuje](../windows/implements-structure.md) stucture.  
  
## <a name="members"></a>Členové  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Chaininterfaces::cancastto – metoda](../windows/chaininterfaces-cancastto-method.md)|Určuje, zda zadaný rozhraní ID lze převést na každý specializací definované ChainInterface parametry šablony.|  
|[Chaininterfaces::casttounknown – metoda](../windows/chaininterfaces-casttounknown-method.md)|Ukazatel rozhraní typu definované vrhá `I0` parametr šablony na ukazatel IUnknown.|  
|[Chaininterfaces::fillarraywithiid – metoda](../windows/chaininterfaces-fillarraywithiid-method.md)|Ukládá ID rozhraní definované `I0` parametr šablony do zadaného umístění v zadané pole rozhraní ID.|  
|[Chaininterfaces::Verify – metoda](../windows/chaininterfaces-verify-method.md)|Ověřuje, že každé rozhraní definované parametry šablony `I0` prostřednictvím `I9` dědí z IUnknown nebo IInspectable a že `I0` dědí z `I1` prostřednictvím `I9`.|  
  
### <a name="protected-constants"></a>Chráněné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[Chaininterfaces::iidcount – konstanta](../windows/chaininterfaces-iidcount-constant.md)|Celkový počet rozhraní ID obsažené v rozhraní určeného parametry šablony `I0` prostřednictvím `I9`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `I0`  
  
 `ChainInterfaces`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)