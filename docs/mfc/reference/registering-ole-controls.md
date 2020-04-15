---
title: Registrace ovládacích prvků OLE
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 2f2d7872e8b9369b5eef283e5b52a54c29afd563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372962"
---
# <a name="registering-ole-controls"></a>Registrace ovládacích prvků OLE

K ovládacím prvkům OLE, stejně jako k ostatním objektům serveru OLE, přistupují jiné aplikace podporující technologie OLE. Toho je dosaženo registrací knihovny typů a třídy ovládacího prvku.

Následující funkce umožňují přidat a odebrat třídu ovládacího prvku, stránky vlastností a knihovnu typů v registrační databázi systému Windows:

### <a name="registering-ole-controls"></a>Registrace ovládacích prvků OLE

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Přidá třídu ovládacího prvku do registrační databáze.|
|[Třída AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Přidá stránku vlastností ovládacího prvku do registrační databáze.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Přidá knihovnu typů ovládacího prvku do registrační databáze.|
|[Třída AfxOleUnregisterClass](#afxoleunregisterclass)|Odebere třídu ovládacího prvku nebo třídu stránky vlastností z registrační databáze.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Odebere knihovnu typů ovládacího prvku z registrační databáze.|

`AfxOleRegisterTypeLib`je obvykle volána v implementaci řídicí `DllRegisterServer`dll . Podobně `AfxOleUnregisterTypeLib` je volána `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`a `AfxOleUnregisterClass` jsou obvykle volány `UpdateRegistry` členskou funkcí třídy ovládacího prvku nebo stránky vlastností.

## <a name="afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

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
Popisovač instance modulu přidruženého ke třídě ovládacího prvku.

*Identifikátor clsid*<br/>
Jedinečné ID třídy ovládacího prvku.

*pszProgID*<br/>
Jedinečné ID programu ovládacího prvku.

*idTypeName*<br/>
ID prostředku řetězce, který obsahuje uživatelem čitelný název typu ovládacího prvku.

*idBitmap*<br/>
ID prostředku bitmapy, která slouží k reprezentaci ovládacího prvku OLE na panelu nástrojů nebo paletě.

*nRegFlags*<br/>
Obsahuje jeden nebo více z následujících příznaků:

- `afxRegInsertable`Umožňuje, aby se ovládací prvek zobrazil v dialogovém okně Vložit objekt pro objekty OLE.

- `afxRegApartmentThreading`Nastaví model podprocesu v registru na ThreadingModel=Apartment.

- `afxRegFreeThreading`Nastaví model podprocesu v registru na ThreadingModel=Free.

   Můžete kombinovat dva `afxRegApartmentThreading` příznaky `afxRegFreeThreading` a nastavit ThreadingModel=Both. Další informace o registraci modelu vlákna naleznete v části [InprocServer32](/windows/win32/com/inprocserver32) v sadě Windows SDK.

> [!NOTE]
> Ve verzích knihovny MFC před knihovnou MFC 4.2 byl **parametrem int** *nRegFlags* parametr *bInsertable*, který umožňoval nebo nepovolil vložení ovládacího prvku z dialogového okna Vložit objekt.

*dwMiscStav*<br/>
Obsahuje jeden nebo více z následujících příznaků stavu (popis příznaků naleznete v tématu výčet OLEMISC v sadě Windows SDK):

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
Jedinečné ID třídy ovládacího prvku.

*wVerMajor*<br/>
Číslo hlavní verze třídy ovládacího prvku.

*wNeminor*<br/>
Číslo dílčí verze třídy ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla registrována třída ovládacího prvku; jinak 0.

### <a name="remarks"></a>Poznámky

To umožňuje ovládací prvek, který má být použit kontejnery, které jsou vědomi řízení OLE. `AfxOleRegisterControlClass`Aktualizuje registr s názvem ovládacího prvku a umístění v systému a také nastaví model podprocesu, který podporuje ovládací prvek v registru. Další informace naleznete [v technické poznámce 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment-Model zřetězení v ole ovládací prvky" a [o procesech a podprocesech](/windows/win32/ProcThread/about-processes-and-threads) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

Výše uvedený příklad `AfxOleRegisterControlClass` ukazuje, jak je volána s příznakem pro vložitelné a příznak pro model apartment ORed společně vytvořit šestý parametr:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Ovládací prvek se zobrazí v dialogovém okně Vložit objekt pro povolené kontejnery a bude model apartment aware. Ovládací prvky podporující model apartment musí zajistit, že data statické třídy je chráněna zámky, takže zatímco ovládací prvek v jednom apartment je přístup ke statickým datům, není zakázán plánovačem před dokončením a jiné instance stejné třídy začne používat stejná statická data. Všechny přístupy ke statickým datům budou obklopeny kritickým kódem oddílu.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a>Třída AfxOleRegisterPropertyPageClass

Zaregistruje třídu stránky vlastností s registrační databází systému Windows.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač instance modulu přidruženého ke třídě stránky vlastností.

*Identifikátor clsid*<br/>
Jedinečné ID třídy stránky vlastností.

*idTypeName*<br/>
ID prostředku řetězce, který obsahuje uživatelem čitelný název stránky vlastností.

*nRegFlags*<br/>
Může obsahovat příznak:

- `afxRegApartmentThreading`Nastaví model podprocesu v registru na ThreadingModel = Apartment.

> [!NOTE]
> Ve verzích knihovny MFC před knihovnou MFC 4.2 nebyl parametr **int** *nRegFlags* k dispozici. Všimněte si `afxRegInsertable` také, že příznak není platnou volbou pro stránky vlastností a způsobí ASSERT v knihovně MFC, pokud je nastavena

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla registrována třída ovládacího prvku; jinak 0.

### <a name="remarks"></a>Poznámky

To umožňuje stránku vlastností, které mají být použity kontejnery, které jsou ole ovládací prvek vědomi. `AfxOleRegisterPropertyPageClass`Aktualizuje registr s názvem stránky vlastností a jeho umístění v systému a také nastaví model podprocesu, který ovládací prvek podporuje v registru. Další informace naleznete [v technické poznámce 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment-Model zřetězení v ole ovládací prvky" a [o procesech a podprocesech](/windows/win32/ProcThread/about-processes-and-threads) v sadě Windows SDK.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

Registruje knihovnu typů s registrační databází systému Windows a umožňuje knihovnu typů, která má být použita jinými kontejnery, které jsou vědomi řízení OLE.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač instance aplikace přidružené ke knihovně typů.

*tlid*<br/>
Jedinečné ID knihovny typů.

*pszNázev_souboru*<br/>
Odkazuje na volitelný název souboru lokalizované knihovny typů (. TLB) pro ovládací prvek.

*pszHelpDir*<br/>
Název adresáře, ve kterém lze nalézt soubor nápovědy pro knihovnu typů. Pokud null, soubor nápovědy se předpokládá, že je ve stejném adresáři jako samotná knihovna typů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla knihovna typů zaregistrována; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce aktualizuje registr názvem knihovny typů a jeho umístěním v systému.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a>Třída AfxOleUnregisterClass

Odebere položku třídy ovládacího prvku nebo vlastností z registrační databáze systému Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
Jedinečné ID třídy ovládacího prvku nebo stránky vlastností.

*pszProgID*<br/>
Jedinečné ID programu na stránce ovládacího prvku nebo vlastností.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla třída stránky ovládacího prvku nebo vlastnosti úspěšně nezaregistrována. jinak 0.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib

Voláním této funkce odeberte položku knihovny typů z registrační databáze systému Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Parametry

*tlID*<br/>
Jedinečné ID knihovny typů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla knihovna typů úspěšně neregistrována; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
