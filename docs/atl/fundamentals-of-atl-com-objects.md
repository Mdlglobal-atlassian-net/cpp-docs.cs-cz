---
title: Základy ATL COM – objekty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 955f8f6be96feeaf0f22f02c125dcdeaceb8e7f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358287"
---
# <a name="fundamentals-of-atl-com-objects"></a>Základy ATL COM – objekty
Následující obrázek znázorňuje vztahy mezi třídy a rozhraní, které definují objekt ATL COM.  
  
 ![Struktura ATL](../atl/media/vc307y1.gif "vc307y1")  
  
> [!NOTE]
>  Tento diagram ukazuje, že `CComObject` je odvozený od `CYourClass` zatímco `CComAggObject` a `CComPolyObject` zahrnují `CYourClass` jako členské proměnné.  
  
 Existují tři způsoby, jak definovat objekt ATL COM. Standardní možností je používat `CComObject` třídy odvozené z `CYourClass`. Druhou možností je vytvořit agregovaný objekt pomocí `CComAggObject` třídy. Třetí možností je používat `CComPolyObject` třídy. `CComPolyObject` funguje jako hybrid: může fungovat jako `CComObject` třídy nebo jako `CComAggObject` třídy, v závislosti na tom, jak je prvním vytvoření. Další informace o tom, jak používat `CComPolyObject` třídy najdete v tématu [CComPolyObject třída](../atl/reference/ccompolyobject-class.md).  
  
 Při použití standardní ATL COM, můžete použít dva objekty: objekt vnější a vnitřní objekt. Externí klienti přistupovat k funkcím vnitřní objekt prostřednictvím funkce obálky, které jsou definovány v vnější objektu. Vnější objekt je typu `CComObject`.  
  
 Při použití agregovaný objekt neposkytuje vnější objekt obálky pro funkci vnitřní objekt. Místo toho objekt vnější poskytuje ukazatele, který je přímo přistupovat externí klienti. V tomto scénáři vnější objekt je typu `CComAggObject`. Vnitřní objekt je členské proměnné vnější objektu, a je typu `CYourClass`.  
  
 Vzhledem k tomu, že klient nebude muset projít vnější objekt, který chcete pracovat s vnitřní objekt, agregované objekty jsou obvykle je efektivnější. Navíc vnější objekt nemá vědět funkce agregovaný objekt, vzhledem k tomu, že rozhraní agregovaného objektu je přímo dostupných pro klienta. Ne všechny objekty však můžete agregovat. Pro objekt mají agregovat musí se měly navrhovat s agregace v paměti.  
  
 Implementuje ATL [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) ve dvou fázích:  
  
-   [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), nebo [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje **IUnknown** metody.  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) spravuje počet odkazů a vnější ukazatele tohoto **IUnknown**.  
  
 Další aspekty vašeho ATL COM objektu jsou zpracovávány jiné třídy:  
  
-   [CComCoClass](../atl/reference/ccomcoclass-class.md) definuje model objektu výchozí třídy objektu pro vytváření a agregaci.  
  
-   [IDispatchImpl](../atl/reference/idispatchimpl-class.md) poskytuje výchozí implementaci třídy `IDispatch Interface` část žádné duální rozhraní pro objekt.  
  
-   [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementuje **ISupportErrorInfo** rozhraní, které zajišťuje, aby informace o chybě můžete rozšířit řetězem volání správně.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Implementace CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)  
 Zobrazit příklad položek mapování COM pro implementaci `CComObjectRootEx`.  
  
 [Implementace CComObject, CComAggObject a CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)  
 Popisuje, jak **DECLARE_\*_AGGREGATABLE** makra mají vliv na použití `CComObject`, `CComAggObject`, a `CComPolyObject`.  
  
 [Podpora IDispatch a IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)  
 Uvádí implementace třídy ATL používat pro podporu `IDispatch` a **IErrorInfo** rozhraní.  
  
 [Podpora IDispEventImpl](../atl/supporting-idispeventimpl.md)  
 Popisuje kroky pro implementaci bod připojení pro třídu.  
  
 [Změna výchozího objektu pro vytváření tříd a agregačního modelu](../atl/changing-the-default-class-factory-and-aggregation-model.md)  
 Zobrazit, jaké makra sloužící k změňte model třída výchozí tovární nastavení a agregace.  
  
 [Vytvoření agregovaného objektu](../atl/creating-an-aggregated-object.md)  
 Jsou uvedené kroky pro vytvoření agregovaného objektu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vytvoření projektu ATL](../atl/reference/creating-an-atl-project.md)  
 Poskytuje informace o vytvoření objektu ATL COM.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Obsahuje odkazy na koncepční témata o tom, jak program pomocí knihovny Active šablony.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)

