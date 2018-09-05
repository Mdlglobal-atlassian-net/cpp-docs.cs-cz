---
title: Makra kategorií | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
dev_langs:
- C++
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b8f07a559c6353bb66a210bf450c15376720cdac
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753032"
---
# <a name="category-macros"></a>Makra kategorií

Tato makra definují kategorie mapy.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Označuje začátek toho mapy kategorie.|
|[END_CATEGORY_MAP](#end_category_map)|Označuje konec mapování kategorie.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Určuje kategorie, které jsou implementovány pomocí objektu COM.|
|[REQUIRED_CATEGORY](#required_category)|Označuje kategorií, které jsou požadovány kontejneru v modelu COM objektu.|  

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom  

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP

Označuje začátek toho mapy kategorie.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*  
[in] Název třídy obsahující mapování kategorie.

### <a name="remarks"></a>Poznámky

Kategorie mapování slouží k určení komponenty kategorií, které implementuje třída modelu COM a kategorie, které vyžaduje ze svého kontejneru.

Přidat [IMPLEMENTED_CATEGORY](#implemented_category) položku do mapy pro každou kategorii implementováno třídou COM. Přidat [REQUIRED_CATEGORY](#required_category) položku do mapy pro každou kategorii, která vyžaduje třídu klientů k implementaci. Konec mapování [END_CATEGORY_MAP](#end_category_map) – makro.

Součást kategorie uvedené v objektu map se zaregistruje automaticky po registraci modulu, pokud třída má přiřazený [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .

> [!NOTE]
>  ATL – používá správce kategorií standardní součástí k registraci komponenty kategorií. Pokud správce není k dispozici v systému, když je zaregistrovaný v modulu, registrace úspěšná, ale součást kategorie nebude registrována pro danou třídu.

Další informace o kategoriích komponenty, naleznete v tématu [co jsou součástí kategorie a jak fungují](/windows/desktop/com/component-categories-and-how-they-work) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>  END_CATEGORY_MAP

Označuje konec mapování kategorie.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_CATEGORY_MAP](#begin_category_map).

##  <a name="implemented_category"></a>  IMPLEMENTED_CATEGORY

Přidat makro aplikace IMPLEMENTED_CATEGORY vaší komponentě [kategorie mapování](#begin_category_map) k určení, že by měl být zaregistrován jako implementace kategorie identifikován *catID* parametru.

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parametry

*catID*  
[in] Konstanta CATID nebo proměnná drží globálně jedinečný identifikátor (GUID) pro kategorii implementovaná. Adresa *catID* bude přijata a přidán do mapování. Najdete v následující tabulce pro výběr uložených kategorií.

### <a name="remarks"></a>Poznámky

Součást kategorie uvedené v objektu map se zaregistruje automaticky po registraci modulu, pokud třída má přiřazený [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra.

Klienty můžete použít informace o kategoriích, které jsou registrovány pro třídu k určení jeho možnosti a požadavky bez nutnosti vytvořit její instanci.

Další informace o kategoriích komponenty, naleznete v tématu [co jsou součástí kategorie a jak fungují](/windows/desktop/com/component-categories-and-how-they-work) v sadě Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Výběr základní kategorie

|Popis|Symbol|Registru GUID|
|-----------------|------------|-------------------|
|Bezpečné pro skriptování|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpečné pro inicializaci|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Jednoduchý rámeček webu členství ve skupině|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Jednoduchá vazba dat|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Rozšířená datová vazba|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Ovládací prvky bez oken|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|S ohledem na Internetu objekty|Zobrazit [vědět objekty Internet](/windows/desktop/com/internet-aware-objects) v sadě Windows SDK pro seznam ukázek.||

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>  REQUIRED_CATEGORY

Přidat makro REQUIRED_CATEGORY vaší komponentě [kategorie mapování](#begin_category_map) k určení, že by měl být zaregistrován jako vyžadující kategorie identifikován *catID* parametru.

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parametry

*catID*  
[in] Konstanta CATID nebo proměnná drží globálně jedinečný identifikátor (GUID) pro požadovaná kategorie. Adresa *catID* bude přijata a přidán do mapování. Najdete v následující tabulce pro výběr uložených kategorií.

### <a name="remarks"></a>Poznámky

Součást kategorie uvedené v objektu map se zaregistruje automaticky po registraci modulu, pokud třída má přiřazený [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra.

Klienty můžete použít informace o kategoriích, které jsou registrovány pro třídu k určení jeho možnosti a požadavky bez nutnosti vytvořit její instanci. Ovládací prvek může například vyžadovat, že kontejner podporuje datovou vazbu. Kontejner můžete zjistit se jeho funkce, které jsou nezbytné pro hostování ovládacího prvku dotazem správce kategorií pro kategorie vyžaduje ovládací prvek. Pokud kontejner nepodporuje požadované funkce, může odmítnout k hostování objektu COM.

Další informace o kategoriích komponenty, včetně seznamu vzorku, naleznete v tématu [co jsou součástí kategorie a jak fungují](/windows/desktop/com/component-categories-and-how-they-work) v sadě Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Výběr základní kategorie

|Popis|Symbol|Registru GUID|
|-----------------|------------|-------------------|
|Bezpečné pro skriptování|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpečné pro inicializaci|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Jednoduchý rámeček webu členství ve skupině|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Jednoduchá vazba dat|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Rozšířená datová vazba|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Ovládací prvky bez oken|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|S ohledem na Internetu objekty|Zobrazit [vědět objekty Internet](/windows/desktop/com/internet-aware-objects) v sadě Windows SDK pro seznam ukázek.||

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
