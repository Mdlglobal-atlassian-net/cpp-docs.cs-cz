---
title: EventSource::getsize – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::GetSize
dev_langs:
- C++
helpviewer_keywords:
- GetSize method
ms.assetid: 7825aab5-1a6b-465f-9159-3a6684142d1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 60c52c711c85caa64c289937f39fe50ec18e1839
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="eventsourcegetsize-method"></a>EventSource::GetSize – metoda
Načte číslo přidružené k aktuálnímu objektu EventSource obslužné rutiny událostí  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t GetSize() const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet obslužných rutin událostí v [targets_ –](../windows/eventsource-targets-data-member.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [EventSource – třída](../windows/eventsource-class.md)