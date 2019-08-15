---
title: Makra záznamů rozhraní COM
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
ms.openlocfilehash: 1e1674bad1164e640939d430a860beac7a6e4208
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496726"
---
# <a name="com_interface_entry-macros"></a>Makra COM_INTERFACE_ENTRY

Tato makra zadávají rozhraní objektu do své mapy modelu COM, aby k nim bylo možné přihlédnout pomocí `QueryInterface`. Pořadí záznamů v mapě modelu COM je pořadí, ve kterém bude během `QueryInterface`příkazu zkontrolováno porovnání identifikátoru IID.

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|Vloží rozhraní do mapy rozhraní modelu COM.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Pomocí tohoto makra lze rozlišit dvě větve dědičnosti.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Pomocí tohoto makra můžete zadat rozhraní do mapy modelu COM a zadat jeho identifikátor IID.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Stejné jako [COM_INTERFACE_ENTRY2](#com_interface_entry2), s výjimkou, že můžete zadat jiný identifikátor IID.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Když je rozhraní identifikované *identifikátorem IID* dotazováno na, `COM_INTERFACE_ENTRY_AGGREGATE` je předáno `punk`na.|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s tím rozdílem, že dotazování pro jakýkoli identifikátor IID má za následek předání dotazu do *punk*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s výjimkou případů, kdy *punk* má hodnotu null, automaticky vytvoří agregaci popsanou v *CLSID*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Stejné jako [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), s tím rozdílem, že dotazování pro jakýkoli identifikátor IID má za následek předání dotazu do *punk*a pokud *punk* je null, automatické vytváření agregace popsané *identifikátorem CLSID*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Způsobí, že program zavolá [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) při dotazování zadaného rozhraní.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Uloží data pro každou instanci specifická pro rozhraní.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Zpřístupňuje vaše nepřesná rozhraní.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Zpracuje mapu modelu COM základní třídy, pokud zpracování dosáhne této položky v mapě modelu COM.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Obecný mechanismus, který se připojí k `QueryInterface` Logic ATL.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Stejné jako [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), s tím rozdílem, že dotazování pro jakýkoli identifikátor IID má za následek volání funkce *Func*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Vrátí E_NOINTERFACE a ukončí zpracování mapy COM, pokud je zadané rozhraní dotazováno.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

## <a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

Vloží rozhraní do mapy rozhraní modelu COM.

### <a name="syntax"></a>Syntaxe

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
pro Název rozhraní, ze kterého je objekt třídy odvozen přímo.

### <a name="remarks"></a>Poznámky

Obvykle je to typ položky, který používáte nejčastěji.

### <a name="example"></a>Příklad

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

Pomocí tohoto makra lze rozlišit dvě větve dědičnosti.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Parametry

*x*<br/>
pro Název rozhraní, které chcete vystavit z vašeho objektu.

*x2*<br/>
pro Název větve dědičnosti, ze které je vystaveno *x* .

### <a name="remarks"></a>Poznámky

Například pokud odvozujete objekt třídy ze dvou duálních rozhraní, vystavíte `IDispatch` pomocí COM_INTERFACE_ENTRY2, `IDispatch` protože lze získat z jednoho z rozhraní.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

Pomocí tohoto makra můžete zadat rozhraní do mapy modelu COM a zadat jeho identifikátor IID.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor GUID vystaveného rozhraní

*x*<br/>
pro Název třídy, jejíž tabulka vtable bude vystavena jako rozhraní identifikované *identifikátorem IID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

Stejné jako [COM_INTERFACE_ENTRY2](#com_interface_entry2), s výjimkou, že můžete zadat jiný identifikátor IID.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor GUID, který zadáváte pro rozhraní.

*x*<br/>
pro Název rozhraní, ze kterého je objekt třídy odvozen přímo.

*x2*<br/>
pro Název druhého rozhraní, ze kterého je objekt třídy odvozen přímo.

##  <a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

Když je rozhraní identifikované *identifikátorem IID* dotazováno na, COM_INTERFACE_ENTRY_AGGREGATE se přepošle na *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor GUID rozhraní, na které se má dotazovat

*punk*<br/>
pro Název `IUnknown` ukazatele.

### <a name="remarks"></a>Poznámky

Předpokládá se, že parametr *punk* odkazuje na vnitřní neznámý objekt agregace nebo na hodnotu null. v takovém případě se položka ignoruje. Obvykle byste `CoCreate` měli agregovat v `FinalConstruct`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s tím rozdílem, že dotazování pro jakýkoli identifikátor IID má za následek předání dotazu do *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Parametry

*punk*<br/>
pro Název `IUnknown` ukazatele.

### <a name="remarks"></a>Poznámky

Pokud se dotaz rozhraní nedaří, zpracování mapování modelu COM pokračuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

Stejné jako [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), s výjimkou případů, kdy *punk* má hodnotu null, automaticky vytvoří agregaci popsanou v *CLSID*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor GUID rozhraní, na které se má dotazovat

*punk*<br/>
pro Název `IUnknown` ukazatele. Musí být členem třídy, která obsahuje mapu modelu COM.

*CLSID*<br/>
pro Identifikátor agregace, která bude vytvořena, pokud má *punk* hodnotu null.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Stejné jako [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), s tím rozdílem, že dotazování pro jakýkoli identifikátor IID má za následek předání dotazu do *punk*a pokud *punk* je null, automatické vytváření agregace popsané *identifikátorem CLSID*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Parametry

*punk*<br/>
pro Název `IUnknown` ukazatele. Musí být členem třídy, která obsahuje mapu modelu COM.

*CLSID*<br/>
pro Identifikátor agregace, která bude vytvořena, pokud má *punk* hodnotu null.

### <a name="remarks"></a>Poznámky

Pokud se dotaz rozhraní nedaří, zpracování mapování modelu COM pokračuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

Způsobí, že program zavolá [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) při dotazování zadaného rozhraní.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
pro Text použitý k vytvoření identifikátoru rozhraní

### <a name="remarks"></a>Poznámky

Identifikátor IID rozhraní bude vytvořen připojením *x* k `IID_`. Například pokud je `IPersistStorage`x, IID bude. `IID_IPersistStorage`

##  <a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Uloží data pro každou instanci specifická pro rozhraní.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor GUID nevypnutého rozhraní.

*x*<br/>
pro Název třídy, která implementuje rozhraní.

*punk*<br/>
pro Název `IUnknown` ukazatele. Musí být členem třídy, která obsahuje mapu modelu COM. By měl být v konstruktoru objektu třídy inicializován na hodnotu NULL.

### <a name="remarks"></a>Poznámky

Pokud rozhraní není použito, tím se sníží celková velikost instance objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

Zpřístupňuje vaše nepřesná rozhraní.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor GUID nevypnutého rozhraní.

*x*<br/>
pro Název třídy, která implementuje rozhraní.

### <a name="remarks"></a>Poznámky

Rozhraní pro odložení je implementováno jako samostatný objekt, jehož instance je vytvořena pokaždé, když je na něj dotazováno rozhraní, které představuje. Obvykle sestavíte rozhraní jako nejenom v případě, že se rozhraní používá zřídka, protože to ukládá ukazatel vtable do každé instance hlavního objektu. Trhlina se odstraní, když se jejich počet odkazů stane nula. Třída implementující trhlinu by měla být odvozena z `CComTearOffObjectBase` a mít vlastní mapu com.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

Zpracuje mapu modelu COM základní třídy, pokud zpracování dosáhne této položky v mapě modelu COM.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Parametry

*NázevTřídy*<br/>
pro Základní třída aktuálního objektu.

### <a name="remarks"></a>Poznámky

Například v následujícím kódu:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Všimněte si, že první položka v mapě modelu COM musí být rozhraní objektu, který obsahuje mapu modelu COM. Proto nelze spustit položky mapování modelu COM pomocí COM_INTERFACE_ENTRY_CHAIN, což způsobí, že mapa modelu COM jiného objektu bude prohledána v místě, kde se zobrazí **COM_INTERFACE_ENTRY_CHAIN (** `COtherObject` **)** v mapě objektu com. Pokud chcete nejprve vyhledat mapu modelu COM jiného objektu, přidejte položku rozhraní pro `IUnknown` mapu modelu COM a potom proveďte zřetězení mapy modelu COM jiného objektu. Příklad:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

Obecný mechanismus, který se připojí k `QueryInterface` Logic ATL.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor GUID vystaveného rozhraní

*dw*<br/>
pro Parametr předaný funkci *Func*.

*func*<br/>
pro Ukazatel funkce, který bude vracet *identifikátor IID*.

### <a name="remarks"></a>Poznámky

Pokud *IID* odpovídá IID rozhraní, pro které bylo dotazováno, pak je volána funkce určená funkcí *Func* . Deklarace funkce by měla být:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Když je vaše funkce volána, `pv` odkazuje na objekt třídy. Parametr *riid* odkazuje na rozhraní, na které se dotazuje, `ppv` je ukazatel na umístění, kde by měla funkce Uložit ukazatel na rozhraní a *DW* je parametr, který jste zadali v položce. Funkce by měla být \* nastavena `ppv` na hodnotu null a vracet E_NOINTERFACE nebo S_FALSE, pokud se rozhodne, že nevrátí rozhraní. S E_NOINTERFACE končí zpracování mapy modelu COM. Pomocí S_FALSE pokračuje zpracování mapy COM i v případě, že nebyl vrácen žádný ukazatel rozhraní. Pokud funkce vrátí ukazatel rozhraní, měla by vrátit S_OK.

##  <a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

Stejné jako [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), s tím rozdílem, že dotazování pro jakýkoli identifikátor IID má za následek volání funkce *Func*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Parametry

*dw*<br/>
pro Parametr předaný funkci *Func*.

*func*<br/>
pro Funkce, která se volá při zpracování této položky v mapě modelu COM.

### <a name="remarks"></a>Poznámky

Jakákoli chyba způsobí, že zpracování bude pokračovat na mapě modelu COM. Pokud funkce vrátí ukazatel rozhraní, měla by vrátit S_OK.

##  <a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

Vrátí E_NOINTERFACE a ukončí zpracování mapy COM, pokud je zadané rozhraní dotazováno.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
pro Text použitý k vytvoření identifikátoru rozhraní

### <a name="remarks"></a>Poznámky

Toto makro můžete použít k zabránění použití rozhraní v konkrétním případě. Například můžete vložit toto makro do mapy modelu COM přímo před COM_INTERFACE_ENTRY_AGGREGATE_BLIND, aby se zabránilo tomu, aby dotaz na rozhraní bylo přesměrován na vnitřní neznámý objekt agregace.

Identifikátor IID rozhraní bude vytvořen připojením *x* k `IID_`. Například pokud je `IPersistStorage`x, IID bude. `IID_IPersistStorage`
