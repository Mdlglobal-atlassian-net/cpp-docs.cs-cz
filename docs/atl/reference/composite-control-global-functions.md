---
title: Globální funkce složeného ovládacího prvku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c62d5056f28460644084296598ae865c6ff5f48
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366598"
---
# <a name="composite-control-global-functions"></a>Globální funkce složeného ovládacího prvku
Tyto funkce poskytuje podporu pro vytváření dialogových oken a pro vytváření, hostování a licencování ovládacích prvků ActiveX.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze používat v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[AtlAxDialogBox](#atlaxdialogbox)|Vytvoří modální dialogové okno z uživatelem zadané šablony dialogového okna. Dialogové okno může obsahovat ovládací prvky ActiveX.|  
|[AtlAxCreateDialog](#atlaxcreatedialog)|Vytvoří nemodální dialogové okno z uživatelem zadané šablony dialogového okna. Dialogové okno může obsahovat ovládací prvky ActiveX.|  
|[AtlAxCreateControl](#atlaxcreatecontrol)|Vytvoří, inicializuje a hostuje ovládací prvek ActiveX v zadaném okně.|  
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Vytvoří ovládací prvek ActiveX, inicializuje ji, hostitelem v zadané okno a načte ukazatele rozhraní (nebo ukazatele) z ovládacího prvku.|  
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.|  
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Vytvoří licencované ovládací prvek ActiveX, inicializuje ji, hostitelem v zadané okno a načte ukazatele rozhraní (nebo ukazatele) z ovládacího prvku.|  
|[AtlAxAttachControl](#atlaxattachcontrol)|Připojí předchozí vytvořený ovládací prvek k zadanému oknu.|  
|[AtlAxGetHost](#atlaxgethost)|Použít k získání přímého rozhraní ukazatel na kontejner pro vybrané okno (pokud existuje), zadána svého popisovače.|  
|[AtlAxGetControl](#atlaxgetcontrol)|Použít k získání přímého rozhraní ukazatel na ovládací prvek nachází v zadané okno (pokud existuje), zadána svého popisovače.|  
|[AtlSetChildSite](#atlsetchildsite)|Inicializuje **IUnknown** podřízené lokality.|  
|[AtlAxWinInit](#atlaxwininit)|Inicializuje hostování kódu pro AxWin objekty.|  
|[AtlAxWinTerm](#atlaxwinterm)|Uninitializes kód hostování pro AxWin objekty.|  
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Vrací informace o rozhraní výchozí zdrojového objektu.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlhost.h  

##  <a name="atlaxdialogbox"></a>  AtlAxDialogBox  
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
 `hInstance`  
 [v] Označuje instanci modulu, jehož spustitelný soubor obsahuje pole šablony dialogového okna.  
  
 `lpTemplateName`  
 [v] Určuje pole šablony dialogového okna. Tento parametr je buď má ukazatel na řetězec znaků ukončené hodnotou null, který určuje název pole šablony dialogového okna, nebo celočíselná hodnota, která určuje identifikátor prostředku šablony pole dialogového okna. Pokud tento parametr určuje identifikátor prostředku, word jeho horní musí být nula a jeho nejnižší word musí obsahovat identifikátor. Můžete použít [MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029) makro pro vytvoření této hodnoty.  
  
 `hWndParent`  
 [v] Identifikuje okně, které vlastní dialogové okno.  
  
 `lpDialogProc`  
 [v] Body k postupu dialogové okno pole. Další informace o postupu pole dialogovém okně najdete v tématu [DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469).  
  
 `dwInitParam`  
 [v] Určuje hodnotu, která mají být předána do dialogového okna aplikace **lParam** parametr **WM_INITDIALOG** zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Použít **AtlAxDialogBox** s šablony dialogového okna, který obsahuje ovládací prvek ActiveX, zadejte platný **CLSID**, **APPID** nebo řetězce adresy URL jako *text* pole z **řízení** části prostředku dialogového okna, společně s "AtlAxWin80" jako *název třídy* pole stejné části. Ukazuje, jaké platná následující **řízení** části může vypadat například:  
  
```  
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,  
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100  
```  
  
 Další informace o úpravách prostředků skriptů, najdete v části [postupy: otevření souboru skriptu prostředků v textovém formátu](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Další informace o řídicí příkazy definice prostředků najdete v tématu [společné parametry řízení](http://msdn.microsoft.com/library/windows/desktop/aa380902) v rámci sady Windows SDK *: SDK Tools*.  
  
 Další informace o dialogových oknech v obecné, najdete v části [DialogBox](http://msdn.microsoft.com/library/windows/desktop/ms645452) a [CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) ve Windows SDK.  
  
##  <a name="atlaxcreatedialog"></a>  AtlAxCreateDialog  
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
 `hInstance`  
 [v] Označuje instanci modulu, jehož spustitelný soubor obsahuje pole šablony dialogového okna.  
  
 `lpTemplateName`  
 [v] Určuje pole šablony dialogového okna. Tento parametr je buď má ukazatel na řetězec znaků ukončené hodnotou null, který určuje název pole šablony dialogového okna, nebo celočíselná hodnota, která určuje identifikátor prostředku šablony pole dialogového okna. Pokud tento parametr určuje identifikátor prostředku, word jeho horní musí být nula a jeho nejnižší word musí obsahovat identifikátor. Můžete použít [MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029) makro pro vytvoření této hodnoty.  
  
 `hWndParent`  
 [v] Identifikuje okně, které vlastní dialogové okno.  
  
 `lpDialogProc`  
 [v] Body k postupu dialogové okno pole. Další informace o postupu pole dialogovém okně najdete v tématu [DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469).  
  
 `dwInitParam`  
 [v] Určuje hodnotu, která mají být předána do dialogového okna aplikace **lParam** parametr **WM_INITDIALOG** zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno může obsahovat ovládací prvky ActiveX.  
  
 V tématu [CreateDialog](http://msdn.microsoft.com/library/windows/desktop/ms645434) a [CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) ve Windows SDK.  
  
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
 `lpszName`  
 Ukazatel na řetězec předávané do ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresu URL, například "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, například "MSHTML:\<HTML >\<textu > Toto je na řádku textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, tak, aby je určený jako MSHTML datového proudu.  
  
 `hWnd`  
 [v] Zpracování do okna Ovládací prvek bude připojen k.  
  
 `pStream`  
 [v] Ukazatel na datový proud, který se používá k chybě při inicializaci vlastností ovládacího prvku. Může být **NULL**.  
  
 `ppUnkContainer`  
 [out] Adresu ukazatele, který se zobrazí **IUnknown** kontejneru. Může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Globální funkce získáte stejný výsledek jako volání [AtlAxCreateControlEx](#atlaxcreatecontrolex)( `lpszName` **,** `hWnd` **,** `pStream` **, NULL, NULL, NULL, NULL** );.  
  
 Vytvořit licencované ovládací prvek ActiveX, najdete v části [AtlAxCreateControlLic](#atlaxcreatecontrollic).  
  
##  <a name="atlaxcreatecontrolex"></a>  AtlAxCreateControlEx  
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
 `lpszName`  
 Ukazatel na řetězec předávané do ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresu URL, například "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, například "MSHTML:\<HTML >\<textu > Toto je na řádku textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, tak, aby je určený jako MSHTML datového proudu.  
  
 `hWnd`  
 [v] Zpracování do okna Ovládací prvek bude připojen k.  
  
 `pStream`  
 [v] Ukazatel na datový proud, který se používá k chybě při inicializaci vlastností ovládacího prvku. Může být **NULL**.  
  
 `ppUnkContainer`  
 [out] Adresu ukazatele, který se zobrazí **IUnknown** kontejneru. Může být **NULL**.  
  
 `ppUnkControl`  
 [out] Adresu ukazatele, který se zobrazí **IUnknown** vytvořený ovládacího prvku. Může být **NULL**.  
  
 `iidSink`  
 Identifikátor rozhraní odchozí rozhraní na obsažený objekt.  
  
 *punkSink*  
 Ukazatel **IUnknown** rozhraní podřízený objekt, který má být připojen k bodu připojení určeného `iidSink` na obsažený objekt po obsažený objekt byl úspěšně vytvořen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 `AtlAxCreateControlEx` je podobná [AtlAxCreateControl](#atlaxcreatecontrol) ale můžete taky přijímat ukazatele rozhraní do ovládacího prvku nově vytvořený a nastavení jímky událostí pro příjem událostí aktivováno pomocí ovládacího prvku.  
  
 Vytvořit licencované ovládací prvek ActiveX, najdete v části [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).  
  
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
 `lpszName`  
 Ukazatel na řetězec předávané do ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresu URL, například "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, například "MSHTML:\<HTML >\<textu > Toto je na řádku textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, tak, aby je určený jako MSHTML datového proudu.  
  
 `hWnd`  
 Zpracování do okna Ovládací prvek bude připojen k.  
  
 `pStream`  
 Ukazatel na datový proud, který se používá k chybě při inicializaci vlastností ovládacího prvku. Může být **NULL**.  
  
 `ppUnkContainer`  
 Adresu ukazatele, který se zobrazí **IUnknown** kontejneru. Může být **NULL**.  
  
 `bstrLic`  
 BSTR obsahující licence pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázkové použití `AtlAxCreateControlLic`.  
  
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
 `lpszName`  
 Ukazatel na řetězec předávané do ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresu URL, například "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, například "MSHTML:\<HTML >\<textu > Toto je na řádku textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, tak, aby je určený jako MSHTML datového proudu.  
  
 `hWnd`  
 Zpracování do okna Ovládací prvek bude připojen k.  
  
 `pStream`  
 Ukazatel na datový proud, který se používá k chybě při inicializaci vlastností ovládacího prvku. Může být **NULL**.  
  
 `ppUnkContainer`  
 Adresu ukazatele, který se zobrazí **IUnknown** kontejneru. Může být **NULL**.  
  
 `ppUnkControl`  
 [out] Adresu ukazatele, který se zobrazí **IUnknown** vytvořený ovládacího prvku. Může být **NULL**.  
  
 `iidSink`  
 Identifikátor rozhraní odchozí rozhraní na obsažený objekt.  
  
 *punkSink*  
 Ukazatel **IUnknown** rozhraní podřízený objekt, který má být připojen k bodu připojení určeného `iidSink` na obsažený objekt po obsažený objekt byl úspěšně vytvořen.  
  
 `bstrLic`  
 BSTR obsahující licence pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 `AtlAxCreateControlLicEx` je podobná [AtlAxCreateControlLic](#atlaxcreatecontrollic) ale můžete taky přijímat ukazatele rozhraní do ovládacího prvku nově vytvořený a nastavení jímky událostí pro příjem událostí aktivováno pomocí ovládacího prvku.  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázkové použití `AtlAxCreateControlLicEx`.  
  
##  <a name="atlaxattachcontrol"></a>  AtlAxAttachControl  
 Připojí předchozí vytvořený ovládací prvek k zadanému oknu.  
  
```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 [v] Ukazatel **IUnknown** ovládacího prvku.  
  
 `hWnd`  
 [v] Popisovač okna, který bude hostitelem ovládacího prvku.  
  
 `ppUnkContainer`  
 [out] Ukazatel na ukazatel **IUnknown** objektu kontejneru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Použití [AtlAxCreateControlEx](#atlaxcreatecontrolex) a [AtlAxCreateControl](#atlaxcreatecontrol) současně vytvořit a připojit ovládacího prvku.  
  
> [!NOTE]
>  Připojovaný objekt ovládacího prvku se musí správně inicializovat před voláním `AtlAxAttachControl`.  
  
##  <a name="atlaxgethost"></a>  AtlAxGetHost  
 Získá přímý ukazatel rozhraní na kontejner zadaného okna (pokud existuje) s uvedením jeho popisovače.  
  
```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 [v] Obslužná rutina do okna, který je hostitelem ovládacího prvku.  
  
 `pp`  
 [out] **IUnknown** kontejneru ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl  
 Získá přímý ukazatel rozhraní na ovládací prvek obsažený uvnitř zadaného okna s uvedením jeho popisovače.  
  
```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 [v] Obslužná rutina do okna, který je hostitelem ovládacího prvku.  
  
 `pp`  
 [out] **IUnknown** hostované ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="atlsetchildsite"></a>  AtlSetChildSite  
 Volání této funkce nastavit webu podřízený objekt, který má **IUnknown** nadřazeného objektu.  
  
```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```  
  
### <a name="parameters"></a>Parametry  
 *punkChild*  
 [v] Ukazatel **IUnknown** rozhraní podřízeného.  
  
 `punkParent`  
 [v] Ukazatel **IUnknown** rozhraní nadřazeného objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
##  <a name="atlaxwininit"></a>  AtlAxWinInit  
 Tato funkce inicializuje ovládací prvek ATL pro hostování kódu tak, že zaregistrujete **"AtlAxWin80"** a **"AtlAxWinLic80"** třídy oken s plus několik vlastní okno zprávy.  
  
```
ATLAPI_(BOOL) AtlAxWinInit();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se inicializace ovládacího prvku hostování kódu byla úspěšná. v opačném případě **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce musí být volána před použitím ovládacího prvku ATL – hostování rozhraní API. Následující volání této funkce **"AtlAxWin"** okno třídu lze použít v jeho voláních [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) nebo [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680), jak je popsáno v sadě Windows SDK.  

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm  
 Tato funkce uninitializes řízení ATL pro hostování kódu zrušením registrace **"AtlAxWin80"** a **"AtlAxWinLic80"** třídy oken.  
  
```
inline BOOL AtlAxWinTerm();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu **TRUE**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce jednoduše volá [UnregisterClass](http://msdn.microsoft.com/library/windows/desktop/ms644899) jak je popsáno v sadě Windows SDK.  
  
 Volání této funkce odstraňování až po všechny existující hostitele windows mají byl zničen, pokud jste volali metodu [AtlAxWinInit](#atlaxwininit) a už je potřeba vytvořit hostitele windows. Pokud nemáte volání této funkce, třída okno bude zrušena automaticky při ukončení procesu.  
  
##  <a name="atlgetobjectsourceinterface"></a>  AtlGetObjectSourceInterface  
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
 `punkObj`  
 [v] Ukazatel na objekt, pro který má být vrácen informace.  
  
 `plibid`  
 [out] Ukazatel na ID KNIHOVNY obsahující definice rozhraní zdroje knihovny typů.  
  
 `piid`  
 [out] Ukazatel rozhraní ID objektu výchozí zdroj rozhraní.  
  
 *pdwMajor*  
 [out] Ukazatel na hlavní číslo verze knihovny typů obsahující definice rozhraní zdroje.  
  
 *pdwMinor*  
 [out] Ukazatel na číslo podverze knihovny typů obsahující definice rozhraní zdroje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 `AtlGetObjectSourceInterface` můžete zadat můžete s ID rozhraní výchozí zdroj rozhraní, společně s ID KNIHOVNY a hlavní a podverze čísla knihovny typů popisující tohoto rozhraní.  
  
> [!NOTE]
>  Pro tuto funkci úspěšně načíst požadované informace o objektu reprezentována `punkObj` musí implementovat `IDispatch` (a vrátí informace o typu prostřednictvím **IDispatch::GetTypeInfo**) a také musí implementovat buď `IProvideClassInfo2` nebo `IPersist`. Informace o typu pro rozhraní zdroje musí být ve stejné knihovny typů jako typ informace pro `IDispatch`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak se definuje třídu jímky událostí `CEasySink`, která omezuje počet argumentů šablony, které můžete předat do `IDispEventImpl` na nezbytné součásti. `EasyAdvise` a `EasyUnadvise` použít `AtlGetObjectSourceInterface` k chybě při inicializaci [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) členy před voláním [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) nebo [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).  
  
 [!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)   
 [Makra složených ovládacích prvků](../../atl/reference/composite-control-macros.md)
