---
title: Třídy zásad kopírování atl
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: f40f31124d4547076249a7459ac4b63cc25305d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317384"
---
# <a name="atl-copy-policy-classes"></a>Třídy zásad kopírování atl

Třídy zásad kopírování jsou [třídy nástrojů](../atl/utility-classes.md) používané k inicializaci, kopírování a odstraňování dat. Kopírovat třídy zásad umožňují definovat sémantiku kopírování pro libovolný typ dat a definovat převody mezi různými datovými typy.

Knihovna ATL používá třídy zásad kopírování ve svých implementacích následujících šablon:

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLimpl](../atl/reference/icollectiononstlimpl-class.md)

Zapouzdřením informací potřebných ke kopírování nebo převodu dat ve třídě zásad kopírování, které mohou být předány jako argument šablony, vývojáři knihovny ATL poskytli extrémní opětovné použití těchto tříd. Například pokud potřebujete implementovat kolekci pomocí libovolného datového typu, vše, co potřebujete poskytnout, je příslušná zásada kopírování; nikdy nebudete muset dotknout kódu, který implementuje kolekci.

## <a name="definition"></a>Definice

Podle definice je třída, která poskytuje následující statické funkce, třídou zásad kopírování:

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

Typy `DestinationType` a *SourceType* můžete nahradit libovolnými datovými typy pro každou zásadu kopírování.

> [!NOTE]
> I když můžete definovat třídy zásad kopírování pro libovolné datové typy, použití tříd v kódu ATL by mělo omezit typy, které dávají smysl. Například při použití třídy zásad kopírování s implementací kolekce nebo `DestinationType` čítače protokolu ATL musí být typ, který lze použít jako parametr v metodě rozhraní COM.

Pomocí **inicializace** dat, **kopírování** zkopírovat data a **zničit,** aby se data uvolnila. Přesný význam inicializace, kopírování a zničení jsou doménou třídy zásad kopírování a budou se lišit v závislosti na souvisejících datových typech.

Existují dva požadavky na použití a implementaci třídy zásad kopírování:

- První parametr, který chcete **zkopírovat,** musí obdržet pouze ukazatel na data, která jste dříve inicializovali pomocí **init**.

- **destroy** musí vždy obdržet pouze ukazatel na data, která jste dříve inicializovali pomocí **initunebo** zkopírovali pomocí **kopie**.

## <a name="standard-implementations"></a>Standardní implementace

Knihovna ATL poskytuje dvě třídy `_Copy` `_CopyInterface` zásad kopírování ve formě tříd a šablony:

- Třída `_Copy` umožňuje pouze homogenní kopírování (nikoli převod mezi datovými typy), protože nabízí `DestinationType` pouze jeden parametr šablony pro určení obou a *SourceType*. Obecná implementace této šablony neobsahuje žádný kód `memcpy` inicializace nebo zničení a používá ke kopírování dat. ATL také poskytuje specializace `_Copy` pro datové typy VARIANT, LPOLESTR, OLEVERB a CONNECTDATA.

- Třída `_CopyInterface` poskytuje implementaci pro kopírování ukazatelů rozhraní podle standardních pravidel COM. Opět tato třída umožňuje pouze homogenní kopírování, takže používá jednoduché `AddRef` přiřazení a volání k provedení kopie.

## <a name="custom-implementations"></a>Vlastní implementace

Obvykle budete muset definovat vlastní třídy zásad kopírování pro heterogenní kopírování (to znamená převod mezi datovými typy). Některé příklady vlastních tříd zásad kopírování nahlédnou na soubory VCUE_Copy.h a VCUE_CopyString.h v ukázkovém souboru [ATLCollections.](../overview/visual-cpp-samples.md) Tyto soubory obsahují dvě třídy zásad kopírování šablony `GenericCopy` a `MapCopy` `GenericCopy` navíc řadu specializací pro různé datové typy.

### <a name="genericcopy"></a>GenericCopy

`GenericCopy`umožňuje zadat *SourceType* a `DestinationType` jako argumenty šablony. Zde je nejobecnější forma `GenericCopy` třídy z VCUE_Copy.h:

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h obsahuje také následující specializace této `GenericCopy<BSTR>` `GenericCopy<VARIANT, BSTR>`třídy: , , `GenericCopy<BSTR, VARIANT>`. VCUE_CopyString.h obsahuje specializace pro kopírování z **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`a `GenericCopy<BSTR, std::string>`. Dalo by `GenericCopy` se zvýšit tím, že další specializace své vlastní.

### <a name="mapcopy"></a>Mapcopy

`MapCopy`předpokládá, že kopírovaná data jsou uložena do mapy ve stylu standardní knihovny jazyka C++, takže umožňuje určit typ mapy, ve které jsou data uložena, a cílový typ. Implementace třídy pouze používá typedefs dodané *MapType* třídy k určení typu zdrojových `GenericCopy` dat a volání příslušné třídy. Nejsou potřeba žádné specializace této třídy.

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>Viz také

[Implementace kolekce založené na standardní knihovně c++](../atl/implementing-an-stl-based-collection.md)<br/>
[Ukázka atlcollections](../overview/visual-cpp-samples.md)
