---
title: Třída CComObjectRootEx
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
ms.openlocfilehash: 87e2d7dca81221f4fac2a5189ecb0effbdceddc2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747900"
---
# <a name="ccomobjectrootex-class"></a>Třída CComObjectRootEx

Tato třída poskytuje metody pro zpracování správy počtu odkazů na objekty pro neagregované i agregované objekty.

## <a name="syntax"></a>Syntaxe

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parametry

*Model vlákna*<br/>
Třída, jejíž metody implementují požadovaný model zřetězení. Model zřetězení můžete explicitně zvolit nastavením *ThreadModel* na [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)nebo [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Výchozí model vlákna serveru můžete přijmout nastavením *threadmodelu* na [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) nebo [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Konstruktor|
|[InternalAddRef](#internaladdref)|Zvýšení počtu odkazů pro neagregovaný objekt.|
|[InternalRelease](#internalrelease)|Sníží počet odkazů pro neagregovaný objekt.|
|[Zámek](#lock)|Pokud je model vlákna vícevláknový, získá vlastnictví objektu kritické části.|
|[Odemknout](#unlock)|Pokud je model vlákna vícevláknový, uvolní vlastnictví objektu kritickéčásti.|

### <a name="ccomobjectrootbase-methods"></a>Metody CComObjectRootBase

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Přepište ve své třídě provést inicializaci vyžadované objektem.|
|[Konečné vydání](#finalrelease)|Přepište ve své třídě provádět jakékoli vyčištění vyžadované objektem.|
|[OuterAddRef](#outeraddref)|Zvýšení počtu odkazů pro agregovaný objekt.|
|[OuterQueryInterface](#outerqueryinterface)|Delegáti na `IUnknown` vnější agregované objektu.|
|[OuterRelease](#outerrelease)|Sníží počet odkazů pro agregovaný objekt.|

### <a name="static-functions"></a>Statické funkce

|||
|-|-|
|[Rozhraní InternalQueryInterface](#internalqueryinterface)|Delegáti `IUnknown` neagregované objektu.|
|[ObjektMain](#objectmain)|Volána během inicializace modulu a ukončení pro odvozené třídy uvedené v mapě objektu.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|[m_dwRef](#m_dwref)|S `m_pOuterUnknown`, část unie. Používá se v případě, že objekt není `AddRef` `Release`agregován pro uložení počtu odkazů a .|
|[m_pOuterUnknown](#m_pouterunknown)|S `m_dwRef`, část unie. Používá se při agregaci objektu pro uložení ukazatele na vnější neznámý.|

## <a name="remarks"></a>Poznámky

`CComObjectRootEx`zpracovává správu počtu odkazů na objekty pro neagregované i agregované objekty. Obsahuje počet odkazů na objekt, pokud váš objekt není agregován, a podrží ukazatel na vnější neznámé, pokud je objekt agregován. Pro agregované `CComObjectRootEx` objekty lze metody použít ke zpracování selhání vnitřní objekt konstrukce a k ochraně vnějšího objektu před odstraněním při uvolnění vnitřních rozhraní nebo odstranění vnitřního objektu.

Třída, která implementuje server `CComObjectRootEx` COM, musí dědit z [cComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Pokud definice třídy určuje [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) makro, atl `CComPolyObject<CYourClass>` `IClassFactory::CreateInstance` vytvoří instanci, kdy je volána. Během vytváření je zkontrolována hodnota vnějšího neznámého. Pokud je NULL, `IUnknown` je implementována pro neagregovaný objekt. Pokud vnější neznámý není `IUnknown` NULL, je implementována pro agregovaný objekt.

Pokud vaše třída neurčuje DECLARE_POLY_AGGREGATABLE makro, ATL `CAggComObject<CYourClass>` vytvoří instanci pro `CComObject<CYourClass>` agregované objekty nebo instanci pro neagregované objekty.

Výhodou použití `CComPolyObject` je, že se `CComAggObject` `CComObject` vyhnete tomu, abyste měli oba a v modulu pro zpracování agregovaných a neagregovaných případů. Jeden `CComPolyObject` objekt zpracovává oba případy. Proto pouze jedna kopie vtable a jednu kopii funkcí existují ve vašem modulu. Pokud je vaše vtable je velký, to může podstatně snížit velikost modulu. Pokud je však vaše vtable malá, může použití `CComPolyObject` způsobit o něco větší velikost modulu, protože není `CComAggObject` optimalizována pro agregovaný nebo neagregovaný objekt, jako jsou a . `CComObject`

Pokud je objekt agregován, `CComAggObject` [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) je implementována nebo `CComPolyObject`. Tyto `QueryInterface`třídy `AddRef`delegují , , a `Release` `CComObjectRootEx`volání na 's `OuterQueryInterface`, `OuterAddRef`a `OuterRelease` předávají do neznáma. Obvykle přepsat `CComObjectRootEx::FinalConstruct` ve vaší třídě vytvořit všechny agregované objekty a přepsat `CComObjectRootEx::FinalRelease` na volné všechny agregované objekty.

Pokud váš objekt není `IUnknown` agregována, je implementována `CComObject` nebo `CComPolyObject`. V tomto případě `QueryInterface`volání `AddRef`, `Release` , a `CComObjectRootEx`jsou `InternalQueryInterface` `InternalAddRef`delegovány na 's , a `InternalRelease` provádět skutečné operace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a>CComObjectrootex::CComObjectrootex

Konstruktor inicializuje počet odkazů na 0.

```
CComObjectRootEx();
```

## <a name="ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a>CComObjectRootex::FinalConstruct

Tuto metodu můžete přepsat v odvozené třídě a provést inicializaci požadovanou pro váš objekt.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Vrátit S_OK na úspěch nebo jednu ze standardních chyb HRESULT hodnoty.

### <a name="remarks"></a>Poznámky

Ve výchozím `CComObjectRootEx::FinalConstruct` nastavení jednoduše vrátí S_OK.

Existují výhody provádění inicializace v `FinalConstruct` spíše než konstruktor vaší třídy:

- Nelze vrátit stavový kód z konstruktoru, ale můžete vrátit `FinalConstruct`HRESULT pomocí 's vrácená hodnota. Při vytváření objektů vaší třídy pomocí standardní třídy factory poskytované ATL, tato vrácená hodnota je rozšířena zpět do klienta modelu COM, což umožňuje poskytnout jim podrobné informace o chybě.

- Virtuální funkce nelze volat prostřednictvím mechanismu virtuální funkce z konstruktoru třídy. Volání virtuální funkce z konstruktoru třídy má za následek staticky vyřešené volání funkce tak, jak je definována v tomto bodě v hierarchii dědičnosti. Volání čistě virtuální funkce za následek chyby propojovacího systému.

   Vaše třída není nejvíce odvozené třídy v hierarchii dědičnosti – spoléhá na odvozené třídy poskytované ATL poskytnout některé jeho funkce. Je pravděpodobné, že vaše inicializace bude muset použít funkce poskytované touto třídou (to je jistě pravda, když objekty vaší třídy potřebují agregovat další objekty), ale konstruktor ve vaší třídě nemá žádný způsob, jak získat přístup k těmto funkcím. Konstrukční kód pro vaši třídu je proveden před nejvíce odvozené třídy je plně konstruována.

   Je `FinalConstruct` však volána ihned po nejvíce odvozené třídy je plně konstruována umožňuje volat virtuální funkce a použít implementaci počítání odkazů poskytované ATL.

### <a name="example"></a>Příklad

Obvykle přepsat tuto metodu ve třídě `CComObjectRootEx` odvozené z vytvořit všechny agregované objekty. Příklad:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Pokud konstrukce selže, můžete vrátit chybu. Makro [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) můžete také použít k ochraně vnějšího objektu před odstraněním, pokud během vytváření vnitřní agregovaný objekt zvětší počet odkazů a pak sníží počet na 0.

Zde je typický způsob, jak vytvořit agregát:

- Přidejte `IUnknown` ukazatel do objektu třídy a inicializovat jej na HODNOTU NULL v konstruktoru.

- Přepsání `FinalConstruct` majekce vytvoříte agregaci.

- Použijte `IUnknown` ukazatel, který jste definovali jako parametr pro [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) makro.

- Přepsáním `FinalRelease` `IUnknown` uvolníte ukazatel.

## <a name="ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a>CComObjectRootEx::FinalRelease CComObjectRootEx::FinalRelease CComObjectRootEx::FinalRelease CCom

Tuto metodu můžete přepsat v odvozené třídě a provést jakékoli vyčištění požadované pro váš objekt.

```cpp
void FinalRelease();
```

### <a name="remarks"></a>Poznámky

Ve výchozím `CComObjectRootEx::FinalRelease` nastavení neprovede žádné akci.

Provádění vyčištění v `FinalRelease` je vhodnější přidat kód do destruktoru vaší třídy, protože objekt je `FinalRelease` stále plně konstruována v bodě, ve kterém je volána. To umožňuje bezpečný přístup k metodám poskytovaným nejvíce odvozenou třídou. To je obzvláště důležité pro uvolnění všech agregovaných objektů před odstraněním.

## <a name="ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a>CComObjectrootex::InternalAddref

Zvýšení počtu odkazů neagregovaného objektu o 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku a testování.

### <a name="remarks"></a>Poznámky

Pokud je model podprocesu `InterlockedIncrement` vícevláknové, slouží k zabránění více než jedno vlákno změnit počet odkazů ve stejnou dobu.

## <a name="ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a>CComObjectRootex::InternalQueryInterface

Načte ukazatel na požadované rozhraní.

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*pToto*<br/>
[v] Ukazatel na objekt, který obsahuje mapu COM `QueryInterface`rozhraní vystavených .

*pPoložky*<br/>
[v] Ukazatel na `_ATL_INTMAP_ENTRY` strukturu, která přistupuje k mapě dostupných rozhraní.

*Iid*<br/>
[v] Identifikátor GUID požadovaného rozhraní.

*ppvObjekt*<br/>
[out] Ukazatel na ukazatel rozhraní zadaný v *iid*nebo NULL, pokud rozhraní nebylo nalezeno.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

`InternalQueryInterface`zpracovává pouze rozhraní v tabulce mapy COM. Pokud je objekt agregován, `InternalQueryInterface` nedeleguje na vnější neznámé. Rozhraní můžete zadat do tabulky mapy COM pomocí [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) maker nebo jedné z jeho variant.

## <a name="ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a>CComObjectRootex::Vnitřní uvolnění

Sníží počet odkazů neagregovaného objektu o 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění a ladění vrátí tato funkce hodnotu, která může být užitečná pro diagnostiku nebo testování. Přesná vrácená hodnota závisí na mnoha faktorech, jako je například použitý operační systém, a může nebo nemusí být počtem odkazů.

### <a name="remarks"></a>Poznámky

Pokud je model podprocesu `InterlockedDecrement` vícevláknové, slouží k zabránění více než jedno vlákno změnit počet odkazů ve stejnou dobu.

## <a name="ccomobjectrootexlock"></a><a name="lock"></a>CComObjectRootex::Zamknout

Pokud je model vlákna vícevláknový, tato metoda volá funkci Rozhraní API Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), která čeká, dokud vlákno může převzít vlastnictví objektu kritické části získaného prostřednictvím soukromého datového člena.

```cpp
void Lock();
```

### <a name="remarks"></a>Poznámky

Po dokončení provádění chráněného kódu musí `Unlock` vlákno volat uvolnění vlastnictví kritické části.

Pokud je model vlákna jednovláknový, tato metoda neprovede žádnou akci.

## <a name="ccomobjectrootexm_dwref"></a><a name="m_dwref"></a>CComObjectRootEx::m_dwRef

Část unie, která přistupuje čtyři bajty paměti.

```
long m_dwRef;
```

### <a name="remarks"></a>Poznámky

S `m_pOuterUnknown`, část unie:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Pokud objekt není agregován, počet `AddRef` odkazů, ke kterým přistupuje a `Release` je uložen v aplikaci `m_dwRef`. Pokud je objekt agregován, je ukazatel na vnější neznámý uložen v [m_pOuterUnknown](#m_pouterunknown).

## <a name="ccomobjectrootexm_pouterunknown"></a><a name="m_pouterunknown"></a>CComObjectRootEx::m_pOuterUnknown

Část unie, která přistupuje čtyři bajty paměti.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Poznámky

S `m_dwRef`, část unie:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Pokud je objekt agregován, je v `m_pOuterUnknown`aplikaci uložen ukazatel na vnější neznámý . Pokud objekt není agregován, počet `AddRef` odkazů `Release` přistupovat a je uložen v [m_dwRef](#m_dwref).

## <a name="ccomobjectrootexobjectmain"></a><a name="objectmain"></a>CComObjectrootex::ObjectMain

Pro každou třídu uvedenou v mapě objektu je tato funkce volána jednou při inicializování modulu a znovu při jeho ukončení.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parametry

*bZahájení*<br/>
[out] Hodnota je PRAVDA, pokud je třída inicializována; jinak FALSE.

### <a name="remarks"></a>Poznámky

Hodnota parametru *bStarting* označuje, zda je modul inicializován nebo ukončen. Výchozí implementace `ObjectMain` neprovede žádné, ale můžete přepsat tuto funkci ve vaší třídě k inicializaci nebo vyčištění prostředků, které chcete přidělit pro třídu. Všimněte `ObjectMain` si, že je volána před všechny instance třídy jsou požadovány.

`ObjectMain`je volána ze vstupního bodu dll, takže typ operace, kterou může funkce vstupního bodu provádět, je omezen. Další informace o těchto omezeních naleznete [v tématu Knihovny DLL a Visual C++ run-time knihovny chování](../../build/run-time-library-behavior.md) a [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

## <a name="ccomobjectrootexouteraddref"></a><a name="outeraddref"></a>CComObjectrootex::outerAddRef

Zvýšení počet odkazů vnější neznámý agregace.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku a testování.

## <a name="ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a>CComObjectRootex::OuterQueryInterface

Načte nepřímý ukazatel na požadované rozhraní.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor GUID požadovaného rozhraní.

*ppvObjekt*<br/>
[out] Ukazatel rozhraní zadaný v *iid*nebo NULL, pokud agregace nepodporuje rozhraní.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomobjectrootexouterrelease"></a><a name="outerrelease"></a>CComObjectrootex::vnější uvolnění

Sníží počet odkazů vnější neznámé agregace.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění vždy vrátí 0. V sestavení ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování.

## <a name="ccomobjectrootexunlock"></a><a name="unlock"></a>CComObjectRootex::Odemknout

Pokud je model vlákna vícevláknový, tato metoda volá funkci Rozhraní API Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), která uvolní vlastnictví objektu kritické části získaného prostřednictvím soukromého datového člena.

```cpp
void Unlock();
```

### <a name="remarks"></a>Poznámky

Chcete-li získat vlastnictví, `Lock`podproces musí volat . Každé volání `Lock` vyžaduje odpovídající `Unlock` volání k uvolnění vlastnictví kritické části.

Pokud je model vlákna jednovláknový, tato metoda neprovede žádnou akci.

## <a name="see-also"></a>Viz také

[Třída CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Třída CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Třída CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
