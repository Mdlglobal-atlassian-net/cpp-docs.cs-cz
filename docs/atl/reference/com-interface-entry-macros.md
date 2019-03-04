---
title: Makra COM Interface Entry
ms.date: 03/28/2017
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
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
ms.openlocfilehash: ed2b8445a0f13b82338d2904d43fd17688d05b9e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276374"
---
# <a name="cominterfaceentry-macros"></a>COM_INTERFACE_ENTRY – makra

Tato makra zadejte rozhraní objektu do jeho mapy modelu COM, tak, aby k nim může přistupovat pomocí `QueryInterface`. Pořadí položek v objektu map COM je rozhraní pořadí bude sloužit k odpovídající IID během `QueryInterface`.

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|Zadá do objektu map rozhraní COM rozhraní.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Použijte toto makro k rozlišení dvou větví dědičnosti.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Pomocí tohoto makra zadejte rozhraní do mapy modelu COM a jeho IID.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Stejné jako [COM_INTERFACE_ENTRY2](#com_interface_entry2)s výjimkou případů, můžete určit jiný identifikátor IID.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Když rozhraní identifikovaný *iid* dotaz na, `COM_INTERFACE_ENTRY_AGGREGATE` předá `punk`.|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s tím rozdílem, že dotazování pro libovolný identifikátor IID výsledkem předávání dotaz tak, aby *punk*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), kromě případu, kdy *punk* má hodnotu NULL, automaticky vytvoří agregace popsaného *clsid*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Stejné jako [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), s tím rozdílem, že dotazování pro libovolný identifikátor IID výsledkem předávání dotaz tak, aby *punk*a pokud *punk* má hodnotu NULL, se automaticky vytvoří agregace popsaného *clsid*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Způsobí, že program k volání [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297) při dotázali zadané rozhraní.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Ukládá data specifická pro rozhraní pro každou instanci.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Zpřístupňuje odtržených rozhraní.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Zpracovává mapu COM základní třídy tuto položku v objektu map COM dosáhne zpracování.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Obecný mechanismus pro zapojení do ATL `QueryInterface` logiku.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Stejné jako [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), s tím rozdílem, že dotazování pro libovolný identifikátor IID výsledkem volání *func*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Vrátí E_NOINTERFACE a ukončí zpracování mapy modelu COM, když zadané rozhraní se dotazují pro.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

## <a name="com_interface_entry"></a> COM_INTERFACE_ENTRY

Zadá do objektu map rozhraní COM rozhraní.

### <a name="syntax"></a>Syntaxe

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Název rozhraní, které objekt třídy přímo odvozena.

### <a name="remarks"></a>Poznámky

Obvykle je to typ položky, které nejčastěji používáte.

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

Použijte toto makro k rozlišení dvou větví dědičnosti.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Název rozhraní, které chcete zpřístupnit z objektu.

*x2*<br/>
[in] Název větve dědičnosti, ze kterého *x* je přístupný.

### <a name="remarks"></a>Poznámky

Například pokud odvozujete objekt třídy ze dvou duální rozhraní, zpřístupníte `IDispatch` pomocí COM_INTERFACE_ENTRY2 od `IDispatch` můžete získat jednu rozhraní.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>  COM_INTERFACE_ENTRY_IID

Pomocí tohoto makra zadejte rozhraní do mapy modelu COM a jeho IID.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
[in] Identifikátor GUID rozhraní vystavené.

*x*<br/>
[in] Název třídy, jejíž vtable se zveřejní jako rozhraní identifikovaný *iid*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>  COM_INTERFACE_ENTRY2_IID

Stejné jako [COM_INTERFACE_ENTRY2](#com_interface_entry2)s výjimkou případů, můžete určit jiný identifikátor IID.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
[in] Identifikátor GUID, které zadáváte pro rozhraní.

*x*<br/>
[in] Název rozhraní, které objekt třídy přímo odvozena.

*x2*<br/>
[in] Název druhého rozhraní, které objekt třídy přímo odvozena.

##  <a name="com_interface_entry_aggregate"></a>  COM_INTERFACE_ENTRY_AGGREGATE

Když rozhraní identifikovaný *iid* je dotazován pro COM_INTERFACE_ENTRY_AGGREGATE předá *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
[in] Identifikátor GUID rozhraní pro dotazování.

*punk*<br/>
[in] Název `IUnknown` ukazatele.

### <a name="remarks"></a>Poznámky

*Punk* parametr se předpokládá, že tak, aby odkazoval na vnitřní Neznámý agregace nebo na hodnotu NULL, v takovém případě položka je ignorována. Obvykle by `CoCreate` agregační funkci v `FinalConstruct`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>  COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s tím rozdílem, že dotazování pro libovolný identifikátor IID výsledkem předávání dotaz tak, aby *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Parametry

*punk*<br/>
[in] Název `IUnknown` ukazatele.

### <a name="remarks"></a>Poznámky

Pokud dotaz rozhraní nezdaří, bude pokračovat zpracování COM map.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE

Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), kromě případu, kdy *punk* má hodnotu NULL, automaticky vytvoří agregace popsaného *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
[in] Identifikátor GUID rozhraní pro dotazování.

*punk*<br/>
[in] Název `IUnknown` ukazatele. Musíte být členem třídy obsahující mapy modelu COM.

*clsid*<br/>
[in] Identifikátor agregace, který se vytvoří, pokud *punk* má hodnotu NULL.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Stejné jako [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), s tím rozdílem, že dotazování pro libovolný identifikátor IID výsledkem předávání dotaz tak, aby *punk*a pokud *punk* má hodnotu NULL, se automaticky vytvoří agregace popsaného *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Parametry

*punk*<br/>
[in] Název `IUnknown` ukazatele. Musíte být členem třídy obsahující mapy modelu COM.

*clsid*<br/>
[in] Identifikátor agregace, který se vytvoří, pokud *punk* má hodnotu NULL.

### <a name="remarks"></a>Poznámky

Pokud dotaz rozhraní nezdaří, bude pokračovat zpracování COM map.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>  COM_INTERFACE_ENTRY_BREAK

Způsobí, že program k volání [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297) při dotázali zadané rozhraní.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Text použitý k vytvoření identifikátoru rozhraní.

### <a name="remarks"></a>Poznámky

Rozhraní IID částka se vypočte připojením *x* k `IID_`. Například pokud *x* je `IPersistStorage`, bude IID `IID_IPersistStorage`.

##  <a name="com_interface_entry_cached_tear_off"></a>  COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Ukládá data specifická pro rozhraní pro každou instanci.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
[in] Identifikátor GUID odtržených rozhraní.

*x*<br/>
[in] Název třídy implementující rozhraní.

*punk*<br/>
[in] Název `IUnknown` ukazatele. Musíte být členem třídy obsahující mapy modelu COM. By měl být inicializována na hodnotu NULL v konstruktoru objektu třídy.

### <a name="remarks"></a>Poznámky

Pokud se nepoužívá rozhraní, to snižuje celkové velikosti instance objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>  COM_INTERFACE_ENTRY_TEAR_OFF

Zpřístupňuje odtržených rozhraní.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
[in] Identifikátor GUID odtržených rozhraní.

*x*<br/>
[in] Název třídy implementující rozhraní.

### <a name="remarks"></a>Poznámky

Rozhraní s odnímatelnými nabídkami je implementován jako samostatný objekt, který je vytvořena instance pokaždé, když se rozhraní představuje se dotazují pro. Obvykle vytvoříte rozhraní jako odnímatelnými nabídkami Pokud rozhraní se používá jen občas, protože to v každé instanci hlavním objektem ukládá ukazatel vtable. Odtrhnout se odstraní při jeho počet odkazů klesne na nulu. Třída implementace odtrhnout by měl být odvozen od `CComTearOffObjectBase` a mají svůj vlastní mapy modelu COM.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>  COM_INTERFACE_ENTRY_CHAIN

Zpracovává mapu COM základní třídy tuto položku v objektu map COM dosáhne zpracování.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Parametry

*classname*<br/>
[in] Základní třída aktuálního objektu.

### <a name="remarks"></a>Poznámky

Například v následujícím kódu:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Všimněte si, že první položka v objektu map COM musí být rozhraní na objekt obsahující mapy modelu COM. Proto nelze spustit zadané mapy modelu COM s COM_INTERFACE_ENTRY_CHAIN, což způsobí, že mapy modelu COM z jiného objektu pro hledání v okamžiku, kdy **COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** se zobrazí váš objekt modelu COM mapě. Pokud budete chtít nejprve hledejte mapy modelu COM z jiného objektu, přidejte záznam rozhraní pro `IUnknown` do mapy modelu COM, pak zřetězit jiný objekt modelu COM mapy. Příklad:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>  COM_INTERFACE_ENTRY_FUNC

Obecný mechanismus pro zapojení do ATL `QueryInterface` logiku.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
[in] Identifikátor GUID rozhraní vystavené.

*dw*<br/>
[in] Parametr předaný prostřednictvím *func*.

*Func*<br/>
[in] Ukazatel funkce, která vrátí *iid*.

### <a name="remarks"></a>Poznámky

Pokud *iid* odpovídá identifikátor IID rozhraní pro dotazování a pak funkci zadanou na základě *func* je volána. Deklarace funkce by měla být:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Při volání funkce `pv` odkazuje na objekt třídy. *Riid* parametr odkazuje na rozhraní, která je dotazována, `ppv` je ukazatel na umístění, kam by měla funkce ukládat ukazatel na rozhraní a *dw* je tento parametr je zadané v položce. Funkce by měl nastavit \* `ppv` na hodnotu NULL a vrácení E_NOINTERFACE nebo S_FALSE, je-li zvolí nevrátí rozhraní. S E_NOINTERFACE ukončí zpracování map COM. S S_FALSE zpracování map COM pokračuje, i když byl vrácen žádný ukazatel rozhraní. Pokud funkce vrátí ukazatel rozhraní, měla by vrátit hodnotu S_OK.

##  <a name="com_interface_entry_func_blind"></a>  COM_INTERFACE_ENTRY_FUNC_BLIND

Stejné jako [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), s tím rozdílem, že dotazování pro libovolný identifikátor IID výsledkem volání *func*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Parametry

*dw*<br/>
[in] Parametr předaný prostřednictvím *func*.

*Func*<br/>
[in] Funkce, která je volána při zpracování této položky v objektu map COM.

### <a name="remarks"></a>Poznámky

Jakékoli neúspěchy způsobí, že zpracování pokračovat na mapě COM. Pokud funkce vrátí ukazatel rozhraní, měla by vrátit hodnotu S_OK.

##  <a name="com_interface_entry_nointerface"></a>  COM_INTERFACE_ENTRY_NOINTERFACE

Vrátí E_NOINTERFACE a ukončí zpracování mapy modelu COM, když zadané rozhraní se dotazují pro.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Text použitý k vytvoření identifikátoru rozhraní.

### <a name="remarks"></a>Poznámky

Aby se zabránilo rozhraní z používání v konkrétním případě můžete použít toto makro. Například můžete vložit toto makro do mapy modelu COM. bezprostředně před COM_INTERFACE_ENTRY_AGGREGATE_BLIND zabránit předávaná neznámé vnitřní agregační dotaz na rozhraní.

Rozhraní IID částka se vypočte připojením *x* k `IID_`. Například pokud *x* je `IPersistStorage`, bude IID `IID_IPersistStorage`.
