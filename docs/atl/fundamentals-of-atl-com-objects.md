---
title: Základy objektů ATL COM
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: ec83539b2d7101c534bbc1df33577df422e76152
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492371"
---
# <a name="fundamentals-of-atl-com-objects"></a>Základy objektů ATL COM

Následující ilustrace znázorňuje vztah mezi třídami a rozhraními, které se používají k definování objektu ATL modelu COM.

![ATL – struktura](../atl/media/vc307y1.gif "ATL – struktura")

> [!NOTE]
>  Tento diagram ukazuje, `CComObject` že je odvozen `CYourClass` `CComAggObject` z daného `CComPolyObject` a `CYourClass` zahrnutí jako členské proměnné.

Existují tři způsoby, jak definovat objekt modelu COM ATL. Standardní možnost je použít `CComObject` třídu, která je odvozena z. `CYourClass` Druhou možností je vytvořit agregovaný objekt pomocí `CComAggObject` třídy. Třetí možností je použít `CComPolyObject` třídu. `CComPolyObject`funguje jako hybridní: může fungovat jako `CComObject` třída nebo `CComAggObject` jako třída, v závislosti na tom, jak je poprvé vytvořen. Další informace o použití `CComPolyObject` třídy naleznete v tématu [Třída CComPolyObject](../atl/reference/ccompolyobject-class.md).

Použijete-li standardní ATL COM, použijete dva objekty: vnější objekt a vnitřní objekt. Externí klienti přistupují k funkcím vnitřního objektu prostřednictvím funkcí obálky, které jsou definovány v vnějším objektu. Vnější objekt je typu `CComObject`.

Použijete-li agregovaný objekt, vnější objekt neposkytuje obálky pro fungování vnitřního objektu. Místo toho vnější objekt poskytuje ukazatel, ke kterému má přímý pøístup externí klienti. V tomto scénáři je vnější objekt typu `CComAggObject`. Vnitřní objekt je členskou proměnnou vnějšího objektu a je typu `CYourClass`.

Vzhledem k tomu, že klient nemusí projít vnějším objektem pro interakci s vnitřním objektem, jsou agregované objekty obvykle efektivnější. Kromě toho vnější objekt nemusí znát funkčnost agregovaného objektu vzhledem k tom, že rozhraní agregovaného objektu je přímo k dispozici klientovi. Ne všechny objekty ale mohou být agregovány. Pro objekt, který se má agregovat, musí být navržený s ohledem na agregaci.

ATL implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ve dvou fázích:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)nebo [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje `IUnknown` metody.

- [Třídy CComObjectRoot](../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) spravuje počet odkazů a vnější `IUnknown`ukazatele.

Další aspekty objektu ATL COM jsou zpracovávány jinými třídami:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) definuje výchozí objekt pro vytváření tříd a agregaci objektu.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) poskytuje výchozí implementaci `IDispatch Interface` části všech duálních rozhraní objektu.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementuje `ISupportErrorInfo` rozhraní, které zajišťuje informace o chybách, lze správně rozšířit řetězcem volání.

## <a name="in-this-section"></a>V tomto oddílu

[Implementace CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Zobrazit ukázkové položky mapování modelu COM pro `CComObjectRootEx`implementaci.

[Implementace CComObject, CComAggObject a CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
Popisuje, jak **makra\*DECLARE_ _AGGREGATABLE** `CComObject`ovlivňují použití, `CComAggObject`a `CComPolyObject`.

[Podpora IDispatch a IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Seznam tříd implementace knihovny ATL, které se mají použít `IDispatch` pro `IErrorInfo` podporu rozhraní a.

[Podpora IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
Popisuje kroky pro implementaci bodu připojení pro vaši třídu.

[Změna výchozího objektu pro vytváření tříd a agregačního modelu](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Zobrazit, jaká makra se mají použít ke změně výchozího modelu pro vytváření a agregaci tříd.

[Vytvoření agregovaného objektu](../atl/creating-an-aggregated-object.md)<br/>
Obsahuje seznam kroků pro vytvoření agregovaného objektu.

## <a name="related-sections"></a>Související oddíly

[Vytvoření projektu ATL](../atl/reference/creating-an-atl-project.md)<br/>
Poskytuje informace o vytvoření objektu COM ATL.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovny Active Template Library.

## <a name="see-also"></a>Viz také:

[Charakteristiky](../atl/active-template-library-atl-concepts.md)
