---
title: "TN038: MFC OLE – implementace třídy IUnknown | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.ole
dev_langs: C++
helpviewer_keywords:
- aggregation macros [MFC]
- COM interfaces, base interface
- IUnknown interface
- END_INTERFACE_MAP macro [MFC]
- TN038
- BEGIN_INTERFACE_PART macro [MFC]
- DECLARE_INTERFACE_MAP macro [MFC]
- BEGIN_INTERFACE_MAP macro [MFC]
- OLE [MFC], implementing IUnknown interface
- METHOD_PROLOGUE macro [MFC]
- STDMETHOD macro [MFC]
- END_INTERFACE_PART macro [MFC]
- INTERFACE_PART macro
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6ef848d5b00df1140850e19611a426d289539ef0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: MFC/OLE – implementace třídy IUnknown
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Jádrem OLE 2 je "OLE – Komponentový objektový Model" nebo COM. COM definuje standard pro objekty, jak spolupracující komunikaci mezi sebou. To zahrnuje podrobnosti o jaké "objekt" vypadá jako, včetně toho, jak jsou metody odeslaných na objekt. COM také definuje základní třídu, ze které jsou odvozeny všechny kompatibilní třídy COM. Tato základní třída je [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509). I když [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) rozhraní se označuje jako třída C++, COM není specifická pro žádné jeden jazyk – se dá implementovat v C, PASCAL nebo jiného jazyka, který může podporovat binární rozložení objektu COM.  
  
 OLE odkazuje na všechny třídy odvozené od [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) jako "rozhraní." Jde o důležité odlišení od "rozhraní", jako [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) představuje s ním žádné implementace. Definuje jednoduše protokol, podle kterého objekty komunikovat, není specifika co dělat tyto implementace. To je možné logicky pro systém, který umožňuje flexibilní. Je na MFC úlohy k implementaci výchozí chování pro MFC/C++ – programy.  
  
 Zjistit implementace MFC na [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) nejdřív je potřeba pochopit, co toto rozhraní je. Zjednodušené verzi [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) je definován pod:  
  
```  
class IUnknown  
{  
public:  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;  
    virtual ULONG AddRef() = 0;  
    virtual ULONG Release() = 0;  
};  
```  
  
> [!NOTE]
>  Podrobnosti určité nezbytné konvence volání, jako například `__stdcall` jsou ponechána pro tento obrázek.  
  
 [Addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317) členské funkce řízení správy paměti objektu. COM používá ke sledování objektů počítání schéma odkazu. Objekt se nikdy odkazuje přímo, stejně jako v jazyce C++. Místo toho COM – objekty odkazují vždy prostřednictvím ukazatele. K uvolnění objektu, pokud se provádí vlastník pomocí jeho, objekt [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317) člen nazývá (na rozdíl od použití delete – operátor, jako by být provedeno pro tradiční C++ objekt). Počítání mechanismus referencí umožňuje více odkazů pro jediný objekt ke správě. Implementace [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317) udržuje počet odkazů na objekt – tento objekt není odstranit, dokud jeho počet odkazů hodnota nula.  
  
 [Addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317) jsou poměrně jednoduché z hlediska implementace. Tady je trivial implementace:  
  
```  
ULONG CMyObj::AddRef()   
{   
    return ++m_dwRef;   
}  
 
ULONG CMyObj::Release()   
{   
    if (--m_dwRef == 0)   
 {  
    delete this;   
    return 0;  
 }  
    return m_dwRef;  
}  
```  
  
 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) je o něco zajímavějšího – členská funkce. Není velmi zajímavé pro objekt, jehož jediným členské funkce jsou [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317) – je dobrý říct objekt, který chcete provádět další akce, než [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) poskytuje. To je, kdy [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) je užitečné. Umožňuje získat jiné "rozhraní" na stejný objekt. Tato rozhraní jsou obvykle odvozená od [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) a přidat další funkce přidáním nové členské funkce. COM – rozhraní nikdy mít člen proměnných deklarovaných v rozhraní a všechny členské funkce, které jsou deklarovány jako čistý virtuální. Například  
  
```  
class IPrintInterface : public IUnknown  
{  
public:  
    virtual void PrintObject() = 0;  
};  
```  
  
 Chcete-li získat IPrintInterface, pokud máte pouze [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), volání [QueryInterface –](http://msdn.microsoft.com/library/windows/desktop/ms682521) pomocí `IID` z **IPrintInterface**. `IID` Je 128-bit číslo, které jednoznačně identifikuje rozhraní. Došlo `IID` pro každém rozhraní, které můžete případně OLE definovat. Pokud `pUnk` je ukazatel na [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) objekt, může být kód pro načtení IPrintInterface z něj:  
  
```  
IPrintInterface* pPrint = NULL;  
if (pUnk->QueryInterface(IID_IPrintInterface,   
 (void**)&pPrint) == NOERROR)  
{  
    pPrint->PrintObject();
pPrint->Release();
*// release pointer obtained via QueryInterface  
}  
```  
  
 Který zdá se, že poměrně snadno, ale jak můžete implementovat jako objekt podporující i IPrintInterface a [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) rozhraní v tomto případě je jednoduchý vzhledem k tomu, že IPrintInterface je odvozený přímo z [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) – implementací IPrintInterface, [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) je automaticky dostupná podpora. Příklad:  
  
```  
class CPrintObj : public CPrintInterface  
{  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);

    virtual ULONG AddRef();
virtual ULONG Release();
virtual void PrintObject();

};  
```  
  
 Implementace [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317) by přesně stejné jako ty, které jsou implementované výše. **CPrintObj::QueryInterface** by vypadat přibližně takto:  
  
```  
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)  
{  
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)  
 {  
 *ppvObj = this;  
    AddRef();
return NOERROR;  
 }  
    return E_NOINTERFACE;  
}  
```  
  
 Jak můžete vidět, pokud se rozpozná identifikátor rozhraní (IID), ukazatel je vrácen do objektu; v opačném případě dojde k chybě. Všimněte si také, že úspěšně [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) vede předpokládané [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379). Samozřejmě také nutné implementovat CEditObj::Print. To je jednoduché, protože IPrintInterface přímo odvozený z [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) rozhraní. Ale pokud jste chtěli podporovat dvě různé rozhraní, i odvozený od [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), zvažte následující:  
  
```  
class IEditInterface : public IUnkown  
{  
public:  
    virtual void EditObject() = 0;  
};  
```  
  
 I když existuje několik různých způsobů, jak implementovat třídu podpora IEditInterface a IPrintInterface, včetně použití C++ vícenásobná dědičnost tato poznámka se zaměří na použití vnořené třídy k implementaci tuto funkci.  
  
```  
class CEditPrintObj  
{  
public:  
    CEditPrintObj();

 
    HRESULT QueryInterface(REFIID iid,
    void**);

    ULONG AddRef();
ULONG Release();
DWORD m_dwRef;  
 
    class CPrintObj : public IPrintInterface  
 {  
    public: 
    CEditPrintObj* m_pParent;  
    virtual HRESULT QueryInterface(REFIID iid,
    void** ppvObj);

    virtual ULONG AddRef();
virtual ULONG Release();

 } m_printObj;  
 
    class CEditObj : public IEditInterface  
 {  
    public: 
    CEditPrintObj* m_pParent;  
    virtual ULONG QueryInterface(REFIID iid,
    void** ppvObj);

    virtual ULONG AddRef();
virtual ULONG Release();

 } m_editObj;  
};  
```  
  
 Dále jsou uvedeny celý implementace:  
  
```  
CEditPrintObj::CEditPrintObj()  
{  
    m_editObj.m_pParent = this;  
    m_printObj.m_pParent = this;  
}  
 
ULONG CEditPrintObj::AddRef()   
{   
    return ++m_dwRef;  
}  
 
CEditPrintObj::Release()  
{  
    if (--m_dwRef == 0)  
 {  
    delete this;  
    return 0;  
 }  
    return m_dwRef;  
}  
 
HRESULT CEditPrintObj::QueryInterface(REFIID iid,
    void** ppvObj)  
{  
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)  
 {  
 *ppvObj = &m_printObj;  
    AddRef();
return NOERROR;  
 }  
    else if (iid == IID_IEditInterface)  
 {  
 *ppvObj = &m_editObj;  
    AddRef();
return NOERROR;  
 }  
    return E_NOINTERFACE;  
}  
 
ULONG CEditPrintObj::CEditObj::AddRef()   
{   
    return m_pParent->AddRef();

}  
 
ULONG CEditPrintObj::CEditObj::Release()   
{   
    return m_pParent->Release();

}  
 
HRESULT CEditPrintObj::CEditObj::QueryInterface(
    REFIID iid,
    void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid,
    ppvObj);

}  
 
ULONG CEditPrintObj::CPrintObj::AddRef()   
{   
    return m_pParent->AddRef();

}  
 
ULONG CEditPrintObj::CPrintObj::Release()   
{   
    return m_pParent->Release();

}  
 
HRESULT CEditPrintObj::CPrintObj::QueryInterface(
    REFIID iid,
    void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid,
    ppvObj);

}  
```  
  
 Všimněte si, že většina [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) implementace je umístěn do třídy CEditPrintObj místo duplikování kód v CEditPrintObj::CEditObj a CEditPrintObj::CPrintObj. To snižuje množství kódu a zabraňuje chyby. Klíče bod je, aby bylo možné k volání z rozhraní IUnknown [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) k načtení všech rozhraní může podporovat objekt, a z každé z těchto rozhraní je možné provést stejný. To znamená, že všechny [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funkce dostupné z každé rozhraní musí chovají stejným způsobem. Aby tyto vložené objekty volat implementace v "vnější objekt" je back ukazatel použité (m_pParent). Ukazatel m_pParent je inicializován během CEditPrintObj konstruktor. Potom by implementovat CEditPrintObj::CPrintObj::PrintObject a také CEditPrintObj::CEditObj::EditObject. S malou část kódu, byla přidána do přidat jedna z funkcí – možnost upravit objekt. Naštěstí je dost neobvyklé pro rozhraní, které se mají jenom jednu členské funkce (i když k tomu dojít) a v takovém případě EditObject a PrintObject by obvykle zkombinovat do jednoho rozhraní.  
  
 To je velké vysvětlení a kódu pro jednoduchého scénáře. Třídy MFC/OLE poskytují jednodušší alternativní. Implementace MFC využívá techniku, podobně jako, které jsou zabalené zpráv systému Windows s mapy zpráv. Pokud tuto funkci je volána *rozhraní mapy* který je popsán v následující části.  
  
## <a name="mfc-interface-maps"></a>Mapy rozhraní MFC  
 MFC/OLE zahrnuje implementace "Rozhraní map" podobné "Mapy zpráv" a "Expediční mapy" knihovny MFC v koncept a spouštění. Základní funkce služby Maps knihovny MFC rozhraní jsou následující:  
  
-   Standardní implementace objektu [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), integrované do `CCmdTarget` třídy.  
  
-   Údržba počet odkazů, upraveném [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317)  
  
-   Implementace řízených daty [– QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)  
  
 Kromě toho rozhraní mapy podporují následující pokročilé funkce:  
  
-   Podpora pro vytváření agregovatelné COM – objekty  
  
-   Podpora pro použití objekty agregace implementace objektu modelu COM  
  
-   Implementace je hookable a rozšiřitelný  
  
 Další informace o agregace, najdete v článku [agregace](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx) tématu.  
  
 Podpora knihovny MFC rozhraní mapy je integrován do `CCmdTarget` třídy. `CCmdTarget`"*má a*" odkazovat počet a také všechny přidružené členské funkce [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) implementace (počet odkazů je třeba v `CCmdTarget`). Pokud chcete vytvořit třídu, která podporuje OLE COM, odvození třídy z `CCmdTarget` a používat různé makra a také členské funkce `CCmdTarget` implementovat požadované rozhraní. Knihovny MFC implementace používá k definování každou implementaci rozhraní podobně jako v předchozím příkladu vnořené třídy. To je snazší díky standardní implementace IUnknown, jakož i počet makra, takže některé opakovaných kódu.  
  
## <a name="interface-map-basics"></a>Základy rozhraní mapy  
  
#### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>K implementaci třídy pomocí knihovny MFC rozhraní mapy  
  
1.  Odvození třídy z přímo nebo nepřímo `CCmdTarget`.  
  
2.  Použití `DECLARE_INTERFACE_MAP` funkce v definici odvozené třídy.  
  
3.  Pro každé rozhraní, které chcete podporovat, použijte `BEGIN_INTERFACE_PART` a `END_INTERFACE_PART` makra v definici třídy.  
  
4.  V souboru implementace použít `BEGIN_INTERFACE_MAP` a `END_INTERFACE_MAP` makra k definování třídy rozhraní mapy.  
  
5.  Pro každý IID podporovány, použijte `INTERFACE_PART` makro mezi `BEGIN_INTERFACE_MAP` a `END_INTERFACE_MAP` maker, pro tento IID namapovat na konkrétní "část" vaší třídy.  
  
6.  Implementujte všechny vnořené třídy, které představují rozhraní, které podporujete.  
  
7.  Použití `METHOD_PROLOGUE` makro přístupu k nadřazenému `CCmdTarget`-odvozené objektu.  
  
8. [Addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379), [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317), a [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) můžete delegovat na `CCmdTarget` provádění těchto funkcí (`ExternalAddRef`, `ExternalRelease`, a `ExternalQueryInterface` ).  
  
 V předchozím příkladu CPrintEditObj může být implementováno takto:  
  
```  
class CPrintEditObj : public CCmdTarget  
{  
public: *// member data and member functions for CPrintEditObj go here  
 
// Interface Maps  
protected:  
    DECLARE_INTERFACE_MAP() 
 
    BEGIN_INTERFACE_PART(EditObj,
    IEditInterface)  
    STDMETHOD_(void,
    EditObject)();
END_INTERFACE_PART(EditObj) 
 
    BEGIN_INTERFACE_PART(PrintObj,
    IPrintInterface)  
    STDMETHOD_(void,
    PrintObject)();
END_INTERFACE_PART(PrintObj) 
};  
```  
  
 Výše uvedené deklaraci vytvoří třídy odvozené od `CCmdTarget`. `DECLARE_INTERFACE_MAP` Makro informuje rozhraní, že tato třída bude mít vlastní rozhraní mapy. Kromě toho `BEGIN_INTERFACE_PART` a `END_INTERFACE_PART` makra definovat vnořené třídy, v takovém případě s názvy CEditObj a CPrintObj (X slouží pouze k odlišení od globální třídy, které začínat "C" a rozhraní třídy, které začínat "I vnořené třídy "). Budou vytvořeny dva vnořené členy z těchto tříd: m_CEditObj a m_CPrintObj, v uvedeném pořadí. Makra automaticky deklarovat [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379), [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317), a [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funkce; proto je pouze deklarovat funkce specifické pro toto rozhraní: EditObject a PrintObject (makro OLE `STDMETHOD` se používá, aby `_stdcall` a virtuální klíčová slova jsou dostupné jako vhodný pro cílové platformy).  
  
 K implementaci rozhraní mapy pro tuto třídu:  
  
```  
BEGIN_INTERFACE_MAP(CPrintEditObj,
    CCmdTarget)  
    INTERFACE_PART(CPrintEditObj,
    IID_IPrintInterface,
    PrintObj)  
    INTERFACE_PART(CPrintEditObj,
    IID_IEditInterface,
    EditObj)  
END_INTERFACE_MAP()  
```  
  
 To připojí IID_IPrintInterface IID s m_CPrintObj a IID_IEditInterface m_CEditObj v uvedeném pořadí. `CCmdTarget` Implementace [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) (`CCmdTarget::ExternalQueryInterface`) používá k vrácení ukazatele m_CPrintObj a m_CEditObj vyžádání mapy. Není nutné zahrnovat záznam pro `IID_IUnknown`; rozhraní použije první rozhraní v mapě (v tomto případě m_CPrintObj) při `IID_IUnknown` se požaduje.  
  
 I když `BEGIN_INTERFACE_PART` makro automaticky deklarován [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379), [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317) a [QueryInterface –](http://msdn.microsoft.com/library/windows/desktop/ms682521) funkce pro vás, stále je třeba implementovat:  
  
```  
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj)  
    return pThis->ExternalAddRef();

}  
 
ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj)  
    return pThis->ExternalRelease();

}  
 
HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj)  
    return (HRESULT)pThis->ExternalQueryInterface(&iid,
    ppvObj);

}  
 
void FAR EXPORT CEditPrintObj::XEditObj::EditObject()  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj) *// code to "Edit" the object,
    whatever that means...  
}  
```  
  
 Implementace pro CEditPrintObj::CPrintObj, bude podobně jako výše uvedená definice pro CEditPrintObj::CEditObj. I když je možné vytvořit makro, které může automaticky generovat tyto funkce (ale dříve v MFC/OLE vývoj šlo o tento případ), bude obtížné a nastavte body rozdělení, když makra generuje více než jeden řádek kódu. Z tohoto důvodu je tento kód rozšířit ručně.  
  
 Pomocí implementace framework mapy zpráv existuje několik věcí, které nebyly nutné udělat:  
  
-   QueryInterface – implementace  
  
-   Addref – implementace a verze  
  
-   Na obou vašich rozhraní deklarovat žádnou z těchto předdefinovaných metod  
  
 Kromě toho rozhraní používá interně mapy zpráv. To umožňuje odvozena od třídy framework vyslovte `COleServerDoc`, který již podporuje určitá rozhraní a poskytuje náhrady nebo doplňky rozhraní poskytované rozhraní. To můžete provést, protože rozhraní plně podporuje dědění mapování rozhraní ze základní třídy. Proč se z důvodu `BEGIN_INTERFACE_MAP` používá jako její druhý parametr název základní třídy.  
  
> [!NOTE]
>  Obecně není možné znovu použít, implementace MFC na předdefinované implementace rozhraní OLE právě embedded specializace tohoto rozhraní, která dědí z verze rozhraní MFC. To není možné protože použití `METHOD_PROLOGUE` makro získat přístup k obsahující `CCmdTarget`-znamená odvozené objektu *pevné odsazení* embedded objektu z `CCmdTarget`-odvozené objektu. To znamená, například embedded XMyAdviseSink nelze odvodit z implementace knihovny MFC ve `COleClientItem::XAdviseSink`, protože XAdviseSink používá tento údaj na konkrétní posunu z horní části `COleClientItem` objektu.  
  
> [!NOTE]
>  Můžete, ale delegovat na implementace MFC pro všechny funkce, které chcete MFC je výchozí chování. To se provádí v implementace MFC `IOleInPlaceFrame` (XOleInPlaceFrame) v `COleFrameHook` – třída (dojde k delegaci na m_xOleInPlaceUIWindow pro mnoho funkcí). Tento návrh byl zvolen ke snížení velikosti runtime objekty, které implementují třídu mnoho rozhraní; eliminuje nutnost back ukazatel (například m_pParent způsob, jak byl použit v předchozí části).  
  
### <a name="aggregation-and-interface-maps"></a>Agregace a rozhraní mapy  
 Vedle podpory samostatné objekty modelu COM, MFC také podporuje agregace. Agregace, samotné je příliš složitý téma a proberte zde; odkazovat [agregace](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx) téma pro další informace o agregaci. Tato poznámka se jednoduše popisují podporu agregace součástí mapy framework a rozhraní.  
  
 Existují dva způsoby, jak používat agregace: (1) pomocí objektu COM, která podporuje agregace a (2) implementace objekt, který se dají agregovat v jiné. Tyto možnosti můžete se označuje jako "použití agregovaný objekt" a "Změna objektu na agregovatelných". MFC podporuje obě.  
  
### <a name="using-an-aggregate-object"></a>Pomocí agregovaný objekt  
 Použití agregační objekt, a tam, musí být nějakým způsobem ke svázání agregace do QueryInterface mechanismu. Jinými slovy agregovaný objekt musí chovat, jako kdyby je nativní součástí objektu. Jak tedy této vazbě do knihovny MFC rozhraní mapování mechanismus kromě `INTERFACE_PART` makro, kde vnořeného objektu je namapována na IID, můžete také deklarovat agregovaný objekt v rámci vaší `CCmdTarget` odvozené třídy. Uděláte to tak, `INTERFACE_AGGREGATE` makro se používá. To vám umožní určit členské proměnné (která musí být ukazatel na [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) nebo odvozené třídy), což je integraci do mapy mechanismu rozhraní. Pokud je ukazatel nemá hodnotu NULL při `CCmdTarget::ExternalQueryInterface` je názvem rozhraní automaticky zavolá agregovaný objekt [QueryInterface –](http://msdn.microsoft.com/library/windows/desktop/ms682521) člen fungovat, pokud `IID` požadovaný není jedním z nativního `IID`s nepodporuje `CCmdTarget` samotného objektu.  
  
##### <a name="to-use-the-interfaceaggregate-macro"></a>Chcete-li použít makro INTERFACE_AGGREGATE  
  
1.  Deklarovat členské proměnné ( `IUnknown*`) který bude obsahovat ukazatel na agregovaný objekt.  
  
2.  Patří `INTERFACE_AGGREGATE` makro v mapě rozhraní, která odkazuje na členské proměnné podle názvu.  
  
3.  V určitém okamžiku (obvykle při `CCmdTarget::OnCreateAggregates`), inicializace členské proměnné na jinou hodnotu než NULL.  
  
 Příklad:  
  
```  
class CAggrExample : public CCmdTarget  
{  
public:  
    CAggrExample();

 
protected:  
    LPUNKNOWN m_lpAggrInner;  
    virtual BOOL OnCreateAggregates();

 
    DECLARE_INTERFACE_MAP() *// "native" interface part macros may be used here  
};  
 
CAggrExample::CAggrExample()  
{  
    m_lpAggrInner = NULL;  
}  
 
BOOL CAggrExample::OnCreateAggregates()  
{ *// wire up aggregate with correct controlling unknown  
    m_lpAggrInner = CoCreateInstance(CLSID_Example,  
    GetControllingUnknown(),
    CLSCTX_INPROC_SERVER,  
    IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)  
    return FALSE; *// optionally,
    create other aggregate objects here  
    return TRUE;  
}  
 
BEGIN_INTERFACE_MAP(CAggrExample,
    CCmdTarget) *// native "INTERFACE_PART" entries go here  
    INTERFACE_AGGREGATE(CAggrExample,
    m_lpAggrInner)  
END_INTERFACE_MAP()  
```  
  
 Proměnná m_lpAggrInner je inicializován v konstruktoru na hodnotu NULL. Rozhraní framework ignoruje členské proměnné NULL výchozí implementace [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521). `OnCreateAggregates`je vhodná k samotnému vytvoření vaší objekty agregace. Budete muset volat explicitně při vytváření objektu mimo MFC implementace `COleObjectFactory`. Důvod pro vytváření agregací ve `CCmdTarget::OnCreateAggregates` a také použití `CCmdTarget::GetControllingUnknown` bude se objeví při vytváření objektů agregovatelné popsané.  
  
 Tento postup vám poskytne váš objekt všechna rozhraní, které podporuje agregovaný objekt plus jeho nativní rozhraní. Pokud chcete pouze podmnožinu rozhraní, která podporuje agregace, můžete přepsat `CCmdTarget::GetInterfaceHook`. To vám umožní hookability velmi nízké úrovně, podobně jako [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521). Obvykle je vhodné všechna rozhraní, které podporuje agregace.  
  
### <a name="making-an-object-implementation-aggregatable"></a>Provedení agregovatelné implementace objektu  
 Pro objekt být agregovatelné, provádění [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379), [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317), a [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) musí delegovat na "řízení neznámý". Jinými slovy, pro něj se jednat o část objektu, se musí delegovat [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379), [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317), a [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) na jiný objekt, také odvozené z [ IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509). Tento "řízení neznámý" je zadaný do objektu při vytvoření, to znamená, je poskytována na implementaci `COleObjectFactory`. Tato implementace představuje malé množství práce a v některých případech není žádoucí, aby MFC díky volitelné. Chcete-li povolit objekt být agregovatelné, zavolejte `CCmdTarget::EnableAggregation` z konstruktoru objektu.  
  
 Pokud objekt také používá agregace, musíte být také nutné předejte správného "řízení neznámý" agregované objekty. Obvykle to [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) ukazatel předaný objekt při vytvoření agregace. Parametr pUnkOuter je například "řízení neznámý" pro všechny objekty vytvořené pomocí `CoCreateInstance`. Správné "řízení neznámý" ukazatele mohou být načteny voláním `CCmdTarget::GetControllingUnknown`. Hodnota vrácená z funkce, ale není platný při konstruktoru. Z tohoto důvodu doporučujeme vytvářet vaše agregace jenom v přepsání `CCmdTarget::OnCreateAggregates`, kdy se z hodnoty návratový `GetControllingUnknown` je spolehlivé, i když vytvořené z `COleObjectFactory` implementace.  
  
 Je také důležité, aby objekt manipulaci správný referenční počet při přidávání nebo vydání počty umělé odkazů. Je tomu tak vždycky voláním `ExternalAddRef` a `ExternalRelease` místo `InternalRelease` a `InternalAddRef`. Navíc není obvyklé volání `InternalRelease` nebo `InternalAddRef` na třídu, která podporuje agregace.  
  
### <a name="reference-material"></a>Referenční materiály  
 Rozšířené použití OLE, jako je například definování vlastní rozhraní nebo přepsání rozhraní framework implementace rozhraní OLE vyžaduje použití podkladový mechanismus mapy rozhraní.  
  
 Tato část popisuje každý makro a rozhraní API, který se používá k implementaci tyto pokročilé funkce.  
  
### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation – Popis funkce  
  
```  
 
void EnableAggregation();

 
```  
  
## <a name="remarks"></a>Poznámky  
 Volání této funkce v konstruktoru odvozené třídy, pokud chcete podporovat OLE agregace pro objekty tohoto typu. To připraví speciální IUnknown implementace, která je vyžadována pro agregovatelné objekty.  
  
### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface – Popis funkce  
  
```  
 
    DWORD ExternalQueryInterface(constvoidFAR* lpIID, LPVOIDFAR* ppvObj);
```  
  
## <a name="remarks"></a>Poznámky  
  
#### <a name="parameters"></a>Parametry  
 `lpIID`  
 Úplně ukazatel na IID (první argument QueryInterface)  
  
 `ppvObj`  
 Ukazatel na IUnknown * (druhý argument QueryInterface)  
  
## <a name="remarks"></a>Poznámky  
 Třídě volání této funkce ve vaší implementace IUnknown pro jednotlivá rozhraní implementuje. Tato funkce poskytuje standardní implementace řízené daty QueryInterface – na základě tohoto objektu rozhraní mapy. Je nutné převést návratovou hodnotu pro HRESULT. Pokud je objekt agregován, tato funkce bude volat "Řízení IUnknown" místo pomocí místního rozhraní mapy.  
  
### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef – Popis funkce  
  
```  
 
DWORD ExternalAddRef();

 
```  
  
## <a name="remarks"></a>Poznámky  
 Třídě volání této funkce ve vaší implementace IUnknown::AddRef u každého rozhraní implementuje. Vrácená hodnota je počet nových odkaz na objekt CCmdTarget. Pokud je objekt agregován, tato funkce bude volat "Řízení IUnknown" místo manipulace s místní odkaz počet.  
  
### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease – Popis funkce  
  
```  
 
DWORD ExternalRelease();

 
```  
  
## <a name="remarks"></a>Poznámky  
 Třídě volání této funkce ve vaší implementace IUnknown::Release u každého rozhraní implementuje. Návratová hodnota určuje počet nových odkaz na objekt. Pokud je objekt agregován, tato funkce bude volat "Řízení IUnknown" místo manipulace s místní odkaz počet.  
  
### <a name="declareinterfacemap--macro-description"></a>Declare_interface_map – – Popis makro  
  
```  
 
DECLARE_INTERFACE_MAP  
 
```  
  
## <a name="remarks"></a>Poznámky  
 Použití tohoto makra v jakékoli třídy odvozené od `CCmdTarget` , bude mít rozhraní mapy. Použít stejným způsobem jako `DECLARE_MESSAGE_MAP`. Toto volání makro musí být umístěny v definici třídy, obvykle v hlavičce (. H) soubor. Třída s `DECLARE_INTERFACE_MAP` musí definovat mapy rozhraní v souboru implementace (. CPP) s `BEGIN_INTERFACE_MAP` a `END_INTERFACE_MAP` makra.  
  
### <a name="begininterfacepart-and-endinterfacepart--macro-descriptions"></a>Begin_interface_part – a end_interface_part – – makro popisy  
  
```  
 
    BEGIN_INTERFACE_PART(
 localClass,   
    iface);

END_INTERFACE_PART(
 localClass)  
```  
  
## <a name="remarks"></a>Poznámky  
  
#### <a name="parameters"></a>Parametry  
 `localClass`  
 Název třídy, který implementuje rozhraní  
  
 `iface`  
 Název rozhraní, které tato třída implementuje  
  
## <a name="remarks"></a>Poznámky  
 U každého rozhraní, která implementuje třídu, je potřeba mít `BEGIN_INTERFACE_PART` a `END_INTERFACE_PART` pár. Tyto makra definovat místní třídy odvozené z rozhraní OLE, které definujete a také embedded členské proměnné této třídy. [Addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379), [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317), a [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) jsou automaticky deklarované členy. Musí zahrnovat deklarace pro jiné členské funkce, které jsou součástí rozhraní se implementuje (tyto deklarace jsou umístěny mezi `BEGIN_INTERFACE_PART` a `END_INTERFACE_PART` makra).  
  
 `iface` Argument je rozhraní OLE, které chcete implementovat, jako například `IAdviseSink`, nebo `IPersistStorage` (nebo vaše vlastní vlastní rozhraní).  
  
 `localClass` Argument je název místní třídu, která bude definována. ' X' bude automaticky před název. Tyto zásady vytváření názvů se používá k zabrání se tím kolizím s globální třídy se stejným názvem. Kromě toho název vloženého člena, stejně jako `localClass` název s výjimkou předponou 'm_x'.  
  
 Příklad:  
  
```  
BEGIN_INTERFACE_PART(MyAdviseSink,
    IAdviseSink)  
    STDMETHOD_(void,
    OnDataChange)(LPFORMATETC,
    LPSTGMEDIUM);

    STDMETHOD_(void,
    OnViewChange)(DWORD,
    LONG);

    STDMETHOD_(void,
    OnRename)(LPMONIKER);

 STDMETHOD_(void,
    OnSave)();
STDMETHOD_(void,
    OnClose)();

END_INTERFACE_PART(MyAdviseSink) 
```  
  
 nadefinovat místní třídu s názvem XMyAdviseSink odvozené z IAdviseSink a členem třídy, ve kterém je deklarovaná s názvem m_xMyAdviseSink.Note:  
  
> [!NOTE]
>  Řádky začínající `STDMETHOD`_ jsou v podstatě kopírovány z OLE2. H a mírně upravit. Kopírování je z OLE2. H můžete snížit počet chyb, které jsou řešení.  
  
### <a name="begininterfacemap-and-endinterfacemap--macro-descriptions"></a>Begin_interface_map – a end_interface_map – – makro popisy  
  
```  
 
    BEGIN_INTERFACE_MAP(
 theClass,   
    baseClass)END_INTERFACE_MAP 
```  
  
## <a name="remarks"></a>Poznámky  
  
#### <a name="parameters"></a>Parametry  
 `theClass`  
 Třída, ve kterém má být definován mapy rozhraní  
  
 `baseClass`  
 Třídu, ze které `theClass` je odvozena z.  
  
## <a name="remarks"></a>Poznámky  
 `BEGIN_INTERFACE_MAP` a `END_INTERFACE_MAP` makra se používají v souboru implementace ve skutečnosti definovat mapy rozhraní. U každého rozhraní, která je implementována je jeden nebo více `INTERFACE_PART` makro volání. Pro každý agregaci, která používá třídu, existuje jedno `INTERFACE_AGGREGATE` makro volání.  
  
### <a name="interfacepart--macro-description"></a>Interface_part – – Popis makro  
  
```  
 
    INTERFACE_PART(
 theClass,   
    iid, 
    localClass) 
```  
  
## <a name="remarks"></a>Poznámky  
  
#### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy, která obsahuje mapy rozhraní.  
  
 `iid`  
 `IID` , Který má být namapovaný na vložené třídy.  
  
 `localClass`  
 Název třídy místní (méně 'X').  
  
## <a name="remarks"></a>Poznámky  
 Toto makro se používá mezi `BEGIN_INTERFACE_MAP` makro a `END_INTERFACE_MAP` makro u každého rozhraní objektu bude podporovat. Umožňuje mapovat IID členem třídy indikován `theClass` a `localClass`. 'm_x' bude přidán do `localClass` automaticky. Všimněte si, že více než jeden `IID` může být přidružen jednoho člena. To je užitečné, když jsou implementace pouze "nejvíce odvozené" rozhraní a chcete zajistit také všechny zprostředkující rozhraní. Dobrým příkladem toho je `IOleInPlaceFrameWindow` rozhraní. Hierarchii vypadá takto:  
  
```  
IUnknown  
    IOleWindow 
    IOleUIWindow 
    IOleInPlaceFrameWindow 
```  
  
 Pokud objekt implementuje `IOleInPlaceFrameWindow`, může klient `QueryInterface` na žádném z těchto rozhraní: `IOleUIWindow`, `IOleWindow`, nebo [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), kromě rozhraní "nejodvozenějších" `IOleInPlaceFrameWindow` (ten se ve skutečnosti implementace). Chcete-li se o to postarají můžete použít více než jeden `INTERFACE_PART` makro pro každé základní rozhraní pro mapování `IOleInPlaceFrameWindow` rozhraní:  
  
 v souboru definice třídy:  
  
```  
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)  
```  
  
 v souboru implementace třídy:  
  
```  
BEGIN_INTERFACE_MAP(CMyWnd,
    CFrameWnd)  
    INTERFACE_PART(CMyWnd,
    IID_IOleWindow,
    MyFrameWindow)  
    INTERFACE_PART(CMyWnd,
    IID_IOleUIWindow,
    MyFrameWindow)  
    INTERFACE_PART(CMyWnd,
    IID_IOleInPlaceFrameWindow,
    MyFrameWindow)  
END_INTERFACE_MAP  
```  
  
 Rozhraní framework postará IUnknown protože bude vždy požadován.  
  
### <a name="interfacepart--macro-description"></a>Interface_part – – Popis makro  
  
```  
 
    INTERFACE_AGGREGATE(
 theClass,   
    theAggr) 
```  
  
## <a name="remarks"></a>Poznámky  
  
#### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy, která obsahuje rozhraní mapy  
  
 `theAggr`  
 Název členské proměnné, které se mají agregovat.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro se používá rozhraní říct, že třída používá agregovaný objekt. Musí být mezi `BEGIN_INTERFACE_PART` a `END_INTERFACE_PART` makra. Agregovaný objekt je samostatný objekt, odvozené od [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509). Pomocí agregace a `INTERFACE_AGGREGATE` makro, můžete provést všechny rozhraní, která zobrazí agregační podporuje přímo podporovaná objektem. `theAggr` Argument je jednoduše název členské proměnné třídy, které je odvozeno z [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) (přímo ani nepřímo). Všechny `INTERFACE_AGGREGATE` musí následovat makra `INTERFACE_PART` makra při uvedení v mapě služby rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

