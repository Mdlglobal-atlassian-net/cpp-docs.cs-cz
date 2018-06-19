---
title: Pomocí IDispEventImpl (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 520d1129234a26ff6eb4c402154969ad7e166211
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361148"
---
# <a name="using-idispeventimpl"></a>Pomocí IDispEventImpl
Při použití `IDispEventImpl` ke zpracování událostí, budete muset:  
  
-   Odvození třídě z [IDispEventImpl](../atl/reference/idispeventimpl-class.md).  
  
-   Přidáte mapu jímky událostí na třídu.  
  
-   Přidání položky do mapy jímek událostí pomocí [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) nebo [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) makro.  
  
-   Implementace metody, co vás zajímá zpracování.  
  
-   Poradit a unadvise zdroj události.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob zpracování **DocumentChange** událost je aktivována po slovech na **aplikace** objektu. Tato událost je definována jako metodu na **ApplicationEvents** dispinterface.  
  
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
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]  
  
 Zobrazí se následující kód v NotSoSimple.h. Odpovídající kód je uvedeno ve komentáře:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]  
  
## <a name="see-also"></a>Viz také  
 [Zpracování událostí](../atl/event-handling-and-atl.md)   
 [Ukázka ATLEventHandling](../visual-cpp-samples.md)

