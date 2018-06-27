---
title: 'TN065: Podpora duálního rozhraní u automatizačních serverů OLE | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: b066ac483de127e0ce469cf8aaf24991ae5f6ef8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953035"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: Podpora duálního rozhraní u automatizačních serverů OLE
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka se probírá, jak přidat podpora duálního rozhraní na serveru aplikace na základě MFC automatizace OLE. [Acdual –](../visual-cpp-samples.md) ukázka ukazuje podpora duálního rozhraní a ukázkový kód v této poznámky jsou převzaty z acdual –. Makra popsané v této poznámky, například DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART a IMPLEMENT_DUAL_ERRORINFO, jsou součástí acdual – ukázka a lze nalézt v MFCDUAL. H.  
  
## <a name="dual-interfaces"></a>Duální rozhraní  
 I když automatizace OLE umožňuje implementovat `IDispatch` rozhraní, rozhraní VTBL nebo duální rozhraní (které zahrnuje i), společnost Microsoft důrazně doporučuje implementovat duální rozhraní, pro všechny vystavené objekty automatizace OLE. Duální rozhraní mají významné výhody `IDispatch`-pouze nebo jen VTBL rozhraní:  
  
-   Vazba můžete provádět v době kompilace přes rozhraní VTBL nebo v době běhu pomocí `IDispatch`.  
  
-   Řadiče automatizace OLE, které můžete použít rozhraní VTBL mohou využít lepší výkon.  
  
-   Existující automatizace OLE řadiče, které používají `IDispatch` rozhraní budou nadále fungovat.  
  
-   Rozhraní VTBL je snazší volání z jazyka C++.  
  
-   Duální rozhraní jsou požadovány pro kompatibilitu s funkce podpory objektů jazyka Visual Basic.  
  
## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Přidání podpora duálního rozhraní na základě CCmdTarget třídu  
 Duální rozhraní je odvozen od skutečně právě vlastní rozhraní `IDispatch`. Nejjednodušší způsob, jak implementovat podpora duálního rozhraní v `CCmdTarget`– na základě třídy je první implementace rozhraní na vaší třídě pomocí knihovny MFC a ClassWizard normální odesílání a potom přidat vlastní rozhraní později. Ve většině případů bude vaše implementace vlastní rozhraní jednoduše delegovat zpět do knihovny MFC `IDispatch` implementace.  
  
 Nejprve upravte soubor ODL pro váš server můžete definovat duální rozhraní pro objektů. Chcete-li definovat duální rozhraní, musíte použít příkaz jazyka rozhraní místo `DISPINTERFACE` příkaz, který generovat průvodci Visual C++. Místo odebrání stávající `DISPINTERFACE` příkazu Přidat nové prohlášení rozhraní. Zachováním `DISPINTERFACE` formulář, nadále používat ClassWizard k přidání vlastnosti a metody do objektu, ale vaše rozhraní příkazu musíte přidat ekvivalentní vlastnosti a metody.  
  
 Příkaz jazyka rozhraní pro duální rozhraní musí mít *OLEAUTOMATION* a *DUÁLNÍ* atributy a rozhraní musí být odvozen od `IDispatch`. Můžete použít [Guidgen –](../visual-cpp-samples.md) vzorek k vytvoření **IID** pro duální rozhraní:  
  
```  
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick  
    oleautomation, 
    dual 
]  
interface IDualAClick : IDispatch  
 {  
 };  
```  
  
 Když máte příkaz rozhraní na místě, můžete začít přidávat položky pro metody a vlastnosti. Duální rozhraní, musíte ke změně uspořádání seznamy parametrů metody a vlastnosti přistupující objekt funkce v duální rozhraní, vrátí **HRESULT** a předejte jejich návratové hodnoty jako parametry s atributy `[retval,out]`. Mějte na paměti, že pro vlastnosti, budete muset přidat i pro čtení (`propget`) a zápis (`propput`) přístup k funkci se stejným id. Příklad:  
  
```  
[propput,
    id(1)] HRESULT text([in] BSTR newText);

[propget,
    id(1)] HRESULT text([out,
    retval] BSTR* retval);
```  
  
 Po metody a vlastnosti jsou definovány, je nutné přidat odkaz na příkaz rozhraní v příkazu třída typu coclass. Příklad:  
  
```  
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]  
coclass Document  
{  
    dispinterface IAClick;  
 [default] interface IDualAClick;  
};  
```  
  
 Po aktualizaci souboru ODL se používat knihovny MFC rozhraní mapy mechanismus a definovat třídu implementace pro duální rozhraní v třídě objektu a proveďte odpovídající položky v prostředí MFC na `QueryInterface` mechanismus. Je třeba jedna položka v `INTERFACE_PART` blok pro každou položku v rozhraní prohlášení o ODL plus položky pro odesílající rozhraní. Každý záznam ODL s *propput –* atribut potřebuje funkci s názvem `put_propertyname`. Každé položky se *propget –* atribut potřebuje funkci s názvem `get_propertyname`.  
  
 Chcete-li definovat třídu implementace pro duální rozhraní, přidejte `DUAL_INTERFACE_PART` blok k vaší definici třídy objektu. Příklad:  
  
```  
BEGIN_DUAL_INTERFACE_PART(DualAClick,
    IDualAClick)  
    STDMETHOD(put_text)(THIS_ BSTR newText);

    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);

    STDMETHOD(put_x)(THIS_ short newX);

    STDMETHOD(get_x)(THIS_ short FAR* retval);

    STDMETHOD(put_y)(THIS_ short newY);

    STDMETHOD(get_y)(THIS_ short FAR* retval);

    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);

    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);

    STDMETHOD(RefreshWindow)(THIS);

 STDMETHOD(SetAllProps)(THIS_ short x,
    short y,
    BSTR text);

    STDMETHOD(ShowWindow)(THIS);

END_DUAL_INTERFACE_PART(DualAClick) 
```  
  
 Pro připojení k knihovny MFC rozhraní duální [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) mechanismus, přidejte `INTERFACE_PART` položku na mapě rozhraní:  
  
```  
BEGIN_INTERFACE_MAP(CAutoClickDoc,
    CDocument)  
    INTERFACE_PART(CAutoClickDoc,
    DIID_IAClick,
    Dispatch)  
    INTERFACE_PART(CAutoClickDoc,
    IID_IDualAClick,
    DualAClick)  
END_INTERFACE_MAP()  
```  
  
 Dále je nutné vyplnit k implementaci rozhraní. Ve většině případů bude možné delegovat na existující MFC `IDispatch` implementace. Příklad:  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalAddRef();

}  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalRelease();

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalQueryInterface(&iid,
    ppvObj);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfoCount(pctinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo,
    lcid,
    pptinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,  
    LCID lcid,
    DISPID FAR* rgdispid)   
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid,
    rgszNames,
    cNames,   
    lcid,
    rgdispid);

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
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember,
    riid,
    lcid,  
    wFlags,
    pdispparams,
    pvarResult,  
    pexcepinfo,
    puArgErr);

}  
```  
  
 Pro tohoto objektu metody a vlastnosti přistupující objekt funkce je nutné vyplnit implementace. Funkce metod a vlastností můžete delegovat obecně zpět do metod generována pomocí ClassWizard. Ale pokud nastavíte vlastnosti pro přístup k proměnným, budete muset napsat kód pro get nebo put hodnotu do proměnné. Příklad:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Unicode BSTR to *// Ansi CString,
    if necessary...  
    pThis->m_str = newText;  
    return NOERROR;  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Ansi CString to *// Unicode BSTR,
    if necessary...  
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
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
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
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDisp;  
    lpDisp = pThis->GetPosition();
lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);

    return NOERROR;  
}  
```  
  
## <a name="registering-the-applications-type-library"></a>Registraci knihovny typů aplikace  
 Objekty AppWizard nevygeneruje žádný kód pro registraci knihovny typů aplikace automatizace OLE server v systému. Když existují další způsoby, jak se zaregistrovat knihovnu typů, je vhodné používat aplikaci zaregistrovat knihovnu typů, během aktualizace jeho informace o typu OLE tedy při každém spuštění samostatné aplikace.  
  
 K registraci knihovny typů aplikace vždy, když je aplikace spuštěna samostatná:  
  
-   Zahrnout AFXCTL. H ve vašem standard zahrnuje soubor hlaviček, STDAFX. H pro přístup k definici `AfxOleRegisterTypeLib` funkce.  
  
-   Ve vaší aplikaci `InitInstance` fungovat, vyhledejte volání `COleObjectFactory::UpdateRegistryAll`. Následující toto volání, že přidáte volání `AfxOleRegisterTypeLib`, zadání **ID KNIHOVNY** odpovídající vaší knihovny typů, společně s názvem vaší knihovny typů:  
  
 "' * / Při spuštění aplikace server samostatné je vhodné * / / k aktualizaci systémového registru v případě, že byl poškozen.  
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

 COleObjectFactory::UpdateRegistryAll(); * / Nebo DUAL_SUPPORT_START * / / zajistěte, aby se zaregistrovat knihovnu typů nebo duální rozhraní nebude fungovat.  
AfxOleRegisterTypeLib(AfxGetInstanceHandle(), LIBID_ACDual, _T("AutoClik.TLB")); * / NEBO DUAL_SUPPORT_END  
 ```  
  
## Modifying Project Build Settings to Accommodate Type Library Changes  
 To modify a project's build settings so that a header file containing **UUID** definitions is generated by MkTypLib whenever the type library is rebuilt:  
  
1.  On the **Build** menu, click **Settings**, and then select the ODL file from the file list for each configuration.  
  
2.  Click the **OLE Types** tab and specify a filename in the **Output header** filename field. Use a filename that is not already used by your project, because MkTypLib will overwrite any existing file. Click **OK** to close the **Build Settings** dialog box.  
  
 To add the **UUID** definitions from the MkTypLib-generated header file to your project:  
  
1.  Include the MkTypLib-generated header file in your standard includes header file, STDAFX.H.  
  
2.  Create a new file, INITIIDS.CPP, and add it to your project. In this file, include your MkTypLib-generated header file after including OLE2.H and INITGUID.H:  
  
 ```  
    initIIDs.c: definuje identifikátory IID pro duální rozhraní  
    To nesmí být vytvořené s nástroji předkompilovaných hlaviček.  
      #<a name="include-ole2h"></a>Zahrnout < ole2.h >  
      #<a name="include-initguidh"></a>Zahrnout < initguid.h >  
      #<a name="include-acdualh"></a>Zahrnout "acdual.h"  
 ```  
  
3.  On the **Build** menu, click **Settings**, and then select INITIIDS.CPP from the file list for each configuration.  
  
4.  Click the **C++** tab, click category **Precompiled Headers**, and select the **Not using precompiled headers** radio button. Click OK to close the **Build Settings** dialog box.  
  
## Specifying the Correct Object Class Name in the Type Library  
 The wizards shipped with Visual C++ incorrectly use the implementation class name to specify the coclass in the server's ODL file for OLE-creatable classes. While this will work, the implementation class name is probably not the class name you want users of your object to use. To specify the correct name, open the ODL file, locate each coclass statement, and replace the implementation class name with the correct external name.  
  
 Note that when the coclass statement is changed, the variable names of **CLSID**s in the MkTypLib-generated header file will change accordingly. You will need to update your code to use the new variable names.  
  
## Handling Exceptions and the Automation Error Interfaces  
 Your automation object's methods and property accessor functions may throw exceptions. If so, you should handle them in your dual-interface implementation and pass information about the exception back to the controller through the OLE Automation error-handling interface, `IErrorInfo`. This interface provides for detailed, contextual error information through both `IDispatch` and VTBL interfaces. To indicate that an error handler is available, you should implement the `ISupportErrorInfo` interface.  
  
 To illustrate the error-handling mechanism, assume that the ClassWizard-generated functions used to implement the standard dispatch support throw exceptions. MFC's implementation of `IDispatch::Invoke` typically catches these exceptions and converts them into an EXCEPTINFO structure that is returned through the `Invoke` call. However, when VTBL interface is used, you are responsible for catching the exceptions yourself. As an example of protecting your dual-interface methods:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    Method_prologue – (CAutoClickDoc, DualAClick)  
    TRY_DUAL(IID_IDualAClick) {* / / MFC automaticky převede z BSTR Unicode do * / nebo Ansi CString, v případě potřeby...  
    pThis->m_str = newText;  
    Vrátí NOERROR;  
 }  
    CATCH_ALL_DUAL }  
```  
  
 `CATCH_ALL_DUAL` takes care of returning the correct error code when an exception occurs. `CATCH_ALL_DUAL` converts an MFC exception into OLE Automation error-handling information using the `ICreateErrorInfo` interface. (An example `CATCH_ALL_DUAL` macro is in the file MFCDUAL.H in the [ACDUAL](../visual-cpp-samples.md) sample. The function it calls to handle exceptions, `DualHandleException`, is in the file MFCDUAL.CPP.) `CATCH_ALL_DUAL` determines the error code to return based on the type of exception that occurred:  
  
- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) - In this case, `HRESULT` is constructed using the following code:  
  
 ```  
    hr = MAKE_HRESULT(SEVERITY_ERROR,
    FACILITY_ITF,   
 (e->m_wCode + 0x200));

 ```  
  
     This creates an `HRESULT` specific to the interface that caused the exception. The error code is offset by 0x200 to avoid any conflicts with system-defined `HRESULT`s for standard OLE interfaces.  
  
- [CMemoryException](../mfc/reference/cmemoryexception-class.md) - In this case, `E_OUTOFMEMORY` is returned.  
  
-   Any other exception - In this case, `E_UNEXPECTED` is returned.  
  
 To indicate that the OLE Automation error handler is used, you should also implement the `ISupportErrorInfo` interface.  
  
 First, add code to your automation class definition to show it supports `ISupportErrorInfo`.  
  
 Second, add code to your automation class's interface map to associate the `ISupportErrorInfo` implementation class with MFC's `QueryInterface` mechanism. The `INTERFACE_PART` statement matches the class defined for `ISupportErrorInfo`.  
  
 Finally, implement the class defined to support `ISupportErrorInfo`.  
  
 (The [ACDUAL](../visual-cpp-samples.md) sample contains three macros to help do these three steps, `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, and `IMPLEMENT_DUAL_ERRORINFO`, all contained in MFCDUAL.H.)  
  
 The following example implements a class defined to support `ISupportErrorInfo`. `CAutoClickDoc` is the name of your automation class and `IID_IDualAClick` is the **IID** for the interface that is the source of errors reported through the OLE Automation error object:  
  
```  
STDMETHODIMP_(ulong) CAutoClickDoc::XSupportErrorInfo::AddRef()   
{  
    Method_prologue – (CAutoClickDoc, SupportErrorInfo)   
    Návratový pThis -> ExternalAddRef();

}   
STDMETHODIMP_(ulong) CAutoClickDoc::XSupportErrorInfo::Release()   
{   
    Method_prologue – (CAutoClickDoc, SupportErrorInfo)   
    Návratový pThis -> ExternalRelease();

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface (REFIID iid, LPVOID * ppvObj)   
{   
    Method_prologue – (CAutoClickDoc, SupportErrorInfo)   
    Návratový pThis -> ExternalQueryInterface (& iid, ppvObj);

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo (REFIID iid)   
{   
    Method_prologue – (CAutoClickDoc, SupportErrorInfo)   
    Vrátí (iid == IID_IDualAClick) S_OK: S_FALSE;   
}  
```  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

