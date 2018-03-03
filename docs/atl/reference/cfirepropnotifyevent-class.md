---
title: "Třída CFirePropNotifyEvent | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
dev_langs:
- C++
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c9571ad4ba928c208c6c028f6e30cf7c27c196d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent – třída
Tato třída poskytuje metody pro oznamování kontejneru podřízený týkající se změny vlastností ovládacího prvku.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statické) Upozorní kontejneru podřízený, které se změnily vlastnosti ovládacího prvku.|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Statické) Upozorní podřízený kontejneru, který vlastnost ovládacího prvku se má změnit.|  
  
## <a name="remarks"></a>Poznámky  
 `CFirePropNotifyEvent`má dvě metody, které oznámit podřízený kontejneru, který vlastnost ovládacího prvku došlo ke změně nebo se chystáte se změnit.  
  
 Pokud třída implementace vlastního ovládacího prvku je odvozený od `IPropertyNotifySink`, `CFirePropNotifyEvent` metody jsou vyvolány při volání `FireOnRequestEdit` nebo `FireOnChanged`. Pokud vaše třída ovládacích prvků není odvozen od `IPropertyNotifySink`, vrátí volání na tyto funkce `S_OK`.  
  
 Další informace o vytváření ovládacích prvků, najdete v článku [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged  
 Oznámí všechny připojené [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní (na každý spojovací bod objektu), která se změnila vlastnost zadaný objekt.  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [v] Ukazatel **IUnknown** objektu odesílání oznámení.  
  
 *dispID*  
 [v] Identifikátor vlastnosti, která se změnila.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je bezpečné volat i v případě, že vaše ovládací prvek nepodporuje spojovací body.  
  
##  <a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit  
 Oznámí všechny připojené [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní (na každý spojovací bod objektu), která vlastnost zadaný objekt je Chystáte se změnit.  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [v] Ukazatel **IUnknown** objektu odesílání oznámení.  
  
 *dispID*  
 [v] Identifikátor vlastnosti Chystáte se změnit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je bezpečné volat i v případě, že vaše ovládací prvek nepodporuje spojovací body.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
