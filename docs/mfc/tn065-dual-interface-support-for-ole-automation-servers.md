---
title: 'TN065: Podpora duálního rozhraní u automatizačních serverů OLE | Dokumentace Microsoftu'
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
ms.openlocfilehash: 837149397ec45ebd8b41808b170b9f5e25146d6a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387689"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: Podpora duálního rozhraní u automatizačních serverů OLE

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje, jak přidat podpora duálního rozhraní založené na knihovně MFC OLE aplikaci automatizačního serveru. [Acdual –](../visual-cpp-samples.md) ukázka ilustruje podpora duálního rozhraní a vzorový kód v této poznámky je převzat z acdual –. Makra popsané v této poznámky, jako je například DECLARE_DUAL_ERRORINFO DUAL_ERRORINFO_PART a IMPLEMENT_DUAL_ERRORINFO, jsou součástí vzorku acdual – a lze nalézt v MFCDUAL. H.

## <a name="dual-interfaces"></a>Duální rozhraní

I když OLE Automation umožňuje implementovat `IDispatch` rozhraní, VTBL rozhraní nebo duální rozhraní (která zahrnuje i) společnost Microsoft důrazně doporučuje implementovat duální rozhraní pro všechny vystavené objekty automatizace OLE. Duální rozhraní mají významné výhody `IDispatch`– pouze nebo jen VTBL rozhraní:

- Vazby může proběhnout v době kompilace VTBL rozhraní nebo v době běhu pomocí `IDispatch`.

- Řadiče automatizace OLE, které můžete použít rozhraní VTBL můžou mít užitek z vylepšení výkonu.

- Existující řadiče automatizace OLE, které používají `IDispatch` rozhraní budou nadále fungovat.

- Rozhraní VTBL je snazší volat z jazyka C++.

- Duální rozhraní jsou nutná pro kompatibilitu s funkcí podporu objektů Visual Basic.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Přidání podpory duálního rozhraní na základě CCmdTarget – třída

Duální rozhraní je odvozena z vlastně jenom vlastní rozhraní `IDispatch`. Nejjednodušší způsob implementace podpora duálního rozhraní v `CCmdTarget`– první implementovat rozhraní na třídě pomocí knihovny MFC a ClassWizard normální odesílání a potom později přidat vlastní rozhraní je založené na třídě. Ve většině případů bude vaše implementace vlastního rozhraní jednoduše delegovat zpět do knihovny MFC `IDispatch` implementace.

Nejprve upravte soubor ODL pro váš server k definování duální rozhraní pro objekty. Chcete-li definovat duální rozhraní, musíte použít příkaz rozhraní místo `DISPINTERFACE` příkaz, který generovat průvodců aplikace Visual C++. Místo odstranění existující `DISPINTERFACE` příkaz, přidejte nový příkaz rozhraní. Tak, že zachová `DISPINTERFACE` formuláře, můžete nadále používat ClassWizard přidávat vlastnosti a metody do objektu, ale musíte přidat odpovídající vlastnosti a metody pro váš výpis z rozhraní.

Interface – příkaz pro duální rozhraní musí mít *OLEAUTOMATION* a *DUÁLNÍ* atributy a rozhraní musí být odvozen od `IDispatch`. Můžete použít [Guidgen –](../visual-cpp-samples.md) vzorek k vytvoření **IID** pro duální rozhraní:

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Jakmile budete mít interface – příkaz na místě, začněte přidávat položky pro metody a vlastnosti. Duální rozhraní, budete muset změnit uspořádání seznamu parametrů tak, aby metody a vlastnosti přístupového objektu funkce duální rozhraní vrátit **HRESULT** a předat jejich návratové hodnoty jako parametry s atributy `[retval,out]`. Mějte na paměti, že pro vlastnosti, budete muset přidat čtení (`propget`) a zápis (`propput`) přístup k funkci se stejným id. Příklad:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

Poté, co jsou definovány metody a vlastnosti, budete muset přidat odkaz na rozhraní příkaz v příkazu coclass. Příklad:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

Jakmile se aktualizoval váš soubor ODL pomocí mechanismu mapování rozhraní knihovny MFC k definování třídy implementace pro duální rozhraní ve třídě objektu a provést odpovídající položky v knihovně MFC `QueryInterface` mechanismus. Je třeba jedna položka v `INTERFACE_PART` blok pro každou položku v příkazu rozhraní ODL. navíc položky pro rozhraní odbavení. Každá položka ODL s *propput* atribut vyžaduje funkci s názvem `put_propertyname`. Každá položka se *propget* atribut vyžaduje funkci s názvem `get_propertyname`.

Chcete-li definovat třídu implementace pro duální rozhraní, přidejte `DUAL_INTERFACE_PART` bloku do definice třídy objektu. Příklad:

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

Pro připojení duální rozhraní MFC [QueryInterface](/windows/desktop/com/queryinterface--navigating-in-an-object) mechanismus, přidejte `INTERFACE_PART` položku do mapy rozhraní:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

Dále je třeba vyplnit implementaci rozhraní. Ve většině případů bude možné delegovat do existujícího MFC `IDispatch` implementace. Příklad:

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

Pro váš objekt metody a vlastnosti přístupového objektu funkce je nutné vyplnit v implementaci. Funkce metod a vlastností můžete delegovat obecně zpět do metody vygenerované pomocí ClassWizard. Ale pokud nastavíte vlastnosti pro přístup k proměnným, musíte napsat kód pro get/put hodnotu do proměnné. Příklad:

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

## <a name="passing-dual-interface-pointers"></a>Předávání ukazatelů duálního rozhraní

Předání ukazatele duálního rozhraní není jasné, zejména v případě, že je potřeba volat `CCmdTarget::FromIDispatch`. `FromIDispatch` funguje pouze na knihovně MFC `IDispatch` ukazatele. Jeden ze způsobů, jak tento problém obejít je k dotazování pro původní `IDispatch` sada ukazatel myši nahoru v prostředí MFC a předat tento ukazatel do funkce, které potřebujete. Příklad:

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

## <a name="registering-the-applications-type-library"></a>Registrace knihovny typů aplikace

AppWizard negeneruje kód pro registraci knihovny typů aplikace serveru OLE Automation v systému. I když existují další možnosti, jak zaregistrovat knihovnu typů, je vhodné mít aplikaci zaregistrovat knihovnu typů, během aktualizace informace o typu OLE, to znamená, že při každém spuštění samostatné aplikace.

Registrace knihovny typů aplikace při každém spuštění aplikace samostatně:

- Zahrnout AFXCTL. H do standardního obsahuje soubor hlaviček, STDAFX. H, pro přístup k definici `AfxOleRegisterTypeLib` funkce.

- Ve vaší aplikaci `InitInstance` funkční, vyhledejte volání `COleObjectFactory::UpdateRegistryAll`. Za toto volání, přidejte volání `AfxOleRegisterTypeLib`, zadání **LIBID** odpovídající knihovna typů, spolu s názvem vaší knihovny typů:

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

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Úprava nastavení projektu sestavení tak, aby vyhovovaly změny knihovny typů

Chcete-li změnit nastavení projektu sestavení tak, aby soubor záhlaví obsahující **UUID** definice pokaždé, když se znovu sestaví knihovny typů generuje s MkTypLib:

1. Na **sestavení** nabídky, klikněte na tlačítko **nastavení**a potom vyberte soubor ODL ze seznamu souborů pro každou konfiguraci.

2. Klikněte na tlačítko **typy OLE** kartě a zadejte název souboru v **výstupní hlavičky** pole název souboru. Použijte název souboru, který se již nepoužívá ve vašem projektu, protože s MkTypLib přepíše existující soubor. Klikněte na tlačítko **OK** zavřete **nastavení sestavení** dialogové okno.

Chcete-li přidat **UUID** definice z generovaných s MkTypLib hlavičkový soubor do projektu:

1. Zahrnout s MkTypLib generovaný soubor hlaviček v standardního obsahuje soubor hlaviček, STDAFX. H.

2. Vytvořte nový soubor, INITIIDS. CPP a přidejte ho do projektu. V tomto souboru zahrňte soubor hlavičky generované s MkTypLib po zahrnutí OLE2. H a INITGUID. V:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. Na **sestavení** nabídky, klikněte na tlačítko **nastavení**a pak vyberte INITIIDS. CPP ze seznamu souborů pro každou konfiguraci.

4. Klikněte na tlačítko **C++** klikněte na tlačítko kategorie **předkompilované hlavičky**a vyberte **bez použití předkompilovaných hlaviček** přepínač. Kliknutím na OK zavřete **nastavení sestavení** dialogové okno.

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Zadání názvu třídy správný objekt v knihovně typů

Průvodce nesprávně součástí Visual C++ používá název třídy implementace k určení v souboru ODL serveru pro OLE vytvořitelné třídy coclass. Když to bude fungovat, název třídy implementace není pravděpodobně mají uživatelé objektu použijte název třídy. Zadejte správný název, otevřete soubor ODL, vyhledejte každý coclass příkaz a nahraďte správný název externí název třídy implementace.

Všimněte si, že pokud změníte příkaz coclass, názvy proměnných z **CLSID**s v souboru hlaviček generovaných s MkTypLib bude odpovídajícím způsobem měnit. Je potřeba aktualizovat kód Refaktorovat pro použití nové názvy proměnných.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Zpracování výjimek a chyb rozhraní automatizace

Automatizační objekt metody a vlastnosti přístupového objektu funkce může vyvolat výjimky. Pokud tedy by měl zpracovávat vaše implementace duálního rozhraní a předávání informací o výjimce zpět do kontroleru rozhraní automatizace OLE zpracování chyb, `IErrorInfo`. Toto rozhraní poskytuje informace o chybě podrobné, kontextové prostřednictvím obě `IDispatch` a VTBL rozhraní. K označení, že obslužná rutina chyby je k dispozici, měli byste implementovat `ISupportErrorInfo` rozhraní.

Pro ilustraci mechanismus zpracování chyb, se předpokládá, že funkce generované ClassWizard používaný k implementaci podpory standard odeslání vyvolávat výjimky. Implementace MFC atributu `IDispatch::Invoke` obvykle zachycuje tyto výjimky a převede je na strukturu EXCEPTINFO, která je vrácena prostřednictvím `Invoke` volání. Ale při použití rozhraní VTBL zodpovídáte za zachytávání výjimek sami. Jako příklad duálního rozhraní metody ochrany:

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

`CATCH_ALL_DUAL` postará o vrácení kódu chyby opravte, když dojde k výjimce. `CATCH_ALL_DUAL` převádí výjimku MFC OLE Automation zpracování chyb informací pomocí `ICreateErrorInfo` rozhraní. (Příklad `CATCH_ALL_DUAL` – makro je v souboru MFCDUAL. H [acdual –](../visual-cpp-samples.md) vzorku. Funkce, které volá pro zpracování výjimek, `DualHandleException`, je umístěný v souboru MFCDUAL. CPP.) `CATCH_ALL_DUAL` Určuje kód chyby se vraťte na základě typu výjimky, ke které došlo:

- [Coledispatchexception –](../mfc/reference/coledispatchexception-class.md) – v takovém případě `HRESULT` je vytvořená pomocí následujícího kódu:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

     Tím se vytvoří `HRESULT` specifické pro rozhraní, který způsobil výjimku. Kód chyby je posunut 0x200, aby se zabránilo konfliktům s definovaných systémem `HRESULT`s pro standardní rozhraní OLE.

- [Cmemoryexception –](../mfc/reference/cmemoryexception-class.md) – v takovém případě `E_OUTOFMEMORY` je vrácena.

- Jakoukoli jinou výjimku – v takovém případě `E_UNEXPECTED` je vrácena.

K označení, že se používá obslužnou rutinu chyb automatizace OLE, byste měli také implementovat `ISupportErrorInfo` rozhraní.

Nejprve přidejte kód do definice třídy automatizace zobrazíte podporuje `ISupportErrorInfo`.

Za druhé, přidání kódu do mapy rozhraní klientská automatizační třída přidružení `ISupportErrorInfo` implementace třídy pomocí knihovny MFC `QueryInterface` mechanismus. `INTERFACE_PART` Příkaz shoduje se třída definovaná pro `ISupportErrorInfo`.

Nakonec implementace třídy definované pro podporu `ISupportErrorInfo`.

( [Acdual –](../visual-cpp-samples.md) ukázka obsahuje tři makra umožňující provádět tyto tři kroky `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, a `IMPLEMENT_DUAL_ERRORINFO`, všechny obsažené v MFCDUAL. H.)

Následující příklad implementuje třída definována pro podporu `ISupportErrorInfo`. `CAutoClickDoc` je název třídy automatizace a `IID_IDualAClick` je **IID** rozhraní, které je zdrojem chyby ohlášení chyby objekt automatizace OLE:

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

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
