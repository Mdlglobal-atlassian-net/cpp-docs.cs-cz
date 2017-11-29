---
title: "ATL COM vlastnost stránky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: de062b5c9aedb064206dfc40f7c722a298ded774
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atl-com-property-pages"></a>ATL COM – stránky vlastností
COM – stránky vlastností nabízí uživatelské rozhraní pro nastavení vlastností (nebo volání metody) jeden nebo více objektů COM. Stránky vlastností jsou používány v ovládacích prvcích ActiveX pro zajištění bohaté uživatelské rozhraní, které umožňují vlastností ovládacího prvku na nastavit v době návrhu.  
  
 Stránky vlastností jsou, které implementují objekty COM [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) nebo [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) rozhraní. Tato rozhraní poskytují metody, které umožňují stránky přidružen `site` (objekt COM představující kontejneru stránky) a počet *objekty* (COM – objekty jejichž metody bude volána v reakci na změny provedené uživatelem na stránku vlastností). Stránka kontejneru vlastnost je zodpovědná za volání metod v rozhraní vlastnost stránky říct stránky, pokud chcete zobrazit nebo skrýt jeho uživatelské rozhraní a kdy se mají použít změny provedené uživatelem na základní objekty.  
  
 Každý stránka vlastností se dají vytvářet zcela nezávisle na objekty, jejichž vlastnosti lze nastavit. Stránky vlastností všechno, co vyžaduje je pochopit konkrétní rozhraní (nebo sadu rozhraní) a nabízí uživatelské rozhraní pro volání metody tohoto rozhraní.  
  
 Další informace najdete v tématu [vlastností a stránky vlastností](http://msdn.microsoft.com/library/windows/desktop/ms686577) v [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Určení stránky vlastností](../atl/specifying-property-pages.md)  
 Jsou uvedené kroky pro zadání stránky vlastností pro ovládací prvek je a zobrazí ukázka třídy.  
  
 [Implementace stránky vlastností](../atl/implementing-property-pages.md)  
 Jsou uvedené kroky pro implementaci stránky vlastností, včetně metody k přepsání. Vás provede kompletní příklad podle ATLPages ukázka programu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ukázka ATLPages](../visual-cpp-samples.md)  
 Ukázka abstraktní pro ATLPages ukázku, která implementuje pomocí stránky vlastností `IPropertyPageImpl`.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Obsahuje odkazy na koncepční témata o tom, jak program pomocí knihovny Active šablony.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)
