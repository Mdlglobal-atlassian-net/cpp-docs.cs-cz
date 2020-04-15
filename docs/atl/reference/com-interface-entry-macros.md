---
title: Makra pro zadávání rozhraní COM
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
ms.openlocfilehash: bb7498f639f463290a4a6593ef7c0fbac09b539b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326681"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY makra

Tato makra zadávají rozhraní objektu do mapy com, aby `QueryInterface`k nim měl přístup aplikace . Pořadí položek v mapě COM je pořadí rozhraní budou kontrolovány pro odpovídající `QueryInterface`IID během .

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|Zadá rozhraní do mapy rozhraní COM.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Toto makro slouží k rozdvojení dvou větví dědičnosti.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Toto makro slouží k zadání rozhraní do mapy com a určení jeho IID.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Stejné jako [COM_INTERFACE_ENTRY2](#com_interface_entry2), s výjimkou můžete zadat jiné IID.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Pokud je dotazováno rozhraní identifikované *iid,* `COM_INTERFACE_ENTRY_AGGREGATE` předávají se na . `punk`|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s tím rozdílem, že dotazování pro všechny IID má za následek předávání dotazu na *punk*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s výjimkou, pokud *punk* je NULL, automaticky vytvoří agregaci popsanou *clsid*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Stejné jako [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), s tím rozdílem, že dotazování pro všechny IID má za následek předání dotazu *punku*, a *pokud* punk je NULL, automaticky vytváří agregaci popsanou *clsid*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Způsobí, že program volat [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) při dotazovaném rozhraní zadané.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Uloží data specifická pro rozhraní pro každou instanci.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Odhaluje rozhraní odtržení.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Zpracuje mapu COM základní třídy, když zpracování dosáhne této položky v mapě COM.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Obecný mechanismus pro hákování do `QueryInterface` logiky ATL.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Stejné jako [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), s tím rozdílem, že dotazování na jakékoli IID má za následek volání *func*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Vrátí E_NOINTERFACE a ukončí zpracování mapy COM při dotazování zadaného rozhraní.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="com_interface_entry"></a><a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

Zadá rozhraní do mapy rozhraní COM.

### <a name="syntax"></a>Syntaxe

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název rozhraní objektu třídy je odvozen přímo.

### <a name="remarks"></a>Poznámky

Obvykle se jedná o typ položky, který používáte nejčastěji.

### <a name="example"></a>Příklad

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="com_interface_entry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

Toto makro slouží k rozdvojení dvou větví dědičnosti.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název rozhraní, které chcete vystavit z objektu.

*x2*<br/>
[v] Název větve dědičnosti, ze které je vystaven *x.*

### <a name="remarks"></a>Poznámky

Například pokud odvodit objekt třídy ze `IDispatch` dvou duálních rozhraní, vystavit pomocí COM_INTERFACE_ENTRY2 protože `IDispatch` lze získat z jednoho z rozhraní.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

## <a name="com_interface_entry_iid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

Toto makro slouží k zadání rozhraní do mapy com a určení jeho IID.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Guid rozhraní vystaveny.

*X*<br/>
[v] Název třídy, jejíž vtable bude vystaven jako rozhraní označené *iid*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

## <a name="com_interface_entry2_iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

Stejné jako [COM_INTERFACE_ENTRY2](#com_interface_entry2), s výjimkou můžete zadat jiné IID.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor GUID, který pro rozhraní zadáváte.

*X*<br/>
[v] Název rozhraní, které objekt třídy je odvozen přímo.

*x2*<br/>
[v] Název druhé rozhraní, které objekt třídy je odvozen přímo.

## <a name="com_interface_entry_aggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

Pokud je dotazováno rozhraní identifikované *iid,* COM_INTERFACE_ENTRY_AGGREGATE předává *punku*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Guid rozhraní dotazované.

*Punk*<br/>
[v] Název `IUnknown` ukazatele.

### <a name="remarks"></a>Poznámky

Předpokládá se, že *punkový* parametr přejde na vnitřní neznámou agregátu nebo null, v takovém případě je položka ignorována. Obvykle by `CoCreate` agregaci `FinalConstruct`v .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

## <a name="com_interface_entry_aggregate_blind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s tím rozdílem, že dotazování pro všechny IID má za následek předávání dotazu na *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[v] Název `IUnknown` ukazatele.

### <a name="remarks"></a>Poznámky

Pokud se dotaz na rozhraní nezdaří, zpracování mapy COM pokračuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

## <a name="com_interface_entry_autoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s výjimkou, pokud *punk* je NULL, automaticky vytvoří agregaci popsanou *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Guid rozhraní dotazované.

*Punk*<br/>
[v] Název `IUnknown` ukazatele. Musí být členem třídy obsahující mapu COM.

*Identifikátor clsid*<br/>
[v] Identifikátor agregátu, který bude *vytvořen,* pokud punk je NULL.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

## <a name="com_interface_entry_autoaggregate_blind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Stejné jako [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), s tím rozdílem, že dotazování pro všechny IID má za následek předání dotazu *punku*, a *pokud* punk je NULL, automaticky vytváří agregaci popsanou *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[v] Název `IUnknown` ukazatele. Musí být členem třídy obsahující mapu COM.

*Identifikátor clsid*<br/>
[v] Identifikátor agregátu, který bude *vytvořen,* pokud punk je NULL.

### <a name="remarks"></a>Poznámky

Pokud se dotaz na rozhraní nezdaří, zpracování mapy COM pokračuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

## <a name="com_interface_entry_break"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

Způsobí, že program volat [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) při dotazovaném rozhraní zadané.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Text použitý k vytvoření identifikátoru rozhraní.

### <a name="remarks"></a>Poznámky

IID rozhraní bude vytvořena připojením *x* x `IID_`k . Například pokud *x* x `IPersistStorage`je , IID bude `IID_IPersistStorage`.

## <a name="com_interface_entry_cached_tear_off"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Uloží data specifická pro rozhraní pro každou instanci.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor GUID rozhraní odtržení.

*X*<br/>
[v] Název třídy implementující rozhraní.

*Punk*<br/>
[v] Název `IUnknown` ukazatele. Musí být členem třídy obsahující mapu COM. By měla být inicializována na HODNOTU NULL v konstruktoru objektu třídy.

### <a name="remarks"></a>Poznámky

Pokud rozhraní není použit, tím se sníží celková velikost instance objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

## <a name="com_interface_entry_tear_off"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

Odhaluje rozhraní odtržení.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor GUID rozhraní odtržení.

*X*<br/>
[v] Název třídy implementující rozhraní.

### <a name="remarks"></a>Poznámky

Rozhraní odtržení je implementováno jako samostatný objekt, který je vytvořena instance pokaždé, když rozhraní, které představuje je dotazován. Obvykle vytvoříte rozhraní jako odtržení, pokud rozhraní se používá zřídka, protože to uloží vtable ukazatel v každé instanci hlavního objektu. Odtržení se odstraní, když se počet odkazů stane nulou. Třída implementující odtržení by měla být `CComTearOffObjectBase` odvozena od a mít vlastní mapu COM.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="com_interface_entry_chain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

Zpracuje mapu COM základní třídy, když zpracování dosáhne této položky v mapě COM.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
[v] Základní třída aktuálního objektu.

### <a name="remarks"></a>Poznámky

Například v následujícím kódu:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Všimněte si, že první položka v mapě COM musí být rozhraní na objekt obsahující mapu COM. Proto nelze spustit položky mapy COM s COM_INTERFACE_ENTRY_CHAIN, což způsobí, že mapa COM jiného objektu, které mají být prohledány v místě, kde **COM_INTERFACE_ENTRY_CHAIN(**`COtherObject`**)** se zobrazí v mapě COM objektu. Chcete-li nejprve prohledat mapu COM jiného objektu, přidejte položku rozhraní pro `IUnknown` daný objekt a potom zřetězení mapy COM druhého objektu. Příklad:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

## <a name="com_interface_entry_func"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

Obecný mechanismus pro hákování do `QueryInterface` logiky ATL.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Guid rozhraní vystaveny.

*Dw*<br/>
[v] Parametr prošel do *func*.

*func*<br/>
[v] Ukazatel funkce, který vrátí *iid*.

### <a name="remarks"></a>Poznámky

Pokud *iid* odpovídá IID rozhraní dotazované pro, pak se nazývá funkce určené *func.* Prohlášení pro funkci by mělo být:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Když je vaše `pv` funkce volána, odkazuje na objekt třídy. *Riid* Parametr odkazuje na rozhraní dotazován, `ppv` je ukazatel na umístění, kde by měla funkce uložit ukazatel na rozhraní a *dw* je parametr, který jste zadali v položce. Funkce by \* `ppv` měla být nastavena na hodnotu NULL a vrátit E_NOINTERFACE nebo S_FALSE pokud se rozhodne nevracet rozhraní. Při E_NOINTERFACE bude zpracování mapy COM ukončeno. Při S_FALSE pokračuje zpracování mapy COM, i když nebyl vrácen žádný ukazatel rozhraní. Pokud funkce vrátí ukazatel rozhraní, by měla vrátit S_OK.

## <a name="com_interface_entry_func_blind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

Stejné jako [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), s tím rozdílem, že dotazování na jakékoli IID má za následek volání *func*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Parametry

*Dw*<br/>
[v] Parametr prošel do *func*.

*func*<br/>
[v] Funkce, která je volána při zpracování této položky v mapě COM.

### <a name="remarks"></a>Poznámky

Jakékoli selhání způsobí, že zpracování bude pokračovat na mapě COM. Pokud funkce vrátí ukazatel rozhraní, by měla vrátit S_OK.

## <a name="com_interface_entry_nointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

Vrátí E_NOINTERFACE a ukončí zpracování mapy COM při dotazování zadaného rozhraní.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Text použitý k vytvoření identifikátoru rozhraní.

### <a name="remarks"></a>Poznámky

Toto makro můžete použít k zabránění použití rozhraní v konkrétním případě. Toto makro můžete například vložit do mapy com těsně před COM_INTERFACE_ENTRY_AGGREGATE_BLIND, abyste zabránili předání dotazu na rozhraní do vnitřníneznámy agregátu.

IID rozhraní bude vytvořena připojením *x* x `IID_`k . Například pokud *x* x `IPersistStorage`je , IID bude `IID_IPersistStorage`.
