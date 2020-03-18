---
title: Registrace ovládacích prvků OLE
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 9fcbc002913cc6cce86276796a371231ef0f32e1
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420755"
---
# <a name="registering-ole-controls"></a>Registrace ovládacích prvků OLE

Ovládací prvky OLE, jako jsou jiné objekty serveru OLE, mohou být k dispozici pro jiné aplikace podporující technologii OLE. Toho dosáhnete registrací knihovny typů a třídy ovládacího prvku.

Následující funkce umožňují přidat a odebrat třídu ovládacího prvku, stránky vlastností a knihovnu typů v registrační databázi systému Windows:

### <a name="registering-ole-controls"></a>Registrace ovládacích prvků OLE

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Přidá třídu ovládacího prvku do registrační databáze.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Přidá stránku vlastností ovládacího prvku do registrační databáze.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Přidá knihovnu typů ovládacího prvku do registrační databáze.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Odebere třídu ovládacího prvku nebo třídu stránky vlastností z registrační databáze.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Odebere z registrační databáze knihovnu typů ovládacího prvku.|

`AfxOleRegisterTypeLib` se obvykle volá v implementaci `DllRegisterServer`knihovny DLL ovládacího prvku. Podobně `AfxOleUnregisterTypeLib` je volána `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`a `AfxOleUnregisterClass` jsou obvykle volány `UpdateRegistry` členskou funkcí ovládacího prvku třídy nebo objektu vlastnosti ovládacího prvku.

##  <a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

Registruje třídu ovládacího prvku s registrační databází systému Windows.

```
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,
    REFCLSID clsid,
    LPCTSTR pszProgID,
    UINT idTypeName,
    UINT idBitmap,
    int nRegFlags,
    DWORD dwMiscStatus,
    REFGUID tlid,
    WORD wVerMajor,
    WORD wVerMinor);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Obslužná rutina instance modulu přidruženého k třídě ovládacího prvku.

*CLSID*<br/>
Jedinečné ID třídy ovládacího prvku

*pszProgID*<br/>
Jedinečné ID programu ovládacího prvku.

*idTypeName*<br/>
ID prostředku řetězce, který obsahuje název typu čitelný uživatelem pro ovládací prvek.

*idBitmap*<br/>
ID prostředku rastrového obrázku používaného k reprezentaci ovládacího prvku OLE na panelu nástrojů nebo v paletě

*nRegFlags*<br/>
Obsahuje jeden nebo více následujících příznaků:

- `afxRegInsertable` umožňuje ovládacímu prvku zobrazit v dialogovém okně Vložit objekt pro objekty OLE.

- `afxRegApartmentThreading` nastaví model vláken v registru na ThreadingModel = Apartment.

- `afxRegFreeThreading` nastaví model vláken v registru na ThreadingModel = Free.

   Můžete zkombinovat dva příznaky `afxRegApartmentThreading` a `afxRegFreeThreading` a nastavit ThreadingModel = obojí. Další informace o registraci modelu vláken naleznete v tématu [InprocServer32](/windows/win32/com/inprocserver32) v Windows SDK.

> [!NOTE]
>  V verzích MFC před verzí MFC 4,2 byl parametr **int** *nRegFlags* parametr bool, *bInsertable*, který povolil nebo zakázal ovládacímu prvku vložení z dialogového okna Vložit objekt.

*dwMiscStatus*<br/>
Obsahuje jeden nebo více následujících příznaků stavu (pro popis příznaků, viz výčet OLEMISC v Windows SDK):

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTIVATEWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTIVATE

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid*<br/>
Jedinečné ID třídy ovládacího prvku

*wVerMajor*<br/>
Hlavní číslo verze třídy ovládacího prvku.

*wVerMinor*<br/>
Číslo dílčí verze třídy ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla třída ovládacího prvku registrována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

To umožňuje ovládacímu prvku používat kontejnery, které mají technologii OLE Control. `AfxOleRegisterControlClass` aktualizuje registr s názvem a umístěním ovládacího prvku v systému a také nastaví model vláken, který ovládací prvek podporuje v registru. Další informace naleznete v části [Technická poznámka 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment-model threading v ovládacích prvcích OLE" a [o procesech a vláknech](/windows/win32/ProcThread/about-processes-and-threads) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

Výše uvedený příklad ukazuje, jak je volána `AfxOleRegisterControlClass` s příznakem pro vkládání a příznakem pro model Apartment ORed společně pro vytvoření šestého parametru:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Ovládací prvek se zobrazí v dialogovém okně Vložit objekt pro povolené kontejnery a bude s ním pracují modelem Apartment. Ovládací prvky s přímým přístupem modelu musí zajistit, aby data statické třídy byla chráněná zámky, takže zatímco ovládací prvek v jednom objektu Apartment přistupuje ke statickým datům, není neaktivní v Plánovači před jeho dokončením a další instance stejné třídy začne používat. stejná statická data. Veškerý přístup ke statickým datům bude uzavřený podle kritického kódu oddílu.

### <a name="requirements"></a>Požadavky

  **Header** AFXCTL. h

##  <a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass

Zaregistruje třídu stránky vlastností do registrační databáze systému Windows.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Obslužná rutina instance modulu přidruženého k třídě stránky vlastností.

*CLSID*<br/>
Jedinečné ID třídy stránky vlastností

*idTypeName*<br/>
ID prostředku řetězce, který obsahuje název čitelný uživatelem pro stránku vlastností.

*nRegFlags*<br/>
Může obsahovat příznak:

- `afxRegApartmentThreading` nastaví model vláken v registru na ThreadingModel = Apartment.

> [!NOTE]
>  V verzích knihovny MFC před verzí MFC 4,2 nebyl parametr **int** *nRegFlags* k dispozici. Všimněte si také, že příznak `afxRegInsertable` není platná možnost pro stránky vlastností a v případě, že je nastavená, vyvolá v MFC kontrolní výraz.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla třída ovládacího prvku registrována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

To umožňuje, aby se stránka vlastností použila kontejnery, které mají technologii OLE Control. `AfxOleRegisterPropertyPageClass` aktualizuje registr s názvem stránky vlastností a jeho umístěním v systému a také nastaví model vláken, který ovládací prvek podporuje v registru. Další informace naleznete v části [Technická poznámka 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment-model threading v ovládacích prvcích OLE" a [o procesech a vláknech](/windows/win32/ProcThread/about-processes-and-threads) v Windows SDK.

### <a name="requirements"></a>Požadavky

  **Header** AFXCTL. h

##  <a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

Zaregistruje knihovnu typů s registrační databází Windows a umožňuje, aby se knihovna typů použila v jiných kontejnerech, které podporují ovládací prvky OLE.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač instance aplikace přidružené k knihovně typů

*tlid*<br/>
Jedinečné ID knihovny typů

*pszFileName*<br/>
Odkazuje na nepovinný název souboru lokalizované knihovny typů (. TLB) pro ovládací prvek.

*pszHelpDir*<br/>
Název adresáře, kde lze nalézt soubor s nápovědu pro knihovnu typů. Pokud má hodnotu NULL, předpokládá se, že se soubor Help nachází ve stejném adresáři jako samotná knihovna typů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla zaregistrována knihovna typů; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce aktualizuje registr s názvem knihovny typů a jeho umístěním v systému.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxdisp. h

##  <a name="afxoleunregisterclass"></a>AfxOleUnregisterClass

Odebere položku ovládacího prvku nebo třídy stránky vlastností z registrační databáze systému Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Parametry

*clsID*<br/>
Jedinečné ID třídy ovládacího prvku nebo stránky vlastností.

*pszProgID*<br/>
Jedinečné ID programu ovládacího prvku nebo stránky vlastností.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla třída ovládacího prvku nebo stránky vlastností úspěšně odregistrována; v opačném případě 0.

### <a name="requirements"></a>Požadavky

  **Header** AFXCTL. h

##  <a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib

Voláním této funkce odeberete položku knihovny typů z registrační databáze systému Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Parametry

*tlID*<br/>
Jedinečné ID knihovny typů

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se knihovna typů úspěšně zrušila. v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxdisp. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
