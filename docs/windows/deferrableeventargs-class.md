---
title: Deferrableeventargs – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 72f5ee2beca3a3985258b12cea9091665eb74cfa
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571259"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs – třída
Třída šablony použité pro typy argumentů událostí pro odložení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
```  
  
#### <a name="parameters"></a>Parametry  
 *TEventArgsInterface*  
 Typ rozhraní, který deklaruje argumenty pro odložené událost.  
  
 *TEventArgsClass*  
 Třída, která implementuje *TEventArgsInterface*.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[DeferrableEventArgs::GetDeferral – metoda](../windows/deferrableeventargs-getdeferral-method.md)|Získá odkaz na [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objekt, který představuje odložené událost.|  
|[DeferrableEventArgs::InvokeAllFinished – metoda](../windows/deferrableeventargs-invokeallfinished-method.md)|Volá se, že je veškeré zpracování zpracování odložené události dokončení.|  
  
## <a name="remarks"></a>Poznámky  
 Instance této třídy jsou předány do obslužné rutiny událostí pro odložené události. Parametry šablony představují rozhraní, které definuje podrobnosti argumenty událostí pro konkrétní typ odloženého události a třídu, která implementuje rozhraní.  
  
 Třída se zobrazí jako první argument pro obslužnou rutinu události pro odložené událost. Můžete volat [GetDeferral](../windows/deferrableeventargs-getdeferral-method.md) metodu k získání [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objektu, ze kterého můžete získat všechny informace o odložených události. Po dokončení zpracování událostí, měli byste zavolat Complete odložení objektu. Potom byste měli volat [InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md) na konci metody obslužné rutiny události, které zajišťuje, že je správně adrese dokončení všech odložené události.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)