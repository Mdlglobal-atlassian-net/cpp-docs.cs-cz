---
title: Stránky vlastností knihovny ATL modelu COM projektu | Dokumentace Microsoftu
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
ms.openlocfilehash: 0da9a0299679ec140888e9536329f0957a786279
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760000"
---
# <a name="atl-com-property-pages"></a>ATL COM – stránky vlastností

Com – stránky vlastností nabízí uživatelské rozhraní pro nastavení vlastností (nebo volání metody) z jednoho nebo více objektů COM. Stránky vlastností jsou používány v ovládacích prvcích ActiveX pro poskytování bohatá uživatelská rozhraní, které umožňují vlastností ovládacího prvku na nastavení v době návrhu.

Stránky vlastností jsou objekty COM, které implementují [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) nebo [IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2) rozhraní. Tato rozhraní poskytuje metody, které umožňují stránce přidruženo `site` (objekt modelu COM představující kontejneru stránky) a počet *objekty* (objekty modelu COM zavolá se jejíž metody v reakci na změny provedené uživatelem na stránce vlastností). Kontejner vlastnosti stránky je zodpovědná za volání metod na rozhraní stránky vlastností předat stránce při zobrazení nebo skrytí uživatelského rozhraní a kdy se mají použít změny provedené uživatelem pro příslušné objekty.

Každou stránku vlastností se dají úplně nezávisle na objekty, jejichž vlastnosti můžete nastavit. Stránky vlastností všechno, musí je pochopení konkrétní rozhraní (nebo sadu rozhraní) a nabízí uživatelské rozhraní pro volání metody tohoto rozhraní.

Další informace najdete v tématu [seznamy vlastností a stránky vlastností](/windows/desktop/com/property-sheets-and-property-pages) v sadě Windows SDK.

## <a name="in-this-section"></a>V tomto oddílu

[Zadání stránek vlastností](../atl/specifying-property-pages.md)  
Jsou uvedené kroky pro zadání stránek vlastností pro ovládací prvek je a ukazuje příklad třídy.

[Implementace stránek vlastností](../atl/implementing-property-pages.md)  
Jsou uvedené kroky pro implementaci stránky vlastností, včetně metod k přepsání. Vás provede kompletní příklad podle ATLPages ukázkový program.

## <a name="related-sections"></a>Související oddíly

[Ukázka ATLPages](../visual-cpp-samples.md)  
Abstraktní ukázky pro ukázku ATLPages, který implementuje stránku vlastností pomocí `IPropertyPageImpl`.

[ATL](../atl/active-template-library-atl-concepts.md)  
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovnu Active Template Library.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)

