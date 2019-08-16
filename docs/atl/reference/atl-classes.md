---
title: Třídy a struktury ATL | Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 2bf13700ada3284b8a32718d21971e89e30e5b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498051"
---
# <a name="atl-classes-and-structs"></a>Třídy a struktury ATL

Knihovna ATL (Active Template Library) obsahuje následující třídy a struktury. Chcete-li najít konkrétní třídu podle kategorie, přečtěte si [Přehled třídy ATL](../../atl/atl-class-overview.md).

|Třída/struktura|Popis|Hlavičkový soubor|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|Obsahuje informace používané pro vykreslování do různých cílů, jako je například tiskárna, metasoubor nebo ovládací prvek ActiveX.|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|Obsahuje data instance třídy v kódu okna v ATL.|atlbase. h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|Používáno jakýmkoli projektem, který používá ATL.|atlbase. h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|Používá se v kódu souvisejícím s COM v ATL.| atlbase. h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|Obsahuje informace o typu používané k popisu metody nebo vlastnosti pro odesílající rozhraní.|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|Obsahuje data používaná všemi moduly ATL.|atlbase. h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|Používá se kódem okna v ATL.|atlbase. h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|Tato třída je používána makry převodu řetězce CA2TEX a CT2AEX a typedef CA2A.|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|Tato třída je používána makry převodu řetězce CA2CTEX a CT2CAEX a typedef CA2CA.|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|Tato třída se používá v makrech převodu řetězce CA2TEX, CA2CTEX, CT2WEX a CT2CWEX a v CA2W typedef.|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|Tato třída je obálkou pro přístupový token.|atlsecurity. h|
|[CAcl](../../atl/reference/cacl-class.md)|Tato třída je obálkou pro strukturu seznamu řízení přístupu (ACL).|atlsecurity. h|
|[CAdapt](../../atl/reference/cadapt-class.md)|Tato šablona se používá k zabalení tříd, které mění definici operátoru address-of tak, aby vracely něco jiného než adresu objektu.|Atlcomcli. h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|Tato třída implementuje objekt Array.|atlcoll. h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|Tato třída implementuje Server COM ve fondu vláken s modelem Apartment.|atlbase. h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|Tato třída poskytuje metody pro implementaci serveru modelu COM s více vlákny ve fondu.|atlbase. h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|Tato třída je vytvořena v každém projektu ATL.|atlcore. h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|Tato třída implementuje modul COM serveru.|atlbase. h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|Tato třída poskytuje podporu pro rozhraní ladění.|atlbase. h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|Tato třída reprezentuje modul pro knihovnu DLL.|atlbase. h|
|[CAtlException](../../atl/reference/catlexception-class.md)|Tato třída definuje výjimku ATL.|atlexcept. h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|Tato třída reprezentuje modul pro aplikaci.|atlbase. h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|Tato třída poskytuje tenké obálky kolem rozhraní API pro zpracování souborů systému Windows.|atlfile. h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|Tato třída reprezentuje soubor mapované paměti a přidává do metod [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)operátor přetypování.|atlfile. h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|Tato třída reprezentuje soubor mapované paměti.|atlfile. h|
|[CAtlList](../../atl/reference/catllist-class.md)|Tato třída poskytuje metody pro vytváření a správu objektu seznamu.|atlcoll. h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|Tato třída poskytuje metody pro vytvoření a správu objektu mapy.|atlcoll. h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|Tato třída poskytuje metody používané několika třídami modulů ATL.|atlbase. h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|Tato třída implementuje modul ATL.|atlbase. h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|Tato třída je implementací okna ATL okna, které je umístěno v hostitelském okně poskytnutém prostředím pro bohatou verzi Preview.|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|Tato třída implementuje službu.|atlbase. h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|Tato třída poskytuje metody pro vytvoření a použití dočasného souboru.|atlfile. h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|Tato třída poskytuje obálku funkcí správce transakcí jádra (KTM).|atltransactionmanager. h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|Tato třída poskytuje podporu pro komponenty okna knihovny ATL.|atlbase. h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|Tato třída reprezentuje objekt inteligentního ukazatele.|atlbase. h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|Tato třída poskytuje metody užitečné při vytváření pole inteligentních ukazatelů.|atlbase. h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice typedef užitečné při vytváření kolekcí inteligentních ukazatelů.|atlcoll. h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|Tato třída poskytuje metody užitečné při sestavování seznamu inteligentních ukazatelů.|atlcoll. h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|Tato třída reprezentuje objekt inteligentního ukazatele pomocí operátorů Vector New a DELETE.|atlbase. h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice typedef užitečné při vytváření kolekcí inteligentních ukazatelů pomocí operátorů Vector New a DELETE.|atlcoll. h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|Tato třída implementuje dialogové okno (modální nebo nemodální), které hostuje ovládací prvky ActiveX.|atlwin. h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|Tato třída poskytuje metody pro práci s oknem, který je hostitelem ovládacího prvku ActiveX.|atlwin. h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|Tato třída poskytuje metody pro práci s oknem, který je hostitelem ovládacího prvku ActiveX a také podporuje hostování licencovaných ovládacích prvků ActiveX.|atlwin. h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|Tato třída implementuje `IBindStatusCallback` rozhraní.|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|Tato třída implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro agregovaný objekt.|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|Tato třída poskytuje metody pro správu paměti pomocí rutin paměti modelu COM.|atlbase. h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|Tato třída poskytuje podporu pro správu objektů Apartment v modulu EXE ve fondu vláken.|atlbase. h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritického oddílu.|atlcore. h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|Od ATL 7,0 `CComAutoThreadModule` je zastaralé: Další informace naleznete v [modulech ATL](../../atl/atl-module-classes.md) .|atlbase. h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|Tato třída je obálkou pro BSTR.|atlbase. h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|Tato třída implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro odkládací rozhraní.|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|Tato třída implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|Tato třída implementuje rozhraní [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|Tato třída implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) a umožňuje vytvářet objekty ve více objektech Apartment.|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|Tato třída je odvozena z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|Tato třída poskytuje metody pro vytváření instancí třídy a získání jejích vlastností.|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|Tato třída poskytuje metody vyžadované k implementaci složeného ovládacího prvku.|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|Tato třída implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pomocí delegování objektu `IUnknown`vlastníka.|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|Tato třída poskytuje metody pro vytváření a správu ovládacích prvků ATL.|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|Tato třída poskytuje metody pro vytváření a správu ovládacích prvků ATL.|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritického oddílu.|atlcore. h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|Tato třída poskytuje metody pro uzamykání a odemknutí kritického objektu oddílu.|atlbase. h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|Tato třída obsahuje metody a operátory pro vytváření a správu objektu měny.|atlcur.h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|Tato třída ukládá pole `IUnknown` ukazatelů.|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|Tato třída definuje objekt enumerátoru COM založený na poli.|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|Tato třída poskytuje implementaci rozhraní enumerátoru modelu COM, kde jsou položky výčtové v poli uloženy.|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|Tato třída definuje objekt enumerátoru COM na základě C++ standardní kolekce knihoven.|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|Tato třída poskytuje stejné metody jako [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) , ale neposkytuje kritickou část.|atlcore. h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|Tato třída poskytuje metody pro práci s ukazateli rozhraní a globální tabulkou rozhraní (GIT).|atlbase. h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí přidělování paměti com.|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|Třída inteligentního ukazatele pro správu ukazatelů haldy.|atlbase. h|
|[CComModule](../../atl/reference/ccommodule-class.md)|Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v [modulech ATL](../../atl/atl-module-classes.md) .|atlbase. h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|Tato třída poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení hodnoty proměnné.|atlbase. h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|Tato třída poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení hodnoty proměnné bez důležitého zamykání oddílů nebo odemknutí funkčnosti.|atlbase. h|
|[CComObject](../../atl/reference/ccomobject-class.md)|Tato třída implementuje `IUnknown` neagregovaný objekt.|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|Tato třída spravuje počet odkazů pro modul, který obsahuje váš `Base` objekt.|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|Tato třída implementuje `IUnknown` neagregovaný objekt, ale nezvyšuje počet zámků modulu v konstruktoru.|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Tento typ typedef pro [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) je založena na výchozím modelu vláken serveru.|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|Tato třída poskytuje metody pro zpracování správy počtu odkazů na objekty pro neagregované i agregované objekty.|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|Tato třída vytvoří dočasný objekt COM a poskytne mu základní implementaci `IUnknown`.|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|Tato třída implementuje `IUnknown` agregovaný nebo neagregovaný objekt.|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|Třída inteligentního ukazatele pro správu ukazatelů rozhraní modelu COM.|Atlcomcli. h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|Tato třída poskytuje základ pro třídy inteligentních ukazatelů pomocí rutin paměti založených na modelu COM.|Atlcomcli. h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|Třída inteligentního ukazatele pro správu ukazatelů rozhraní modelu COM.|Atlcomcli. h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice typedef užitečné při vytváření kolekcí ukazatelů rozhraní modelu COM.|atlcoll. h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|Tato třída je obálkou pro `SAFEARRAY Data Type` strukturu.|atlsafe. h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|Tato třída je obálkou pro `SAFEARRAYBOUND` strukturu.|atlsafe. h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|Tato třída spravuje výběr vláken pro třídu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).|atlbase. h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|Tato třída poskytuje metody pro zvýšení a snížení hodnoty proměnné.|atlbase. h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|Tato třída implementuje odkládací rozhraní.|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|Tato třída ukládá `IUnknown` ukazatele a je navržena tak, aby se použila jako parametr pro třídu šablony [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|Tato třída zalomí typ VARIANT a poskytne člen označující typ uložených dat.|Atlcomcli. h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|Tato třída implementuje okno obsažené v jiném objektu.|atlwin. h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|Tato třída poskytuje metody pro správu paměti pomocí rutin paměti CRT.|atlcore. h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí haldy CRT.|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|Tato třída je obálkou pro seznam DACL (volitelný seznam řízení přístupu).|atlsecurity. h|
|[CDebugReportHook – třída](../../atl/reference/cdebugreporthook-class.md)|Tato třída slouží k posílání ladicích sestav do pojmenovaného kanálu.|atlutil.h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|Tato třída poskytuje dvě statické funkce pro převod znaků mezi velkými a malými písmeny.|atlcoll. h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|Tato třída poskytuje výchozí funkce pro porovnání prvků.|atlcoll. h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|Tato třída poskytuje výchozí metody a funkce pro třídu kolekce.|atlcoll. h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|Tato třída poskytuje statickou funkci pro výpočet hodnot hash.|atlcoll. h|
|[CDialogImpl –](../../atl/reference/cdialogimpl-class.md)|Tato třída poskytuje metody pro vytvoření modálního nebo nemodálního dialogového okna.|atlwin. h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|Tato třída poskytuje metody podporující dynamické řetězení map zpráv.|atlwin. h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|Tato třída je používána třídami kolekcí k poskytování metod a funkcí pro operace přesunu, kopírování, porovnání a zpracování hodnoty hash.|atlcoll. h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|Tato třída poskytuje výchozí metody kopírování a přesunutí pro třídu kolekce.|atlcoll. h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|Tato třída poskytuje metody pro upozorňování jímky kontejneru týkající se změn vlastností ovládacího prvku.|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí globálních funkcí haldy Win32.|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|Tato třída poskytuje metody pro vytvoření a použití objektu popisovače.|atlbase. h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|Třída inteligentního ukazatele pro správu ukazatelů haldy.|atlcore. h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|Tato třída tvoří základ pro několik tříd ukazatelů inteligentní haldy.|atlcore. h|
|[CHeapPtrElementTraits – třída](../../atl/reference/cheapptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice typedef užitečné při vytváření kolekcí ukazatelů haldy.|atlcoll. h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|Tato třída poskytuje metody užitečné při sestavování seznamu ukazatelů haldy.|atlcoll. h|
|[Služby CImage ve](../../atl-mfc-shared/reference/cimage-class.md)|Poskytuje rozšířenou podporu rastrového obrázku, včetně možnosti načítání a ukládání obrázků ve formátech JPEG, GIF, BMP a PNG (Portable Network Graphics).|atlimage. h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|Tato třída poskytuje metody užitečné při vytváření pole ukazatelů rozhraní modelu COM.|atlcoll. h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|Tato třída poskytuje metody užitečné při sestavování seznamu ukazatelů rozhraní modelu COM.|atlcoll. h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí lokální haldy Win32.|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|Tato třída umožňuje mapovat zprávy objektu na jiný objekt.|atlwin. h|
|[CNonStatelessWorker – třída](../../atl/reference/cnonstatelessworker-class.md)|Přijímá požadavky z fondu vláken a předává je do objektu pracovního procesu, který je vytvořen a zničen na každém požadavku.|atlutil.h|
|[CNoWorkerThread – třída](../../atl/reference/cnoworkerthread-class.md)|Tuto třídu použijte jako argument pro `MonitorClass` třídy mezipaměti parametrů šablony, pokud chcete zakázat údržbu dynamické mezipaměti.|atlutil.h|
|[CPathT – třída](../../atl/reference/cpatht-class.md)|Tato třída reprezentuje cestu.|atlpath. h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|Tato třída poskytuje výchozí metody a funkce pro třídu kolekce složenou ze primitivních datových typů.|atlcoll. h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|Tato třída reprezentuje objekt popisovače zabezpečení privátního objektu.|atlsecurity. h|
|[CRBMap](../../atl/reference/crbmap-class.md)|Tato třída reprezentuje strukturu mapování pomocí binárního stromu červeného černého.|atlcoll. h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|Tato třída reprezentuje strukturu mapování, která umožňuje přidružení každého klíče k více než jedné hodnotě pomocí binárního stromu červeného černého.|atlcoll. h|
|[CRBTree](../../atl/reference/crbtree-class.md)|Tato třída poskytuje metody pro vytvoření a použití červeného černého stromu.|atlcoll. h|
|[CRegKey](../../atl/reference/cregkey-class.md)|Tato třída poskytuje metody pro manipulaci s položkami v systémovém registru.|atlbase. h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|Tato třída poskytuje funkci vytváření pro vlákno CRT. Tuto třídu použijte v případě, že vlákno bude používat funkce CRT.|atlbase. h|
|[CSacl](../../atl/reference/csacl-class.md)|Tato třída je obálkou struktury SACL (seznam řízení přístupu k systému).|atlsecurity. h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|Tato třída je tenkou obálkou pro `SECURITY_ATTRIBUTES` strukturu.|atlsecurity. h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|Tato třída je obálkou pro `SECURITY_DESCRIPTOR` strukturu.|atlsecurity. h|
|[Identifikátor](../../atl/reference/csid-class.md)|Tato třída je obálkou `SID` struktury (identifikátoru zabezpečení).|atlsecurity. h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|Tato třída poskytuje metody pro správu jednoduchého pole.|atlsimpcoll. h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|Tato třída je pomocná pro třídu [CSimpleArray](../../atl/reference/csimplearray-class.md) .|atlsimpcoll. h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|Tato třída je pomocná pro třídu [CSimpleArray](../../atl/reference/csimplearray-class.md) .|atlsimpcoll. h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|Tato třída implementuje základní modální dialogové okno.|atlwin. h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|Tato třída poskytuje podporu pro jednoduché pole mapování.|atlsimpcoll. h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|Tato třída je pomocná pro třídu [CSimpleMap](../../atl/reference/csimplemap-class.md) .|atlsimpcoll. h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|Tato třída je pomocná pro třídu [CSimpleMap](../../atl/reference/csimplemap-class.md) .|atlsimpcoll. h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|Tato třída poskytuje metody pro implementaci objektu uzlu modulu snap-in.|atlsnap. h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|Tato třída poskytuje metody pro implementaci objektu stránky vlastností modulu snap-in.|atlsnap. h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|Tato třída poskytuje metody pro podporu hodnot uložených vlastností.|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|Tato třída poskytuje statické funkce, které používají třídy kolekcí `CString` pro ukládání objektů.|CStringT. h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|Tato třída poskytuje statické funkce související s řetězci uloženými v objektech třídy kolekce. Je podobný jako [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), ale provádí porovnávání bez rozlišování velkých a malých písmen.|atlcoll. h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|Tato třída poskytuje statické funkce související s řetězci uloženými v objektech třídy kolekce. Řetězcové objekty jsou řešeny jako odkazy.|atlcoll. h|
|[CThreadPool – třída](../../atl/reference/cthreadpool-class.md)|Tato třída poskytuje fond pracovních vláken, která zpracovávají frontu pracovních položek.|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|Tato třída je obálkou pro `TOKEN_GROUPS` strukturu.|atlsecurity. h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|Tato třída je obálkou pro `TOKEN_PRIVILEGES` strukturu.|atlsecurity. h|
|[CUrl – třída](../../atl/reference/curl-class.md)|Tato třída představuje adresu URL. Umožňuje manipulaci s každým prvkem adresy URL nezávisle na tom, zda analyzuje existující řetězec adresy URL nebo vytváří řetězec od začátku.|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|Tato třída se používá v makrech převodu řetězce CT2AEX, CW2TEX, CW2CTEX a CT2CAEX a v CW2A typedef.|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|Tato třída je používána makry převodu řetězce CW2CTEX a CT2CWEX a typedef CW2CW.|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|Tato třída je používána makry převodu řetězce CW2TEX a CT2WEX a typedef CW2W.|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí přidělení haldy Win32.|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|Tato třída poskytuje metody pro manipulaci s oknem.|atlwin. h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|Tato třída poskytuje metody pro vytvoření nebo roztřídění okna.|atlwin. h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|Tato třída poskytuje metodu pro standardizaci stylů použitých při vytváření objektu okna.|atlwin. h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|Tato třída poskytuje metodu pro standardizaci stylů použitých při vytváření objektu okna.|atlwin. h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|Tato třída poskytuje metody pro registraci informací pro třídu okna.|atlwin. h|
|[CWorkerThread – třída](../../atl/reference/cworkerthread-class.md)|Tato třída vytvoří pracovní vlákno nebo použije existující, počká na jeden nebo více popisovačů objektů jádra a spustí zadanou klientskou funkci, pokud je jeden z popisovačů signalizována.|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|Tato třída představuje rozhraní pro `CreateInstance` metodu.|atlbase. h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|Tato třída představuje rozhraní pro správce paměti.|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|Toto rozhraní poskytuje metody pro určení vlastností hostovaného ovládacího prvku nebo kontejneru.|atlbase. h, ATLIFace. h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|Toto rozhraní implementuje dodatečné ambientní vlastnosti hostovaného ovládacího prvku.|atlbase. h, ATLIFace. h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|Toto rozhraní poskytuje metody pro manipulaci s ovládacím prvkem a jeho hostitelským objektem.|atlbase. h, ATLIFace. h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|Toto rozhraní poskytuje metody pro manipulaci s licencovaným ovládacím prvkem a jeho hostitelským objektem.|atlbase. h, ATLIFace. h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|Tato třída poskytuje metody používané třídou kolekce.|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|Tato třída implementuje kontejner spojovacího bodu pro správu kolekce objektů [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|Tato třída implementuje bod připojení.|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|Tato třída poskytuje metody pro podporu jednotných Přenos dat a správu připojení.|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|Tato třída poskytuje výchozí implementaci pro `IDispatch` část duálního rozhraní.|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|Tato třída poskytuje implementace `IDispatch` metod.|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|Tato třída poskytuje implementace `IDispatch` metod bez získání informací o typu z knihovny typů.|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Rozhraní pro modul analýzy a vykreslování Microsoft HTML.|atlbase. h, ATLIFace. h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|Tato třída definuje rozhraní enumerátoru na základě C++ standardní kolekce knihoven.|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|Tato třída poskytuje výchozí implementaci `IObjectSafety` rozhraní, aby klient mohl načítat a nastavovat bezpečnostní úrovně objektu.|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|Tato třída poskytuje metody, které umožňují objektu komunikovat s jeho lokalitou.|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|Tato třída poskytuje výchozí implementaci `IOleControl` rozhraní a implementuje. `IUnknown`|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|Tato třída poskytuje metody pro pomoc s komunikací mezi místně umístěným ovládacím prvkem a jeho kontejnerem.|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje metody, které umožňují řízení bez oken přijímat zprávy oken a zúčastnit se operací přetažení.|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|Tato třída implementuje `IUnknown` a je hlavní rozhraní, pomocí kterého kontejner komunikuje s ovládacím prvkem.|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|Tato třída implementuje `IUnknown` a umožňuje klientovi přístup k informacím na stránkách vlastností objektu.|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|Tato třída implementuje `IUnknown` a umožňuje objektu ukládat jeho vlastnosti do kontejneru vlastností dodaných klientem.|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|Tato třída implementuje rozhraní [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) .|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci rozhraní [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|Tato třída implementuje `IUnknown` a metody rozhraní [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) .|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|Tato třída zpřístupňuje rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) jako odchozí rozhraní na připojeném objektu.|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|Tato třída implementuje `IUnknown` a dědí výchozí implementaci [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci rozhraní [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) .|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|Tato třída poskytuje výchozí implementaci metod [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) a [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) .|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|Tato třída kombinuje inicializaci ovládacího prvku Containers do jednoho volání.|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci rozhraní [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) .|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|Tato třída poskytuje výchozí implementaci `IServiceProvider` rozhraní.|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci rozhraní [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) .|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|Tato třída poskytuje výchozí implementaci `ISupportErrorInfo Interface` rozhraní a lze jej použít, pokud pouze jedno rozhraní generuje chyby v objektu.|atlcom.h|
|[IThreadPoolConfig – rozhraní](../../atl/reference/ithreadpoolconfig-interface.md)|Toto rozhraní poskytuje metody pro konfiguraci fondu vláken.|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|Tato třída implementuje `IUnknown` a poskytuje výchozí implementace rozhraní [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)a [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) .|atlctl.h|
|[IWorkerThreadClient – rozhraní](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient`je rozhraní implementované klienty třídy [CWorkerThread](../../atl/reference/cworkerthread-class.md) .|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|Tato třída poskytuje obálky pro `CreateWindow` a. `CreateWindowEx`|atlwin. h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|Tato třída adaptérů argumentů umožňuje `RECT` předání ukazatelů nebo odkazů do funkce, která je implementována v souvislosti s ukazateli.|atlwin. h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|Tato třída adaptéru argumentu umožňuje předat názvy prostředků (LPCTSTRs) nebo ID prostředků (UINTs) funkci bez nutnosti volajícího převést ID na řetězec pomocí makra MAKEINTRESOURCE.|atlwin. h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|Tato třída poskytuje funkci vytváření pro vlákno systému Windows. Tuto třídu použijte v případě, že vlákno nebude používat funkce CRT.|atlbase. h|

## <a name="see-also"></a>Viz také:

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)<br/>
[Funkce](../../atl/reference/atl-functions.md)<br/>
[Globální proměnné](../../atl/reference/atl-global-variables.md)<br/>
[Definice typedef](../../atl/reference/atl-typedefs.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
