---
title: Základy ATL – objekty COM | Dokumentace Microsoftu
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
ms.openlocfilehash: 7873b7006962449a40a8e67d118b6699ac61f263
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762090"
---
# <a name="fundamentals-of-atl-com-objects"></a>Základy ATL – objekty COM

Následující ilustrace znázorňuje vztah mezi třídy a rozhraní, které se používají k definování objekt knihovny ATL modelu COM.

![Struktura knihovny ATL](../atl/media/vc307y1.gif "vc307y1")

> [!NOTE]
>  Tento diagram znázorňuje, že `CComObject` je odvozen z `CYourClass` vzhledem k tomu `CComAggObject` a `CComPolyObject` zahrnují `CYourClass` jako členské proměnné.

Existují tři způsoby, jak definovat objekt knihovny ATL modelu COM. Standardní možností je použít `CComObject` třídy, které je odvozeno z `CYourClass`. Druhou možností je vytvoření agregovaného objektu pomocí `CComAggObject` třídy. Třetí možností je použít `CComPolyObject` třídy. `CComPolyObject` funguje jako hybrid: může fungovat jako `CComObject` třídy nebo jako `CComAggObject` třídy, v závislosti na tom, jak se nejprve vytvoří. Další informace o tom, jak používat `CComPolyObject` najdete v tématu [CComPolyObject – třída](../atl/reference/ccompolyobject-class.md).

Při použití standardní knihovny ATL modelu COM použít dva objekty: objekt vnější a vnitřní objekt. Externí klienti přístup k funkci vnitřní objekt pomocí funkce obálky, které jsou definovány v vnějšího objektu. Vnější objekt je typu `CComObject`.

Při použití agregovaného objektu neposkytuje vnějšího objektu obálky pro funkci vnitřní objekt. Místo toho vnějšího objektu poskytuje ukazatel, který je přímo přistupovat externí klienti. V tomto scénáři vnější objekt je typu `CComAggObject`. Vnitřní objekt je členskou proměnnou z vnějšího objektu a má typ `CYourClass`.

Vzhledem k tomu, že klient nebude muset projít vnějšího objektu k interakci s vnitřní objekt, jsou agregovaných objektů obvykle efektivnější. Navíc vnějšího objektu nemá znát funkce agregovaného objektu, vzhledem k tomu, že rozhraní agregovaného objektu je přímo do klienta k dispozici. Ne všechny objekty se ale dají agregovat. Pro objekt agregace je potřeba navrhovat pomocí agregace v úvahu.

ATL – implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) ve dvou fázích:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), nebo [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje `IUnknown` metody.

- [Ccomobjectroot –](../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) spravuje počet odkazů a vnější ukazatele na `IUnknown`.

Další aspekty objekt knihovny ATL modelu COM jsou zpracovávány jiné třídy:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) definuje model objektu pro vytváření a agregace výchozí třídy objektu.

- [Idispatchimpl –](../atl/reference/idispatchimpl-class.md) poskytuje výchozí implementaci třídy `IDispatch Interface` část jakékoli duální rozhraní objektu.

- [Isupporterrorinfoimpl –](../atl/reference/isupporterrorinfoimpl-class.md) implementuje `ISupportErrorInfo` rozhraní, které zajišťuje informace o chybě můžete rozšířit řetězem volání správně.

## <a name="in-this-section"></a>V tomto oddílu

[Implementace CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)  
Zobrazit příklad položky mapy modelu COM pro implementaci `CComObjectRootEx`.

[Implementace CComObject, CComAggObject a CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)  
Popisuje, jak **DECLARE_\*_AGGREGATABLE** makra mají vliv na použití `CComObject`, `CComAggObject`, a `CComPolyObject`.

[Podpora IDispatch a IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)  
Obsahuje seznam ATL – implementace třídy pro podporu `IDispatch` a `IErrorInfo` rozhraní.

[Podpora IDispEventImpl](../atl/supporting-idispeventimpl.md)  
Tento článek popisuje kroky pro implementaci bod připojení pro vaši třídu.

[Změna výchozího objektu pro vytváření tříd a agregačního modelu](../atl/changing-the-default-class-factory-and-aggregation-model.md)  
Zobrazit jaké makra použít ke změně třídy výchozí model objektu pro vytváření a agregace.

[Vytvoření agregovaného objektu](../atl/creating-an-aggregated-object.md)  
Seznam kroků pro vytvoření agregovaného objektu.

## <a name="related-sections"></a>Související oddíly

[Vytvoření projektu ATL](../atl/reference/creating-an-atl-project.md)  
Poskytuje informace o vytvoření objektu ATL COM.

[ATL](../atl/active-template-library-atl-concepts.md)  
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovnu Active Template Library.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)

