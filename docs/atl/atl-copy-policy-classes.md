---
title: Třídy ATL kopie zásad | Microsoft Docs
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
ms.openlocfilehash: 34b9ed5dca45633a5ab980d38b8a7cda151f5dc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358524"
---
# <a name="atl-copy-policy-classes"></a>Třídy ATL kopie zásad
Kopírování zásad třídy jsou [nástroj třídy](../atl/utility-classes.md) použitý k inicializaci, kopírování a odstranit data. Kopírování zásad třídy umožňují definovat sémantiku kopie pro jakýkoli typ dat a k definování převody mezi různými datovými typy.  
  
 Používá kopie zásady třídy ATL v jeho implementace z následujících šablon:  
  
-   [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)  
  
-   [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)  
  
-   [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)  
  
 Zapouzdřením informace potřebné k zkopírovat nebo převést data v třídě zásad kopie, které lze předat jako argument šablony vývojáři ATL zadali pro extrémně – opětovné použití těchto tříd. Pokud potřebujete implementovat v kolekci pomocí libovolného typu libovolná data, všechny, které potřebují pro poskytování je například kopírování příslušné zásady; není nutné touch kód, který implementuje kolekce.  
  
## <a name="definition"></a>Definice  
 Podle definice třídu, která poskytuje následující funkce statický je třída zásad kopie:  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 Můžete nahradit typy `DestinationType` a *SourceType* s typy libovolná data pro každou zásadu kopírování.  
  
> [!NOTE]
>  I když můžete definovat zásady třídy kopie pro všechny typy libovolná data, měli omezit použití třídy v kódu ATL typy, které dávají smysl. Například když pomocí zásad kopie třídy ATL pro kolekci nebo implementace enumerátor `DestinationType` musí být typu, který lze použít jako parametr v metodu rozhraní COM.  
  
 Použití **init** inicializace dat, **kopie** ke zkopírování dat, a **destroy** k bezplatným data. Přesné význam inicializace, kopírování a odstraňování jsou domény třídy zásady kopírování a budou lišit v závislosti na zahrnutých datové typy.  
  
 Existují dva požadavky na použití a implementaci třídy kopie zásad:  
  
-   První parametr **kopie** musí přijímat pouze ukazatel na data, která jste dříve inicializována pomocí **init**.  
  
-   **Destroy** musí vždy jen obdržet ukazatel na data, která jste dříve inicializována pomocí **init** nebo zkopírovaný prostřednictvím **kopie**.  
  
## <a name="standard-implementations"></a>Standardní implementace  
 ATL poskytuje dvě kopie zásady třídy ve formě **_Copy** a **_CopyInterface** tříd šablon:  
  
-   **_Copy** třída umožňuje homogenní kopírování pouze (není převod mezi typy dat) vzhledem k tomu, že nabízí pouze jednu šablonu parametr, který se zadat oba seznamy `DestinationType` a *SourceType*. Obecnou implementaci Tato šablona neobsahuje žádný kód inicializace nebo zničení a používá `memcpy` kopírovat data. ATL také poskytuje specializací **_Copy** pro **VARIANT**, `LPOLESTR`, **OLEVERB**, a **CONNECTDATA** datové typy.  
  
-   **_CopyInterface** třída poskytuje implementaci pro kopírování ukazatele rozhraní následující standardní pravidla COM. Ještě jednou Tato třída umožňuje pouze homogenní kopírování, takže používá jednoduché přiřazení a volání `AddRef` pro kopírování.  
  
## <a name="custom-implementations"></a>Vlastní implementace  
 Obvykle budete muset definovat vaše vlastní třídy kopie zásady pro heterogenní kopírování (to znamená, převod mezi typy dat). Některé příklady vlastní kopie zásady třídy, podívejte se na soubory VCUE_Copy.h a VCUE_CopyString.h v [ATLCollections](../visual-cpp-samples.md) ukázka. Tyto soubory obsahují dvě třídy zásady kopírování šablony `GenericCopy` a `MapCopy`, plus počet specializací `GenericCopy` pro různé datové typy.  
  
### <a name="genericcopy"></a>GenericCopy  
 `GenericCopy` Umožňuje zadat *SourceType* a `DestinationType` jako argumenty pro šablony. Tady je nejobecnější formu `GenericCopy` třídy z VCUE_Copy.h:  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]  
  
 VCUE_Copy.h taky obsahuje následující specializací této třídy: `GenericCopy<BSTR>`, `GenericCopy<VARIANT, BSTR>`, `GenericCopy<BSTR, VARIANT>`. VCUE_CopyString.h obsahuje specializací kopírování z **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, a `GenericCopy<BSTR, std::string>`. Může zvýšit `GenericCopy` tím, že poskytuje další vlastní specializací.  
  
### <a name="mapcopy"></a>MapCopy  
 `MapCopy` předpokládá kopírovány uložení dat do knihovny C++ Standard-style mapu, takže ho můžete zadat typ mapy, ve kterém jsou data uložena a zadejte cíl. Implementace třídy právě používá definice TypeDef poskytl *MapType* třídu k určení typu zdroje dat a k volání odpovídající `GenericCopy` třídy. Je potřeba žádné specializací této třídy.  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]  
  
## <a name="see-also"></a>Viz také  
 [Implementace kolekci na základě knihovny C++ Standard](../atl/implementing-an-stl-based-collection.md)   
 [Ukázka ATLCollections](../visual-cpp-samples.md)

