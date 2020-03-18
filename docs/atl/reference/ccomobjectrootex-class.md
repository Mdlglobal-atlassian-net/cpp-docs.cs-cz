---
title: CComObjectRootEx – třída
ms.date: 11/04/2016
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: 8fa4e7a035ded2e1a20dd278a5d54d40252e1958
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417927"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx – třída

Tato třída poskytuje metody pro zpracování správy počtu odkazů na objekty pro neagregované i agregované objekty.

## <a name="syntax"></a>Syntaxe

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parametry

*ThreadModel*<br/>
Třída, jejíž metody implementují požadovaný model vláken. Model vláken můžete explicitně zvolit nastavením *ThreadModel* na [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)nebo [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Můžete přijmout výchozí model vláken serveru nastavením *ThreadModel* na [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) nebo [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Konstruktor|
|[InternalAddRef –](#internaladdref)|Zvýší počet odkazů pro neagregovaný objekt.|
|[InternalRelease –](#internalrelease)|Sníží počet odkazů pro neagregovaný objekt.|
|[Získáte](#lock)|Pokud je model vlákna vícevláknový, získá vlastnictví objektu kritického oddílu.|
|[Uzamknout](#unlock)|Pokud je model vlákna vícevláknový, uvolňuje vlastnictví objektu kritické části.|

### <a name="ccomobjectrootbase-methods"></a>Metody CComObjectRootBase

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Přepište ve třídě, aby prováděla jakoukoli inicializaci potřebnou vaším objektem.|
|[FinalRelease](#finalrelease)|Přepište ve třídě, aby se provádělo jakékoli vyčištění vyžadované vaším objektem.|
|[OuterAddRef](#outeraddref)|Zvýší počet odkazů pro agregovaný objekt.|
|[OuterQueryInterface](#outerqueryinterface)|Deleguje na vnější `IUnknown` agregovaného objektu.|
|[OuterRelease](#outerrelease)|Sníží počet odkazů agregovaného objektu.|

### <a name="static-functions"></a>Statické funkce

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Deleguje `IUnknown` neagregovaného objektu.|
|[ObjectMain](#objectmain)|Volá se během inicializace modulu a ukončení pro odvozené třídy uvedené v mapě objektů.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_dwRef](#m_dwref)|V `m_pOuterUnknown`je součástí sjednocení. Používá se, pokud objekt není agregovaný tak, aby obsahoval počet odkazů `AddRef` a `Release`.|
|[m_pOuterUnknown](#m_pouterunknown)|V `m_dwRef`je součástí sjednocení. Používá se, když je objekt agregovaný tak, aby obsahoval ukazatel na vnější neznámý.|

## <a name="remarks"></a>Poznámky

`CComObjectRootEx` zpracovává správu počtu odkazů na objekty pro neagregované i agregované objekty. Obsahuje počet odkazů na objekty, pokud není objekt agregovaný, a drží ukazatel na vnější neznámý, pokud je objekt agregován. U agregovaných objektů lze `CComObjectRootEx` metody použít pro zpracování selhání vnitřního objektu a k ochraně vnějšího objektu před odstraněním, když jsou uvolněna vnitřní rozhraní nebo je odstraněn vnitřní objekt.

Třída, která implementuje Server COM, musí dědit z `CComObjectRootEx` nebo [třídy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Pokud definice třídy určuje makro [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) , knihovna ATL vytvoří instanci `CComPolyObject<CYourClass>` při volání `IClassFactory::CreateInstance`. Při vytváření se kontroluje hodnota vnějšího neznámého. Pokud je NULL, `IUnknown` je implementován pro neagregovaný objekt. Pokud vnější neznámý není NULL, `IUnknown` je implementován pro agregovaný objekt.

Pokud vaše třída neurčí makro DECLARE_POLY_AGGREGATABLE, knihovna ATL vytvoří instanci `CAggComObject<CYourClass>` pro agregované objekty nebo instanci `CComObject<CYourClass>` pro neagregované objekty.

Výhodou použití `CComPolyObject` je, že se vyhnete tomu, že v modulu máte `CComAggObject` a `CComObject`, aby bylo možné zpracovávat agregované a neagregované případy. Jeden objekt `CComPolyObject` zpracovává oba případy. Proto v modulu existují pouze jednu kopii vtable a jednu kopii funkcí. Pokud je tabulka vtable velká, může to podstatně snížit velikost modulu. Pokud je však tabulka vtable malá, může použití `CComPolyObject` mít za následek mírně větší velikost modulu, protože není optimalizována pro agregovaný nebo neagregovaný objekt, jak jsou `CComAggObject` a `CComObject`.

Pokud je objekt agregován, je [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) implementován pomocí `CComAggObject` nebo `CComPolyObject`. Tyto třídy deleguje `QueryInterface`, `AddRef`a `Release` volání `CComObjectRootEx``OuterQueryInterface`, `OuterAddRef`a `OuterRelease` k předání na vnější neznámý. Obvykle můžete přepsat `CComObjectRootEx::FinalConstruct` ve vaší třídě a vytvořit tak všechny agregované objekty a přepsat `CComObjectRootEx::FinalRelease` a uvolnit všechny agregované objekty.

Pokud objekt není agregovaný, `IUnknown` je implementováno pomocí `CComObject` nebo `CComPolyObject`. V takovém případě jsou volání `QueryInterface`, `AddRef`a `Release` delegována `CComObjectRootEx``InternalQueryInterface`, `InternalAddRef`a `InternalRelease` k provedení skutečných operací.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="ccomobjectrootex"></a>CComObjectRootEx:: CComObjectRootEx

Konstruktor inicializuje počet odkazů na 0.

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>CComObjectRootEx:: FinalConstruct

Tuto metodu můžete přepsat v odvozené třídě, abyste mohli provést jakoukoli inicializaci potřebnou pro váš objekt.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo jednu z hodnot standardní chyby HRESULT.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CComObjectRootEx::FinalConstruct` jednoduše vrátí S_OK.

Existují výhody pro inicializaci v `FinalConstruct` spíše než konstruktoru třídy:

- Z konstruktoru nelze vrátit stavový kód, ale můžete vrátit hodnotu HRESULT prostřednictvím návratové hodnoty `FinalConstruct`. Při vytváření objektů třídy pomocí standardního objektu pro vytváření tříd poskytovaných knihovnou ATL se tato návratová hodnota šíří zpátky na klienta modelu COM, což vám umožní poskytnout jim podrobné informace o chybě.

- Virtuální funkce nelze volat pomocí mechanismu virtuální funkce z konstruktoru třídy. Volání virtuální funkce z konstruktoru třídy má za následek staticky vyřešené volání funkce, jak je definováno v tomto okamžiku v hierarchii dědičnosti. Výsledkem volání čistě virtuálních funkcí je chyba linkeru.

   Vaše třída není nejvíce odvozenou třídou v hierarchii dědičnosti – spoléhá na odvozenou třídu poskytnutou knihovnou ATL k poskytnutí některých funkcí. Je velmi pravděpodobné, že vaše inicializace bude potřebovat použití funkcí poskytovaných touto třídou (to je určitě true, pokud objekty vaší třídy potřebují agregovat jiné objekty), ale konstruktor ve vaší třídě nemá žádný způsob, jak získat přístup k těmto funkcím. Kód konstrukce pro třídu je proveden před úplným sestavením nejvyšší odvozené třídy.

   Nicméně `FinalConstruct` je volána bezprostředně po úplném sestavení nejvyšší odvozené třídy, což vám umožňuje volat virtuální funkce a používat implementaci počítání odkazů poskytovanou knihovnou ATL.

### <a name="example"></a>Příklad

Obvykle přepište tuto metodu ve třídě odvozené z `CComObjectRootEx` pro vytvoření libovolných agregovaných objektů. Příklad:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Pokud se konstrukce nezdařila, můžete vrátit chybu. Můžete také použít [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) makra k ochraně vnějšího objektu před smazáním, pokud během vytváření, interní agregovaný objekt zvýší počet odkazů a pak sníží počet na 0.

Tady je typický způsob, jak vytvořit agregaci:

- Přidejte do objektu třídy ukazatel `IUnknown` a inicializujte ho v konstruktoru na hodnotu NULL.

- Přepište `FinalConstruct` pro vytvoření agregace.

- Použijte ukazatel `IUnknown`, který jste definovali jako parametr, do makra [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) .

- Přepište `FinalRelease` pro uvolnění ukazatele `IUnknown`.

##  <a name="finalrelease"></a>CComObjectRootEx:: FinalRelease

Tuto metodu můžete přepsat v odvozené třídě, aby se provádělo jakékoli vyčištění vyžadované pro váš objekt.

```
void FinalRelease();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CComObjectRootEx::FinalRelease` neprovede žádnou akci.

Provádění čištění v `FinalRelease` je vhodnější pro přidání kódu do destruktoru vaší třídy, protože objekt je stále plně sestaven v bodě, kde je volána `FinalRelease`. To umožňuje bezpečný přístup k metodám poskytovaným největší odvozenou třídou. To je důležité zejména pro uvolnění všech agregovaných objektů před odstraněním.

##  <a name="internaladdref"></a>CComObjectRootEx:: InternalAddRef –

Zvýší počet odkazů neagregovaného objektu o 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku a testování.

### <a name="remarks"></a>Poznámky

Pokud je model vlákna vícevláknový, používá se `InterlockedIncrement`, aby se zabránilo více než jednomu vláknu v změně počtu odkazů současně.

##  <a name="internalqueryinterface"></a>CComObjectRootEx:: InternalQueryInterface

Načte ukazatel na požadované rozhraní.

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*pThis*<br/>
pro Ukazatel na objekt, který obsahuje mapu COM rozhraní, které jsou vystaveny `QueryInterface`.

*pEntries*<br/>
pro Ukazatel na strukturu `_ATL_INTMAP_ENTRY`, která přistupuje k mapě dostupných rozhraní.

*identifikátor*<br/>
pro Identifikátor GUID požadovaného rozhraní

*ppvObject*<br/>
mimo Ukazatel na ukazatel rozhraní určený v *IID*nebo hodnotu null, pokud rozhraní nebylo nalezeno.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

`InternalQueryInterface` zpracovává pouze rozhraní v tabulce map modelu COM. Pokud je objekt agregovaný, `InternalQueryInterface` nedelegovat na vnější neznámou hodnotu. Do tabulky map COM můžete zadat rozhraní pomocí makra [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) nebo jedné z jeho variant.

##  <a name="internalrelease"></a>CComObjectRootEx:: InternalRelease –

Sníží počet odkazů neagregovaného objektu o 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění a ladění tato funkce vrací hodnotu, která může být užitečná pro diagnostiku nebo testování. Přesná hodnota, která je vrácena, závisí na mnoha faktorech, jako je například používaný operační systém a může nebo nemusí být počet odkazů.

### <a name="remarks"></a>Poznámky

Pokud je model vlákna vícevláknový, používá se `InterlockedDecrement`, aby se zabránilo více než jednomu vláknu v změně počtu odkazů současně.

##  <a name="lock"></a>CComObjectRootEx:: Lock

Pokud je model vlákna vícevláknový, tato metoda volá funkci Win32 API [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), která čeká, až vlákno převezme vlastnictví objektu kritického oddílu získaného prostřednictvím privátního datového členu.

```
void Lock();
```

### <a name="remarks"></a>Poznámky

Jakmile se dokončí chráněný kód, vlákno musí volat `Unlock` k uvolnění vlastnictví kritické části.

Pokud je model vlákna s jedním vláknem, tato metoda neprovede žádnou akci.

##  <a name="m_dwref"></a>CComObjectRootEx:: m_dwRef

Část sjednocení, která přistupuje k čtyřem bajtů paměti.

```
long m_dwRef;
```

### <a name="remarks"></a>Poznámky

V `m_pOuterUnknown`je součástí sjednocení:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Pokud objekt není agregovaný, je počet odkazů, ke kterým se přistupovalo pomocí `AddRef` a `Release`, uložen v `m_dwRef`. Pokud je objekt agregovaný, je ukazatel na vnější neznámý uložen v [m_pOuterUnknown](#m_pouterunknown).

##  <a name="m_pouterunknown"></a>CComObjectRootEx:: m_pOuterUnknown

Část sjednocení, která přistupuje k čtyřem bajtů paměti.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Poznámky

V `m_dwRef`je součástí sjednocení:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Pokud je objekt agregovaný, je ukazatel na vnější neznámý uložen v `m_pOuterUnknown`. Pokud objekt není agregovaný, je počet odkazů, ke kterým se přistupovalo pomocí `AddRef` a `Release`, uložen v [m_dwRef](#m_dwref).

##  <a name="objectmain"></a>CComObjectRootEx:: ObjectMain

Pro každou třídu uvedenou v mapě objektů je tato funkce volána jednou při inicializaci modulu a znovu po jeho ukončení.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parametry

*bStarting*<br/>
mimo Hodnota je TRUE, pokud je třída inicializována; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Hodnota parametru *bStarting* označuje, zda se modul inicializuje nebo ukončí. Výchozí implementace `ObjectMain` nedělá nic, ale tuto funkci můžete v třídě přepsat pro inicializaci nebo vyčištění prostředků, které chcete přidělit pro třídu. Všimněte si, že `ObjectMain` je volána před vyžádáním jakýchkoli instancí třídy.

`ObjectMain` se volá z vstupního bodu knihovny DLL, takže typ operace, kterou funkce vstupního bodu může provádět, je omezený. Další informace o těchto omezeních naleznete v tématu [knihovny DLL C++ a chování běhové knihovny jazyka Visual runtime](../../build/run-time-library-behavior.md) a [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>CComObjectRootEx:: OuterAddRef

Zvýší počet odkazů vnějšího neznámého prvku agregace.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku a testování.

##  <a name="outerqueryinterface"></a>CComObjectRootEx:: OuterQueryInterface

Načte nepřímý ukazatel na požadované rozhraní.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*identifikátor*<br/>
pro Identifikátor GUID požadovaného rozhraní

*ppvObject*<br/>
mimo Ukazatel na ukazatel rozhraní určený v *IID*nebo hodnotu null, pokud agregace nepodporuje rozhraní.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="outerrelease"></a>CComObjectRootEx:: OuterRelease

Sníží počet odkazů vnějšího neznámého prvku agregace.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění vždy vrátí hodnotu 0. V sestavení ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování.

##  <a name="unlock"></a>CComObjectRootEx:: Unlock

Pokud je model vlákna vícevláknový, tato metoda volá funkci Win32 API [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), která uvolňuje vlastnictví objektu kritického oddílu získaného prostřednictvím privátního datového členu.

```
void Unlock();
```

### <a name="remarks"></a>Poznámky

Pro získání vlastnictví vlákno musí volat `Lock`. Každé volání `Lock` vyžaduje odpovídající volání `Unlock` k uvolnění vlastnictví oddílu kritické.

Pokud je model vlákna s jedním vláknem, tato metoda neprovede žádnou akci.

## <a name="see-also"></a>Viz také

[CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject – třída](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
