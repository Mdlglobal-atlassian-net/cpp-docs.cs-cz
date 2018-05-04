---
title: Kategorie makra | Microsoft Docs
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
ms.openlocfilehash: b1eba97ef5253041752d4b8abfcd6ea7300b8492
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="category-macros"></a>Kategorie makra
Tyto makra definovat kategorie mapy.  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Označuje začátek kategorie mapy.|  
|[END_CATEGORY_MAP](#end_category_map)|Označuje konec kategorie mapy.|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|Určuje, kategorií, které jsou implementovány pomocí objektu COM.|  
|[REQUIRED_CATEGORY](#required_category)|Určuje, kategorií, které jsou požadovány kontejneru objektu COM.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP  
 Označuje začátek kategorie mapy.  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 [v] Název třídy obsahující kategorie mapy.  
  
### <a name="remarks"></a>Poznámky  
 Kategorie mapy slouží k určení součást kategorie, které bude implementace třídy COM a kategorie, které vyžaduje z jeho kontejneru.  
  
 Přidat [IMPLEMENTED_CATEGORY](#implemented_category) položku s mapy pro každou kategorii implementované třídy COM. Přidat [REQUIRED_CATEGORY](#required_category) položku s mapy pro každou kategorii, která vyžaduje jeho klienty k implementaci třídy. Konec mapa s [END_CATEGORY_MAP](#end_category_map) makro.  
  
 Součást kategorií uvedených v mapě registrovat automaticky, když modul je zaregistrovaná, pokud má přidruženou třídu [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .  
  
> [!NOTE]
>  ATL používá správce kategorií standardní součástí zaregistrovat součást kategorie. Pokud správce není v systému, když je registrovaný modul, registrace úspěšná, ale součást kategorie nebude registrována pro tuto třídu.  
  
 Další informace o součást kategorií najdete v tématu [co jsou součástí kategorií a jak pracují](http://msdn.microsoft.com/library/windows/desktop/ms694322) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="end_category_map"></a>  END_CATEGORY_MAP  
 Označuje konec kategorie mapy.  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [BEGIN_CATEGORY_MAP](#begin_category_map).  
  
##  <a name="implemented_category"></a>  IMPLEMENTED_CATEGORY  
 Přidat `IMPLEMENTED_CATEGORY` makro k příslušné součásti [kategorie mapy](#begin_category_map) k určení, které by měl být registrován jako implementace kategorie identifikovaný `catID` parametr.  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>Parametry  
 `catID`  
 [v] A **CATID** konstanta, nebo proměnnou, která uchovává globálně jedinečný identifikátor (GUID) pro implementovaná kategorii. Na adresu `catID` bude provedena a přidat do mapy. Najdete v následující tabulce pro výběr uložených kategorií.  
  
### <a name="remarks"></a>Poznámky  
 Součást kategorií uvedených v mapě registrovat automaticky, když modul je zaregistrovaná, pokud má přidruženou třídu [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro.  
  
 Klienty můžete použít informace o kategoriích, které jsou registrované pro třídu k určení požadavky a možnosti, aniž by bylo nutné vytvořit její instanci.  
  
 Další informace o součást kategorií najdete v tématu [co jsou součástí kategorií a jak pracují](http://msdn.microsoft.com/library/windows/desktop/ms694322) ve Windows SDK.  
  
### <a name="a-selection-of-stock-categories"></a>Výběr uložených kategorií  
  
|Popis|Symbol|Registru GUID|  
|-----------------|------------|-------------------|  
|Bezpečné pro skriptování|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Inicializaci|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Jednoduchý rámeček lokality členství ve skupině|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|Jednoduchá datová vazba|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Rozšířené datové vazby|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Bez oken ovládací prvky|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Objekty používající Internet|V tématu [objekty využívající Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) ve Windows SDK pro seznam ukázek.||  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="required_category"></a>  REQUIRED_CATEGORY  
 Přidat `REQUIRED_CATEGORY` makro k příslušné součásti [kategorie mapy](#begin_category_map) k určení, které by měl být registrován jako vyžadující kategorie identifikovaný `catID` parametr.  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>Parametry  
 `catID`  
 [v] A **CATID** konstanta nebo proměnná, která uchovává globálně jedinečný identifikátor (GUID) pro požadované kategorii. Na adresu `catID` bude provedena a přidat do mapy. Najdete v následující tabulce pro výběr uložených kategorií.  
  
### <a name="remarks"></a>Poznámky  
 Součást kategorií uvedených v mapě registrovat automaticky, když modul je zaregistrovaná, pokud má přidruženou třídu [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) nebo [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro.  
  
 Klienty můžete použít informace o kategoriích, které jsou registrované pro třídu k určení požadavky a možnosti, aniž by bylo nutné vytvořit její instanci. Ovládacího prvku může například vyžadovat, že kontejner podporují datové vazby. Kontejner můžete zjistit Pokud má schopnosti, které jsou nezbytné k hostování ovládacího prvku pomocí dotazu kategorie správce pro tento ovládací prvek vyžaduje kategorie. Pokud kontejner nepodporuje požadované funkce, můžete odmítnout k hostování objekt COM.  
  
 Další informace o kategoriích součásti, včetně seznamu, ukázkové najdete v části [co jsou součástí kategorií a jak pracují](http://msdn.microsoft.com/library/windows/desktop/ms694322) ve Windows SDK.  
  
### <a name="a-selection-of-stock-categories"></a>Výběr uložených kategorií  
  
|Popis|Symbol|Registru GUID|  
|-----------------|------------|-------------------|  
|Bezpečné pro skriptování|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Inicializaci|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Jednoduchý rámeček lokality členství ve skupině|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|Jednoduchá datová vazba|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Rozšířené datové vazby|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Bez oken ovládací prvky|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Objekty používající Internet|V tématu [objekty využívající Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) ve Windows SDK pro seznam ukázek.||  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
