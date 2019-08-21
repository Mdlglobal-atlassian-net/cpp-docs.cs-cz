---
title: 'TN065: Podpora duálního rozhraní pro automatizační servery OLE'
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: 1508b5219f7bb7fd2e9c9a56c42c30bb99686804
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630396"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: Podpora duálního rozhraní pro automatizační servery OLE

> [!NOTE]
> Následující technická Poznámka nebyla od prvního zařazení do online dokumentace aktualizována. V důsledku toho mohou být některé postupy a témata neaktuální nebo nesprávné. Nejnovější informace najdete v tématu informace o tom, co je důležité v online katalogu dokumentace najít.

Tato poznámka popisuje, jak přidat podporu duálního rozhraní do aplikace automatizačního serveru OLE založené na knihovně MFC. Ukázka [ACDUAL](../overview/visual-cpp-samples.md) znázorňuje podporu duálního rozhraní a ukázkový kód v této poznámce je pořízen z ACDUAL. Makra popsaná v této poznámce, například DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART a IMPLEMENT_DUAL_ERRORINFO, jsou součástí ukázky ACDUAL a lze je najít v MFCDUAL. Y.

## <a name="dual-interfaces"></a>Duální rozhraní

I když automatizace technologie OLE umožňuje implementovat `IDispatch` rozhraní, rozhraní VTBL nebo duální rozhraní (které zahrnuje obojí), společnost Microsoft důrazně doporučuje, abyste implementovali duální rozhraní pro všechny exponované objekty automatizace OLE. Duální rozhraní mají významné výhody pouze `IDispatch`v rozhraních pouze nebo VTBL:

- Vazba může probíhat v době kompilace prostřednictvím rozhraní VTBL nebo v době běhu do `IDispatch`.

- Ovladače automatizace OLE, které můžou používat rozhraní VTBL, můžou mít lepší výkon.

- Existující řadiče automatizace OLE, které používají `IDispatch` rozhraní, budou i nadále fungovat.

- Rozhraní VTBL je snazší volat z C++.

- Pro kompatibilitu s funkcemi podpory Visual Basic objektů jsou vyžadovány duální rozhraní.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Přidání podpory duálního rozhraní pro třídu založenou na CCmdTarget

Duální rozhraní je opravdu pouze vlastní rozhraní odvozené z `IDispatch`. Nejjednodušší způsob, jak implementovat podporu duálního rozhraní ve `CCmdTarget`třídě založené na platformě, je nejprve implementovat normální rozhraní dispatching ve vaší třídě pomocí knihovny MFC a ClassWizard a pak přidat vlastní rozhraní později. Ve většině případů vaše implementace vlastního rozhraní bude jednoduše delegována zpět na implementaci MFC `IDispatch` .

Nejdřív upravte soubor ODL pro váš server, abyste definovali duální rozhraní pro vaše objekty. Chcete-li definovat duální rozhraní, je nutné použít příkaz rozhraní namísto `DISPINTERFACE` příkazu, který generují vizuální C++ průvodce. Místo odebrání existujícího `DISPINTERFACE` příkazu přidejte nové prohlášení o rozhraní. Uchováním `DISPINTERFACE` formuláře můžete nadále používat ClassWizard k přidání vlastností a metod do objektu, ale je nutné přidat ekvivalentní vlastnosti a metody do příkazu rozhraní.

Příkaz rozhraní pro duální rozhraní musí mít atributy *oleautomation* a *Dual* a rozhraní musí být odvozeno z `IDispatch`. Pomocí ukázky [Guidgen](../overview/visual-cpp-samples.md) můžete vytvořit **IID** pro duální rozhraní:

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Jakmile budete mít příkaz rozhraní, začněte přidávat položky pro metody a vlastnosti. Pro duální rozhraní je potřeba změnit uspořádání seznamů parametrů tak, aby vaše metody a přístup k vlastnostem v duálním rozhraní vracely **HRESULT** a předaly návratové hodnoty jako parametry s atributy `[retval,out]`. Nezapomeňte, že pro vlastnosti budete muset přidat funkci přístupu Read (`propget`) i Write (`propput`) se stejným ID. Příklad:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

Po definování metod a vlastností je třeba přidat odkaz na příkaz rozhraní v rámci vašeho příkazu coclass. Příklad:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

Po aktualizaci souboru ODL použijte mechanismus mapování rozhraní knihovny MFC k definování třídy implementace pro duální rozhraní ve třídě objektu a proveďte odpovídající položky v `QueryInterface` mechanismu knihovny MFC. Budete potřebovat jeden záznam v `INTERFACE_PART` bloku pro každou položku v příkazu rozhraní jazyka ODL a položky pro rozhraní dispatch. Každá položka jazyka ODL s atributem *propput* vyžaduje funkci s `put_propertyname`názvem. Každá položka s atributem *propget* vyžaduje funkci s názvem `get_propertyname`.

Chcete-li definovat implementační třídu pro vaše duální rozhraní, přidejte `DUAL_INTERFACE_PART` blok do definice třídy objektu. Příklad:

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

Chcete-li připojit duální rozhraní k mechanismu [QueryInterface](/windows/win32/com/queryinterface--navigating-in-an-object) v knihovně MFC, `INTERFACE_PART` přidejte položku do mapy rozhraní:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

Dál je potřeba vyplnit implementaci rozhraní. Ve většině případů bude možné delegovat na stávající implementaci knihovny MFC `IDispatch` . Příklad:

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

Pro funkce objektu a přístup k vlastnostem přistupujícího objektu musíte vyplnit implementaci. Vaše funkce metody a vlastností mohou obecně delegovat zpět na metody generované pomocí ClassWizard. Nicméně pokud nastavíte vlastnosti pro přímý přístup k proměnným, je nutné napsat kód pro získání nebo vložení hodnoty do proměnné. Příklad:

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

## <a name="passing-dual-interface-pointers"></a>Předávání ukazatelů s dvojitým rozhraním

Předání ukazatele na duální rozhraní není jednoduché, zejména v případě, že je třeba `CCmdTarget::FromIDispatch`volat. `FromIDispatch`funguje pouze na `IDispatch` ukazatelích knihovny MFC. Jedním ze způsobů, jak tento problém obejít, je zadat `IDispatch` dotaz na původní ukazatel nastavený pomocí knihovny MFC a předat ukazatel na funkce, které ho potřebují. Příklad:

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

Před předáním ukazatele zpět metodou dvojího rozhraní může být nutné jej převést z ukazatele knihovny MFC `IDispatch` na ukazatel na duální rozhraní. Příklad:

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

AppWizard negeneruje kód pro registraci knihovny typů aplikace automatizačního serveru OLE se systémem. I když existují i jiné způsoby, jak knihovnu typů zaregistrovat, je vhodné mít aplikaci možnost Registrovat knihovnu typů při aktualizaci informací o typu OLE, to znamená, když je aplikace spuštěna samostatně.

Chcete-li zaregistrovat knihovnu typů aplikace vždy, když je aplikace samostatná, proveďte následující:

- Zahrnout AFXCTL H ve vašem standardu obsahuje hlavičkový soubor STDAFX. H pro přístup k definici `AfxOleRegisterTypeLib` funkce.

- Ve `InitInstance` funkci aplikace vyhledejte `COleObjectFactory::UpdateRegistryAll`volání. Po tomto volání přidejte volání do `AfxOleRegisterTypeLib`a určete **LIBID** odpovídající vaší knihovně typů spolu s názvem knihovny typů:

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

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Úprava nastavení sestavení projektu pro přizpůsobení změn knihovny typů

Chcete-li upravit nastavení sestavení projektu tak, aby soubor hlaviček obsahující definice **UUID** byl vygenerován MkTypLib vždy, když je znovu sestavena knihovna typů:

1. V nabídce **sestavení** klikněte na **Nastavení**a potom vyberte soubor ODL ze seznamu souborů pro každou konfiguraci.

2. Klikněte na kartu **typy OLE** a zadejte název souboru do pole název výstupního souboru s **hlavičkou** . Použijte název souboru, který se už v projektu nepoužívá, protože MkTypLib přepíše existující soubor. Kliknutím na tlačítko **OK** zavřete dialogové okno **nastavení sestavení** .

Chcete-li přidat definice **identifikátorů UUID** ze souboru hlaviček generovaného MkTypLib do projektu:

1. Zahrňte do svého standardu hlavičkový soubor generovaný MkTypLib, *stdafx. h*.

2. Vytvořte nový soubor INITIIDS. CPP a přidejte ho do projektu. V tomto souboru zahrňte soubor hlaviček generovaný MkTypLib po zahrnutí OLE2. H a INITGUID. Y

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. V nabídce **sestavení** klikněte na **Nastavení**a pak vyberte INITIIDS. CPP ze seznamu souborů pro každou konfiguraci.

4. Klikněte na **C++** kartu, klikněte na **Předkompilovaná záhlaví**kategorie a vyberte přepínač **Nepoužívat předkompilované hlavičky** . Kliknutím na tlačítko OK zavřete dialogové okno **nastavení sestavení** .

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Určení správného názvu třídy objektu v knihovně typů

Průvodce dodaný s vizuálu C++ nesprávně používá název třídy implementace k určení coclass třídy v souboru jazyka ODL serveru pro třídy využívající technologii OLE. I když to bude fungovat, název třídy implementace pravděpodobně není název třídy, kterou mají uživatelé vašeho objektu používat. Chcete-li zadat správný název, otevřete soubor ODL, vyhledejte každý příkaz coclass a nahraďte název třídy implementace správným externím názvem.

Všimněte si, že při změně třídy coclass se odpovídajícím způsobem změní názvy proměnných **CLSID**s v souboru hlaviček generovaného MkTypLib. Budete muset aktualizovat svůj kód, aby používal nové názvy proměnných.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Zpracování výjimek a chybových rozhraní automatizace

Metody objektu automatizace a funkce přistupující k vlastnostem mohou vyvolat výjimky. Pokud ano, měli byste je zpracovat ve své implementaci s duálním rozhraním a předávat informace o výjimce zpátky do kontroleru prostřednictvím rozhraní `IErrorInfo`OLE Automation pro zpracování chyb. Toto rozhraní poskytuje podrobné kontextové informace o chybách prostřednictvím `IDispatch` rozhraní a VTBL. Pro indikaci, že je k dispozici obslužná rutina chyby `ISupportErrorInfo` , byste měli implementovat rozhraní.

Pro ilustraci mechanismu zpracování chyb Předpokládejme, že funkce generované ClassWizard, které slouží k implementaci standardního odeslání, podporují výjimky. Implementace `IDispatch::Invoke` knihovny MFC obvykle zachycuje tyto výjimky a převede je do struktury EXCEPTINFO, která je vrácena `Invoke` prostřednictvím volání. Pokud se však používá rozhraní VTBL, zodpovídáte za zachycení výjimek sami. Jako příklad ochrany metod dvojího rozhraní:

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

`CATCH_ALL_DUAL`Při výskytu výjimky se postará o vrácení správného kódu chyby. `CATCH_ALL_DUAL`Převede výjimku knihovny MFC na informace o zpracování chyb automatizace OLE pomocí `ICreateErrorInfo` rozhraní. (Příklad `CATCH_ALL_DUAL` makra je v souboru MFCDUAL. H v ukázce [ACDUAL](../overview/visual-cpp-samples.md) . Funkce, která volá pro zpracování výjimek, `DualHandleException`, je v souboru MFCDUAL. CPP.) `CATCH_ALL_DUAL` Určuje kód chyby, který se má vrátit na základě typu výjimky, ke které došlo:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) – v tomto případě `HRESULT` je vytvořen pomocí následujícího kódu:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   Tím se vytvoří `HRESULT` konkrétní rozhraní, které způsobilo výjimku. Kód chyby je posunut pomocí 0x200, aby nedocházelo ke konfliktům se systémem `HRESULT`definovaným s pro standardní rozhraní OLE.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) – v tomto případě `E_OUTOFMEMORY` se vrátí.

- Všechny ostatní výjimky – v tomto případě `E_UNEXPECTED` se vrátí.

Pro indikaci, že se používá obslužná rutina chyby automatizace OLE, byste měli `ISupportErrorInfo` také implementovat rozhraní.

Nejdřív přidejte kód do definice třídy automatizace, aby se zobrazila podpora `ISupportErrorInfo`.

Za druhé přidejte kód do mapy rozhraní vaší třídy automatizace a přidružte `ISupportErrorInfo` k ní implementační třídu s `QueryInterface` mechanismem knihovny MFC. Příkaz odpovídá třídě definované pro `ISupportErrorInfo`. `INTERFACE_PART`

Nakonec implementujte třídu definovanou pro podporu `ISupportErrorInfo`.

(Ukázka [ACDUAL](../overview/visual-cpp-samples.md) obsahuje tři makra, která vám pomůžou provést tyto tři `DECLARE_DUAL_ERRORINFO`kroky `DUAL_ERRORINFO_PART`,, `IMPLEMENT_DUAL_ERRORINFO`a, které jsou obsaženy v MFCDUAL. H.)

Následující příklad implementuje třídu definovanou pro podporu `ISupportErrorInfo`. `CAutoClickDoc`je název vaší třídy automatizace a `IID_IDualAClick` je **IID** pro rozhraní, které je zdrojem chyb hlášených prostřednictvím objektu chyby automatizace OLE:

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
