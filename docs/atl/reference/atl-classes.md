---
title: ATL – třídy a struktury | Dokumentace Microsoftu
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 561d6cb41ca066f5a2435b4eb1e8710ccaa99ea1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248937"
---
# <a name="atl-classes-and-structs"></a>ATL – třídy a struktury

Aktivní šablony knihovny (ATL) obsahuje následující třídy a struktury. Určité třídy podle kategorie najdete v tématu [přehled třídy ATL](../../atl/atl-class-overview.md).

|Třída / struktura|Popis|Hlavičkový soubor|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|Obsahuje informace, které slouží pro vykreslení na různé cíle, například tiskárny, metafile nebo ovládací prvek ActiveX.|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|Obsahuje data instance třídy v kódu časová okna v knihovně ATL|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|Používat jakýkoli projekt, který používá knihovnu ATL.|atlbase.h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|Používaný kód související s modelu COM v knihovně ATL| atlbase.h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|Obsahuje informace o typu používané k popisu metody nebo vlastnosti na dispinterface.|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|Data používaná každého modulu ATL obsahuje.|atlbase.h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|Používaný kód časová okna v knihovně ATL|atlbase.h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|Tato třída se používá makra převodu řetězců CA2TEX CT2AEX a definice typedef CA2A.|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|Tato třída se používá řetězec převodních maker CA2CTEX CT2CAEX a definice typedef CA2CA.|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|Tato třída se používá makra převodu řetězců CA2TEX, CA2CTEX, CT2WEX a CT2CWEX a definice typedef CA2W.|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|Tato třída představuje obálku pro přístupový token.|atlsecurity.h|
|[CAcl](../../atl/reference/cacl-class.md)|Tato třída představuje obálku pro strukturu (řízení přístupu na seznam ACL).|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|Tato šablona se používá k zabalení tříd, které mění definici operátoru address-of tak, aby vracely něco jiného než adresu objektu.|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|Tato třída implementuje objekt typu pole.|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|Tato třída implementuje ve fondu vláken, apartment model modelu COM serveru.|atlbase.h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|Tato třída poskytuje metody pro implementaci serveru ve fondu vláken, apartment model modelu COM.|atlbase.h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|V každém projektu ATL je vytvořena instance této třídy.|atlcore.h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|Tato třída implementuje modul COM serveru.|atlbase.h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|Tato třída poskytuje podporu pro ladění v rozhraní.|atlbase.h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|Tato třída reprezentuje modulu pro knihovnu DLL.|atlbase.h|
|[CAtlException](../../atl/reference/catlexception-class.md)|Tato třída definuje ATL výjimky.|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|Tato třída reprezentuje modulu pro aplikaci.|atlbase.h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|Tato třída poskytuje rozhraní API pro zpracování souborů dynamického zajišťování obálku Windows.|atlfile.h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|Tato třída reprezentuje soubor mapovaných do paměti, přidání operátor přetypování na metody [catlfilemappingbase –](../../atl/reference/catlfilemappingbase-class.md).|atlfile.h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|Tato třída reprezentuje soubor mapovaných do paměti.|atlfile.h|
|[CAtlList](../../atl/reference/catllist-class.md)|Tato třída poskytuje metody pro vytváření a správa seznamu objektů.|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|Tato třída poskytuje metody pro vytváření a správu objektu map.|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|Tato třída poskytuje metody používané v několika ATL – třídy modulů.|atlbase.h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|Tato třída implementuje modul knihovny ATL.|atlbase.h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|Tato třída je implementace knihovny ATL okna, které se umístí do hostitelského okna poskytnutého shellem pro náhled ve formátu RTF.|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|Tato třída implementuje služby.|atlbase.h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|Tato třída poskytuje metody pro vytváření a používání dočasný soubor.|atlfile.h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|Tato třída poskytuje obálku pro funkce transakcí správce KTM (Kernel).|atltransactionmanager.h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|Tato třída poskytuje podporu pro komponenty ATL časová okna.|atlbase.h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|Tato třída reprezentuje objekt inteligentního ukazatele.|atlbase.h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|Tato třída poskytuje metody, které jsou užitečné při vytváření pole inteligentních ukazatelů.|atlbase.h|
|[Cautoptrelementtraits –](../../atl/reference/cautoptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice TypeDef, které jsou užitečné při vytváření kolekce inteligentních ukazatelů.|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|Tato třída poskytuje metody, které jsou užitečné při vytváření seznamu inteligentní ukazatele.|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|Tato třída představuje objekt inteligentního ukazatele pomocí vektoru nové a odstranit operátory.|atlbase.h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice TypeDef, které jsou užitečné při vytváření kolekce inteligentních ukazatelů pomocí nové vektoru a odstranit operátory.|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|Tato třída implementuje dialog (modálním nebo nemodálním), který je hostitelem ovládacích prvků ActiveX.|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|Tato třída poskytuje metody pro práci s okno hostování ovládacího prvku ActiveX.|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|Tato třída poskytuje metody pro práci s okno, které hostuje ovládací prvek ActiveX a také zahrnuje podporu pro hostování licencované ovládací prvky ActiveX.|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|Tato třída implementuje `IBindStatusCallback` rozhraní.|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|Tato třída implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pro agregovaného objektu.|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|Tato třída poskytuje metody pro správu paměti používá rutiny COM paměti.|atlbase.h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|Tato třída poskytuje podporu pro správu v souboru EXE modulu ve fondu vláken typu apartment.|atlbase.h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritický oddíl.|atlcore.h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL moduly](../../atl/atl-module-classes.md) další podrobnosti.|atlbase.h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|Tato třída představuje obálku pro datových typů BSTR.|atlbase.h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|Tato třída implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pro rozhraní s odnímatelnými nabídkami.|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|Tato třída implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) rozhraní.|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|Tato třída implementuje [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) rozhraní.|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|Tato třída implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) rozhraní a umožňuje objektů bude vytvořena ve více objekty apartment.|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|Tato třída je odvozena z [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) a používá [ccomobjectglobal –](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|Tato třída poskytuje metody pro vytvoření instance třídy a získání jeho vlastnosti.|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|Tato třída poskytuje metody potřebnou k implementaci složeného ovládacího prvku.|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|Tato třída implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) delegováním objekt vlastníka `IUnknown`.|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|Tato třída poskytuje metody pro vytváření a správu ATL – ovládací prvky.|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|Tato třída poskytuje metody pro vytváření a správu ATL – ovládací prvky.|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritický oddíl.|atlcore.h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|Tato třída poskytuje metody pro zamknutí a odemknutí objektu kritický oddíl.|atlbase.h|
|[Ccomcurrency –](../../atl/reference/ccomcurrency-class.md)|Tato třída obsahuje metody a operátory k vytváření a správě objekt měny.|atlcur.h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|Tato třída obsahuje pole z `IUnknown` ukazatele.|atlcom.h|
|[Ccomenum –](../../atl/reference/ccomenum-class.md)|Tato třída definuje objekt enumerátoru modelu COM na základě pole.|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|Tato třída poskytuje implementaci pro uložení položky výčtu v poli rozhraní modelu COM enumerátor.|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|Tato třída definuje objekt enumerátoru modelu COM na základě kolekce standardní knihovny C++.|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|Tato třída poskytuje metody stejný jako [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md) ale neposkytuje kritický oddíl.|atlcore.h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|Tato třída poskytuje metody pro práci s ukazatele rozhraní a tabulky globálního rozhraní (GIT).|atlbase.h|
|[Ccomheap –](../../atl/reference/ccomheap-class.md)|Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí přidělení paměti COM.|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|Třída inteligentní ukazatel pro správu haldy ukazatele.|atlbase.h|
|[CComModule](../../atl/reference/ccommodule-class.md)|Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL moduly](../../atl/atl-module-classes.md) další podrobnosti.|atlbase.h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|Tato třída poskytuje metody bezpečným pro vlákno pro zvyšování a dekrementace hodnotu proměnné.|atlbase.h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|Tato třída poskytuje metody bezpečným pro vlákno pro zvyšování a dekrementace hodnotu proměnné, bez kritický oddíl zamykání a odemykání funkce.|atlbase.h|
|[CComObject](../../atl/reference/ccomobject-class.md)|Tato třída implementuje `IUnknown` pro neagregovaná objekt.|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|Tato třída spravuje počet odkazů na modul obsahující vaše `Base` objektu.|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|Tato třída implementuje `IUnknown` pro neagregovaná objektu, ale nemá není přírůstek počet zámků modulů v konstruktoru.|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Tato definice typu z [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) je založena na výchozí model serveru vláken.|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|Tato třída poskytuje metody pro zpracování správy referenční počet objektů pro neagregovaná a agregované objekty.|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|Tato třída se vytvoří dočasný objekt modelu COM a poskytuje základní implementaci `IUnknown`.|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|Tato třída implementuje `IUnknown` agregované nebo neagregovaná objektu.|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|Třída inteligentní ukazatel pro správu ukazatele rozhraní modelu COM.|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|Tato třída poskytuje základ pro inteligentní ukazatel tříd pomocí rutiny založené na modelu COM. paměti.|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|Třída inteligentní ukazatel pro správu ukazatele rozhraní modelu COM.|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice TypeDef, které jsou užitečné při vytváření kolekce ukazatele rozhraní modelu COM.|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|Tato třída představuje obálku pro `SAFEARRAY Data Type` struktury.|atlsafe.h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|Tato třída představuje obálku pro `SAFEARRAYBOUND` struktury.|atlsafe.h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|Tato třída spravuje výběr vlákna pro třídu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).|atlbase.h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|Tato třída poskytuje metody pro zvyšování a dekrementace hodnotu proměnné.|atlbase.h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|Tato třída implementuje rozhraní s odnímatelnými nabídkami.|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|Tato třída obsahuje `IUnknown` ukazatele a je určená pro použití jako parametr, který se [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) šablony třídy.|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|Tato třída zabalí typ VARIANT, poskytování člen označující typ dat uložených.|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|Tato třída implementuje oken obsažených v rámci jiného objektu.|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|Tato třída poskytuje metody pro správu paměti používá rutiny paměti CRT.|atlcore.h|
|[Ccrtheap –](../../atl/reference/ccrtheap-class.md)|Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí haldy CRT.|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|Tato třída představuje obálku pro strukturu DACL (seznam volitelných řízení přístupu).|atlsecurity.h|
|[CDebugReportHook – třída](../../atl/reference/cdebugreporthook-class.md)|Tato třída slouží k odesílání sestav ladění k pojmenovanému kanálu.|atlutil.h|
|[Cdefaultchartraits –](../../atl/reference/cdefaultchartraits-class.md)|Tato třída poskytuje dvě statické funkce pro převod znaků mezi velkými a malými písmeny.|atlcoll.h|
|[Cdefaultcomparetraits –](../../atl/reference/cdefaultcomparetraits-class.md)|Tato třída poskytuje výchozí element porovnání funkcí.|atlcoll.h|
|[Cdefaultelementtraits –](../../atl/reference/cdefaultelementtraits-class.md)|Tato třída poskytuje výchozí metody a funkce pro třídy kolekce.|atlcoll.h|
|[Cdefaulthashtraits –](../../atl/reference/cdefaulthashtraits-class.md)|Tato třída poskytuje statické funkce pro výpočet hodnoty hash.|atlcoll.h|
|[CDialogImpl –](../../atl/reference/cdialogimpl-class.md)|Tato třída poskytuje metody pro vytváření modální a nemodální dialogové okno.|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|Tato třída poskytuje metody, které podporuje dynamické řetězení mapy zpráv.|atlwin.h|
|[Celementtraits –](../../atl/reference/celementtraits-class.md)|Tato třída používá kolekce tříd poskytují metody a funkce pro přesunutí, kopírování, porovnání a hash operace.|atlcoll.h|
|[Celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md)|Tato třída poskytuje výchozí kopie a přesunutí metody pro třídu kolekce.|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|Tato třída poskytuje metody pro oznámení kontejneru jímky týkající se změny vlastností ovládacího prvku.|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkce globální haldy Win32.|atlmem.h|
|[Chandle –](../../atl/reference/chandle-class.md)|Tato třída poskytuje metody pro vytváření a používání popisovač objektu.|atlbase.h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|Třída inteligentní ukazatel pro správu haldy ukazatele.|atlcore.h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|Tato třída je základem pro několik tříd haldy inteligentního ukazatele.|atlcore.h|
|[CHeapPtrElementTraits – třída](../../atl/reference/cheapptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice TypeDef, které jsou užitečné při vytváření kolekce haldy ukazatelů.|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|Tato třída poskytuje metody, které jsou užitečné při vytváření seznamu haldy ukazatele.|atlcoll.h|
|[Cimage –](../../atl-mfc-shared/reference/cimage-class.md)|poskytuje podporu rozšířenou rastrový obrázek, včetně možnosti k načtení a uložení Image ve formátu JPEG, GIF, BMP a Portable Network Graphics (PNG).|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|Tato třída poskytuje metody, které jsou užitečné při vytváření pole z ukazatele rozhraní modelu COM.|atlcoll.h|
|[Cinterfacelist –](../../atl/reference/cinterfacelist-class.md)|Tato třída poskytuje metody, které jsou užitečné při vytváření seznamu ukazatele rozhraní modelu COM.|atlcoll.h|
|[Clocalheap –](../../atl/reference/clocalheap-class.md)|Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí lokální haldy Win32.|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|Tato třída umožňuje že přístup k jiným objektem mapy zpráv objektu.|atlwin.h|
|[CNonStatelessWorker – třída](../../atl/reference/cnonstatelessworker-class.md)|Přijímá požadavky od fondu vláken a předává je do objektu pracovního procesu, který je vytvořeno a zničeno při každém požadavku.|atlutil.h|
|[CNoWorkerThread – třída](../../atl/reference/cnoworkerthread-class.md)|Použijte tuto třídu jako argument pro `MonitorClass` mezipaměti parametr šablony třídy, pokud chcete zakázat dynamické mezipaměti údržby.|atlutil.h|
|[CPathT – třída](../../atl/reference/cpatht-class.md)|Tato třída reprezentuje cestu.|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|Tato třída poskytuje výchozí metody a funkce pro třídy kolekce tvořené primitivní datové typy.|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|Tato třída reprezentuje objekt popisovače zabezpečení privátní objekt.|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|Tato třída reprezentuje strukturu mapování pomocí binárního stromu Red Black.|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|Tato třída reprezentuje strukturu mapování, která umožňuje každý klíč, který se má přidružit více než jednu hodnotu pomocí binárního stromu Red Black.|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|Tato třída poskytuje metody pro vytváření a využívání Red černé stromu.|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|Tato třída poskytuje metody pro práci s položkami v systémovém registru.|atlbase.h|
|[Crtthreadtraits –](../../atl/reference/crtthreadtraits-class.md)|Tato třída poskytuje funkce vytvoření vlákna CRT. Pokud vlákno použije funkce CRT, použijte tuto třídu.|atlbase.h|
|[CSacl](../../atl/reference/csacl-class.md)|Tato třída představuje obálku pro strukturu SACL (seznam řízení přístupu systému).|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|Tato třída je obálka dynamického zajišťování pro `SECURITY_ATTRIBUTES` struktury.|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|Tato třída představuje obálku pro `SECURITY_DESCRIPTOR` struktury.|atlsecurity.h|
|[Identifikační číslo volané stanice](../../atl/reference/csid-class.md)|Tato třída představuje obálku pro `SID` strukturu (security identifier).|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|Tato třída poskytuje metody pro správu jednoduché pole.|atlsimpcoll.h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|Tato třída je pomocné rutiny pro [csimplearray –](../../atl/reference/csimplearray-class.md) třídy.|atlsimpcoll.h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|Tato třída je pomocné rutiny pro [csimplearray –](../../atl/reference/csimplearray-class.md) třídy.|atlsimpcoll.h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|Tato třída implementuje základní modální dialogové okno.|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|Tato třída poskytuje podporu pro jednoduché mapování pole.|atlsimpcoll.h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|Tato třída je pomocné rutiny pro [csimplemap –](../../atl/reference/csimplemap-class.md) třídy.|atlsimpcoll.h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|Tato třída je pomocné rutiny pro [csimplemap –](../../atl/reference/csimplemap-class.md) třídy.|atlsimpcoll.h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|Tato třída poskytuje metody pro implementaci modulu snap-in uzel objektu.|atlsnap.h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|Tato třída poskytuje metody pro implementaci objektu page vlastnost modul snap-in.|atlsnap.h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|Tato třída poskytuje metody pro podporu uložených vlastností hodnoty.|atlctl.h|
|[Cstringelementtraits –](../../atl/reference/cstringelementtraits-class.md)|Tato třída poskytuje statické funkce, které používají třídy kolekcí ukládání `CString` objekty.|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|Tato třída poskytuje statické funkce související se ukládají v objektech třídy kolekce řetězců. Je to podobné [cstringelementtraits –](../../atl/reference/cstringelementtraits-class.md), ale provádí porovnávání bez rozlišování.|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|Tato třída poskytuje statické funkce související se ukládají v objektech třídy kolekce řetězců. Řetězcových objektů jsou zpracovány jako odkazy.|atlcoll.h|
|[CThreadPool – třída](../../atl/reference/cthreadpool-class.md)|Tato třída poskytuje fondu pracovních vláken, které zpracovávají fronty pracovních položek.|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|Tato třída představuje obálku pro `TOKEN_GROUPS` struktury.|atlsecurity.h|
|[Ctokenprivileges –](../../atl/reference/ctokenprivileges-class.md)|Tato třída představuje obálku pro `TOKEN_PRIVILEGES` struktury.|atlsecurity.h|
|[CUrl – třída](../../atl/reference/curl-class.md)|Tato třída představuje adresu URL. To umožňuje pracovat s každý prvek adresu URL nezávisle na ostatních, zda analýza stávající adresy URL řetězec nebo vytváření řetězec od začátku.|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|Tato třída se používá makra převodu řetězců CT2AEX, CW2TEX, CW2CTEX a CT2CAEX a definice typedef CW2A.|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|Tato třída se používá makra převodu řetězců CW2CTEX CT2CWEX a definice typedef CW2CW.|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|Tato třída se používá makra převodu řetězců CW2TEX CT2WEX a definice typedef CW2W.|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí přidělení haldy Win32.|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|Tato třída poskytuje metody pro práci s časového období.|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|Tato třída poskytuje metody pro vytváření nebo vytvoření podtřídy časového období.|atlwin.h|
|[Cwintraits –](../../atl/reference/cwintraits-class.md)|Tato třída poskytuje metody pro standardizaci stylů použitých při vytváření objektu okno.|atlwin.h|
|[Cwintraitsor –](../../atl/reference/cwintraitsor-class.md)|Tato třída poskytuje metody pro standardizaci stylů použitých při vytváření objektu okno.|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|Tato třída poskytuje metody pro registraci informace pro třídu okna.|atlwin.h|
|[CWorkerThread – třída](../../atl/reference/cworkerthread-class.md)|Tato třída vytvoří pracovní vlákno nebo použije existující předplatné, čeká na jeden nebo více jádra manipulačních bodů objektu a provede funkci zadaného klienta v případě jednoho z úchytů signalizován.|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|Tato třída reprezentuje rozhraní pro `CreateInstance` metoda.|atlbase.h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|Tato třída reprezentuje rozhraní pro správce paměti.|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|Toto rozhraní poskytuje metody pro zadání vlastnosti hostovaného ovládacího prvku nebo kontejneru.|atlbase.h, ATLIFace.h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|Toto rozhraní implementuje dodatečné vlastnosti prostředí pro hostované ovládací prvek.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|Toto rozhraní poskytuje metody pro práci s ovládacím prvkem a jeho objekt hostitele.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|Toto rozhraní poskytuje metody pro manipulaci s licencovaného ovládacího prvku a jeho objekt hostitele.|atlbase.h, ATLIFace.h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|Tato třída poskytuje metody používané třídy kolekce.|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|Tato třída implementuje kontejner bod připojení pro správu kolekce [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objekty.|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|Tato třída implementuje bod připojení.|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|Tato třída poskytuje metody pro podporu jednotného přenosu dat a Správa připojení.|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|Tato třída poskytuje výchozí implementaci pro `IDispatch` část duální rozhraní.|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|Tato třída obsahuje implementaci `IDispatch` metody.|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|Tato třída obsahuje implementaci `IDispatch` metody bez získání informací o typu z knihovny typů.|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Rozhraní pro parsování Microsoft HTML a vykreslovací modul.|atlbase.h, ATLIFace.h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|Tato třída definuje výčet rozhraní na základě kolekce standardní knihovny C++.|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|Tato třída poskytuje výchozí implementaci třídy `IObjectSafety` rozhraní umožňující klientská načíst a nastavit úrovně zabezpečení objektu.|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|Tato třída poskytuje metody umožňující objekt ke komunikaci se svou lokalitou.|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|Tato třída poskytuje výchozí implementaci třídy `IOleControl` rozhraní a implementuje `IUnknown`.|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|Tato třída poskytuje metody pro pomoc komunikace mezi ovládací prvek na místě a jeho kontejneru.|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje metody, které umožňují ovládací prvek bez oken pro příjem zprávy okna a účastnit se operace přetažení myší.|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|Tato třída implementuje `IUnknown` a je hlavní rozhraní, přes který kontejner komunikuje s ovládacím prvkem.|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|Tato třída implementuje `IUnknown` a umožňuje klientům přístup k informacím na stránkách vlastností objektu.|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|Tato třída implementuje `IUnknown` a umožňuje uložit do kontejneru objektů klientem poskytnutý její vlastnosti.|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|Tato třída implementuje [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) rozhraní.|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci třídy [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) rozhraní.|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|Tato třída implementuje `IUnknown` a [IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) metody rozhraní.|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|Tato třída zveřejňuje [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) rozhraní jako odchozí rozhraní umožňující připojení k objektu.|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|Tato třída implementuje `IUnknown` a zdědí výchozí implementace [ipropertypageimpl –](../../atl/reference/ipropertypageimpl-class.md).|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci třídy [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) rozhraní.|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|Tato třída poskytuje výchozí implementaci třídy [iprovideclassinfo –](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) a [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) metody.|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|Tato třída kombinuje Inicializace řízení kontejnerů do jednoho volání.|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci třídy [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) rozhraní.|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|Tato třída poskytuje výchozí implementaci třídy `IServiceProvider` rozhraní.|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci třídy [ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) rozhraní.|atlcom.h|
|[Isupporterrorinfoimpl –](../../atl/reference/isupporterrorinfoimpl-class.md)|Tato třída poskytuje výchozí implementaci třídy `ISupportErrorInfo Interface` rozhraní a lze je použít, když pouze jedno rozhraní vygeneruje chyby na objekt.|atlcom.h|
|[IThreadPoolConfig – rozhraní](../../atl/reference/ithreadpoolconfig-interface.md)|Toto rozhraní poskytuje metody pro konfiguraci fondu vláken.|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci [IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), a [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) rozhraní.|atlctl.h|
|[IWorkerThreadClient – rozhraní](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient` představuje rozhraní implementované klienty [cworkerthread –](../../atl/reference/cworkerthread-class.md) třídy.|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|Tato třída poskytuje obálky pro `CreateWindow` a `CreateWindowEx`.|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|Tato třída argument adaptér umožňuje buď `RECT` ukazatele nebo odkazy, které se mají předat funkci, která je implementovaná jako ukazatele.|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|Tato třída argument adaptér umožňuje názvy prostředků (LPCTSTRs) nebo ID prostředků (uvedený), které se mají předat funkci bez nutnosti volajícího k převodu na řetězec za použití makra MAKEINTRESOURCE ID.|atlwin.h|
|[Win32threadtraits –](../../atl/reference/win32threadtraits-class.md)|Tato třída poskytuje funkce pro vytváření pro Windows vlákno. Pokud vlákno nebude používat funkce CRT, použijte tuto třídu.|atlbase.h|

## <a name="see-also"></a>Viz také:

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)<br/>
[Funkce](../../atl/reference/atl-functions.md)<br/>
[Globální proměnné](../../atl/reference/atl-global-variables.md)<br/>
[Definice TypeDef](../../atl/reference/atl-typedefs.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
