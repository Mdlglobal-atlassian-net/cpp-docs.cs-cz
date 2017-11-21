---
title: "DeferrableEventArgs – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27107c794dfd4987eb0519dfeaa9762f47d0417c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs – třída
Třída Šablona používaná pro typy argumentů událostí pro rozlišených položek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `TEventArgsInterface`  
 Typ rozhraní, který deklaruje argumenty pro odložené událost.  
  
 `TEventArgsClass`  
 Třídu, která implementuje `TEventArgsInterface`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Deferrableeventargs::getdeferral – metoda](../windows/deferrableeventargs-getdeferral-method.md)|Získá odkaz na [odložení](http://go.microsoft.com/fwlink/?LinkId=526520) objekt, který reprezentuje odložené události.|  
|[Deferrableeventargs::invokeallfinished – metoda](../windows/deferrableeventargs-invokeallfinished-method.md)|Voláno k označení, že veškeré zpracování zpracování odložené události je kompletní.|  
  
## <a name="remarks"></a>Poznámky  
 Instance této třídy jsou předány obslužných rutin událostí pro odložené události. Parametry šablony představují rozhraní, které definuje podrobnosti o argumenty událostí pro konkrétní typ odložené události a třídu, která implementuje rozhraní.  
  
 Třída zobrazí jako první argument obslužné rutiny události pro odložené událost. Můžete volat [GetDeferral](../windows/deferrableeventargs-getdeferral-method.md) metoda získat [odložení](http://go.microsoft.com/fwlink/?LinkId=526520) objekt, ze kterého můžete získat všechny informace o odložených událostí. Po dokončení zpracování událostí, by měly volat Complete odložení objektu. Potom by měly volat [InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md) na konci obslužná rutina události, což zajistí, že je správně adrese dokončení všech odložených události.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)