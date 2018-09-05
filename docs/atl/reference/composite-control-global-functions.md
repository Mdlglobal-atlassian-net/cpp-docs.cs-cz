---
title: Globální funkce složených ovládacích prvků | Dokumentace Microsoftu
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
ms.openlocfilehash: cf8c5bf4336df95caabd26d5ba4a395190c9591a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677845"
---
# <a name="composite-control-global-functions"></a>Globální funkce složených ovládacích prvků
Tyto funkce poskytují podporu pro vytváření dialogových oken a pro vytváření, hostování a licencování ovládacích prvků ActiveX.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
|||  
|-|-|  
|[AtlAxDialogBox](#atlaxdialogbox)|Vytvoří modální dialogové okno z uživatelem zadané šablony dialogového okna. Dialogové okno může obsahovat ovládací prvky ActiveX.|  
|[AtlAxCreateDialog](#atlaxcreatedialog)|Vytvoří nemodální dialogové okno z uživatelem zadané šablony dialogového okna. Dialogové okno může obsahovat ovládací prvky ActiveX.|  
|[AtlAxCreateControl](#atlaxcreatecontrol)|Vytvoří, inicializuje a hostuje ovládací prvek ActiveX v zadaném okně.|  
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Vytvoří ovládací prvek ActiveX, inicializuje ji, hostuje v zadaném okně a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|  
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.|  
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji, hostuje v zadaném okně a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|  
|[AtlAxAttachControl](#atlaxattachcontrol)|Připojí předchozí vytvořený ovládací prvek k zadanému oknu.|  
|[AtlAxGetHost](#atlaxgethost)|Získá přímý ukazatel rozhraní na kontejner zadaného okna (pokud existuje), uvedením jeho popisovače.|  
|[AtlAxGetControl](#atlaxgetcontrol)|Získá přímý ukazatel rozhraní na ovládací prvek obsažený uvnitř zadaného okna (pokud existuje), uvedením jeho popisovače.|  
|[AtlSetChildSite](#atlsetchildsite)|Inicializuje `IUnknown` podřízené lokality.|  
|[AtlAxWinInit](#atlaxwininit)|Inicializuje kód hostování AxWin objektů.|  
|[AtlAxWinTerm](#atlaxwinterm)|Zruší inicializaci kód hostování AxWin objektů.|  
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Vrátí informace o výchozím zdrojovém rozhraní objektu.|  

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
 *hInstance*  
 [in] Určuje instanci modulu, jehož spustitelný soubor obsahuje šablony dialogového okna.  
  
 *lpTemplateName*  
 [in] Identifikuje šablony dialogového okna. Tento parametr je buď má ukazatel na řetězec znaků zakončené znakem null, který určuje název šablony dialogového okna nebo celočíselnou hodnotu, která určuje identifikátor prostředku šablony dialogového okna. Pokud parametr určuje identifikátor prostředku, jeho vyšší řád slova musí být nulová a jeho nižší řád slova musí obsahovat identifikátor. Můžete použít [MAKEINTRESOURCE](https://msdn.microsoft.com/library/windows/desktop/ms648029) – makro pro vytvoření této hodnoty.  
  
 *hWndParent*  
 [in] Identifikuje okna, který vlastní dialogové okno.  
  
 *lpDialogProc*  
 [in] Odkazuje na pole proceduru dialogového okna. Další informace o poli proceduru dialogového okna, naleznete v tématu [DialogProc](https://msdn.microsoft.com/library/windows/desktop/ms645469).  
  
 *dwInitParam*  
 [in] Určuje hodnotu pro předání do dialogového okna aplikace *lParam* parametr nezavěsíte zprávu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Použití `AtlAxDialogBox` pomocí šablony dialogového okna, která obsahuje ovládací prvek ActiveX, zadejte platný identifikátor CLSID, APPID nebo adresy URL řetězec jako *text* pole **ovládací PRVEK** oddílu prostředku dialogového okna, spolu s " AtlAxWin80 "jako *název třídy* pole v rámci stejného oddílu. Ukazuje, jaké platný následující **ovládací PRVEK** části může vypadat takto:  
  
```  
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,  
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100  
```  
  
 Další informace o úpravách skripty prostředků najdete v tématu [postupy: otevření souboru skriptu prostředků v textovém formátu](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Další informace o řídicí příkazy definice prostředků najdete v tématu [společné parametry ovládací prvek](/windows/desktop/menurc/common-control-parameters) v rámci sady Windows SDK *: SDK Tools*.  
  
 Další informace v dialogových oknech v Obecné [DialogBox](/windows/desktop/api/winuser/nf-winuser-dialogboxa) a [CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) v sadě Windows SDK.  
  
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
 *hInstance*  
 [in] Určuje instanci modulu, jehož spustitelný soubor obsahuje šablony dialogového okna.  
  
 *lpTemplateName*  
 [in] Identifikuje šablony dialogového okna. Tento parametr je buď má ukazatel na řetězec znaků zakončené znakem null, který určuje název šablony dialogového okna nebo celočíselnou hodnotu, která určuje identifikátor prostředku šablony dialogového okna. Pokud parametr určuje identifikátor prostředku, jeho vyšší řád slova musí být nulová a jeho nižší řád slova musí obsahovat identifikátor. Můžete použít [MAKEINTRESOURCE](https://msdn.microsoft.com/library/windows/desktop/ms648029) – makro pro vytvoření této hodnoty.  
  
 *hWndParent*  
 [in] Identifikuje okna, který vlastní dialogové okno.  
  
 *lpDialogProc*  
 [in] Odkazuje na pole proceduru dialogového okna. Další informace o poli proceduru dialogového okna, naleznete v tématu [DialogProc](https://msdn.microsoft.com/library/windows/desktop/ms645469).  
  
 *dwInitParam*  
 [in] Určuje hodnotu pro předání do dialogového okna aplikace *lParam* parametr nezavěsíte zprávu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno může obsahovat ovládací prvky ActiveX.  
  
 Zobrazit [CreateDialog](/windows/desktop/api/winuser/nf-winuser-createdialoga) a [CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) ve Windows SDK.  
  
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
 *lpszName*  
 Ukazatel na řetězec předají do ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   Identifikátor CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresa URL, jako "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako například "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, jako "MSHTML:\<HTML >\<text > to je řádek textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, takže je určený jako proud MSHTML aplikace.  
  
 *hWnd*  
 [in] Popisovač okna, který ovládací prvek bude připojen k.  
  
 *pStream*  
 [in] Ukazatel na datový proud, který slouží k inicializaci vlastnosti ovládacího prvku. Může mít hodnotu NULL.  
  
 *ppUnkContainer*  
 [out] Adresa ukazatel, který se zobrazí `IUnknown` kontejneru. Může mít hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tato globální funkce získáte stejný výsledek jako volání funkce [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *hWnd*, *pStream*, NULL, NULL, HODNOTA NULL, NULL);.  
  
 Vytvoření licencovaného ovládacího prvku ActiveX, najdete v tématu [AtlAxCreateControlLic](#atlaxcreatecontrollic).  
  
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
 *lpszName*  
 Ukazatel na řetězec předají do ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   Identifikátor CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresa URL, jako "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako například "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, jako "MSHTML:\<HTML >\<text > to je řádek textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, takže je určený jako proud MSHTML aplikace.  
  
 *hWnd*  
 [in] Popisovač okna, který ovládací prvek bude připojen k.  
  
 *pStream*  
 [in] Ukazatel na datový proud, který slouží k inicializaci vlastnosti ovládacího prvku. Může mít hodnotu NULL.  
  
 *ppUnkContainer*  
 [out] Adresa ukazatel, který se zobrazí `IUnknown` kontejneru. Může mít hodnotu NULL.  
  
 *ppUnkControl*  
 [out] Adresa ukazatel, který se zobrazí `IUnknown` vytvořený ovládacího prvku. Může mít hodnotu NULL.  
  
 *iidSink*  
 Identifikátor rozhraní odchozí rozhraní v obsažený objekt.  
  
 *punkSink*  
 Ukazatel `IUnknown` rozhraní jímky objektu k připojení k připojení bodu určeného *iidSink* na obsaženého objektu po úspěšném vytvoření obsažený objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 `AtlAxCreateControlEx` je podobný [AtlAxCreateControl](#atlaxcreatecontrol) , ale také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímky událostí přijímat události vyvolané ovládacího prvku.  
  
 Vytvoření licencovaného ovládacího prvku ActiveX, najdete v tématu [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).  
  
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
 *lpszName*  
 Ukazatel na řetězec předají do ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   Identifikátor CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresa URL, jako "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako například "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, jako "MSHTML:\<HTML >\<text > to je řádek textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, takže je určený jako proud MSHTML aplikace.  
  
 *hWnd*  
 Popisovač okna, který ovládací prvek bude připojen k.  
  
 *pStream*  
 Ukazatel na datový proud, který slouží k inicializaci vlastnosti ovládacího prvku. Může mít hodnotu NULL.  
  
 *ppUnkContainer*  
 Adresa ukazatel, který se zobrazí `IUnknown` kontejneru. Může mít hodnotu NULL.  
  
 *bstrLic*  
 BSTR obsahující licenci pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="example"></a>Příklad  
 Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku toho, jak používat `AtlAxCreateControlLic`.  
  
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
 *lpszName*  
 Ukazatel na řetězec předají do ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   Identifikátor CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresa URL, jako "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako například "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, jako "MSHTML:\<HTML >\<text > to je řádek textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, takže je určený jako proud MSHTML aplikace.  
  
 *hWnd*  
 Popisovač okna, který ovládací prvek bude připojen k.  
  
 *pStream*  
 Ukazatel na datový proud, který slouží k inicializaci vlastnosti ovládacího prvku. Může mít hodnotu NULL.  
  
 *ppUnkContainer*  
 Adresa ukazatel, který se zobrazí `IUnknown` kontejneru. Může mít hodnotu NULL.  
  
 *ppUnkControl*  
 [out] Adresa ukazatel, který se zobrazí `IUnknown` vytvořený ovládacího prvku. Může mít hodnotu NULL.  
  
 *iidSink*  
 Identifikátor rozhraní odchozí rozhraní v obsažený objekt.  
  
 *punkSink*  
 Ukazatel `IUnknown` rozhraní jímky objektu k připojení k připojení bodu určeného *iidSink* na obsaženého objektu po úspěšném vytvoření obsažený objekt.  
  
 *bstrLic*  
 BSTR obsahující licenci pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 `AtlAxCreateControlLicEx` je podobný [AtlAxCreateControlLic](#atlaxcreatecontrollic) , ale také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímky událostí přijímat události vyvolané ovládacího prvku.  
  
### <a name="example"></a>Příklad  
 Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku toho, jak používat `AtlAxCreateControlLicEx`.  
  
##  <a name="atlaxattachcontrol"></a>  AtlAxAttachControl  
 Připojí předchozí vytvořený ovládací prvek k zadanému oknu.  
  
```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parametry  
 *pControl*  
 [in] Ukazatel `IUnknown` ovládacího prvku.  
  
 *hWnd*  
 [in] Popisovač okna, který bude hostitelem ovládacího prvku.  
  
 *ppUnkContainer*  
 [out] Ukazatel na ukazatel `IUnknown` objektu kontejneru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Použití [AtlAxCreateControlEx](#atlaxcreatecontrolex) a [AtlAxCreateControl](#atlaxcreatecontrol) chcete současně vytvořit a připojit ovládacího prvku.  
  
> [!NOTE]
>  Připojovaný objekt ovládacího prvku musí být správně inicializován před voláním `AtlAxAttachControl`.  
  
##  <a name="atlaxgethost"></a>  AtlAxGetHost  
 Získá přímý ukazatel rozhraní na kontejner zadaného okna (pokud existuje) s uvedením jeho popisovače.  
  
```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 [in] Popisovač okna, které je hostitelem ovládacího prvku.  
  
 *str*  
 [out] `IUnknown` Kontejneru ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl  
 Získá přímý ukazatel rozhraní na ovládací prvek obsažený uvnitř zadaného okna s uvedením jeho popisovače.  
  
```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 [in] Popisovač okna, které je hostitelem ovládacího prvku.  
  
 *str*  
 [out] `IUnknown` Hostované ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="atlsetchildsite"></a>  AtlSetChildSite  
 Voláním této funkce nastavíte lokalitu podřízeného objektu `IUnknown` nadřazeného objektu.  
  
```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```  
  
### <a name="parameters"></a>Parametry  
 *punkChild*  
 [in] Ukazatel `IUnknown` rozhraní podřízeného.  
  
 *punkParent*  
 [in] Ukazatel `IUnknown` rozhraní nadřazeného prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
##  <a name="atlaxwininit"></a>  AtlAxWinInit  
 Tato funkce inicializuje ATL řídicího hostitelského kódu tak, že zaregistrujete **"AtlAxWin80"** a **"AtlAxWinLic80"** třídy oken a několika vlastních zpráv okna.  
  
```
ATLAPI_(BOOL) AtlAxWinInit();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud inicializaci řídicího hostitelského kódu byla úspěšná. v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce musí být volána před pomocí ovládacího prvku ATL – hostování rozhraní API. Následující volání této funkce **"AtlAxWin"** třídy okna je možné ve voláních [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) nebo [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa), jak je popsáno v sadě Windows SDK.  

##  <a name="atlaxwinterm"></a>  Call AtlAxWinTerm  
 Tato funkce zruší inicializaci ATL řídicího hostitelského kódu při zrušení registrace **"AtlAxWin80"** a **"AtlAxWinLic80"** tříd oken.  
  
```
inline BOOL AtlAxWinTerm();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Jednoduše volá tuto funkci [UnregisterClass](https://msdn.microsoft.com/library/windows/desktop/ms644899) jak je popsáno v sadě Windows SDK.  
  
 Voláním této funkce Vyčištění po všechny existující hostitele windows nejsou zničeny, pokud jste volali [AtlAxWinInit](#atlaxwininit) a už nebude potřeba vytvořit hostitele windows. Pokud není voláním této funkce, třídy okna se odregistrovat automaticky při ukončení procesu.  
  
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
 *punkObj*  
 [in] Ukazatel na objekt, pro který má být vrácen informace.  
  
 *plibid*  
 [out] Ukazatel na LIBID knihovnu typů obsahující definice zdrojové rozhraní.  
  
 *piid*  
 [out] Ukazatel na Identifikátor rozhraní objektu výchozím zdrojovém rozhraní.  
  
 *pdwMajor*  
 [out] Ukazatel na číslo hlavní verze knihovny typů obsahující definice zdrojové rozhraní.  
  
 *pdwMinor*  
 [out] Ukazatel na číslo podverze knihovnu typů obsahující definice zdrojové rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 `AtlGetObjectSourceInterface` můžete poskytují rozhraní ID výchozím zdrojovém rozhraní, spolu s LIBID a hlavní a podverze čísla knihovnu typů popisující rozhraní.  
  
> [!NOTE]
>  Pro tuto funkci se úspěšně načíst požadované informace objekt reprezentovaný *punkObj* musí implementovat `IDispatch` (a vrátí informace o typu skrze `IDispatch::GetTypeInfo`) a navíc musí také implementovat buď `IProvideClassInfo2` nebo `IPersist`. Informace o typu pro zdrojové rozhraní musí být v knihovně typů jako informace o typu `IDispatch`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak můžete třeba definovat třídu jímky událostí `CEasySink`, který snižuje počet argumentů šablony, které můžete předat `IDispEventImpl` k úplné essentials. `EasyAdvise` a `EasyUnadvise` použít `AtlGetObjectSourceInterface` inicializovat [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) členy před voláním [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) nebo [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).  
  
 [!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)   
 [Makra složených ovládacích prvků](../../atl/reference/composite-control-macros.md)
