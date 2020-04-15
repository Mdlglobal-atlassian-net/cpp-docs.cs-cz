---
title: Makra kategorií
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 1d8bbae4608aa661bbc612604f7d85855f325f5f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321602"
---
# <a name="category-macros"></a>Makra kategorií

Tato makra definují mapy kategorií.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Označuje začátek mapy kategorií.|
|[END_CATEGORY_MAP](#end_category_map)|Označuje konec mapy kategorií.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Označuje kategorie, které jsou implementovány objektem COM.|
|[REQUIRED_CATEGORY](#required_category)|Označuje kategorie, které jsou požadovány od kontejneru objektem COM.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="begin_category_map"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

Označuje začátek mapy kategorií.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[v] Název třídy obsahující mapu kategorií.

### <a name="remarks"></a>Poznámky

Mapa kategorií se používá k určení kategorií součástí, které bude třída COM implementovat a které kategorie vyžaduje od svého kontejneru.

Přidejte [položku IMPLEMENTED_CATEGORY](#implemented_category) do mapy pro každou kategorii implementovanou třídou COM. Přidejte [položku REQUIRED_CATEGORY](#required_category) do mapy pro každou kategorii, kterou třída vyžaduje, aby její klienti implementovali. Označte konec mapy [END_CATEGORY_MAP](#end_category_map) makra.

Kategorie komponent uvedených v mapě budou automaticky zaregistrovány při registraci modulu, pokud má třída přidruženou [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto).

> [!NOTE]
> Společnost ATL používá správce standardních kategorií komponent k registraci kategorií součástí. Pokud správce není přítomen v systému při registraci modulu, registrace proběhne úspěšně, ale kategorie komponent nebudou registrovány pro tuto třídu.

Další informace o kategoriích součástí naleznete v [tématu Co jsou kategorie součástí a jak fungují](/windows/win32/com/component-categories-and-how-they-work) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a>END_CATEGORY_MAP

Označuje konec mapy kategorií.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_CATEGORY_MAP](#begin_category_map).

## <a name="implemented_category"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY

Přidejte IMPLEMENTED_CATEGORY makro do [mapy kategorií komponenty](#begin_category_map) a určete, že by mělo být registrováno jako implementace kategorie identifikované parametrem *catID.*

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parametry

*Catid*<br/>
[v] Konstanta CATID nebo proměnná, která drží globálně jedinečný identifikátor (GUID) pro implementovanou kategorii. Adresa *catID* bude převzata a přidána do mapy. Výběr kategorií akcií naleznete v tabulce níže.

### <a name="remarks"></a>Poznámky

Kategorie komponent uvedených v mapě budou automaticky zaregistrovány při registraci modulu, pokud má třída přidružené [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro.

Klienti mohou použít informace o kategorii registrované pro třídu k určení jejích schopností a požadavků, aniž by museli vytvořit instanci.

Další informace o kategoriích součástí naleznete v [tématu Co jsou kategorie součástí a jak fungují](/windows/win32/com/component-categories-and-how-they-work) v sadě Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Výběr skladových kategorií

|Popis|Symbol|Identifikátor GUID registru|
|-----------------|------------|-------------------|
|Bezpečné pro skriptování|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpečné pro inicializaci|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Jednoduché uzavření rámce|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Jednoduchá datová vazba|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Rozšířená datová vazba|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Ovládací prvky bez oken|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objekty podporující Internet|Ukázkový seznam naleznete v [části Objekty podporující Internet](/windows/win32/com/internet-aware-objects) v sadě Windows SDK.||

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a>REQUIRED_CATEGORY

Přidejte REQUIRED_CATEGORY makro do [mapy kategorií komponenty](#begin_category_map) a určete, že by mělo být registrováno jako vyžadující kategorii označenou parametrem *catID.*

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parametry

*Catid*<br/>
[v] Konstanta CATID nebo proměnná, která drží globálně jedinečný identifikátor (GUID) pro požadovanou kategorii. Adresa *catID* bude převzata a přidána do mapy. Výběr kategorií akcií naleznete v tabulce níže.

### <a name="remarks"></a>Poznámky

Kategorie komponent uvedených v mapě budou automaticky zaregistrovány při registraci modulu, pokud má třída přidružené [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro.

Klienti mohou použít informace o kategorii registrované pro třídu k určení jejích schopností a požadavků, aniž by museli vytvořit instanci. Ovládací prvek může například vyžadovat, aby kontejner podporuje datovou vazbu. Kontejner můžete zjistit, pokud má možnosti potřebné k hostování ovládacího prvku dotazem správce kategorií pro kategorie vyžadované tímto ovládacím prvkem. Pokud kontejner nepodporuje požadovanou funkci, může odmítnout hostovat objekt COM.

Další informace o kategoriích součástí, včetně ukázkového seznamu, naleznete v [tématu Co jsou kategorie součástí a jak fungují](/windows/win32/com/component-categories-and-how-they-work) v sadě Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Výběr skladových kategorií

|Popis|Symbol|Identifikátor GUID registru|
|-----------------|------------|-------------------|
|Bezpečné pro skriptování|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpečné pro inicializaci|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Jednoduché uzavření rámce|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Jednoduchá datová vazba|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Rozšířená datová vazba|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Ovládací prvky bez oken|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objekty podporující Internet|Ukázkový seznam naleznete v [části Objekty podporující Internet](/windows/win32/com/internet-aware-objects) v sadě Windows SDK.||

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
