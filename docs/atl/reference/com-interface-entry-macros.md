---
title: Makra položky rozhraní modelu COM | Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::COM_INTERFACE_ENTRY
- atlcom/ATL::COM_INTERFACE_ENTRY_IID
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_BREAK
- atlcom/ATL::COM_INTERFACE_ENTRY_CACHED_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_CHAIN
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_NOINTERFACE
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c3ba41a05813c4112c1e5dd51bfe447d2c8debf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366585"
---
# <a name="cominterfaceentry-macros"></a>COM_INTERFACE_ENTRY – makra  
 Tyto makra zadejte rozhraní objektu do jeho mapy COM tak, aby přístupná pomocí `QueryInterface`. Pořadí položek v mapě COM je rozhraní pořadí bude ověřen odpovídající **IID** během `QueryInterface`.  

 |||
 |-|-|
 |[COM_INTERFACE_ENTRY –](#com_interface_entry)|Zadá rozhraní do mapy rozhraní COM.|  
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Použití tohoto makra k rozlišení dvou větví dědičnosti.|  
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Pomocí této makro zadejte rozhraní do mapy COM a jeho IID.|  
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Stejné jako [COM_INTERFACE_ENTRY2](#com_interface_entry2), s výjimkou můžete zadat různé identifikátory IID.|  
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Když rozhraní identifikovaný `iid` je dotazován, `COM_INTERFACE_ENTRY_AGGREGATE` předává `punk`.|  
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)kromě toho, že dotazování pro všechny identifikátory IID výsledkem předávání dotaz pro `punk`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), kromě případu, kdy `punk` je **NULL**, automaticky vytvoří agregace popsaného `clsid`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Stejné jako [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)kromě toho, že dotazování pro všechny identifikátory IID výsledkem předávání dotaz pro `punk`a pokud `punk` je **NULL**, automaticky vytváří agregace popsaného `clsid`.|  
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Způsobí, že váš program volat [debugbreak –](http://msdn.microsoft.com/library/windows/desktop/ms679297) když je dotazován specifikované rozhraní pro.|  
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Uloží data rozhraní specifické pro všechny instance.|  
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Zpřístupní úplné vypnutí rozhraní.|  
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Při zpracování dosáhne této položky v mapě COM, zpracuje mapy COM základní třídy.|  
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Obecné mechanismus pro zapojení do knihovny ATL pro `QueryInterface` logiku.|  
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Stejné jako [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)kromě toho, že dotazování pro všechny identifikátory IID výsledkem volání `func`.|  
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Vrátí **E_NOINTERFACE** a ukončí zpracování mapy COM, když je dotazován specifikované rozhraní pro.|  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlcom

## <a name="com_interface_entry"></a> COM_INTERFACE_ENTRY –
Zadá rozhraní do mapy rozhraní COM.

### <a name="syntax"></a>Syntaxe

```
COM_INTERFACE_ENTRY( x )
```
### <a name="parameters"></a>Parametry

x [v] název rozhraní objektu třída odvozená z přímo.

### <a name="remarks"></a>Poznámky
Obvykle se jedná o typ položky, které uživatel používá nejčastěji.

### <a name="example"></a>Příklad
```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```
### <a name="requirements"></a>Požadavky
**Záhlaví:** atlcom
  
##  <a name="com_interface_entry2"></a>  COM_INTERFACE_ENTRY2  
 Použití tohoto makra k rozlišení dvou větví dědičnosti.  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název rozhraní, kterou chcete vystavit z objektu.  
  
 `x2`  
 [v] Název větve dědičnosti, ze kterého *x* zpřístupněn.  
  
### <a name="remarks"></a>Poznámky  
 Například pokud odvodíte třídu objektu ze dvou duální rozhraní, vystavit `IDispatch` pomocí `COM_INTERFACE_ENTRY2` od `IDispatch` lze získat v jedné z rozhraní.  
  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="com_interface_entry_iid"></a>  COM_INTERFACE_ENTRY_IID  
 Pomocí této makro zadejte rozhraní do mapy COM a jeho IID.  
  
```
COM_INTERFACE_ENTRY_IID(iid, x)
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID rozhraní vystavené.  
  
 *x*  
 [v] Název třídy, jejichž vtable k dispozici jako rozhraní identifikovaný `iid`.  
  
 
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]  
  
##  <a name="com_interface_entry2_iid"></a>  COM_INTERFACE_ENTRY2_IID  
 Stejné jako [COM_INTERFACE_ENTRY2](#com_interface_entry2), s výjimkou můžete zadat různé identifikátory IID.  
  
```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```   
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID, které jsou určení pro rozhraní.  
  
 *x*  
 [v] Název rozhraní objektu třída odvozená z přímo.  
  
 `x2`  
 [v] Název druhé rozhraní objektu třída odvozená z přímo.  
  
##  <a name="com_interface_entry_aggregate"></a>  COM_INTERFACE_ENTRY_AGGREGATE  
 Když rozhraní identifikovaný `iid` je dotazován, `COM_INTERFACE_ENTRY_AGGREGATE` předává `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Rozhraní dotaz pro identifikátor GUID.  
  
 `punk`  
 [v] Název **IUnknown** ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 `punk` Parametr se předpokládá, že tak, aby odkazoval na vnitřní Neznámý agregace nebo na **NULL**, v takovém případě tato položka je ignorována. Obvykle byste **CoCreate** agregační funkci v `FinalConstruct`.  
  
  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="com_interface_entry_aggregate_blind"></a>  COM_INTERFACE_ENTRY_AGGREGATE_BLIND  
 Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)kromě toho, že dotazování pro všechny identifikátory IID výsledkem předávání dotaz pro `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```  
  
### <a name="parameters"></a>Parametry  
 `punk`  
 [v] Název **IUnknown** ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se dotaz rozhraní nezdaří, bude pokračovat zpracování COM mapy.  
  
  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]  
  

##  <a name="com_interface_entry_autoaggregate"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), kromě případu, kdy `punk` je **NULL**, automaticky vytvoří agregace popsaného `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Rozhraní dotaz pro identifikátor GUID.  
  
 `punk`  
 [v] Název **IUnknown** ukazatel. Musí být členem skupiny třída obsahující COM mapy.  
  
 `clsid`  
 [v] Identifikátor agregaci, která bude vytvořen, pokud `punk` je **NULL**.  
  
### <a name="remarks"></a>Poznámky  
  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="com_interface_entry_autoaggregate_blind"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND  
 Stejné jako [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)kromě toho, že dotazování pro všechny identifikátory IID výsledkem předávání dotaz pro `punk`a pokud `punk` je **NULL**, automaticky vytváří agregace popsaného `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```  
  
### <a name="parameters"></a>Parametry  
 `punk`  
 [v] Název **IUnknown** ukazatel. Musí být členem skupiny třída obsahující COM mapy.  
  
 `clsid`  
 [v] Identifikátor agregaci, která bude vytvořen, pokud `punk` je **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se dotaz rozhraní nezdaří, bude pokračovat zpracování COM mapy.  
  
  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]  
  
##  <a name="com_interface_entry_break"></a>  COM_INTERFACE_ENTRY_BREAK  
 Způsobí, že váš program volat [debugbreak –](http://msdn.microsoft.com/library/windows/desktop/ms679297) když je dotazován specifikované rozhraní pro.  
  
```
COM_INTERFACE_ENTRY_BREAK(x)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Text, který slouží k vytvoření identifikátor rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní IID bude vypočten připojením *x* k `IID_`. Například pokud *x* je `IPersistStorage`, bude IID `IID_IPersistStorage`.  
  
  
  
##  <a name="com_interface_entry_cached_tear_off"></a>  COM_INTERFACE_ENTRY_CACHED_TEAR_OFF  
 Uloží data rozhraní specifické pro všechny instance.  
  
```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```   
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID rozhraní úplné vypnutí.  
  
 *x*  
 [v] Název třídy implementující rozhraní.  
  
 `punk`  
 [v] Název **IUnknown** ukazatel. Musí být členem skupiny třída obsahující COM mapy. Je třeba inicializovat na **NULL** v konstruktoru objektu třídy.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se nepoužívá rozhraní, to snižuje celkovou velikost instance objektu.  
  
  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]  
  
##  <a name="com_interface_entry_tear_off"></a>  COM_INTERFACE_ENTRY_TEAR_OFF  
 Zpřístupní úplné vypnutí rozhraní.  
  
```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID rozhraní úplné vypnutí.  
  
 *x*  
 [v] Název třídy implementující rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Úplné vypnutí rozhraní je implementováno jako samostatný objekt, který je vytvořena instance rozhraní představuje pokaždé, když je dotazován na. Obvykle vytvoříte vaše rozhraní jako úplné vypnutí Pokud rozhraní se používá jen občas, protože to umožňuje ušetřit ukazatele vtable v každé instanci hlavní objektu. Úplné vypnutí se odstraní při jeho počet odkazů klesne na nulu. Třída implementace úplné vypnutí by měl být odvozen od `CComTearOffObjectBase` a mají svůj vlastní COM mapy.  
  
  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="com_interface_entry_chain"></a>  COM_INTERFACE_ENTRY_CHAIN  
 Při zpracování dosáhne této položky v mapě COM, zpracuje mapy COM základní třídy.  
  
```
COM_INTERFACE_ENTRY_CHAIN(classname)
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 [v] Základní třída aktuálního objektu.  
  
### <a name="remarks"></a>Poznámky  
 Například v následujícím kódu:  
  
 [!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]  
  
 Všimněte si, že první položku v mapě COM musí být rozhraní pro objekt obsahující COM mapy. Proto nelze spustit vaší položek mapování COM s `COM_INTERFACE_ENTRY_CHAIN`, což způsobí, že COM mapu jiný objekt má proběhnout v místě, kde **COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** Zobrazí se v mapě COM tohoto objektu. Pokud chcete hledat mapy COM jiného objektu nejprve, přidejte záznam rozhraní pro **IUnknown** do mapy modelu COM, pak řetězu druhý objekt COM mapy. Příklad:  
  
 [!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]  
  
  
  
##  <a name="com_interface_entry_func"></a>  COM_INTERFACE_ENTRY_FUNC  
 Obecné mechanismus pro zapojení do knihovny ATL pro `QueryInterface` logiku.  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID rozhraní vystavené.  
  
 `dw`  
 [v] Parametr předaný prostřednictvím `func`.  
  
 `func`  
 [v] Ukazatel funkce, která vrátí `iid`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *iid* odpovídá IID rozhraní dotázána ohledně, pak se funkce určeného `func` je volána. Deklarace pro funkci musí být:  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 Při volání funkce `pv` odkazuje na třídu objektu. `riid` Parametr odkazuje na rozhraní, která je dotazována, `ppv` je ukazatel na umístění, kam by měl funkce ukládat má ukazatel na rozhraní a `dw` je parametr zadaný v položce. Funkce měli nastavit \* `ppv` k **NULL** a vrátit **E_NOINTERFACE** nebo **S_FALSE** Pokud zvolí nevrátí rozhraní. S **E_NOINTERFACE**, ukončí zpracování COM mapy. S **S_FALSE**, pokračuje zpracování mapy modelu COM, i když byl vrácen žádný ukazatel rozhraní. Pokud funkce vrátí hodnotu ukazatele rozhraní, by měla vrátit `S_OK`.  
  
  
  
##  <a name="com_interface_entry_func_blind"></a>  COM_INTERFACE_ENTRY_FUNC_BLIND  
 Stejné jako [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)kromě toho, že dotazování pro všechny identifikátory IID výsledkem volání `func`.  
  
```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```  
  
### <a name="parameters"></a>Parametry  
 `dw`  
 [v] Parametr předaný prostřednictvím `func`.  
  
 `func`  
 [v] Funkce, která je volána při zpracování této položky v mapě COM.  
  
### <a name="remarks"></a>Poznámky  
 Jakákoli chyba způsobí, že zpracování pokračovat na mapě COM. Pokud funkce vrátí hodnotu ukazatele rozhraní, by měla vrátit `S_OK`.  
  
  
##  <a name="com_interface_entry_nointerface"></a>  COM_INTERFACE_ENTRY_NOINTERFACE  
 Vrátí **E_NOINTERFACE** a ukončí zpracování mapy COM, když je dotazován specifikované rozhraní pro.  
  
```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Text, který slouží k vytvoření identifikátor rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro můžete zabránit, aby rozhraní používal v konkrétním případě. Například můžete vložit tento makro do vaší COM mapování těsně před `COM_INTERFACE_ENTRY_AGGREGATE_BLIND` zabránit předávaná na agregaci neznámé vnitřní dotaz na rozhraní.  
  
 Rozhraní IID bude vypočten připojením *x* k `IID_`. Například pokud *x* je `IPersistStorage`, bude IID `IID_IPersistStorage`.  
  
  