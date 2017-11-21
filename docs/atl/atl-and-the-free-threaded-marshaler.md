---
title: "ATL a volné zařazování vláken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ed5660be9a5559d5f51d0cdb0ec2e5bc185bd0b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL a volné zařazování vláken
ATL jednoduchý objekt atributy stránce Průvodce poskytuje možnost, která umožňuje třídě k agregaci volné zařazování vláken (FTM).  
  
 Průvodce generuje kód pro vytvoření instance volné zařazování vláken v `FinalConstruct` a verzí v dané instance `FinalRelease`. A `COM_INTERFACE_ENTRY_AGGREGATE` makro se automaticky přidá do mapy COM zajistit, aby `QueryInterface` požadavky [imarshal –](http://msdn.microsoft.com/library/windows/desktop/dd542707) jsou zpracovávány volné zařazování vláken.  
  
 Volné zařazování vláken umožňuje přímý přístup rozhraní na objektu z libovolného vlákna v rámci jednoho procesu urychlení mezi apartment volání. Tato možnost je určena pro třídy, které používají oba model vláken.  
  
 Při použití této možnosti musí třídy převzít odpovědnost za vláken svá data. Objekty, které agregace volné zařazování vláken a potřebují používat ukazatele rozhraní získat z jiných objektů navíc musejí udělat dodatečné kroky k zajištění, že jsou správně zařazeno rozhraní. Obvykle to zahrnuje ukládání ukazatele rozhraní v tabulce globální rozhraní (GIT) a získávání ukazatele z GITU pokaždé, když se používá. Poskytuje třídy ATL [CComGITPtr](../atl/reference/ccomgitptr-class.md) vám pomohou používat ukazatele rozhraní, které jsou uložené v GITU.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [Imarshal –](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [Kdy použít tabulku globální rozhraní](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Proces serveru problémy dělení na vlákna](http://msdn.microsoft.com/library/windows/desktop/ms687205)

