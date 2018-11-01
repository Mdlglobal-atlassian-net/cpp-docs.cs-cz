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
ms.openlocfilehash: 63547405791f7f0391138dd2d23020c62c8a4a28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655803"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx – třída

Tato třída poskytuje metody pro zpracování správy referenční počet objektů pro neagregovaná a agregované objekty.

## <a name="syntax"></a>Syntaxe

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parametry

*ThreadModel*<br/>
Třídy, jejíž metody implementovat požadovaného modelu vlákna. Můžete explicitně nastavit model vláken nastavením *ThreadModel* k [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), nebo [ Ccommultithreadmodelnocs –](../../atl/reference/ccommultithreadmodelnocs-class.md). Model na server výchozí vlákno může přijmout tak, že nastavíte *ThreadModel* k [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) nebo [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Konstruktor|
|[Internaladdref –](#internaladdref)|Zvýší počet odkazů pro neagregovaná objekt.|
|[Internalrelease –](#internalrelease)|Sníží počet referenční pro neagregovaná objekt.|
|[Zámek](#lock)|Pokud je model vláken s více vlákny, nezíská vlastnictví objektu kritický oddíl.|
|[Odemknutí](#unlock)|Pokud je model vláken s více vlákny, uvolní vlastnictví objektu kritický oddíl.|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase metody

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Přepsání ve své třídě pro udělat všechny inicializace, vyžaduje váš objekt.|
|[FinalRelease](#finalrelease)|Přepište ve třídě provádět vyčištění vyžadované objektu.|
|[OuterAddRef](#outeraddref)|Zvýší počet odkazů pro agregovaného objektu.|
|[OuterQueryInterface](#outerqueryinterface)|Delegáty pro vnější `IUnknown` agregované objektu.|
|[OuterRelease](#outerrelease)|Sníží počet referenční pro agregovaného objektu.|

### <a name="static-functions"></a>Statické funkce

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Deleguje se do `IUnknown` neagregovaná objektu.|
|[ObjectMain](#objectmain)|Volané při inicializaci modulu a ukončení pro odvozených tříd uvedených v mapě objektů.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_dwRef](#m_dwref)|S `m_pOuterUnknown`, část sjednocení. Použito pro objekt není agregovaný pro uložení počet odkazů `AddRef` a `Release`.|
|[m_pOuterUnknown](#m_pouterunknown)|S `m_dwRef`, část sjednocení. Použít, pokud objekt je agregován pro uchování ukazatele na vnější neznámá.|

## <a name="remarks"></a>Poznámky

`CComObjectRootEx` zpracovává správy referenční počet objektů pro neagregovaná a agregované objekty. Obsahuje referenční počet objektů, pokud objekt není agregovaný a drží ukazatel vnější neznámá, pokud je agregovaný objekt. Pro agregované objekty `CComObjectRootEx` metody lze použít k vyřešení selhání vnitřní objekt k vytvoření a odstranění k ochraně vnější objekt před odstraněním vydáním vnitřní rozhraní nebo vnitřní objekt.

Třída, která implementuje COM server musí dědit z `CComObjectRootEx` nebo [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md).

Pokud vaše definice třídy určuje [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) makra ATL vytvoří instanci `CComPolyObject<CYourClass>` při `IClassFactory::CreateInstance` je volána. Při vytváření se kontroluje hodnota vnější neznámá. Pokud má hodnotu NULL, `IUnknown` je implementován pro neagregovaná objektu. Pokud není NULL, vnější Neznámá `IUnknown` je implementován pro agregovaného objektu.

Pokud vaše třída neurčuje – makro DECLARE_POLY_AGGREGATABLE, ATL vytvoří instanci `CAggComObject<CYourClass>` agregovaných objektů nebo instanci `CComObject<CYourClass>` pro neagregovaná objekty.

Výhodou použití `CComPolyObject` je, že se vyhnete nutnosti obě `CComAggObject` a `CComObject` v modulu pro zpracování agregované a neagregovaná případech. Jediný `CComPolyObject` objekt zpracovává obou případech. Proto pouze jednu kopii tabulku vtable a jedna kopie funkce existovat v modulu. Pokud je vaše vtable velký, to může výrazně zkrátit velikost vašeho modulu. Nicméně pokud je vaše vtable malá, pomocí `CComPolyObject` může vést o něco větší velikost modulu, protože není optimalizován pro objekt agregována nebo neagregovaná jsou `CComAggObject` a `CComObject`.

Pokud objekt je agregován, [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) je implementováno `CComAggObject` nebo `CComPolyObject`. Tyto třídy delegáta `QueryInterface`, `AddRef`, a `Release` volání `CComObjectRootEx`společnosti `OuterQueryInterface`, `OuterAddRef`, a `OuterRelease` předat vnější neznámá. Obvykle je přepsat `CComObjectRootEx::FinalConstruct` ve své třídě pro vytvoření jakýchkoli agregovaných objektů a přepsání `CComObjectRootEx::FinalRelease` uvolnit všechny agregované objekty.

Pokud není agregovaný objekt, `IUnknown` je implementováno `CComObject` nebo `CComPolyObject`. V takovém případě volání `QueryInterface`, `AddRef`, a `Release` se deleguje na `CComObjectRootEx`společnosti `InternalQueryInterface`, `InternalAddRef`, a `InternalRelease` k provedení vlastní operace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx

Konstruktor inicializuje počet odkazů na hodnotu 0.

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct

Potlačí tuto metodu ve vaší odvozené třídy za účelem udělat všechny inicializace, vyžaduje se pro objekt.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK na úspěch nebo jednu standardní chybu hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CComObjectRootEx::FinalConstruct` jednoduše vrátí hodnotu S_OK.

Existují výhody provedení inicializace v `FinalConstruct` namísto konstruktoru třídy:

- Nelze vrátit stavový kód z konstruktoru, ale můžete se vrátit HRESULT prostřednictvím `FinalConstruct`jeho návratovou hodnotu. Při vytváření objektů třídy pomocí standardní třídu výroby pomocí knihovny ATL, tento návratová hodnota se šíří zpět k klient modelu COM, abyste mohli poskytnout podrobné informace o chybě.

- Nelze volat virtuální funkce pomocí mechanismu virtuální funkce z konstruktoru třídy. Volání virtuální funkce z konstruktoru třídy, výsledkem je staticky řešeného volání funkce, jak jsou definovány v daném okamžiku v hierarchii dědičnosti. Volání čistě virtuální funkce má za následek chyby linkeru.

   Vaše třída není nejvíce odvozené třídy v hierarchii dědičnosti, spoléhá na odvozenou třídu poskytnutých ATL poskytnout některé ze svých funkcí. Je dobré pravděpodobné, že inicializace potřebovat k funkcím, které poskytuje tuto třídu (to platí jistě při objekty třídy potřeba agregovat jiné objekty), ale nemá žádný způsob, jak přistupovat k těm funkcím konstruktoru ve své třídě. Konstrukce kódu pro třídu je spuštěn před úplném nejvíce odvozené třídy.

   Nicméně `FinalConstruct` je volána ihned poté, co nejvíce odvozené třídy úplném díky tomu můžete volat virtuální funkce a použít implementaci počítání odkazů poskytované ATL.

### <a name="example"></a>Příklad

Obvykle, přepište tuto metodu v třídě odvozené z `CComObjectRootEx` vytvořit všechny agregované objekty. Příklad:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Pokud procesu vytváření se nezdaří, můžete se vrátit k chybě. Můžete také použít makra [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) k ochraně před vrácení vnější objekt odstranit, pokud během vytváření, interní agregovaného objektu zvýší počet odkazů pak dekrementuje počet na hodnotu 0.

Zde je typický způsob, jak vytvořit agregace:

- Přidat `IUnknown` ukazatel na třídu objektu a inicializovat na hodnotu NULL v konstruktoru.

- Přepsat `FinalConstruct` vytvoření agregace.

- Použití `IUnknown` ukazatele, které jste definovali jako parametr [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) – makro.

- Přepsat `FinalRelease` uvolnit `IUnknown` ukazatele.

##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease

Potlačí tuto metodu v odvozené třídy provádět všechny požadované čištění pro váš objekt.

```
void FinalRelease();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CComObjectRootEx::FinalRelease` nemá žádný účinek.

Probíhá čištění v `FinalRelease` je vhodnější než přidání kódu destruktoru své třídy, protože objekt je stále plně sestaveny v okamžiku, kdy `FinalRelease` je volána. To umožňuje bezpečně přistupovat k metodám poskytovaných nejvíce odvozené třídy. To je zvlášť důležité pro uvolnění jakýchkoli agregovaných objektů před odstraněním.

##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef

Zvýší počet odkazů neagregovaná objektu 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

### <a name="remarks"></a>Poznámky

Pokud je model vláken s více vlákny, `InterlockedIncrement` umožňuje zabránit ve změně počtu odkazů ve stejnou dobu více než jedno vlákno.

##  <a name="internalqueryinterface"></a>  CComObjectRootEx::InternalQueryInterface

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
[in] Ukazatel na objekt, který obsahuje mapování modelu COM rozhraní vystavena `QueryInterface`.

*pEntries*<br/>
[in] Ukazatel `_ATL_INTMAP_ENTRY` struktura, která přistupuje k mapě dostupné rozhraní.

*identifikátor IID*<br/>
[in] Identifikátor GUID se požadované rozhraní.

*ppvObject*<br/>
[out] Ukazatel na ukazatel rozhraní zadané v *iid*, nebo hodnota NULL, pokud se nenajde rozhraní.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

`InternalQueryInterface` zpracovává pouze v tabulce mapy modelu COM rozhraní. Pokud objekt je agregován, `InternalQueryInterface` není delegovat na vnější neznámá. Rozhraní můžete zadat do tabulky mapování modelu COM s makro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) nebo jeden z jeho variant.

##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease

Sníží odkaz počet neagregovaná objektu 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Návratová hodnota

V obou bez ladění a ladění sestavení, tato funkce vrací hodnotu, která může být užitečné pro diagnostiku a testování. Přesná hodnota vrácená závislá na mnoha faktorech, jako je například operačního systému použít a může nebo nemusí, být počet odkazů.

### <a name="remarks"></a>Poznámky

Pokud je model vláken s více vlákny, `InterlockedDecrement` umožňuje zabránit ve změně počtu odkazů ve stejnou dobu více než jedno vlákno.

##  <a name="lock"></a>  CComObjectRootEx::Lock

Pokud je model vláken s více vlákny, tato metoda volá funkci Win32 API [EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection), které počká, dokud vlákno může převzít vlastnictví objektu kritický oddíl získaných dat soukromých členů.

```
void Lock();
```

### <a name="remarks"></a>Poznámky

Po dokončení provádění chráněné kódu vlákna musí volat `Unlock` uvolnit vlastnictví kritický oddíl.

Pokud je model vláken s jedním vláknem, tato metoda nemá žádný účinek.

##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef

Část sjednocení, který přistupuje k čtyři bajty paměti.

```
long m_dwRef;
```

### <a name="remarks"></a>Poznámky

S `m_pOuterUnknown`sjednocení patří:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Pokud objekt není agregovaný, počet odkazů přistupuje `AddRef` a `Release` je uložen v `m_dwRef`. Pokud objekt je agregován, ukazatel na vnější Neznámá je uložen v [m_pOuterUnknown](#m_pouterunknown).

##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown

Část sjednocení, který přistupuje k čtyři bajty paměti.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Poznámky

S `m_dwRef`sjednocení patří:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Pokud objekt je agregován, ukazatel na vnější Neznámá je uložen v `m_pOuterUnknown`. Pokud objekt není agregovaný, počet odkazů přistupuje `AddRef` a `Release` je uložen v [m_dwRef](#m_dwref).

##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain

Pro každou třídu uvedené v mapě objektů, tato funkce je volána při inicializaci modulu, a znovu když je ukončen.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parametry

*bStarting*<br/>
[out] Hodnota je TRUE, pokud třída je inicializována; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Hodnota *bStarting* parametr označuje, zda se v modulu inicializován nebo ukončen. Výchozí implementace `ObjectMain` nemá žádný účinek, ale můžete přepsat tuto funkci ve své třídě pro inicializaci nebo vyčistit prostředky, které chcete přidělit pro třídu. Všimněte si, že `ObjectMain` je volána před požadavku na všechny instance třídy.

`ObjectMain` je volána z vstupní bod knihovny DLL, je omezený typ operace, které provádí funkci vstupního bodu. Další informace o těchto omezeních najdete v tématu [Visual C++ a knihoven DLL knihovny run-time chování](../../build/run-time-library-behavior.md) a [DllMain](/windows/desktop/Dlls/dllmain).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef

Zvýší počet odkazů vnější Neznámá agregaci.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface

Načte nepřímé ukazatel na požadované rozhraní.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*identifikátor IID*<br/>
[in] Identifikátor GUID se požadované rozhraní.

*ppvObject*<br/>
[out] Ukazatel na ukazatel rozhraní zadané v *iid*, nebo hodnota NULL, pokud agregaci nepodporuje rozhraní.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease

Sníží počet referenční vnější Neznámá agregaci.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění vždy vrátí hodnotu 0. V sestavení ladění vrátí hodnotu, která může být užitečné pro diagnostiku a testování.

##  <a name="unlock"></a>  CComObjectRootEx::Unlock

Pokud je model vláken s více vlákny, tato metoda volá funkci Win32 API [LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection), které verze vlastnictví objektu kritický oddíl získaných dat soukromých členů.

```
void Unlock();
```

### <a name="remarks"></a>Poznámky

Získání vlastnictví, musí volat vlákno `Lock`. Každé volání `Lock` vyžaduje odpovídající volání `Unlock` uvolnit vlastnictví kritický oddíl.

Pokud je model vláken s jedním vláknem, tato metoda nemá žádný účinek.

## <a name="see-also"></a>Viz také

[CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject – třída](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
