---
title: Třídy zásady kopírování ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e633395c9662bde0ad5fa4289294ef4098ab371c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849198"
---
# <a name="atl-copy-policy-classes"></a>Třídy zásady kopírování ATL
Třídy zásady kopírování jsou [užitkové třídy](../atl/utility-classes.md) použitý k inicializaci, kopírování a odstranit data. Třídy zásady kopírování umožňují definovat sémantiku kopírování pro jakýkoli typ dat a definujte převody mezi různými datovými typy.  
  
 Použití třídy zásady kopírování ATL v jeho implementace z následujících šablon:  
  
-   [Ccomenumimpl –](../atl/reference/ccomenumimpl-class.md)  
  
-   [Ienumonstlimpl –](../atl/reference/ienumonstlimpl-class.md)  
  
-   [Icollectiononstlimpl –](../atl/reference/icollectiononstlimpl-class.md)  
  
 Zapouzdřením informací potřebných ke kopírování nebo převést data v, který lze předat jako argument šablony třídy zásady kopírování ATL vývojáři zadali pro extrémní opětovné použití těchto tříd. Například pokud potřebujete implementovat kolekce pomocí libovolného libovolného datového typu, vše, co je potřeba zadat jsou kopie příslušné zásady; si už nikdy nemusíte dotýkat kódu, který implementuje kolekci.  
  
## <a name="definition"></a>Definice  
 Podle definice je třída, která poskytuje následující funkce statické třídy zásady kopírování:  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 Můžete nahradit typy `DestinationType` a *SourceType* s typy libovolná data pro jednotlivé zásady kopírování.  
  
> [!NOTE]
>  Přestože můžete definovat třídy zásady kopírování pro všechny typy libovolná data, použijte třídy v kódu ATL měli omezit typy, které dávají smysl. Například při použití zásad kopírování třídy s shromažďování ATL nebo enumerátoru implementace `DestinationType` musí být typ, který může sloužit jako parametr v metodě rozhraní modelu COM.  
  
 Použití **init** inicializace dat, **kopírování** ke kopírování dat, a **zničit** uvolnit data. Přesné význam inicializace, kopírování a zničení doménou třídy zásady kopírování a se bude lišit podle používané datové typy.  
  
 Existují dva požadavky na použití a implementaci třídy zásady kopírování:  
  
-   První parametr **kopírování** musí přijmout jenom ukazatel na data, která jste dříve inicializován pomocí **init**.  
  
-   **zničit** musí vždy jen přijímat ukazatel na data, která jste dříve inicializován pomocí **init** nebo zkopírované přes **kopírování**.  
  
## <a name="standard-implementations"></a>Standardní implementace  
 Knihovna ATL poskytuje dvě třídy zásady kopírování ve formě `_Copy` a `_CopyInterface` tříd šablon:  
  
-   `_Copy` Třída umožňuje homogenní pouze kopírování (ne převodu mezi datovými typy) od nabízí jenom zadat současně parametr jednou šablonou `DestinationType` a *SourceType*. Obecnou implementaci Tato šablona neobsahuje žádný kód inicializace nebo zničení a používá `memcpy` kopírovat data. Knihovna ATL poskytuje také specializace `_Copy` pro VARIANTU, LPOLESTR, OLEVERB a CONNECTDATA datové typy.  
  
-   `_CopyInterface` Třída poskytuje implementaci pro kopírování standardních pravidel COM ukazatele rozhraní. Ještě jednou Tato třída umožňuje pouze homogenní kopírování, aby používalo jednoduché přiřazení a volání `AddRef` ke kopírování.  
  
## <a name="custom-implementations"></a>Vlastní implementace  
 Obvykle budete potřebovat k definování vlastních tříd zásad kopírování pro heterogenní kopírování (to znamená, převodu mezi datovými typy). Některé příklady užitečných vlastních tříd zásad kopírování, podívejte se na soubory VCUE_Copy.h a VCUE_CopyString.h v [ATLCollections](../visual-cpp-samples.md) vzorku. Tyto soubory obsahují dvě třídy zásady kopírování šablony `GenericCopy` a `MapCopy`, plus počet specializace `GenericCopy` pro různé datové typy.  
  
### <a name="genericcopy"></a>GenericCopy  
 `GenericCopy` můžete zadat *SourceType* a `DestinationType` jako argumenty šablony. Tady je nejobecnější formu `GenericCopy` třídy z VCUE_Copy.h:  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]  
  
 VCUE_Copy.h také obsahuje následující specializace této třídy: `GenericCopy<BSTR>`, `GenericCopy<VARIANT, BSTR>`, `GenericCopy<BSTR, VARIANT>`. VCUE_CopyString.h obsahuje specializace pro kopírování z **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, a `GenericCopy<BSTR, std::string>`. Může vylepšit `GenericCopy` tím, že poskytuje další specializace vlastní.  
  
### <a name="mapcopy"></a>MapCopy  
 `MapCopy` předpokládá, že data kopírovaná je uložen do mapy stylu knihovny C++ Standard, takže ho můžete zadat typ mapy, ve kterém jsou data uložená a zadejte cíl. Implementace třídy používá funkce typedefs poskytnutých *MapType* třídu k určení typu zdroje dat a volat odpovídající `GenericCopy` třídy. Nejsou potřeba žádné specializace této třídy.  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]  
  
## <a name="see-also"></a>Viz také  
 [Implementace kolekce založené na knihovně Standard jazyka C++](../atl/implementing-an-stl-based-collection.md)   
 [Ukázka ATLCollections](../visual-cpp-samples.md)

