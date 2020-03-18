---
title: Makra kategorie
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 411e06cc795827eef356018ba427510fd9eb7c06
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418130"
---
# <a name="category-macros"></a>Makra kategorie

Tato makra definují mapování kategorií.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Označí začátek mapy kategorie.|
|[END_CATEGORY_MAP](#end_category_map)|Označí konec mapy kategorie.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Označuje kategorie implementované objektem COM.|
|[REQUIRED_CATEGORY](#required_category)|Označuje kategorie, které jsou požadovány pro kontejner objektem COM.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

Označí začátek mapy kategorie.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
pro Název třídy, která obsahuje mapu kategorie.

### <a name="remarks"></a>Poznámky

Mapa kategorie se používá k určení, které kategorie komponent bude třída COM implementovat a které kategorie vyžaduje z kontejneru.

Přidejte položku [IMPLEMENTED_CATEGORY](#implemented_category) na mapu pro každou kategorii implementovanou třídou com. Přidejte [REQUIRED_CATEGORY](#required_category) položku na mapu pro každou kategorii, kterou třída vyžaduje k implementaci svých klientů. Označte konec mapy pomocí makra [END_CATEGORY_MAP](#end_category_map) .

Kategorie komponent uvedené v mapě budou registrovány automaticky, pokud je modul zaregistrován, pokud má třída přidruženou [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto).

> [!NOTE]
>  Knihovna ATL používá ke registraci kategorií komponent standardní správce kategorií součástí. Pokud v systému není správce k dispozici, je-li modul registrován, registrace je úspěšná, ale kategorie komponent nebudou pro tuto třídu registrovány.

Další informace o kategoriích komponent naleznete v tématu [co jsou kategorie komponent a jak](/windows/win32/com/component-categories-and-how-they-work) fungují v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>END_CATEGORY_MAP

Označí konec mapy kategorie.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Příklad

Podívejte se na příklad [BEGIN_CATEGORY_MAP](#begin_category_map).

##  <a name="implemented_category"></a>IMPLEMENTED_CATEGORY

Přidejte IMPLEMENTED_CATEGORY makro k [mapě kategorie](#begin_category_map) vaší komponenty a určete tak, že by měl být zaregistrován jako implementace kategorie identifikované parametrem *catID* .

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parametry

*catID*<br/>
pro CATID konstanta nebo proměnná drží globálně jedinečný identifikátor (GUID) pro implementovanou kategorii. Adresa *catID* bude provedena a přidána na mapu. Výběr kategorií akcií najdete v následující tabulce.

### <a name="remarks"></a>Poznámky

Kategorie komponent uvedené v mapě budou registrovány automaticky, pokud je modul registrován, pokud má třída přidružené [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro.

Klienti mohou pomocí informací o kategorii registrovaných pro třídu určit její schopnosti a požadavky, aniž by museli vytvořit její instanci.

Další informace o kategoriích komponent naleznete v tématu [co jsou kategorie komponent a jak](/windows/win32/com/component-categories-and-how-they-work) fungují v Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Výběr kategorií akcií

|Popis|Písmeno|GUID registru|
|-----------------|------------|-------------------|
|Bezpečné pro skriptování|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpečné pro inicializaci|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Zahrnutí jednoduchého snímku webu|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Jednoduchá datová vazba|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Rozšířená datová vazba|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Ovládací prvky bez oken|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Internetové objekty|Seznam ukázek najdete v části věnované [internetovým objektům](/windows/win32/com/internet-aware-objects) v Windows SDK.||

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>REQUIRED_CATEGORY

Přidejte REQUIRED_CATEGORY makro k [mapě kategorie](#begin_category_map) vaší komponenty a určete tak, že by měl být zaregistrován jako požadavek na kategorii identifikovanou parametrem *catID* .

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parametry

*catID*<br/>
pro CATID konstanta nebo proměnná drží globálně jedinečný identifikátor (GUID) pro požadovanou kategorii. Adresa *catID* bude provedena a přidána na mapu. Výběr kategorií akcií najdete v následující tabulce.

### <a name="remarks"></a>Poznámky

Kategorie komponent uvedené v mapě budou registrovány automaticky, pokud je modul registrován, pokud má třída přidružené [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro.

Klienti mohou pomocí informací o kategorii registrovaných pro třídu určit její schopnosti a požadavky, aniž by museli vytvořit její instanci. Ovládací prvek může například vyžadovat, aby vazba dat podporovala kontejner. Kontejner může zjistit, jestli má funkce nezbytné pro hostování ovládacího prvku, a to tak, že se dotazuje správce kategorií na kategorie vyžadované tímto ovládacím prvkem. Pokud kontejner nepodporuje požadovanou funkci, může odmítnout hostování objektu COM.

Další informace o kategoriích součástí, včetně ukázkového seznamu, najdete v tématu [co jsou kategorie komponent a jak](/windows/win32/com/component-categories-and-how-they-work) fungují v Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Výběr kategorií akcií

|Popis|Písmeno|GUID registru|
|-----------------|------------|-------------------|
|Bezpečné pro skriptování|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpečné pro inicializaci|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Zahrnutí jednoduchého snímku webu|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Jednoduchá datová vazba|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Rozšířená datová vazba|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Ovládací prvky bez oken|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Internetové objekty|Seznam ukázek najdete v části věnované [internetovým objektům](/windows/win32/com/internet-aware-objects) v Windows SDK.||

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)
