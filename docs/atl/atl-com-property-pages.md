---
title: ATL COM vlastnost stránky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5d7904b9f31a1be858dadaa8a087c720c277465
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="atl-com-property-pages"></a>ATL COM – stránky vlastností
COM – stránky vlastností nabízí uživatelské rozhraní pro nastavení vlastností (nebo volání metody) jeden nebo více objektů COM. Stránky vlastností jsou používány v ovládacích prvcích ActiveX pro zajištění bohaté uživatelské rozhraní, které umožňují vlastností ovládacího prvku na nastavit v době návrhu.  
  
 Stránky vlastností jsou, které implementují objekty COM [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) nebo [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) rozhraní. Tato rozhraní poskytují metody, které umožňují stránky přidružen `site` (objekt COM představující kontejneru stránky) a počet *objekty* (COM – objekty jejichž metody bude volána v reakci na změny provedené uživatelem na stránku vlastností). Stránka kontejneru vlastnost je zodpovědná za volání metod v rozhraní vlastnost stránky říct stránky, pokud chcete zobrazit nebo skrýt jeho uživatelské rozhraní a kdy se mají použít změny provedené uživatelem na základní objekty.  
  
 Každý stránka vlastností se dají vytvářet zcela nezávisle na objekty, jejichž vlastnosti lze nastavit. Stránky vlastností všechno, co vyžaduje je pochopit konkrétní rozhraní (nebo sadu rozhraní) a nabízí uživatelské rozhraní pro volání metody tohoto rozhraní.  
  
 Další informace najdete v tématu [vlastností a stránky vlastností](http://msdn.microsoft.com/library/windows/desktop/ms686577) v [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zadání stránek vlastností](../atl/specifying-property-pages.md)  
 Jsou uvedené kroky pro zadání stránky vlastností pro ovládací prvek je a zobrazí ukázka třídy.  
  
 [Implementace stránek vlastností](../atl/implementing-property-pages.md)  
 Jsou uvedené kroky pro implementaci stránky vlastností, včetně metody k přepsání. Vás provede kompletní příklad podle ATLPages ukázka programu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ukázka ATLPages](../visual-cpp-samples.md)  
 Ukázka abstraktní pro ATLPages ukázku, která implementuje pomocí stránky vlastností `IPropertyPageImpl`.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Obsahuje odkazy na koncepční témata o tom, jak program pomocí knihovny Active šablony.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)

