---
title: ATL COM – stránky vlastností
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
ms.openlocfilehash: d374569c6c3e9bb63b6b026d2b0f86226d158f36
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768406"
---
# <a name="atl-com-property-pages"></a>ATL COM – stránky vlastností

Com – stránky vlastností nabízí uživatelské rozhraní pro nastavení vlastností (nebo volání metody) z jednoho nebo více objektů COM. Stránky vlastností jsou používány v ovládacích prvcích ActiveX pro poskytování bohatá uživatelská rozhraní, které umožňují vlastností ovládacího prvku na nastavení v době návrhu.

Stránky vlastností jsou objekty COM, které implementují [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) nebo [IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2) rozhraní. Tato rozhraní poskytuje metody, které umožňují stránce přidruženo `site` (objekt modelu COM představující kontejneru stránky) a počet *objekty* (objekty modelu COM zavolá se jejíž metody v reakci na změny provedené uživatelem na stránce vlastností). Kontejner vlastnosti stránky je zodpovědná za volání metod na rozhraní stránky vlastností předat stránce při zobrazení nebo skrytí uživatelského rozhraní a kdy se mají použít změny provedené uživatelem pro příslušné objekty.

Každou stránku vlastností se dají úplně nezávisle na objekty, jejichž vlastnosti můžete nastavit. Stránky vlastností všechno, musí je pochopení konkrétní rozhraní (nebo sadu rozhraní) a nabízí uživatelské rozhraní pro volání metody tohoto rozhraní.

Další informace najdete v tématu [seznamy vlastností a stránky vlastností](/windows/desktop/com/property-sheets-and-property-pages) v sadě Windows SDK.

## <a name="in-this-section"></a>V tomto oddílu

[Zadání stránek vlastností](../atl/specifying-property-pages.md)<br/>
Jsou uvedené kroky pro zadání stránek vlastností pro ovládací prvek je a ukazuje příklad třídy.

[Implementace stránek vlastností](../atl/implementing-property-pages.md)<br/>
Jsou uvedené kroky pro implementaci stránky vlastností, včetně metod k přepsání. Vás provede kompletní příklad podle ATLPages ukázkový program.

## <a name="related-sections"></a>Související oddíly

[Ukázka ATLPages](../overview/visual-cpp-samples.md)<br/>
Abstraktní ukázky pro ukázku ATLPages, který implementuje stránku vlastností pomocí `IPropertyPageImpl`.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovnu Active Template Library.

## <a name="see-also"></a>Viz také:

[Koncepty](../atl/active-template-library-atl-concepts.md)
