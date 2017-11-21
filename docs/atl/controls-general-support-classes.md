---
title: "ATL ovládacích prvků: Třídy pro podporu obecné | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.controls
dev_langs: C++
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5d969481874762c5eefeb805d954ffad6114033e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="controls-general-support-classes"></a>Prvky: Třídy pro podporu obecné
Následující třídy poskytují obecné podporu pro ovládací prvky knihovny ATL:  
  
-   [CComControl](../atl/reference/ccomcontrol-class.md) se skládá z pomocné funkce a data členů, které jsou nezbytné k ovládacím prvkům ATL.  
  
-   [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) poskytuje metody, které jsou nezbytné pro ovládací prvky.  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) poskytuje hlavní metody, pomocí kterých kontejner komunikuje s ovládacím prvkem. Spravuje aktivace a deaktivace ovládacích prvků na místě.  
  
-   [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) kombinuje inicializace do jednoho volání pomohou kontejnery vyhnout zpoždění při načítání ovládacích prvků.  
  
-   [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) poskytuje interakce s myší minimální pro ovládací prvek jinak neaktivní.  
  
## <a name="sample-program"></a>Ukázkový Program  
 [ATLFire](../visual-cpp-samples.md)  
  
## <a name="related-articles"></a>Související články  
 [ATL – tutoriál](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../atl/atl-class-overview.md)

