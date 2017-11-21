---
title: "Třída CComObjectRootEx | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords: reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 987d8fcb8464ab691b915c576194f530cb50842e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx – třída
Tato třída poskytuje metody pro zpracování Správa počet odkaz objektu pro neagregovaná a agregované objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class ThreadModel>  
class CComObjectRootEx : public CComObjectRootBase
```  
  
#### <a name="parameters"></a>Parametry  
 `ThreadModel`  
 Třída, jejichž metody implementovat požadovanou model vláken. Můžete vybrat model vláken explicitně nastavením `ThreadModel` k [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), nebo [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Můžete přijmout model vláken výchozí serveru nastavením `ThreadModel` k [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) nebo [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).  

  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CComObjectRootEx](#ccomobjectrootex)|Konstruktor|  
|[Internaladdref –](#internaladdref)|Zvýší počet odkazů pro objekt neagregovaná.|  
|[Internalrelease –](#internalrelease)|Snižuje počet odkaz na objekt neagregovaná.|  
|[Zámek](#lock)|Pokud je model vláken s více vlákny, získá vlastnictví objektu kritická sekce.|  
|[Odemknutí](#unlock)|Pokud je model vláken s více vlákny, uvolní vlastnictví objektu kritická sekce.|  
  
### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase metody  
  
|||  
|-|-|  
|[FinalConstruct](#finalconstruct)|Přepsání ve třídě provést všechny inicializace vyžadovanou objektu.|  
|[FinalRelease](#finalrelease)|Přepsání ve třídě k vyčištění vyžadované vaší objektem.|  
|[OuterAddRef](#outeraddref)|Zvýší počet odkazů pro agregovaný objekt.|  
|[OuterQueryInterface](#outerqueryinterface)|Delegátů k vnější **IUnknown** agregovaného objektu.|  
|[OuterRelease](#outerrelease)|Snižuje počet odkaz na agregovaný objekt.|  
  
### <a name="static-functions"></a>Statické funkce  
  
|||  
|-|-|  
|[InternalQueryInterface](#internalqueryinterface)|Deleguje **IUnknown** neagregovaná objektu.|  
|[ObjectMain](#objectmain)|Volané během inicializace modulu a ukončení odvozené třídy, které jsou uvedené v mapování objektu.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_dwRef](#m_dwref)|S `m_pOuterUnknown`, součástí spojení. Použít při objekt není agregovaný pro uložení počet odkazů `AddRef` a **verze**.|  
|[m_pOuterUnknown](#m_pouterunknown)|S `m_dwRef`, součástí spojení. Použít, když je objekt agregován do podržte ukazatel na vnější neznámý.|  
  
## <a name="remarks"></a>Poznámky  
 `CComObjectRootEx`zpracovává Správa počet odkaz objektu pro neagregovaná a agregované objekty. Pokud není agregovaný objektu a obsahuje ukazatele na vnější neznámý, pokud je agregovaný objektu drží odkaz počet objektů. Pro agregované objekty `CComObjectRootEx` metody lze použít k vyřešení selhání vnitřní objekt k vytvoření a k ochraně vnější objekt z odstranění, když jsou vydávány vnitřní rozhraní nebo vnitřní objekt se odstraní.  
  
 Třídu, která implementuje COM server musí dědit z `CComObjectRootEx` nebo [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).  
  
 Pokud vaše definice třídy určuje [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) makro, ATL vytvoří instanci **CComPolyObject\<CYourClass >** při **IClassFactory:: CreateInstance –** je volána. Během vytváření se kontroluje hodnota vnější neznámý. Pokud je **NULL**, **IUnknown** je implementována pro objekt neagregovaná. Pokud vnější Neznámý není **NULL**, **IUnknown** je implementována pro agregovaný objekt.  
  
 Pokud vaše třída neurčuje `DECLARE_POLY_AGGREGATABLE` makro, ATL vytvoří instanci **CAggComObject\<CYourClass >** pro agregovaná objektů nebo instanci **CComObject\<CYourClass >** pro neagregovaná objekty.  
  
 Výhodou použití `CComPolyObject` je vyhnout se nutnosti obě `CComAggObject` a `CComObject` v modulu pro zpracování agregované a neagregovaná případy. Jediný `CComPolyObject` objekt zpracovává obou případech. Proto pouze jedné kopie tabulce vtable a jednu kopii funkce existují v modulu. Pokud vaše vtable velká, může to podstatně snížit velikost vašeho modulu. Ale pokud je vaše vtable malá, pomocí `CComPolyObject` může způsobit něco větší velikost modulu, protože není optimalizována pro agregovaná nebo neagregovaná objekt, jako jsou `CComAggObject` a `CComObject`.  
  
 Pokud je agregován objektu, [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) je implementováno modulem `CComAggObject` nebo `CComPolyObject`. Tyto třídy delegovat `QueryInterface`, `AddRef`, a **verze** volání `CComObjectRootEx`na `OuterQueryInterface`, `OuterAddRef`, a `OuterRelease` předávání do vnějšího neznámý. Obvykle je přepsat `CComObjectRootEx::FinalConstruct` v třídě vytvoření agregované objekty a přepsání `CComObjectRootEx::FinalRelease` uvolnit všechny agregovat objekty.  
  
 Pokud nejsou agregovány objektu, **IUnknown** je implementováno modulem `CComObject` nebo `CComPolyObject`. V takovém případě volání `QueryInterface`, `AddRef`, a **verze** jsou přeneseny na `CComObjectRootEx`na `InternalQueryInterface`, `InternalAddRef`, a `InternalRelease` k provedení vlastní operace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="ccomobjectrootex"></a>CComObjectRootEx::CComObjectRootEx  
 Konstruktor inicializuje počet odkazů na hodnotu 0.  
  
```
CComObjectRootEx();
```  
  
##  <a name="finalconstruct"></a>CComObjectRootEx::FinalConstruct  
 Mohou přepsat tuto metodu v odvozené třídě provést jakékoli inicializace požadována pro objekt.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo jeden z standardní chyba `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `CComObjectRootEx::FinalConstruct` jednoduše vrátí `S_OK`.  
  
 Existují výhody provádět inicializace v `FinalConstruct` místo konstruktoru vaší třídy:  
  
-   Stavový kód nemůže vrátit z konstruktoru, ale můžete se vrátit `HRESULT` prostřednictvím `FinalConstruct`na vrátit hodnotu. Při vytváření objektů vaší třídy pomocí objektu pro vytváření standardní třída poskytované ATL, tento návratovou hodnotu rozšířena zpět do klienta COM, což umožňuje jim poskytnout podrobné informace o chybě.  
  
-   Virtuální funkce nelze volat přes mechanismus virtuální funkci z konstruktoru třídy. Volání virtuální funkci z konstruktoru třídy výsledkem statisticky volání funkce, jako je definována v tomto bodě v hierarchii dědičnosti. Volání funkcí čistý virtuální vést k chybám linkeru.  
  
     Vaše třída není nejvíce odvozené třídy v hierarchii dědičnosti – přitom spoléhá na odvozené třídě poskytl ATL zajistit některé ze svých funkcí. Je dobré pravděpodobné, že vaše inicializace budou muset používat funkce poskytované službou třídy (to je určitě true při objekty vaší třídy vyžadují k agregaci jiné objekty), ale konstruktoru ve třídě nemá žádnou možnost přístupu k nim. Vytváření kódu pro třídu je spuštěna před plně sestavený nejvíce odvozené třídy.  
  
     Ale `FinalConstruct` je volána hned po nejvíc odvozené třídy plně sestavený umožňuje volání virtuální funkce a použít počítání odkazů implementace poskytované ATL.  
  
### <a name="example"></a>Příklad  
 Obvykle potlačí tuto metodu do třídy odvozené od `CComObjectRootEx` vytvořit žádné agregovat objekty. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]  
  
 Pokud vytváření nezdaří, můžete se vrátit k chybě. Můžete také použít makro [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) k ochraně před vrácení vnější objektu odstranit, pokud během vytváření interního objektu agregované zvětší počet odkazů a snižuje počet na hodnotu 0.  
  
 Tady je typické způsob, jak vytvořit agregace:  
  
-   Přidat **IUnknown** ukazatel do vaší třídy objektu a inicializujte ho, aby **NULL** v konstruktoru.  
  
-   Přepsání `FinalConstruct` vytvoření agregace.  
  
-   Použití **IUnknown** ukazatel definován jako parametr pro [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) makro.  
  
-   Přepsání `FinalRelease` k uvolnění **IUnknown** ukazatel.  
  
##  <a name="finalrelease"></a>CComObjectRootEx::FinalRelease  
 Mohou přepsat tuto metodu v odvozené třídě k vyčištění vyžadované pro objekt.  
  
```
void FinalRelease();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `CComObjectRootEx::FinalRelease` se nic nestane.  
  
 Provádění vyčištění v `FinalRelease` je vhodnější při přidávání kódu do destruktor vaší třídy, vzhledem k tomu, že objekt je stále plně vytvořený v okamžiku, kdy `FinalRelease` je volána. To vám umožňuje bezpečně přístup metody poskytované nejvíce odvozené třídy. To je obzvláště důležité pro uvolnění všechny agregované objekty před odstraněním.  
  
##  <a name="internaladdref"></a>CComObjectRootEx::InternalAddRef  
 Počet odkazů objekt neagregovaná zvýší o 1.  
  
```
ULONG InternalAddRef();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku a testování.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je model vláken s více vlákny, **InterlockedIncrement** se používá k více než jedno vlákno zabránit ve změně počet odkazů ve stejnou dobu.  
  
##  <a name="internalqueryinterface"></a>CComObjectRootEx::InternalQueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pThis`  
 [v] Ukazatel na objekt, který obsahuje mapy COM rozhraní vystavený `QueryInterface`.  
  
 `pEntries`  
 [v] Ukazatel **_ATL_INTMAP_ENTRY** struktura, která přistupuje k mapu k dispozici rozhraní.  
  
 `iid`  
 [v] Identifikátor GUID se požadované rozhraní.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní zadaný v `iid`, nebo **NULL** Pokud rozhraní nebyl nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 `InternalQueryInterface`zpracovává jenom rozhraní v tabulce COM mapy. Pokud je agregován objektu, `InternalQueryInterface` není delegovat na vnější neznámý. Rozhraní můžete zadat do tabulky mapování COM s makro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) nebo jednoho z jeho variant.  
  
##  <a name="internalrelease"></a>CComObjectRootEx::InternalRelease  
 Snižuje odkaz na počet objekt neagregovaná o 1.  
  
```
ULONG InternalRelease();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V obou jiný debug a ladicí sestavení, tato funkce vrátí hodnotu, která může být užitečné pro diagnostiku nebo testování. Přesná hodnota vrácená závislá na mnoha faktorech, jako je například operačního systému použít a může nebo nemusí, být počet odkazů.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je model vláken s více vlákny, **InterlockedDecrement** se používá k více než jedno vlákno zabránit ve změně počet odkazů ve stejnou dobu.  
  
##  <a name="lock"></a>CComObjectRootEx::Lock  
 Pokud je model vláken s více vlákny, tato metoda volá funkce rozhraní Win32 API [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), které počká na vlákno může převzít vlastnictví objektu kritická sekce získaných pomocí privátní datový člen.  
  
```
void Lock();
```  
  
### <a name="remarks"></a>Poznámky  
 Po dokončení provádění kód chráněné musí volat vlákno `Unlock` k uvolnění vlastnictví kritická sekce.  
  
 Pokud je model vláken jednovláknové, tato metoda neprovede žádnou akci.  
  
##  <a name="m_dwref"></a>CComObjectRootEx::m_dwRef  
 Součást spojení, který používá čtyři bajtů paměti.  
  
```
long m_dwRef;
```  
  
### <a name="remarks"></a>Poznámky  
 S `m_pOuterUnknown`, součástí spojení:  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 Pokud není agregovaný objekt, počet odkazů přístup `AddRef` a **verze** je uložen v `m_dwRef`. Pokud je objekt agregován, má ukazatel na vnější Neznámý je uložen v [m_pOuterUnknown](#m_pouterunknown).  
  
##  <a name="m_pouterunknown"></a>CComObjectRootEx::m_pOuterUnknown  
 Součást spojení, který používá čtyři bajtů paměti.  
  
```
IUnknown*
    m_pOuterUnknown;
```     
  
### <a name="remarks"></a>Poznámky  
 S `m_dwRef`, součástí spojení:  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 Pokud je objekt agregován, má ukazatel na vnější Neznámý je uložen v `m_pOuterUnknown`. Pokud není agregovaný objekt, počet odkazů přístup `AddRef` a **verze** je uložen v [m_dwRef](#m_dwref).  
  
##  <a name="objectmain"></a>CComObjectRootEx::ObjectMain  
 Pro každou třídu uvedené v [mapování objektu](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f), tato funkce je volána po při inicializaci modulu, a znovu při ukončena.  
  
```
static void WINAPI ObjectMain(bool bStarting);
```  
  
### <a name="parameters"></a>Parametry  
 `bStarting`  
 [out] Hodnota je **true** Pokud je třída inicializovaného; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota `bStarting` parametr označuje, zda modul se inicializovat nebo byla ukončena. Výchozí implementaci `ObjectMain` nic neprovádí, ale můžete přepsat tuto funkci v třídě pro inicializaci nebo vyčištění prostředků, které chcete přidělit pro třídu. Všimněte si, že `ObjectMain` je volána před všechny instance třídy jsou požadovány.  
  
 `ObjectMain`je volána ze vstupního bodu knihovny DLL, tak, aby typ operace, která může provádět funkce vstupního bodu s omezeným přístupem. Další informace o těchto omezeních najdete v tématu [knihovny DLL a Visual C++ chování běhové knihovny](../../build/run-time-library-behavior.md) a [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]  
  
##  <a name="outeraddref"></a>CComObjectRootEx::OuterAddRef  
 Zvýší počet odkazů vnější Neznámý agregace.  
  
```
ULONG OuterAddRef();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku a testování.  
  
##  <a name="outerqueryinterface"></a>CComObjectRootEx::OuterQueryInterface  
 Načte nepřímé ukazatel na požadované rozhraní.  
  
```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID se požadované rozhraní.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní zadaný v `iid`, nebo **NULL** Pokud agregace nepodporuje rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
##  <a name="outerrelease"></a>CComObjectRootEx::OuterRelease  
 Snižuje počet odkaz na vnější Neznámá o agregaci.  
  
```
ULONG OuterRelease();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro bez ladění vždy vrátí hodnotu 0. V sestavení pro ladění vrátí hodnotu, která může být užitečné pro diagnostiku nebo testování.  
  
##  <a name="unlock"></a>CComObjectRootEx::Unlock  
 Pokud je model vláken s více vlákny, tato metoda volá funkce rozhraní Win32 API [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), které verze vlastnictví objektu kritická sekce získaných pomocí privátní datový člen.  
  
```
void Unlock();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete získat vlastnictví, musí volat vlákno `Lock`. Každé volání `Lock` vyžaduje odpovídající volání `Unlock` k uvolnění vlastnictví kritická sekce.  
  
 Pokud je model vláken jednovláknové, tato metoda neprovede žádnou akci.  
  
## <a name="see-also"></a>Viz také  
 [CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)   
 [CComObject – třída](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
