---
title: Globální funkce složeného ovládacího prvku
ms.date: 11/04/2016
f1_keywords:
- atlhost/ATL::AtlAxDialogBox
- atlhost/ATL::AtlAxCreateDialog
- atlhost/ATL::AtlAxCreateControl
- atlhost/ATL::AtlAxCreateControlEx
- atlhost/ATL::AtlAxCreateControlLic
- atlhost/ATL::AtlAxCreateControlLicEx
- atlhost/ATL::AtlAxAttachControl
- atlhost/ATL::AtlAxGetHost
- atlhost/ATL::AtlAxGetControl
- atlhost/ATL::AtlSetChildSite
- atlhost/ATL::AtlAxWinInit
- atlhost/ATL::AtlAxWinTerm
- atlhost/ATL::AtlGetObjectSourceInterface
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
ms.openlocfilehash: 525fc01247053a1e2bc993398978cb332262a1a5
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927772"
---
# <a name="composite-control-global-functions"></a>Globální funkce složeného ovládacího prvku

Tyto funkce poskytují podporu pro vytváření dialogových oken a pro vytváření, hostování a licencování ovládacích prvků ActiveX.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Vytvoří modální dialogové okno z uživatelem zadané šablony dialogového okna. Výsledný dialog může obsahovat ovládací prvky ActiveX.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Vytvoří nemodální dialogové okno z uživatelem zadané šablony dialogového okna. Výsledný dialog může obsahovat ovládací prvky ActiveX.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Vytvoří, inicializuje a hostuje ovládací prvek ActiveX v zadaném okně.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Vytvoří ovládací prvek ActiveX, inicializuje ho, hostuje ho v zadaném okně a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Vytvoří licencovaný ovládací prvek ActiveX, inicializuje ho, hostuje ho v zadaném okně a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[AtlAxAttachControl](#atlaxattachcontrol)|Připojí předchozí vytvořený ovládací prvek k zadanému oknu.|
|[AtlAxGetHost](#atlaxgethost)|Slouží k získání přímého ukazatele rozhraní do kontejneru pro zadané okno (pokud existuje), které má za daných popisovačů.|
|[AtlAxGetControl](#atlaxgetcontrol)|Slouží k získání přímého ukazatele rozhraní k ovládacímu prvku obsaženému v zadaném okně (pokud existuje) s daným popisovačem.|
|[AtlSetChildSite](#atlsetchildsite)|`IUnknown` Inicializuje podřízenou lokalitu.|
|[AtlAxWinInit](#atlaxwininit)|Inicializuje hostující kód pro AxWin objekty.|
|[AtlAxWinTerm](#atlaxwinterm)|Zruší inicializaci hostujícího kódu pro objekty AxWin.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Vrátí informace o výchozím zdrojovém rozhraní objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atlhost. h

##  <a name="atlaxdialogbox"></a>AtlAxDialogBox

Vytvoří modální dialogové okno z uživatelem zadané šablony dialogového okna.

```
ATLAPI_(int) AtlAxDialogBox(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
pro Identifikuje instanci modulu, jehož spustitelný soubor obsahuje šablonu dialogového okna.

*lpTemplateName*<br/>
pro Identifikuje šablonu dialogového okna. Tento parametr je buď ukazatel na řetězec znaků zakončený hodnotou null, který určuje název šablony dialogového okna nebo celočíselnou hodnotu, která určuje identifikátor prostředku šablony dialogového okna. Pokud parametr určuje identifikátor prostředku, jeho horní slovo musí být nula a jeho slovo s nižším pořadím musí obsahovat identifikátor. Tuto hodnotu můžete vytvořit pomocí makra [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) .

*hWndParent*<br/>
pro Identifikuje okno, které vlastní dialogové okno.

*lpDialogProc*<br/>
pro Odkazuje na proceduru dialogového okna. Další informace o postupu dialogového okna naleznete v tématu [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
pro Určuje hodnotu, která má být předána do dialogového okna v parametru *lParam* zprávy WM_INITDIALOG.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Chcete- `AtlAxDialogBox` li použít se šablonou dialogového okna, která obsahuje ovládací prvek ActiveX, zadejte platný řetězec CLSID, AppID nebo URL jako textové pole v části **ovládacího prvku** prostředku, společně s *textem* "AtlAxWin80" jako pole *názvu třídy* . v rámci stejné části. Následující příklad ukazuje, jak může být platný oddíl **ovládacího prvku** vypadat takto:

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Další informace o úpravách skriptů prostředků naleznete v [tématu How to: Otevřete soubor skriptu prostředků v textovém formátu](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Další informace o příkazech pro kontrolu definice prostředků naleznete v tématu [běžné kontrolní parametry](/windows/win32/menurc/common-control-parameters) v části Windows SDK: SDK Tools.

Další informace o dialogových oknech obecně naleznete v tématu [dialogbox](/windows/win32/api/winuser/nf-winuser-dialogboxw) a [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) v Windows SDK.

##  <a name="atlaxcreatedialog"></a>AtlAxCreateDialog

Vytvoří nemodální dialogové okno z uživatelem zadané šablony dialogového okna.

```
ATLAPI_(HWND) AtlAxCreateDialog(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
pro Identifikuje instanci modulu, jehož spustitelný soubor obsahuje šablonu dialogového okna.

*lpTemplateName*<br/>
pro Identifikuje šablonu dialogového okna. Tento parametr je buď ukazatel na řetězec znaků zakončený hodnotou null, který určuje název šablony dialogového okna nebo celočíselnou hodnotu, která určuje identifikátor prostředku šablony dialogového okna. Pokud parametr určuje identifikátor prostředku, jeho horní slovo musí být nula a jeho slovo s nižším pořadím musí obsahovat identifikátor. Tuto hodnotu můžete vytvořit pomocí makra [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) .

*hWndParent*<br/>
pro Identifikuje okno, které vlastní dialogové okno.

*lpDialogProc*<br/>
pro Odkazuje na proceduru dialogového okna. Další informace o postupu dialogového okna naleznete v tématu [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
pro Určuje hodnotu, která má být předána do dialogového okna v parametru *lParam* zprávy WM_INITDIALOG.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Výsledný dialog může obsahovat ovládací prvky ActiveX.

Viz [CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw) a [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) v Windows SDK.

##  <a name="atlaxcreatecontrol"></a>  AtlAxCreateControl

Vytvoří, inicializuje a hostuje ovládací prvek ActiveX v zadaném okně.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec, který má být předán ovládacímu prvku. Musí být formátován jedním z následujících způsobů:

- Identifikátor ProgID, například`"MSCAL.Calendar.7"`

- Identifikátor CLSID, jako např.`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL jako`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, jako např.`"file://\\\Documents\MyDoc.doc"`

- Fragment kódu HTML, jako např.`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragment HTML, aby byl označený jako datový proud MSHTML.

*hWnd*<br/>
pro Zpracuje okno, ke kterému bude ovládací prvek připojen.

*pStream*<br/>
pro Ukazatel na datový proud, který slouží k inicializaci vlastností ovládacího prvku. Může mít hodnotu NULL.

*ppUnkContainer*<br/>
mimo Adresa ukazatele, který `IUnknown` dostane z kontejneru. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Tato globální funkce poskytuje stejný výsledek jako volání [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *HWND*, *pStream*, null, null, null, null);.

Chcete-li vytvořit licencovaný ovládací prvek ActiveX, přečtěte si téma [AtlAxCreateControlLic](#atlaxcreatecontrollic).

##  <a name="atlaxcreatecontrolex"></a>AtlAxCreateControlEx

Vytvoří, inicializuje a hostuje ovládací prvek ActiveX v zadaném okně. Pro tento nový ovládací prvek lze také vytvořit ukazatel rozhraní a jímku událostí.

```
ATLAPI AtlAxCreateControlEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec, který má být předán ovládacímu prvku. Musí být formátován jedním z následujících způsobů:

- Identifikátor ProgID, například`"MSCAL.Calendar.7"`

- Identifikátor CLSID, jako např.`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL jako`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, jako např.`"file://\\\Documents\MyDoc.doc"`

- Fragment kódu HTML, jako např.`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragment HTML, aby byl označený jako datový proud MSHTML.

*hWnd*<br/>
pro Zpracuje okno, ke kterému bude ovládací prvek připojen.

*pStream*<br/>
pro Ukazatel na datový proud, který slouží k inicializaci vlastností ovládacího prvku. Může mít hodnotu NULL.

*ppUnkContainer*<br/>
mimo Adresa ukazatele, který `IUnknown` dostane z kontejneru. Může mít hodnotu NULL.

*ppUnkControl*<br/>
mimo Adresa ukazatele, který dostane `IUnknown` z vytvořeného ovládacího prvku. Může mít hodnotu NULL.

*iidSink*<br/>
Identifikátor rozhraní odchozího rozhraní u objektu, který ho obsahuje.

*punkSink*<br/>
Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen ke spojovacímu bodu určenému parametrem *iidSink* na objektu, který byl úspěšně vytvořen.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

`AtlAxCreateControlEx`je podobný jako [AtlAxCreateControl](#atlaxcreatecontrol) , ale také umožňuje získat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímku událostí pro příjem událostí vyvolaných ovládacím prvkem.

Chcete-li vytvořit licencovaný ovládací prvek ActiveX, přečtěte si téma [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

##  <a name="atlaxcreatecontrollic"></a>  AtlAxCreateControlLic

Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.

```
ATLAPI AtlAxCreateControlLic(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec, který má být předán ovládacímu prvku. Musí být formátován jedním z následujících způsobů:

- Identifikátor ProgID, například`"MSCAL.Calendar.7"`

- Identifikátor CLSID, jako např.`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL jako`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, jako např.`"file://\\\Documents\MyDoc.doc"`

- Fragment kódu HTML, jako např.`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragment HTML, aby byl označený jako datový proud MSHTML.

*hWnd*<br/>
Zpracuje okno, ke kterému bude ovládací prvek připojen.

*pStream*<br/>
Ukazatel na datový proud, který slouží k inicializaci vlastností ovládacího prvku. Může mít hodnotu NULL.

*ppUnkContainer*<br/>
Adresa ukazatele, který `IUnknown` dostane z kontejneru. Může mít hodnotu NULL.

*bstrLic*<br/>
BSTR obsahující licenci pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="example"></a>Příklad

Ukázku způsobu použití `AtlAxCreateControlLic`lze najít v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="atlaxcreatecontrollicex"></a>  AtlAxCreateControlLicEx

Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně. Pro tento nový ovládací prvek lze také vytvořit ukazatel rozhraní a jímku událostí.

```
ATLAPI AtlAxCreateControlLicEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec, který má být předán ovládacímu prvku. Musí být formátován jedním z následujících způsobů:

- Identifikátor ProgID, například`"MSCAL.Calendar.7"`

- Identifikátor CLSID, jako např.`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL jako`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, jako např.`"file://\\\Documents\MyDoc.doc"`

- Fragment kódu HTML, jako např.`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragment HTML, aby byl označený jako datový proud MSHTML.

*hWnd*<br/>
Zpracuje okno, ke kterému bude ovládací prvek připojen.

*pStream*<br/>
Ukazatel na datový proud, který slouží k inicializaci vlastností ovládacího prvku. Může mít hodnotu NULL.

*ppUnkContainer*<br/>
Adresa ukazatele, který `IUnknown` dostane z kontejneru. Může mít hodnotu NULL.

*ppUnkControl*<br/>
mimo Adresa ukazatele, který dostane `IUnknown` z vytvořeného ovládacího prvku. Může mít hodnotu NULL.

*iidSink*<br/>
Identifikátor rozhraní odchozího rozhraní u objektu, který ho obsahuje.

*punkSink*<br/>
Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen ke spojovacímu bodu určenému parametrem *iidSink* na objektu, který byl úspěšně vytvořen.

*bstrLic*<br/>
BSTR obsahující licenci pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

`AtlAxCreateControlLicEx`je podobný jako [AtlAxCreateControlLic](#atlaxcreatecontrollic) , ale také umožňuje získat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímku událostí pro příjem událostí vyvolaných ovládacím prvkem.

### <a name="example"></a>Příklad

Ukázku způsobu použití `AtlAxCreateControlLicEx`lze najít v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="atlaxattachcontrol"></a>AtlAxAttachControl

Připojí předchozí vytvořený ovládací prvek k zadanému oknu.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
pro Ukazatel na `IUnknown` ovládací prvek.

*hWnd*<br/>
pro Obsluha okna, které bude hostitelem ovládacího prvku.

*ppUnkContainer*<br/>
mimo Ukazatel na ukazatel na `IUnknown` objekt kontejneru.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

K současnému vytvoření a připojení ovládacího prvku použijte [AtlAxCreateControlEx](#atlaxcreatecontrolex) a [AtlAxCreateControl](#atlaxcreatecontrol) .

> [!NOTE]
>  Objekt ovládacího prvku, který se má připojit, musí být `AtlAxAttachControl`před voláním správně inicializován.

##  <a name="atlaxgethost"></a>  AtlAxGetHost

Získá přímý ukazatel rozhraní na kontejner zadaného okna (pokud existuje) s uvedením jeho popisovače.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*h*<br/>
pro Popisovač okna, který je hostitelem ovládacího prvku.

*pp*<br/>
mimo `IUnknown` Kontejneru ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl

Získá přímý ukazatel rozhraní na ovládací prvek obsažený uvnitř zadaného okna s uvedením jeho popisovače.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*h*<br/>
pro Popisovač okna, který je hostitelem ovládacího prvku.

*pp*<br/>
mimo `IUnknown` Ovládací prvek, který je hostován.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="atlsetchildsite"></a>AtlSetChildSite

Voláním této funkce nastavíte lokalitu podřízeného objektu na `IUnknown` nadřazený objekt.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Parametry

*punkChild*<br/>
pro Ukazatel na `IUnknown` rozhraní podřízeného objektu.

*punkParent*<br/>
pro Ukazatel na `IUnknown` rozhraní nadřazené položky.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="atlaxwininit"></a>AtlAxWinInit

Tato funkce inicializuje kód hostování ovládacího prvku knihovny ATL registrací tříd oken **"AtlAxWin80"** a **"AtlAxWinLic80"** a několika vlastních zpráv okna.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla inicializace kódu hostování ovládacího prvku úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato funkce musí být volána před použitím rozhraní API hostování ovládacího prvku ATL. Po volání této funkce lze třídu okna **AtlAxWin** použít v voláních funkce [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) nebo [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw), jak je popsáno v Windows SDK.

##  <a name="atlaxwinterm"></a>AtlAxWinTerm

Tato funkce zruší inicializaci hostování kódu ovládacího prvku ATL zrušením registrace tříd oken **"AtlAxWin80"** a **"AtlAxWinLic80"** .

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato funkce jednoduše volá [UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) , jak je popsáno v Windows SDK.

Voláním této funkce vyčistíte po zničení všech stávajících hostitelských oken, pokud jste volali [AtlAxWinInit](#atlaxwininit) a už nemusíte vytvářet hostitelské okna. Pokud tuto funkci nezavoláte, třída okna bude při ukončení procesu automaticky odregistrována.

##  <a name="atlgetobjectsourceinterface"></a>AtlGetObjectSourceInterface

Voláním této funkce načtete informace o výchozím zdrojovém rozhraní objektu.

```
ATLAPI AtlGetObjectSourceInterface(
    IUnknown* punkObj,
    GUID* plibid,
    IID* piid,
    unsigned short* pdwMajor,
    unsigned short* pdwMinor);
```

### <a name="parameters"></a>Parametry

*punkObj*<br/>
pro Ukazatel na objekt, pro který mají být vráceny informace.

*plibid*<br/>
mimo Ukazatel na LIBID knihovny typů obsahující definici zdrojového rozhraní.

*piid*<br/>
mimo Ukazatel na ID rozhraní výchozího zdrojového rozhraní objektu.

*pdwMajor*<br/>
mimo Ukazatel na hlavní číslo verze knihovny typů obsahující definici zdrojového rozhraní.

*pdwMinor*<br/>
mimo Ukazatel na číslo dílčí verze knihovny typů, která obsahuje definici zdrojového rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`AtlGetObjectSourceInterface`vám může poskytnout ID rozhraní výchozího zdrojového rozhraní společně s čísly LIBID a hlavní a dílčí verze knihovny typů, které popisují toto rozhraní.

> [!NOTE]
>  Aby tato funkce úspěšně načetla požadované informace, musí objekt reprezentovaný *punkObj* implementovat `IDispatch` (a vracet informace o typu prostřednictvím `IDispatch::GetTypeInfo`) a musí taky implementovat buď `IProvideClassInfo2` nebo. `IPersist`. Informace o typu pro zdrojové rozhraní musí být ve stejné knihovně typů jako informace o typu pro `IDispatch`.

### <a name="example"></a>Příklad

Níže uvedený příklad ukazuje, jak lze definovat třídu `CEasySink`jímky událostí, která snižuje počet argumentů šablony, které lze `IDispEventImpl` předat do úplného základu. `EasyAdvise`a `EasyUnadvise` použijte [](../../atl/reference/idispeventimpl-class.md) [](idispeventsimpleimpl-class.md#dispeventadvise) [](idispeventsimpleimpl-class.md#dispeventunadvise)k inicializaci členů IDispEventImpl před voláním DispEventAdvise nebo DispEventUnadvise. `AtlGetObjectSourceInterface`

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Viz také:

[Funkce](../../atl/reference/atl-functions.md)<br/>
[Makra složených ovládacích prvků](../../atl/reference/composite-control-macros.md)
