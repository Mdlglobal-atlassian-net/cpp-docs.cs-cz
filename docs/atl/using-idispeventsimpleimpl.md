---
title: Pomocí IDispEventSimpleImpl (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed21c862d61686e86efd684a6e88795e4b7bbe51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-idispeventsimpleimpl"></a>Pomocí IDispEventSimpleImpl
Při použití `IDispEventSimpleImpl` ke zpracování událostí, budete muset:  
  
-   Odvození třídě z [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).  
  
-   Přidáte mapu jímky událostí na třídu.  
  
-   Definování [_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) struktury popisující události.  
  
-   Přidání položky do mapy jímek událostí pomocí [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) makro.  
  
-   Implementace metody, co vás zajímá zpracování.  
  
-   Poradit a unadvise zdroj události.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak bude zpracováván **DocumentChange** událost je aktivována po slovech na **aplikace** objektu. Tato událost je definována jako metodu na **ApplicationEvents** dispinterface.  
  
 Příkladem je z [ATLEventHandling ukázka](../visual-cpp-samples.md).  
  
 `[`  
  
 `uuid(000209F7-0000-0000-C000-000000000046),`  
  
 `hidden`  
  
 `]`  
  
 `dispinterface ApplicationEvents {`  
  
 `properties:`  
  
 `methods:`  
  
 `[id(0x00000001), restricted, hidden]`  
  
 `void Startup();`  
  
 `[id(0x00000002)]`  
  
 `void Quit();`  
  
 `[id(0x00000003)]`  
  
 `void DocumentChange();`  
  
 `};`  
  
 Tento příklad používá `#import` generovat požadovaná hlavička soubory z knihovny typů pro Word. Pokud chcete použít tento příklad s jinými verzemi aplikace Word, musíte zadat správný mso soubor knihovny dll. Například Office 2000 poskytuje mso9.dll a OfficeXP poskytuje mso.dll. Tento kód je zjednodušený z stdafx.h:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]  
  
 Veškeré informace z knihovny typů ve skutečnosti použité v tomto příkladu je CLSID aplikace Word **aplikace** objekt a identifikátory IID **ApplicationEvents** rozhraní. Tyto informace se používá pouze v době kompilace.  
  
 Zobrazí se následující kód v Simple.h. Odpovídající kód je uvedeno ve komentáře:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]  
  
 Následující kód je z Simple.cpp:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Zpracování událostí](../atl/event-handling-and-atl.md)   
 [Ukázka ATLEventHandling](../visual-cpp-samples.md)

