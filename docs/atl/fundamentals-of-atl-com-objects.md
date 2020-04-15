---
title: Základy objektů ATL COM
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 651413534ed44143e2a0fdaf00bdabd6e5d57010
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319559"
---
# <a name="fundamentals-of-atl-com-objects"></a>Základy objektů ATL COM

Následující obrázek znázorňuje vztah mezi třídami a rozhraními, které se používají k definování objektu KNIHOVNY KNIHOVNY ATL COM.

![Struktura ATL](../atl/media/vc307y1.gif "Struktura ATL")

> [!NOTE]
> Tento diagram `CComObject` ukazuje, že `CYourClass` je `CComAggObject` `CComPolyObject` odvozen `CYourClass` od vzhledem k tomu a zahrnout jako členské proměnné.

Objekt KNIHOVNY ATL COM lze definovat třemi způsoby. Standardní možností je použít `CComObject` třídu, která `CYourClass`je odvozena od . Druhou možností je vytvořit agregovaný objekt `CComAggObject` pomocí třídy. Třetí možností je použít `CComPolyObject` třídu. `CComPolyObject`funguje jako hybrid: může fungovat `CComObject` jako třída `CComAggObject` nebo jako třída, v závislosti na tom, jak je nejprve vytvořen. Další informace o použití `CComPolyObject` třídy naleznete v tématu [CComPolyObject Class](../atl/reference/ccompolyobject-class.md).

Při použití standardního knihovny ATL COM použijete dva objekty: vnější objekt a vnitřní objekt. Externí klienti přistupují k funkcím vnitřního objektu prostřednictvím funkcí obálky, které jsou definovány ve vnějším objektu. Vnější objekt je `CComObject`typu .

Při použití agregovaného objektu vnější objekt neposkytuje obálky pro funkce vnitřního objektu. Místo toho vnější objekt poskytuje ukazatel, který je přímo přístupný externím klientům. V tomto scénáři vnější objekt `CComAggObject`je typu . Vnitřní objekt je členská proměnná vnějšího objektu `CYourClass`a je typu .

Vzhledem k tomu, že klient nemusí procházet vnější objekt pro interakci s vnitřním objektem, agregované objekty jsou obvykle efektivnější. Vnější objekt také nemusí znát funkce agregovaného objektu vzhledem k tomu, že rozhraní agregovaného objektu je přímo k dispozici klientovi. Však ne všechny objekty lze agregovat. Pro objekt, který má být agregován, musí být navržen s ohledem na agregaci.

ATL implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ve dvou fázích:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)nebo [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje `IUnknown` metody.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) spravuje počet odkazů a `IUnknown`vnější ukazatele .

Další aspekty objektu KNIHOVNY ATL COM jsou zpracovány jinými třídami:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) definuje objekt u výchozí třídy factory a agregační model.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) poskytuje výchozí implementaci `IDispatch Interface` části všech duálních rozhraní na objektu.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementuje `ISupportErrorInfo` rozhraní, které zajišťuje, že informace o chybách mohou být správně rozšířeny do řetězce volání.

## <a name="in-this-section"></a>V tomto oddílu

[Implementace CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Zobrazit ukázkové položky `CComObjectRootEx`mapy COM pro implementaci .

[Implementace CComObject, CComAggObject a CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
Popisuje, jak **\*DECLARE_ _AGGREGATABLE** makra `CComObject` `CComAggObject`ovlivňují `CComPolyObject`použití písmen a, b) a .

[Podpora IDispatch a IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Uvádí třídy implementace knihovny ATL, které mají být používány pro podporu rozhraní `IDispatch` a. `IErrorInfo`

[Podpora IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
Popisuje kroky k implementaci spojovacího bodu pro vaši třídu.

[Změna výchozího modelu výroby tříd a modelu agregace](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Ukažte, jaká makra se mají použít ke změně výchozího modelu výroby tříd a agregace.

[Vytvoření agregovaného objektu](../atl/creating-an-aggregated-object.md)<br/>
Uvádí postup vytvoření agregovaného objektu.

## <a name="related-sections"></a>Související oddíly

[Vytvoření projektu ATL](../atl/reference/creating-an-atl-project.md)<br/>
Obsahuje informace o vytvoření objektu KNIHOVNY ATL COM.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Obsahuje odkazy na koncepční témata týkající se programování pomocí knihovny aktivních šablon.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)
