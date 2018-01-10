---
title: "Jaké jsou přínosy vzdálené automatizace? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Remote Automation, DCOM
ms.assetid: 269ad218-e164-40ef-9b87-25fcc8ba21de
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4a82b26a1e6c208a584dfd19ebfd4530b4bdf76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="what-does-remote-automation-provide"></a>Jaké jsou přínosy vzdálené automatizace?
Vzdálená automatizace umožňuje programy k vyvolání `IDispatch` implementace na jednom počítači z jiného. Mimoto podporuje i jiné rozhraní vyžaduje automatizace, konkrétně **IEnumVARIANT** podpora kolekce. Nenabízí možnost distribuovat jiných rozhraní modelu COM (s výjimkou **IUnknown**, samozřejmě) a jako regulární automatizace obsahuje zařazování podporu pouze pro tyto datové typy podporované automatizace.  
  
 Tato sada zařízení umožňuje aplikaci přístup k metody a vlastnosti, včetně těch, které vrací kolekce nebo další objekty automatizace objektu spuštěna na síť přístupnou uzel. Pokud klientský počítač také běží příslušný software, je možné server zpětné volání klienta, znovu s použitím automatizace zařízení (to se dá použít pro 32bitové a 64bitové verze klientů a je koncepčně podobá události, i když nepoužívá shodný mechanismus).  
  
 Pro aplikaci Reliability jako server vzdálené automatizace, musí být implementované jako spustitelný soubor (tedy jako "místní server", spíše než jako "inproc server").  
  
## <a name="see-also"></a>Viz také  
 [Kde se uplatní Vzdálená automatizace?](where-does-remote-automation-fit-in-q.md)   
 [Historie modelu DCOM](../mfc/history-of-dcom.md)
