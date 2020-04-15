---
title: Globální funkce složených řízení
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
ms.openlocfilehash: 99ecd4cf04b3eb696f897d6ef5a5e3839d46ef17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331603"
---
# <a name="composite-control-global-functions"></a>Globální funkce složených řízení

Tyto funkce poskytují podporu pro vytváření dialogových oken a pro vytváření, hostování a licencování ovládacích prvků ActiveX.

> [!IMPORTANT]
> Funkce uvedené v následující tabulce nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Vytvoří modální dialogové okno z uživatelem zadané šablony dialogového okna. Výsledné dialogové okno může obsahovat ovládací prvky ActiveX.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Vytvoří nemodální dialogové okno z uživatelem zadané šablony dialogového okna. Výsledné dialogové okno může obsahovat ovládací prvky ActiveX.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Vytvoří, inicializuje a hostuje ovládací prvek ActiveX v zadaném okně.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Vytvoří ovládací prvek ActiveX, inicializuje jej, hostuje v zadaném okně a načítá ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Vytvoří licencovaný ovládací prvek ActiveX, inicializuje jej, hostuje v zadaném okně a načítá ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[Ovládací prvek AtlAxAttachControl](#atlaxattachcontrol)|Připojí předchozí vytvořený ovládací prvek k zadanému oknu.|
|[AtlAxGetHost](#atlaxgethost)|Slouží k získání přímého ukazatele rozhraní do kontejneru pro zadané okno (pokud existuje), vzhledem k jeho popisovač.|
|[AtlAxGetControl](#atlaxgetcontrol)|Slouží k získání přímého ukazatele rozhraní na ovládací prvek obsažený uvnitř zadaného okna (pokud existuje), vzhledem k jeho popisovač.|
|[AtlSetChildSite](#atlsetchildsite)|Inicializuje `IUnknown` podřízený web.|
|[AtlAxWinInit](#atlaxwininit)|Inicializuje kód hostování pro objekty AxWin.|
|[AtlAxWinTermín](#atlaxwinterm)|Uninitializes hosting kód pro Objekty AxWin.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Vrátí informace o výchozím zdrojovém rozhraní objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlhost.h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a>AtlAxDialogBox

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
[v] Identifikuje instanci modulu, jehož spustitelný soubor obsahuje šablonu dialogového okna.

*lpTemplateName*<br/>
[v] Identifikuje šablonu dialogového okna. Tento parametr je buď ukazatelem na řetězec znaků zakončený nulou, který určuje název šablony dialogového okna nebo celočíselnou hodnotu, která určuje identifikátor prostředku šablony dialogového okna. Pokud parametr určuje identifikátor prostředku, jeho slovo nejvyššího řádu musí být nulové a jeho slovo nižšího řádu musí obsahovat identifikátor. Tuto hodnotu můžete vytvořit pomocí makra [MAKEINTRESOURCE.](/windows/win32/api/winuser/nf-winuser-makeintresourcew)

*hWndParent*<br/>
[v] Identifikuje okno, které vlastní dialogové okno.

*lpDialogProc*<br/>
[v] Odkazuje na postup dialogového okna. Další informace o postupu dialogového okna naleznete v [tématu DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[v] Určuje hodnotu, která má být předávána dialogovému oknu v parametru *lParam* WM_INITDIALOG zprávy.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Chcete-li `AtlAxDialogBox` použít šablonu dialogu, která obsahuje ovládací prvek ActiveX, zadejte platný řetězec CLSID, APPID nebo URL jako *textové* pole části **CONTROL** prostředku dialogového okna spolu s "AtlAxWin80" jako pole *názvu třídy* ve stejné části. Následující ukazuje, jak může vypadat platný oddíl **CONTROL:**

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Další informace o úpravách skriptů prostředků naleznete v [tématu How to: Open a Resource Script File in Text Format](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Další informace o příkazech definice prostředků ovládacího prvku naleznete v [tématu Common Control Parameters](/windows/win32/menurc/common-control-parameters) v části Windows SDK: Nástroje sady SDK.

Další informace o dialogových oknech obecně naleznete v [dialogových polích](/windows/win32/api/winuser/nf-winuser-dialogboxw) a [v okně CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) v sadě Windows SDK.

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a>AtlAxCreateDialog

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
[v] Identifikuje instanci modulu, jehož spustitelný soubor obsahuje šablonu dialogového okna.

*lpTemplateName*<br/>
[v] Identifikuje šablonu dialogového okna. Tento parametr je buď ukazatelem na řetězec znaků zakončený nulou, který určuje název šablony dialogového okna nebo celočíselnou hodnotu, která určuje identifikátor prostředku šablony dialogového okna. Pokud parametr určuje identifikátor prostředku, jeho slovo nejvyššího řádu musí být nulové a jeho slovo nižšího řádu musí obsahovat identifikátor. Tuto hodnotu můžete vytvořit pomocí makra [MAKEINTRESOURCE.](/windows/win32/api/winuser/nf-winuser-makeintresourcew)

*hWndParent*<br/>
[v] Identifikuje okno, které vlastní dialogové okno.

*lpDialogProc*<br/>
[v] Odkazuje na postup dialogového okna. Další informace o postupu dialogového okna naleznete v [tématu DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[v] Určuje hodnotu, která má být předávána dialogovému oknu v parametru *lParam* WM_INITDIALOG zprávy.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Výsledné dialogové okno může obsahovat ovládací prvky ActiveX.

Viz [CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw) a [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) v sadě Windows SDK.

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a>Ovládací prvek AtlAxCreate

Vytvoří, inicializuje a hostuje ovládací prvek ActiveX v zadaném okně.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Ukazatel na řetězec, který má být předán ovládacímu prvku. Musí být formátován jedním z následujících způsobů:

- ProgID, jako je`"MSCAL.Calendar.7"`

- CLSID, jako je`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL, například`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, například`"file://\\\Documents\MyDoc.doc"`

- Fragment HTML, například`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragmentu HTML tak, aby byl označen jako datový proud MSHTML.

*Hwnd*<br/>
[v] Popisovač okna, ke kterému bude ovládací prvek připojen.

*pStream*<br/>
[v] Ukazatel na datový proud, který se používá k inicializaci vlastností ovládacího prvku. Může být NULL.

*ppUnkContainer*<br/>
[out] Adresa ukazatele, který obdrží `IUnknown` kontejneru. Může být NULL.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Tato globální funkce poskytuje stejný výsledek jako volání [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *hWnd*, *pStream*, NULL, NULL, NULL, NULL,NULL);.

Informace o vytvoření licencovaného ovládacího prvku ActiveX naleznete [v tématu AtlAxCreateControlLic](#atlaxcreatecontrollic).

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a>AtlAxCreateControlEx

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

*název lpsz*<br/>
Ukazatel na řetězec, který má být předán ovládacímu prvku. Musí být formátován jedním z následujících způsobů:

- ProgID, jako je`"MSCAL.Calendar.7"`

- CLSID, jako je`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL, například`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, například`"file://\\\Documents\MyDoc.doc"`

- Fragment HTML, například`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragmentu HTML tak, aby byl označen jako datový proud MSHTML.

*Hwnd*<br/>
[v] Popisovač okna, ke kterému bude ovládací prvek připojen.

*pStream*<br/>
[v] Ukazatel na datový proud, který se používá k inicializaci vlastností ovládacího prvku. Může být NULL.

*ppUnkContainer*<br/>
[out] Adresa ukazatele, který obdrží `IUnknown` kontejneru. Může být NULL.

*ppUnkControl*<br/>
[out] Adresa ukazatele, který obdrží `IUnknown` vytvořený ovládací prvek. Může být NULL.

*IidSink*<br/>
Identifikátor rozhraní odchozí rozhraní na obsažený objekt.

*punkSink*<br/>
Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen k spojovacímu bodu určenému *iidSinkem* na obsaženém objektu po úspěšném vytvoření obsaženého objektu.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

`AtlAxCreateControlEx`je podobný [AtlAxCreateControl,](#atlaxcreatecontrol) ale také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímka událostí přijímat události aktivována ovládacího prvku.

Chcete-li vytvořit licencovaný ovládací prvek ActiveX, přečtěte si informace [o obsahu AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a>AtlAxCreateControlLic

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

*název lpsz*<br/>
Ukazatel na řetězec, který má být předán ovládacímu prvku. Musí být formátován jedním z následujících způsobů:

- ProgID, jako je`"MSCAL.Calendar.7"`

- CLSID, jako je`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL, například`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, například`"file://\\\Documents\MyDoc.doc"`

- Fragment HTML, například`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragmentu HTML tak, aby byl označen jako datový proud MSHTML.

*Hwnd*<br/>
Popisovač okna, ke kterému bude ovládací prvek připojen.

*pStream*<br/>
Ukazatel na datový proud, který se používá k inicializaci vlastností ovládacího prvku. Může být NULL.

*ppUnkContainer*<br/>
Adresa ukazatele, který obdrží `IUnknown` kontejneru. Může být NULL.

*bstrlic*<br/>
BSTR obsahující licenci pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="example"></a>Příklad

Ukázka použití ovládacích [prvků ActiveX pomocí služby ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) naleznete v tématu Hostování ovládacích prvků ActiveX pomocí služby ATL `AtlAxCreateControlLic`AXHost.

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a>AtlAxCreateControlLicEx

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

*název lpsz*<br/>
Ukazatel na řetězec, který má být předán ovládacímu prvku. Musí být formátován jedním z následujících způsobů:

- ProgID, jako je`"MSCAL.Calendar.7"`

- CLSID, jako je`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL, například`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, například`"file://\\\Documents\MyDoc.doc"`

- Fragment HTML, například`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragmentu HTML tak, aby byl označen jako datový proud MSHTML.

*Hwnd*<br/>
Popisovač okna, ke kterému bude ovládací prvek připojen.

*pStream*<br/>
Ukazatel na datový proud, který se používá k inicializaci vlastností ovládacího prvku. Může být NULL.

*ppUnkContainer*<br/>
Adresa ukazatele, který obdrží `IUnknown` kontejneru. Může být NULL.

*ppUnkControl*<br/>
[out] Adresa ukazatele, který obdrží `IUnknown` vytvořený ovládací prvek. Může být NULL.

*IidSink*<br/>
Identifikátor rozhraní odchozí rozhraní na obsažený objekt.

*punkSink*<br/>
Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen k spojovacímu bodu určenému *iidSinkem* na obsaženém objektu po úspěšném vytvoření obsaženého objektu.

*bstrlic*<br/>
BSTR obsahující licenci pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

`AtlAxCreateControlLicEx`je podobný [AtlAxCreateControlLic,](#atlaxcreatecontrollic) ale také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímka událostí přijímat události aktivována ovládacího prvku.

### <a name="example"></a>Příklad

Ukázka použití ovládacích [prvků ActiveX pomocí služby ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) naleznete v tématu Hostování ovládacích prvků ActiveX pomocí služby ATL `AtlAxCreateControlLicEx`AXHost.

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a>Ovládací prvek AtlAxAttachControl

Připojí předchozí vytvořený ovládací prvek k zadanému oknu.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*pOvládací prvek*<br/>
[v] Ukazatel na `IUnknown` ovládací prvek.

*Hwnd*<br/>
[v] Zpracovat okno, které bude hostitelem ovládacího prvku.

*ppUnkContainer*<br/>
[out] Ukazatel na ukazatel na `IUnknown` objekt kontejneru.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pomocí [atlAxCreateControlEx](#atlaxcreatecontrolex) a [AtlAxCreateControl](#atlaxcreatecontrol) současně vytvořit a připojit ovládací prvek.

> [!NOTE]
> Připojený objekt ovládacího prvku musí být `AtlAxAttachControl`před voláním správně inicializován .

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a>AtlAxGetHost

Získá přímý ukazatel rozhraní na kontejner zadaného okna (pokud existuje) s uvedením jeho popisovače.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[v] Popisovač okna, které je hostitelem ovládacího prvku.

*Stran*<br/>
[out] Kontejneru `IUnknown` ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a>AtlAxGetControl

Získá přímý ukazatel rozhraní na ovládací prvek obsažený uvnitř zadaného okna s uvedením jeho popisovače.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[v] Popisovač okna, které je hostitelem ovládacího prvku.

*Stran*<br/>
[out] Ovládací `IUnknown` prvek hostované.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a>AtlSetChildSite

Volání této funkce chcete-li nastavit web `IUnknown` podřízeného objektu nadřazeného objektu.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Parametry

*punkDítě*<br/>
[v] Ukazatel na `IUnknown` rozhraní podřízeného.

*punkParent*<br/>
[v] Ukazatel na `IUnknown` rozhraní nadřazené.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a>AtlAxWinInit

Tato funkce inicializuje atl ovládací ho hosting kód registrací **"AtlAxWin80"** a **"AtlAxWinLic80"** třídy okna plus několik vlastních zpráv okna.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace hostitelského kódu ovládacího prvku úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato funkce musí být volána před použitím rozhraní API pro hostování ovládacího prvku ATL. Po volání této funkce **"AtlAxWin"** třída okna lze použít v volání [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) nebo [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw), jak je popsáno v sadě Windows SDK.

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a>AtlAxWinTermín

Tato funkce uninitializes ATL ovládací ho hosting kód zrušením registrace **"AtlAxWin80"** a **"AtlAxWinLic80"** třídy okna.

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Tato funkce jednoduše volá [UnregisterClass,](/windows/win32/api/winuser/nf-winuser-unregisterclassw) jak je popsáno v sadě Windows SDK.

Volání této funkce vyčistit po všechny existující okna hostitele byly zničeny, pokud jste [volali AtlAxWinInit](#atlaxwininit) a již není nutné vytvářet okna hostitele. Pokud tuto funkci nezavoláte, třída okna bude po ukončení procesu automaticky zrušena.

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a>AtlGetObjectSourceInterface

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
[v] Ukazatel na objekt, pro který mají být vráceny informace.

*plibid*<br/>
[out] Ukazatel na LIBID knihovny typů obsahující definici zdrojového rozhraní.

*piid*<br/>
[out] Ukazatel na ID rozhraní výchozího zdrojového rozhraní objektu.

*pdwMajor*<br/>
[out] Ukazatel na číslo hlavní verze knihovny typů obsahující definici zdrojového rozhraní.

*pdwMinor*<br/>
[out] Ukazatel na číslo dílčí verze knihovny typů obsahující definici zdrojového rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`AtlGetObjectSourceInterface`může poskytnout ID rozhraní výchozího zdrojového rozhraní spolu s čísly hlavních a dílčích verzí knihovny typů popisující toto rozhraní.

> [!NOTE]
> Aby tato funkce úspěšně načíst požadované informace, objekt reprezentované *punkObj* musí `IDispatch` implementovat (a vrátit informace o typu prostřednictvím `IDispatch::GetTypeInfo`) plus musí také implementovat buď `IProvideClassInfo2` nebo `IPersist`. Informace o typu zdrojového rozhraní musí být ve stejné `IDispatch`knihovně typů jako informace o typu pro rozhraní .

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak můžete definovat `CEasySink`třídu jímky událostí , která snižuje `IDispEventImpl` počet argumentů šablony, které můžete předat do úplné základy. `EasyAdvise`a `EasyUnadvise` `AtlGetObjectSourceInterface` slouží k inicializaci [iDispEventImpl](../../atl/reference/idispeventimpl-class.md) členy před voláním [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) nebo [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)<br/>
[Kombinovaná řídicí makra](../../atl/reference/composite-control-macros.md)
