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
ms.openlocfilehash: f6f549388e69e9549c64645de758d92822205fd5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491861"
---
# <a name="atl-com-property-pages"></a>ATL COM – stránky vlastností

Stránky vlastností COM poskytují uživatelské rozhraní pro nastavení vlastností (nebo volání metod) jednoho nebo více objektů COM. Stránky vlastností jsou často používány ovládacími prvky ActiveX pro poskytování bohatých uživatelských rozhraní, která umožňují nastavit vlastnosti ovládacího prvku v době návrhu.

Stránky vlastností jsou objekty COM, které implementují rozhraní [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) nebo [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) . Tato rozhraní poskytují metody, které umožňují, aby stránka byla přidružena `site` k (objekt com představující kontejner stránky) a kolik *objektů* (objekty COM, jejichž metody budou volány v reakci na změny provedené uživatelem Stránka vlastností). Kontejner stránky vlastností je zodpovědný za volání metod v rozhraní stránky vlastností, který informuje stránku, kdy má zobrazit nebo skrýt své uživatelské rozhraní a kdy použít změny provedené uživatelem na podkladové objekty.

Jednotlivé stránky vlastností lze zcela sestavit nezávisle na objektech, jejichž vlastnosti lze nastavit. Vše, co stránka vlastností potřebuje, je pochopit konkrétní rozhraní (nebo sadu rozhraní) a poskytnout uživatelské rozhraní pro volání metod na daném rozhraní.

Další informace najdete v tématu [seznamy vlastností a stránky vlastností](/windows/win32/com/property-sheets-and-property-pages) v Windows SDK.

## <a name="in-this-section"></a>V tomto oddílu

[Zadání stránek vlastností](../atl/specifying-property-pages.md)<br/>
Seznam kroků pro zadání stránek vlastností pro ovládací prvek a ukazuje ukázkovou třídu.

[Implementace stránek vlastností](../atl/implementing-property-pages.md)<br/>
Obsahuje seznam kroků pro implementaci stránek vlastností, včetně metod k přepsání. Provede vás kompletním příkladem na základě ukázkového programu ATLPages.

## <a name="related-sections"></a>Související oddíly

[Ukázka ATLPages](../overview/visual-cpp-samples.md)<br/>
Ukázka abstrakce pro ukázku ATLPages, která implementuje stránku vlastností pomocí `IPropertyPageImpl`.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovny Active Template Library.

## <a name="see-also"></a>Viz také:

[Charakteristiky](../atl/active-template-library-atl-concepts.md)
