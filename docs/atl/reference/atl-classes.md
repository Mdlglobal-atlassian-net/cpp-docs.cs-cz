---
title: ATL – třídy a struktury | Microsoft Docs
ms.custom: ''
ms.date: 05/03/2018
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e887f0adb7812664047fd30c3d9bb48368b9b564
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255750"
---
# <a name="atl-classes-and-structs"></a>ATL – třídy a struktury
Aktivní šablony Library (ATL) zahrnuje následující třídy a struktury. Určité třídy podle kategorie naleznete v tématu [přehledu třídy ATL](../../atl/atl-class-overview.md).  
  
|Třída nebo struktura|Popis|Soubor hlaviček|  
|-----------|-----------------|-----------------|  
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|Obsahuje informace, které slouží pro vykreslení na různé cíle, jako jsou tiskárny, metafile nebo ovládací prvek ActiveX.|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|Obsahuje data instance třídy v oddílová kódu v ATL.|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|Použít žádný projekt, který používá ATL.|atlbase.h|  
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|Používaný kód související s COM v ATL.| atlbase.h|  
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|Obsahuje informace o typu, které používají k popisu metody nebo vlastnosti na odesílajícím rozhraním.|atlcom.h|  
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|Obsahuje data využívaná každých ATL modulu.|atlbase.h|  
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|Používaný kód oddílová v ATL.|atlbase.h|  
|[CA2AEX](../../atl/reference/ca2aex-class.md)|Tato třída se používá ve makra převodů řetězec `CA2TEX` a `CT2AEX`a typedef **CA2A**.|atlconv.h|  
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|Tato třída se používá ve makra převodů řetězec `CA2CTEX` a `CT2CAEX`a typedef **CA2CA**.|atlconv.h|  
|[CA2WEX](../../atl/reference/ca2wex-class.md)|Tato třída se používá ve makra převodů řetězec `CA2TEX`, `CA2CTEX`, `CT2WEX`, a `CT2CWEX`a typedef **CA2W**.|atlconv.h|  
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|Tato třída je obálka pro přístupový token.|atlsecurity.h|  
|[CAcl](../../atl/reference/cacl-class.md)|Tato třída je obálka pro **seznamu ACL** struktury (seznamu řízení přístupu).|atlsecurity.h|  
|[CAdapt](../../atl/reference/cadapt-class.md)|Tato šablona se používá k zabalení tříd, které mění definici operátoru address-of tak, aby vracely něco jiného než adresu objektu.|atlcomcli.h|  
|[CAtlArray](../../atl/reference/catlarray-class.md)|Tato třída implementuje objekt array.|atlcoll.h|  
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|Tato třída implementuje server COM ve fondu vláken, apartment model.|atlbase.h|  
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|Tato třída poskytuje metody pro implementaci serveru COM ve fondu vláken, apartment model.|atlbase.h|  
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|Ve všech projektech ATL vytvoření instance této třídy.|atlcore.h|  
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|Tato třída implementuje modul COM serveru.|atlbase.h|  
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|Tato třída poskytuje podporu pro ladění v rozhraní.|atlbase.h|  
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|Tato třída představuje modul pro knihovny DLL.|atlbase.h|  
|[CAtlException](../../atl/reference/catlexception-class.md)|Tato třída definuje výjimku ATL.|atlexcept.h|  
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|Tato třída reprezentuje modul pro aplikaci.|atlbase.h|  
|[CAtlFile](../../atl/reference/catlfile-class.md)|Tato třída poskytuje dynamické obálku kolem Windows zpracování souborů rozhraní API.|atlfile.h|  
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|Tato třída reprezentuje soubor mapované paměti, operátor přetypování přidávání do metod třídy [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).|atlfile.h|  
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|Tato třída reprezentuje soubor mapované paměti.|atlfile.h|  
|[CAtlList](../../atl/reference/catllist-class.md)|Tato třída poskytuje metody pro vytváření a správu objekt seznamu.|atlcoll.h|  
|[CAtlMap](../../atl/reference/catlmap-class.md)|Tato třída poskytuje metody pro vytváření a správu objekt map.|atlcoll.h|  
|[CAtlModule](../../atl/reference/catlmodule-class.md)|Tato třída poskytuje metody používané v několika ATL – třídy modulů.|atlbase.h|  
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|Tato třída implementuje modul ATL.|atlbase.h|  
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|Tato třída je implementací ATL okno, které je umístěn na hostitelské okno poskytuje prostředí pro verzi Preview formátováním.|atlpreviewctrlimpl.h|  
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|Tato třída implementuje služby.|atlbase.h|  
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|Tato třída poskytuje metody pro vytváření a používání dočasný soubor.|atlfile.h|  
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|Tato třída poskytuje obálku pro funkce správce KTM (Kernel Transaction).|atltransactionmanager.h|  
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|Tato třída poskytuje podporu pro knihovny ATL oddílová součásti.|atlbase.h|  
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|Tato třída reprezentuje objekt chytré ukazatele.|atlbase.h|  
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|Tato třída poskytuje metody, které jsou užitečné při vytváření pole chytré ukazatele.|atlbase.h|  
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice TypeDef užitečné při vytváření kolekcí chytré ukazatele.|atlcoll.h|  
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|Tato třída poskytuje metody, které jsou užitečné při sestavování seznamu chytré ukazatele.|atlcoll.h|  
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|Tato třída reprezentuje objekt chytré ukazatele pomocí vektoru nové a odstraňte operátory.|atlbase.h|  
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice TypeDef užitečné při vytváření kolekcí chytré ukazatele pomocí vektoru nové a odstranit operátory.|atlcoll.h|  
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|Tato třída implementuje dialogové okno (modální nebo nemodální), který je hostitelem – ovládací prvky ActiveX.|atlwin.h|  
|[CAxWindow](../../atl/reference/caxwindow-class.md)|Tato třída poskytuje metody pro práci s okno hostování ovládacího prvku ActiveX.|atlwin.h|  
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|Tato třída poskytuje metody pro práci s okno, které hostuje ovládacího prvku ActiveX a má také podpora pro hostování licencované ovládací prvky ActiveX.|atlwin.h|  
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|Tato třída implementuje `IBindStatusCallback` rozhraní.|atlctl.h|  
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|Tato třída implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) agregovaného objektu.|atlcom.h|  
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|Tato třída poskytuje metody pro správu paměti pomocí rutiny paměti COM.|atlbase.h|  
|[CComApartment](../../atl/reference/ccomapartment-class.md)|Tato třída poskytuje podporu pro správu v modulu EXE ve fondu vláken typu apartment.|atlbase.h|  
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|Tato třída poskytuje metody pro získání a uvolněním vlastnictví objektu kritická sekce.|atlcore.h|  
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL moduly](../../atl/atl-module-classes.md) další podrobnosti.|atlbase.h|  
|[CComBSTR](../../atl/reference/ccombstr-class.md)|Tato třída je obálka pro `BSTR`s.|atlbase.h|  
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|Tato třída implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pro rozhraní úplné vypnutí.|atlcom.h|  
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|Tato třída implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní.|atlcom.h|  
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|Tato třída implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) rozhraní.|atlcom.h|  
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|Tato třída implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní a umožňuje vytvořit v několika Apartment objekty.|atlcom.h|  
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|Tato třída odvozená z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.|atlcom.h|  
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|Tato třída poskytuje metody pro vytvoření instance třídy a získání jeho vlastnosti.|atlcom.h|  
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|Tato třída poskytuje metody potřebnou k implementaci složeného ovládacího prvku.|atlctl.h|  
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|Tato třída implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) delegováním k objektu vlastníka **IUnknown**.|atlcom.h|  
|[CComControl](../../atl/reference/ccomcontrol-class.md)|Tato třída poskytuje metody pro vytváření a správu ATL ovládací prvky.|atlctl.h|  
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|Tato třída poskytuje metody pro vytváření a správu ATL ovládací prvky.|atlctl.h|  
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|Tato třída poskytuje metody pro získání a uvolněním vlastnictví objektu kritická sekce.|atlcore.h|  
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|Tato třída poskytuje metody pro zamykání a odemykání objekt kritická sekce.|atlbase.h|  
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|Tato třída obsahuje metody a operátory k vytváření a správě `CURRENCY` objektu.|atlcur.h|  
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|Tato třída ukládá pole **IUnknown** ukazatele.|atlcom.h|  
|[CComEnum](../../atl/reference/ccomenum-class.md)|Tato třída definuje objekt enumerator COM na základě pole.|atlcom.h|  
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|Tato třída poskytuje implementaci pro rozhraní modelu COM enumerátor ve výčtu jsou umístění v matici.|atlcom.h|  
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|Tato třída definuje objekt enumerator COM na základě kolekce standardní knihovna C++.|atlcom.h|  
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|Tato třída poskytuje stejné metody jako [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) , ale neposkytuje kritická sekce.|atlcore.h|  
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|Tato třída poskytuje metody pro práci s ukazatele rozhraní a globální rozhraní tabulku (GIT).|atlbase.h|  
|[CComHeap](../../atl/reference/ccomheap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkce přidělení paměti COM.|ATLComMem.h|  
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|Chytré ukazatele třída pro správu haldy ukazatele.|atlbase.h|  
|[CComModule](../../atl/reference/ccommodule-class.md)|Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL moduly](../../atl/atl-module-classes.md) další podrobnosti.|atlbase.h|  
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|Tato třída poskytuje metody vláken pro zvyšování a dekrementace hodnotu proměnné.|atlbase.h|  
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|Tato třída poskytuje metody vláken pro zvyšování a dekrementace hodnotu proměnné, bez kritická sekce zamykání a odemykání funkce.|atlbase.h|  
|[CComObject](../../atl/reference/ccomobject-class.md)|Tato třída implementuje **IUnknown** neagregovaná objektu.|atlcom.h|  
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|Tato třída spravuje počet odkazů na modul obsahující vaše `Base` objektu.|atlcom.h|  
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|Tato třída implementuje **IUnknown** neagregovaná objektu, ale nemá není přírůstek zámek modulu počet v konstruktoru.|atlcom.h|  
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Tato definice typu z [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) je převést na šablonu na výchozí model serveru vláken.|atlcom.h|  
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|Tato třída poskytuje metody pro zpracování Správa počet odkaz objektu pro neagregovaná a agregované objekty.|atlcom.h|  
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|Tato třída vytvoří dočasný objekt COM a poskytne mu kosterního provádění **IUnknown**.|atlcom.h|  
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|Tato třída implementuje **IUnknown** pro agregovaná nebo neagregovaná objekt.|atlcom.h|  
|[CComPtr](../../atl/reference/ccomptr-class.md)|Chytré ukazatele třída pro správu ukazatele rozhraní COM.|atlcomcli.h|  
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|Tato třída poskytuje základ pro inteligentní ukazatel třídy pomocí rutiny založené na modelu COM paměti.|atlcomcli.h|  
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|Chytré ukazatele třída pro správu ukazatele rozhraní COM.|atlcomcli.h|  
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice TypeDef užitečné při vytváření kolekcí ukazatele rozhraní COM.|atlcoll.h|  
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|Tato třída je obálka pro `SAFEARRAY Data Type` struktura.|atlsafe.h|  
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|Tato třída je obálka pro `SAFEARRAYBOUND` struktury.|atlsafe.h|  
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|Tato třída spravuje výběr vlákno pro třídu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).|atlbase.h|  
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|Tato třída poskytuje metody pro zvyšování a dekrementace hodnotu proměnné.|atlbase.h|  
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|Tato třída implementuje rozhraní úplné vypnutí.|atlcom.h|  
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|Tato třída ukládá **IUnknown** ukazatele a je určen k použití jako parametr, který se [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) třídy šablony.|atlcom.h|  
|[CComVariant](../../atl/reference/ccomvariant-class.md)|Tato třída zabalí typ VARIANT poskytování členem označující typ data uložená.|atlcomcli.h|  
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|Tato třída implementuje okno obsažené v rámci jiného objektu.|atlwin.h|  
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|Tato třída poskytuje metody pro správu paměti pomocí rutiny CRT paměti.|atlcore.h|  
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) používání haldy funkcí CRT.|atlmem.h|  
|[CDacl](../../atl/reference/cdacl-class.md)|Tato třída je obálku pro strukturu DACL (seznam volitelného řízení přístupu).|atlsecurity.h|  
|[CDebugReportHook – třída](../../atl/reference/cdebugreporthook-class.md)|Tato třída slouží k ladění sestavy poslat pojmenovaný kanál.|atlutil.h|  
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|Tato třída poskytuje dvě statické funkce pro převod znaků mezi velká a malá písmena.|atlcoll.h|  
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|Tato třída poskytuje výchozí element porovnání funkcí.|atlcoll.h|  
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|Tato třída poskytuje výchozí metody a funkce pro třídu kolekce.|atlcoll.h|  
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|Tato třída poskytuje statické funkce pro výpočet hodnoty hash.|atlcoll.h|  
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|Tato třída poskytuje metody pro vytváření modální nebo nemodální dialogového okna.|atlwin.h|  
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|Tato třída poskytuje metody podporující dynamické řetězení mapy zpráv.|atlwin.h|  
|[CElementTraits](../../atl/reference/celementtraits-class.md)|Tato třída je používá k zajištění metody a funkce pro přesunutí, kopírování, porovnání a hash operace třídy kolekce.|atlcoll.h|  
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|Tato třída poskytuje výchozí kopírovat a přesouvat metody pro třídu kolekce.|atlcoll.h|  
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|Tato třída poskytuje metody pro oznamování kontejneru podřízený týkající se změny vlastností ovládacího prvku.|atlctl.h|  
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí globální haldy Win32.|atlmem.h|  
|[CHandle](../../atl/reference/chandle-class.md)|Tato třída poskytuje metody pro vytváření a používání objekt popisovače.|atlbase.h|  
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|Chytré ukazatele třída pro správu haldy ukazatele.|atlcore.h|  
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|Tato třída je základem pro několik tříd inteligentní haldy ukazatele.|atlcore.h|  
|[CHeapPtrElementTraits – třída](../../atl/reference/cheapptrelementtraits-class.md)|Tato třída poskytuje metody, statické funkce a definice TypeDef užitečné při vytváření kolekcí haldy ukazatele.|atlcoll.h|  
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|Tato třída poskytuje metody, které jsou užitečné při sestavování seznamu haldy ukazatele.|atlcoll.h|  
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Poskytuje podporu rozšířené rastrového obrázku, včetně možnosti spouštění a ukládání bitových kopií ve formátech JPEG, GIF, BMP a Portable Network Graphics (PNG).|atlimage.h|  
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|Tato třída poskytuje metody, které jsou užitečné při vytváření pole ukazatele rozhraní COM.|atlcoll.h|  
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|Tato třída poskytuje metody, které jsou užitečné při sestavování seznamu ukazatele rozhraní COM.|atlcoll.h|  
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí lokální haldy Win32.|atlmem.h|  
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|Tato třída umožňuje že přístup k jinému objektu mapy zpráv objektu.|atlwin.h|  
|[CNonStatelessWorker – třída](../../atl/reference/cnonstatelessworker-class.md)|Přijímá požadavky od fondu vláken a předává je na objekt pracovního procesu, který je vytvořen a zničen v každé žádosti.|atlutil.h|  
|[CNoWorkerThread – třída](../../atl/reference/cnoworkerthread-class.md)|Tato třída slouží jako argument pro `MonitorClass` mezipaměti parametr šablony třídy, pokud chcete zakázat dynamické mezipaměti údržby.|atlutil.h|  
|[CPathT – třída](../../atl/reference/cpatht-class.md)|Tato třída reprezentuje cestu.|atlpath.h|  
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|Tato třída poskytuje metody výchozí a funkce pro třídu kolekce tvořený primitivní datové typy.|atlcoll.h|  
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|Tato třída reprezentuje objekt popisovače zabezpečení soukromý objekt.|atlsecurity.h|  
|[CRBMap](../../atl/reference/crbmap-class.md)|Tato třída reprezentuje strukturou mapování pomocí binárního stromu Red černé.|atlcoll.h|  
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|Tato třída reprezentuje strukturu mapování, která umožňuje každý klíč, který se má přidružit více než jednu hodnotu, pomocí binárního stromu Red černé.|atlcoll.h|  
|[CRBTree](../../atl/reference/crbtree-class.md)|Tato třída poskytuje metody pro vytvoření a použití Red černé stromu.|atlcoll.h|  
|[CRegKey](../../atl/reference/cregkey-class.md)|Tato třída poskytuje metody pro práci s položky systémového registru.|atlbase.h|  
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|Tato třída poskytuje funkce vytváření CRT vlákna. Tuto třídu používejte, pokud vlákno používat funkce CRT.|atlbase.h|  
|[CSacl](../../atl/reference/csacl-class.md)|Tato třída je obálku pro strukturu SACL (seznam řízení přístupu systému).|atlsecurity.h|  
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|Tato třída je dynamické obálku pro **SECURITY_ATTRIBUTES** struktura.|atlsecurity.h|  
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|Tato třída je obálka pro **SECURITY_DESCRIPTOR** struktura.|atlsecurity.h|  
|[Identifikační číslo volané stanice](../../atl/reference/csid-class.md)|Tato třída je obálka pro `SID` struktury (security identifier).|atlsecurity.h|  
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|Tato třída poskytuje metody pro správu jednoduchých polí.|atlsimpcoll.h|  
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|Tato třída je Pomocník pro [CSimpleArray](../../atl/reference/csimplearray-class.md) třídy.|atlsimpcoll.h|  
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|Tato třída je Pomocník pro [CSimpleArray](../../atl/reference/csimplearray-class.md) třídy.|atlsimpcoll.h|  
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|Tato třída implementuje základní modální dialogové.|atlwin.h|  
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|Tato třída poskytuje podporu pro jednoduché mapování pole.|atlsimpcoll.h|  
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|Tato třída je Pomocník pro [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy.|atlsimpcoll.h|  
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|Tato třída je Pomocník pro [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy.|atlsimpcoll.h|  
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|Tato třída poskytuje metody pro implementaci objekt modul snap-in uzlu.|atlsnap.h|  
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|Tato třída poskytuje metody pro implementaci objekt modul snap-in Vlastnosti stránky.|atlsnap.h|  
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|Tato třída poskytuje metody pro podporu uložených vlastností hodnoty.|atlctl.h|  
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|Tato třída poskytuje statické funkce používá ukládání třídy kolekce `CString` objekty.|cstringt.h|  
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|Tato třída poskytuje statické funkce související s řetězce, které jsou uložené v objektech třídy kolekce. Je podobná [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), ale provádí porovnávání.|atlcoll.h|  
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|Tato třída poskytuje statické funkce související s řetězce, které jsou uložené v objektech třídy kolekce. Řetězec objekty jsou uvedeny jako odkazy.|atlcoll.h|  
|[CThreadPool – třída](../../atl/reference/cthreadpool-class.md)|Tato třída poskytuje fond pracovních vláken, které zpracovávají fronty pracovních položek.|atlutil.h|  
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|Tato třída je obálka pro **TOKEN_GROUPS** struktury.|atlsecurity.h|  
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|Tato třída je obálka pro **TOKEN_PRIVILEGES** struktury.|atlsecurity.h|  
|[CUrl – třída](../../atl/reference/curl-class.md)|Tato třída představuje adresu URL. Umožňuje pracovat s každý prvek adresy URL nezávisle na ostatních, zda analýza stávající adresy URL řetězec nebo vytváření řetězec od začátku.|atlutil.h|  
|[CW2AEX](../../atl/reference/cw2aex-class.md)|Tato třída se používá ve makra převodů řetězec `CT2AEX`, `CW2TEX`, `CW2CTEX`, a `CT2CAEX`a typedef **CW2A**.|atlconv.h|  
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|Tato třída se používá ve makra převodů řetězec `CW2CTEX` a `CT2CWEX`a typedef **CW2CW**.|atlconv.h|  
|[CW2WEX](../../atl/reference/cw2wex-class.md)|Tato třída se používá ve makra převodů řetězec `CW2TEX` a `CT2WEX`a typedef `CW2W`.|atlconv.h|  
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkce přidělení haldy Win32.|atlmem.h|  
|[CWindow](../../atl/reference/cwindow-class.md)|Tato třída poskytuje metody pro práci s časového období.|atlwin.h|  
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|Tato třída poskytuje metody pro vytvoření nebo vytvoření podtřídy časového období.|atlwin.h|  
|[CWinTraits](../../atl/reference/cwintraits-class.md)|Tato třída poskytuje metody pro standardizaci styly použité při vytváření objektu okno.|atlwin.h|  
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|Tato třída poskytuje metody pro standardizaci styly použité při vytváření objektu okno.|atlwin.h|  
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|Tato třída poskytuje metody pro registraci informace pro třídu okna.|atlwin.h|  
|[CWorkerThread – třída](../../atl/reference/cworkerthread-class.md)|Tato třída vytvoří pracovní vlákno nebo používá existující, čeká na jeden nebo více objektů obslužných rutin jádra a provede funkci zadaného klienta, když se jeden z obslužné rutiny pro zpracování signalizace.|atlutil.h|  
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|Tato třída reprezentuje rozhraní pro `CreateInstance` metoda.|atlbase.h|  
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|Tato třída reprezentuje rozhraní pro správce paměti.|atlmem.h|  
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|Toto rozhraní poskytuje metody pro zadání vlastnosti hostované řízení nebo kontejneru.|atlbase.h ATLIFace.h|  
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|Toto rozhraní implementuje dodatečné vedlejším vlastnostem hostované ovládacího prvku.|atlbase.h ATLIFace.h|  
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|Toto rozhraní poskytuje metody pro manipulaci s ovládacího prvku a jeho objekt hostitele.|atlbase.h ATLIFace.h|  
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|Toto rozhraní poskytuje metody pro manipulaci s licencované ovládací prvek a jeho objekt hostitele.|atlbase.h ATLIFace.h|  
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|Tato třída poskytuje metody používané v třídě kolekce.|atlcom.h|  
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|Tato třída implementuje kontejner bod připojení ke správě kolekce [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objekty.|atlcom.h|  
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|Tato třída implementuje bod připojení.|atlcom.h|  
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|Tato třída poskytuje metody pro podporu Uniform přenos dat a správě připojení.|atlctl.h|  
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|Tato třída poskytuje výchozí implementaci pro `IDispatch` část duální rozhraní.|atlcom.h|  
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|Tato třída poskytuje implementace `IDispatch` metody.|atlcom.h|  
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|Tato třída poskytuje implementace `IDispatch` metody bez získávání informací o typu z knihovny typů.|atlcom.h|  
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Rozhraní Microsoft HTML analýzy a modul vykreslování.|atlbase.h ATLIFace.h|  
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|Tato třída definuje enumerátor rozhraní na základě kolekce standardní knihovna C++.|atlcom.h|  
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|Tato třída poskytuje výchozí implementaci třídy `IObjectSafety` rozhraní a tak dovolit klientským k načtení a nastavení úrovně zabezpečení objektu.|atlctl.h|  
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|Tato třída poskytuje metody, které umožní objekt pro komunikaci se svou lokalitou.|atlcom.h|  
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|Tato třída poskytuje výchozí implementaci třídy **IOleControl** rozhraní a implementuje **IUnknown**.|atlctl.h|  
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|Tato třída poskytuje metody, které komunikaci mezi ovládacího prvku na místě a jejímu kontejneru.|atlctl.h|  
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|Tato třída implementuje **IUnknown** a poskytuje metody, které umožní ovládacího prvku bez oken pro příjem zpráv oken a zapojit se do operací přetažení myší.|atlctl.h|  
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|Tato třída implementuje **IUnknown** a je hlavní rozhraní, pomocí které kontejner komunikuje s ovládacím prvkem.|atlctl.h|  
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|Tato třída implementuje **IUnknown** a umožňuje klientům přístup k informacím na stránkách vlastností objektu.|atlctl.h|  
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|Tato třída implementuje **IUnknown** a umožňuje objekt uložení jeho vlastnosti do kontejneru objektů zadané klienta.|atlcom.h|  
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|Tato třída implementuje [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) rozhraní.|atlcom.h|  
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci třídy [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní.|atlcom.h|  
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|Tato třída implementuje **IUnknown** a [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) metody rozhraní.|atlctl.h|  
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|Tato třída zpřístupní [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní jako odchozí rozhraní na objekt umožňující připojení.|atlctl.h|  
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|Tato třída implementuje **IUnknown** a dědí výchozí implementaci [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).|atlctl.h|  
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci třídy [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) rozhraní.|atlctl.h|  
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|Tato třída poskytuje výchozí implementaci třídy [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) a [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) metody.|atlcom.h|  
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|Tato třída kombinuje Inicializace řízení kontejnerů do jednoho volání.|atlctl.h|  
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci třídy [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) rozhraní.|atlctl.h|  
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|Tato třída poskytuje výchozí implementaci třídy `IServiceProvider` rozhraní.|atlcom.h|  
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci třídy [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) rozhraní.|atlcom.h|  
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|Tato třída poskytuje výchozí implementaci třídy `ISupportErrorInfo Interface` rozhraní a lze použít při pouze jedno rozhraní generuje chyby na objekt.|atlcom.h|  
|[IThreadPoolConfig – rozhraní](../../atl/reference/ithreadpoolconfig-interface.md)|Toto rozhraní poskytuje metody pro konfiguraci fondu vláken.|atlutil.h|  
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), a [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)rozhraní.|atlctl.h|  
|[IWorkerThreadClient – rozhraní](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient` představuje rozhraní implementované klienty [CWorkerThread](../../atl/reference/cworkerthread-class.md) třídy.|atlutil.h|  
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|Tato třída poskytuje obálek pro **CreateWindow** a **CreateWindowEx**.|atlwin.h|  
|[_U_RECT](../../atl/reference/u-rect-class.md)|Tato třída argument adaptér umožňuje buď `RECT` ukazatele nebo odkazy, které mají být předány funkci, která je implementovaná z hlediska ukazatele.|atlwin.h|  
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|Tato třída argument adaptér umožňuje buď názvy prostředků (`LPCTSTR`s) nebo ID prostředku (**Celé_číslo**s) mají být předány funkce bez nutnosti volající převést na řetězec pomocí ID **MAKEINTRESOURCE** makro.|atlwin.h|  
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|Tato třída poskytuje funkce vytváření vlákna systému Windows. Tuto třídu používejte, pokud vlákno nebude používat funkce CRT.|atlbase.h|  
  
## <a name="see-also"></a>Viz také  
 [ATL COM plochy součásti](../../atl/atl-com-desktop-components.md)   
 [Funkce](../../atl/reference/atl-functions.md)   
 [Globální proměnné](../../atl/reference/atl-global-variables.md)   
 [Definice TypeDef](../../atl/reference/atl-typedefs.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)


