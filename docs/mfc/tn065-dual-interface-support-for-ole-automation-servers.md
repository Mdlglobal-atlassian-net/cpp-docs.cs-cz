---
title: 'TN065: Podpora duálního rozhraní u automatizačních serverů OLE | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.ole
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e30be46aeab92f63f1b4cba593cda52bf9aeef9a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122180"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: Podpora duálního rozhraní u automatizačních serverů OLE

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.

Tato poznámka se probírá, jak přidat podpora duálního rozhraní na serveru aplikace na základě MFC automatizace OLE. [Acdual –](../visual-cpp-samples.md) ukázka ukazuje podpora duálního rozhraní a ukázkový kód v této poznámky jsou převzaty z acdual –. Makra popsané v této poznámky, například DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART a IMPLEMENT_DUAL_ERRORINFO, jsou součástí acdual – ukázka a lze nalézt v MFCDUAL. H.

## <a name="dual-interfaces"></a>Duální rozhraní

I když automatizace OLE umožňuje implementovat `IDispatch` rozhraní, rozhraní VTBL nebo duální rozhraní (které zahrnuje i), společnost Microsoft důrazně doporučuje implementovat duální rozhraní, pro všechny vystavené objekty automatizace OLE. Duální rozhraní mají významné výhody `IDispatch`-pouze nebo jen VTBL rozhraní:

- Vazba můžete provádět v době kompilace přes rozhraní VTBL nebo v době běhu pomocí `IDispatch`.

- Řadiče automatizace OLE, které můžete použít rozhraní VTBL mohou využít lepší výkon.

- Existující automatizace OLE řadiče, které používají `IDispatch` rozhraní budou nadále fungovat.

- Rozhraní VTBL je snazší volání z jazyka C++.

- Duální rozhraní jsou požadovány pro kompatibilitu s funkce podpory objektů jazyka Visual Basic.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Přidání podpora duálního rozhraní na základě CCmdTarget třídu

Duální rozhraní je odvozen od skutečně právě vlastní rozhraní `IDispatch`. Nejjednodušší způsob, jak implementovat podpora duálního rozhraní v `CCmdTarget`– na základě třídy je první implementace rozhraní na vaší třídě pomocí knihovny MFC a ClassWizard normální odesílání a potom přidat vlastní rozhraní později. Ve většině případů bude vaše implementace vlastní rozhraní jednoduše delegovat zpět do knihovny MFC `IDispatch` implementace.

Nejprve upravte soubor ODL pro váš server můžete definovat duální rozhraní pro objektů. Chcete-li definovat duální rozhraní, musíte použít příkaz jazyka rozhraní místo `DISPINTERFACE` příkaz, který generovat průvodci Visual C++. Místo odebrání stávající `DISPINTERFACE` příkazu Přidat nové prohlášení rozhraní. Zachováním `DISPINTERFACE` formulář, nadále používat ClassWizard k přidání vlastnosti a metody do objektu, ale vaše rozhraní příkazu musíte přidat ekvivalentní vlastnosti a metody.

Příkaz jazyka rozhraní pro duální rozhraní musí mít *OLEAUTOMATION* a *DUÁLNÍ* atributy a rozhraní musí být odvozen od `IDispatch`. Můžete použít [Guidgen –](../visual-cpp-samples.md) vzorek k vytvoření **IID** pro duální rozhraní:

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Když máte příkaz rozhraní na místě, můžete začít přidávat položky pro metody a vlastnosti. Duální rozhraní, musíte ke změně uspořádání seznamy parametrů metody a vlastnosti přistupující objekt funkce v duální rozhraní, vrátí **HRESULT** a předejte jejich návratové hodnoty jako parametry s atributy `[retval,out]`. Mějte na paměti, že pro vlastnosti, budete muset přidat i pro čtení (`propget`) a zápis (`propput`) přístup k funkci se stejným id. Příklad:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

Po metody a vlastnosti jsou definovány, je nutné přidat odkaz na příkaz rozhraní v příkazu třída typu coclass. Příklad:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

Po aktualizaci souboru ODL se používat knihovny MFC rozhraní mapy mechanismus a definovat třídu implementace pro duální rozhraní v třídě objektu a proveďte odpovídající položky v prostředí MFC na `QueryInterface` mechanismus. Je třeba jedna položka v `INTERFACE_PART` blok pro každou položku v rozhraní prohlášení o ODL plus položky pro odesílající rozhraní. Každý záznam ODL s *propput –* atribut potřebuje funkci s názvem `put_propertyname`. Každé položky se *propget –* atribut potřebuje funkci s názvem `get_propertyname`.

Chcete-li definovat třídu implementace pro duální rozhraní, přidejte `DUAL_INTERFACE_PART` blok k vaší definici třídy objektu. Příklad:

```cpp
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)
    STDMETHOD(put_text)(THIS_ BSTR newText);
    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);
    STDMETHOD(put_x)(THIS_ short newX);
    STDMETHOD(get_x)(THIS_ short FAR* retval);
    STDMETHOD(put_y)(THIS_ short newY);
    STDMETHOD(get_y)(THIS_ short FAR* retval);
    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);
    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);
    STDMETHOD(RefreshWindow)(THIS);
    STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);
    STDMETHOD(ShowWindow)(THIS);
END_DUAL_INTERFACE_PART(DualAClick)
```

Pro připojení k knihovny MFC rozhraní duální [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) mechanismus, přidejte `INTERFACE_PART` položku na mapě rozhraní:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

Dále je nutné vyplnit k implementaci rozhraní. Ve většině případů bude možné delegovat na existující MFC `IDispatch` implementace. Příklad:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);
    return lpDispatch->GetTypeInfoCount(pctinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

Pro tohoto objektu metody a vlastnosti přistupující objekt funkce je nutné vyplnit implementace. Funkce metod a vlastností můžete delegovat obecně zpět do metod generována pomocí ClassWizard. Ale pokud nastavíte vlastnosti pro přístup k proměnným, budete muset napsat kód pro get nebo put hodnotu do proměnné. Příklad:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Unicode BSTR to
    // Ansi CString, if necessary...
    pThis->m_str = newText;
    return NOERROR;
}

STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Ansi CString to
    // Unicode BSTR, if necessary...
    pThis->m_str.SetSysString(retval);
    return NOERROR;
}
```

## <a name="passing-dual-interface-pointers"></a>Předávání ukazatele duální rozhraní

Předávání ukazatel duálního rozhraní není jasné, zvlášť pokud je třeba volat `CCmdTarget::FromIDispatch`. `FromIDispatch` funguje pouze na knihovny MFC `IDispatch` ukazatele. Jeden ze způsobů, jak tento problém obejít je k dotazování pro původní `IDispatch` ukazatel sady až v prostředí MFC a předat tuto ukazatele na funkce, které je třeba ji. Příklad:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp = NULL;
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);
    pThis->SetPosition(lpDisp);
    lpDisp->Release();
    return NOERROR;
}
```

Před předáním ukazatel zpět prostřednictvím metody duálního rozhraní, možná budete muset převést z knihovny MFC `IDispatch` ukazatel na ukazatel duálního rozhraní. Příklad:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp;
    lpDisp = pThis->GetPosition();
    lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);
    return NOERROR;
}
```

## <a name="registering-the-applications-type-library"></a>Registraci knihovny typů aplikace

Objekty AppWizard nevygeneruje žádný kód pro registraci knihovny typů aplikace automatizace OLE server v systému. Když existují další způsoby, jak se zaregistrovat knihovnu typů, je vhodné používat aplikaci zaregistrovat knihovnu typů, během aktualizace jeho informace o typu OLE tedy při každém spuštění samostatné aplikace.

K registraci knihovny typů aplikace vždy, když je aplikace spuštěna samostatná:

- Zahrnout AFXCTL. H ve vašem standard zahrnuje soubor hlaviček, STDAFX. H pro přístup k definici `AfxOleRegisterTypeLib` funkce.

- Ve vaší aplikaci `InitInstance` fungovat, vyhledejte volání `COleObjectFactory::UpdateRegistryAll`. Následující toto volání, že přidáte volání `AfxOleRegisterTypeLib`, zadání **ID KNIHOVNY** odpovídající vaší knihovny typů, společně s názvem vaší knihovny typů:

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Úprava nastavení projektu sestavení zohlednit změny typu knihovny

K úpravě nastavení projektu sestavení tak, aby soubor záhlaví obsahující **UUID** definice je generován MkTypLib – vždy, když je znovu sestavit knihovny typů:

1. Na **sestavení** nabídky, klikněte na tlačítko **nastavení**a pak vyberte příslušný soubor ODL ze seznamu souborů pro každou konfiguraci.

2. Klikněte na tlačítko **OLE typy** a zadejte název souboru v **výstup záhlaví** pole název souboru. Název souboru, který se již nepoužívá vaším projektem použijte, protože MkTypLib – přepíše existující soubor. Klikněte na tlačítko **OK** zavřete **nastavení sestavení** dialogové okno.

Chcete-li přidat **UUID** definice z hlavičky generované MkTypLib – soubor do projektu:

1. Zahrnout generované MkTypLib – soubor hlaviček v vaše standardní zahrnuje soubor hlaviček, STDAFX. H.

2. Vytvořte nový soubor INITIIDS. CPP a přidejte ji do projektu. V tomto souboru zahrňte soubor hlavičky generované MkTypLib – po včetně OLE2. H a INITGUID. V:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. Na **sestavení** nabídky, klikněte na tlačítko **nastavení**a pak vyberte INITIIDS. CPP ze seznamu souborů pro každou konfiguraci.

4. Klikněte na tlačítko **C++** , klikněte na kategorii **předkompilovaných hlaviček**a vyberte **bez použití předkompilovaných hlaviček** přepínač. Kliknutím na OK zavřete **nastavení sestavení** dialogové okno.

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Určení názvu třídy správný objekt v knihovny typů

Průvodci součástí Visual C++ nesprávně použijte k určení coclass v souboru ODL serveru pro OLE vytvořitelné třídy název třídy implementace. Když to bude fungovat, název třídy implementace je pravděpodobně není název třídy, které se mají uživatelé objektu použít. Zadejte správný název, otevřete soubor ODL, vyhledejte každý příkaz třída typu coclass a nahraďte název třídy implementace se správným názvem externí.

Všimněte si, že při změně příkaz třída typu coclass, proměnné názvy **CLSID**s v souboru hlavičky generované MkTypLib – změní odpovídajícím způsobem. Budete muset aktualizovat kód a použít nové názvy proměnných.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Zpracování výjimek a chyb rozhraní automatizace

Objekt automatizace metody a vlastnosti přistupující objekt funkce může vyvolat výjimky. Pokud ano, by měl zpracování je v implementaci duálního rozhraní a předat informace o výjimce zpět řadičem přes rozhraní automatizace OLE zpracování chyb, `IErrorInfo`. Toto rozhraní poskytuje informace o chybě podrobné, kontextové prostřednictvím obě `IDispatch` a VTBL rozhraní. K označení, zda obslužná rutina je k dispozici, měli byste implementovat `ISupportErrorInfo` rozhraní.

Pro ilustraci mechanismus zpracování chyb, předpokládá, že generované ClassWizard funkce, které slouží k implementaci podpory standardní odesílání generování výjimek. Implementace MFC na `IDispatch::Invoke` obvykle zachytí tyto výjimky a převede je na strukturu EXCEPTINFO, která je vrácena prostřednictvím `Invoke` volání. Ale pokud je použita VTBL rozhraní, jste zodpovědní za zachytávání výjimky sami. Jako příklad chrání vaše duálního rozhraní metody:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    TRY_DUAL(IID_IDualAClick)
    {
        // MFC automatically converts from Unicode BSTR to
        // Ansi CString, if necessary...
        pThis->m_str = newText;
        return NOERROR;
    }
    CATCH_ALL_DUAL
}
```

`CATCH_ALL_DUAL` má na starosti vrácení kód správný chyba, když dojde k výjimce. `CATCH_ALL_DUAL` Převede výjimku MFC automatizace OLE zpracování chyb informací pomocí `ICreateErrorInfo` rozhraní. (Příklad `CATCH_ALL_DUAL` makro je v souboru MFCDUAL. H v [acdual –](../visual-cpp-samples.md) ukázka. Funkce volá zpracování výjimek, `DualHandleException`, je v souboru MFCDUAL. CPP.) `CATCH_ALL_DUAL` Určuje kód chyby se vrátíte na základě typu výjimka, ke které došlo k chybě:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) – v takovém případě `HRESULT` je vytvořený pomocí následujícího kódu:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

     Tím se vytvoří `HRESULT` specifické pro rozhraní, který způsobil výjimku. Kód chyby je posunut 0x200 předejdete případné konflikty s definovaná systémem `HRESULT`s pro standardní rozhraní OLE.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) – v takovém případě `E_OUTOFMEMORY` je vrácen.

- Všechny ostatní výjimky – v tomto případě `E_UNEXPECTED` je vrácen.

K označení, že se používá obslužná rutina chyb automatizace OLE, měli byste také implementovat `ISupportErrorInfo` rozhraní.

Nejprve přidejte kód pro vaše definice třídy automatizace zobrazíte podporuje `ISupportErrorInfo`.

Druhý, přidávání kódu do vaší třídy automatizace rozhraní mapy pro přidružení `ISupportErrorInfo` třída implementace MFC na `QueryInterface` mechanismus. `INTERFACE_PART` Příkaz odpovídá definovaný pro třídu `ISupportErrorInfo`.

Nakonec implementace třídy definované pro podporu `ISupportErrorInfo`.

( [Acdual –](../visual-cpp-samples.md) ukázka obsahuje tři makra pomohou, proveďte tyto tři kroky `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, a `IMPLEMENT_DUAL_ERRORINFO`, všechny obsažené v MFCDUAL. H.)

Následující příklad implementuje třídy definované pro podporu `ISupportErrorInfo`. `CAutoClickDoc` je název vaší třídy automatizace a `IID_IDualAClick` je **IID** pro rozhraní, který je zdrojem chyby nahlášené prostřednictvím objekt automatizace OLE Chyba:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)  
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)  
