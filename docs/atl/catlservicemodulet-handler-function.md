---
title: Funkce CAtlServiceModuleT::Handler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
dev_langs:
- C++
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00158bbed5318d919c284b91cd651141a35bd441
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemodulethandler-function"></a>CAtlServiceModuleT::Handler – funkce
`CAtlServiceModuleT::Handler`je rutina, která volá správce řízení služeb (SCM) pro načtení stav služby a pojmenujte ho různé pokyny (například zastavení nebo pozastavení). SCM předá kód operace na `Handler` označující, co má provést službu. Výchozí generovaný ATL služba zpracovává jenom pokyn zastavit. Pokud správce SCM úspěšně projde zastavení pokyn, službu informuje správce SCM, program se chystá ukončit. Pak zavolá službu `PostThreadMessage` ukončete zprávu na sebe sama. To ukončí smyčce zpráv a služby se nakonec zavřete.  
  
 Pro zpracování další pokyny, budete muset změnit `m_status` – datový člen v inicializovat `CAtlServiceModuleT` konstruktor. Tento člen data informuje správce SCM tlačítek, která se povolit, pokud služba je vybraný v ovládacím panelu služby aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)   
 [CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)

