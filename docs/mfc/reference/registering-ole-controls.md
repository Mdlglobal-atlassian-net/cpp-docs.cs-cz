---
title: "Registrace ovládacích prvků OLE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.ole
dev_langs: C++
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b11e943b8aa6427517ecb5b32ddf6f56442f5d0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="registering-ole-controls"></a>Registrace ovládacích prvků OLE
Ovládací prvky OLE, jako u jiných objektů OLE serveru, byla přístupná pomocí jiné aplikace využívající technologii OLE. Toho se dosáhne registrace knihovny typů a třídy ovládacího prvku.  
  
 Následující funkce umožňuje přidávat a odebírat třídy ovládacího prvku, stránky vlastností a knihovny typů v databázi registrace Windows:  
  
### <a name="registering-ole-controls"></a>Registrace ovládacích prvků OLE  
  
|||  
|-|-|  
|[Afxoleregistercontrolclass –](#afxoleregistercontrolclass)|Přidá do registrační databáze třídy ovládacího prvku.|  
|[Afxoleregisterpropertypageclass –](#afxoleregisterpropertypageclass)|Přidá stránky vlastností ovládacího prvku do databáze registrace.|  
|[Afxoleregistertypelib –](#afxoleregistertypelib)|Přidá do databázi registrace knihovny typů ovládacího prvku.|  
|[Afxoleunregisterclass –](#afxoleunregisterclass)|Odebere registrační databáze třídy ovládacího prvku nebo třídy stránky vlastností.|  
|[Afxoleunregistertypelib –](#afxoleunregistertypelib)|Odebere databázi registrace knihovny typů ovládacího prvku.|  
  
 `AfxOleRegisterTypeLib`obvykle nazývá implementace knihovny DLL řízení `DllRegisterServer`. Podobně `AfxOleUnregisterTypeLib` volá `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, a `AfxOleUnregisterClass` se běžně označují jako `UpdateRegistry` členské funkce ovládacího prvku třídy objektu pro vytváření nebo vlastnost stránky.  
  
##  <a name="afxoleregistercontrolclass"></a>Afxoleregistercontrolclass –  
 Zaregistruje třídu ovládacího prvku s registrační databázi systému Windows.  
  
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
 `hInstance`  
 Instance popisovače modul přidružený ke třídě ovládacího prvku.  
  
 `clsid`  
 ID jedinečný třídy ovládacího prvku.  
  
 `pszProgID`  
 Jedinečný Identifikátor programu ovládacího prvku.  
  
 `idTypeName`  
 ID prostředku řetězec, který obsahuje název čitelném pro uživatele typu ovládacího prvku.  
  
 *idBitmap*  
 ID prostředku bitové mapy používá k reprezentování OLE ovládacího prvku panel nástrojů nebo palety.  
  
 `nRegFlags`  
 Obsahuje jeden nebo více z následujících příznaků:  
  
- `afxRegInsertable`Umožňuje zobrazit v dialogovém okně Vložit objekt pro objekty OLE.  
  
- `afxRegApartmentThreading`Nastaví v registru na ThreadingModel model vláken typu Apartment =.  
  
- `afxRegFreeThreading`Nastaví model vláken v registru na ThreadingModel = volné.  
  
     Dvěma příznaky můžete kombinovat `afxRegApartmentThreading` a `afxRegFreeThreading` nastavit ThreadingModel = obě. V tématu [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) ve Windows SDK pro další informace o dělení na vlákna registrace modelu.  
  
> [!NOTE]
>  V MFC – verze před MFC 4.2 `int` `nRegFlags` parametr **BOOL** parametr *bInsertable*, který povolené nebo zakázané má být vložen z dialogového okna Vložit objekt ovládacího prvku pole.  
  
 *dwMiscStatus*  
 Obsahuje jeden nebo více z následujících příznaků stav (Popis příznaků naleznete v tématu **OLEMISC** výčet ve Windows SDK):  
  
-   OLEMISC_RECOMPOSEONRESIZE  
  
-   OLEMISC_ONLYICONIC  
  
-   OLEMISC_INSERTNOTREPLACE  
  
-   OLEMISC_STATIC  
  
-   OLEMISC_CANTLINKINSIDE  
  
-   OLEMISC_CANLINKBYOLE1  
  
-   OLEMISC_ISLINKOBJECT  
  
-   OLEMISC_INSIDEOUT  
  
-   OLEMISC_ACTIVATEWHENVISIBLE  
  
-   OLEMISC_RENDERINGISDEVICEINDEPENDENT  
  
-   OLEMISC_INVISIBLEATRUNTIME  
  
-   OLEMISC_ALWAYSRUN  
  
-   OLEMISC_ACTSLIKEBUTTON  
  
-   OLEMISC_ACTSLIKELABEL  
  
-   OLEMISC_NOUIACTIVATE  
  
-   OLEMISC_ALIGNABLE  
  
-   OLEMISC_IMEMODE  
  
-   OLEMISC_SIMPLEFRAME  
  
-   OLEMISC_SETCLIENTSITEFIRST  
  
 *tlid*  
 Jedinečný Identifikátor třídy ovládacího prvku.  
  
 `wVerMajor`  
 Hlavní číslo verze třídy ovládacího prvku.  
  
 `wVerMinor`  
 Číslo podverze třídy ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl zaregistrován třída ovládacích prvků; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje řídit má být používána kontejnery, které jsou OLE-control. `AfxOleRegisterControlClass`aktualizuje registr ovládacího prvku název a umístění v systému a také nastaví model vláken, která podporuje ovládací prvek v registru. Další informace najdete v tématu [Technická poznámka 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment Model práce s vlákny v OLE ovládacích prvků" a [vláken a procesů o](http://msdn.microsoft.com/library/windows/desktop/ms681917) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]  
  
 Výše uvedený příklad ukazuje, jak `AfxOleRegisterControlClass` je volána s příznakem pro Vložitelný a příznak apartment modelu sloučeny pomocí operátoru OR dohromady a vytvoří šestého parametru:  
  
 [!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]  
  
 Ovládací prvek se zobrazí v dialogovém okně Vložit objekt povoleno kontejnerů a bude podporou modelu typu apartment. Ovládací prvky podporou modelu objektu Apartment musí statické třídy dat je chráněn zámky, zkontrolujte, aby při ovládacího prvku v jedné apartment přistupuje statických dat, než je dokončen, a jiná instance stejné třídy spustí pomocí, že není zakázána plánovačem statické stejná data. Všechny přístupy k datům statickou budou uzavřeny v kritická sekce kódu.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="afxoleregisterpropertypageclass"></a>Afxoleregisterpropertypageclass –  
 Registruje třídy stránky vlastností registrační databázi systému Windows.  
  
```  
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,  
   REFCLSID  clsid,  
   UINT idTypeName,  
   int nRegFlags); 
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Instance popisovače modul přidružené třídy stránky vlastností.  
  
 `clsid`  
 ID jedinečný třídy stránky vlastností.  
  
 `idTypeName`  
 ID prostředku řetězec, který obsahuje uživatelem čitelný název stránky vlastností.  
  
 `nRegFlags`  
 Může obsahovat příznak:  
  
- `afxRegApartmentThreading`Nastaví v registru na ThreadingModel model vláken typu Apartment =.  
  
> [!NOTE]
>  V MFC verze starší než MFC 4.2 `int` `nRegFlags` parametr nebyl k dispozici. Všimněte si také, že `afxRegInsertable` příznak není platná možnost pro stránky vlastností a způsobí ASSERT v prostředí MFC, pokud je nastaveno  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl zaregistrován třída ovládacích prvků; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje stránka vlastností, které má být používána kontejnery, které jsou OLE-control. `AfxOleRegisterPropertyPageClass`aktualizuje registr název stránky vlastností a jeho umístění na serveru a také nastaví model vláken, která podporuje ovládací prvek v registru. Další informace najdete v tématu [Technická poznámka 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment Model práce s vlákny v OLE ovládacích prvků" a [vláken a procesů o](http://msdn.microsoft.com/library/windows/desktop/ms681917) ve Windows SDK.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="afxoleregistertypelib"></a>Afxoleregistertypelib –  
 Registruje knihovny typů registrační databázi systému Windows a umožňuje knihovny typů, který má být používána jiných kontejnerů, které jsou OLE-control.  
  
```   
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,  
    REFGUID tlid,  
    LPCTSTR pszFileName = NULL,  
    LPCTSTR pszHelpDir  = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Popisovač instance aplikace přidružené ke knihovně typů.  
  
 *tlid*  
 Jedinečné ID knihovny typů.  
  
 *pszFileName*  
 Odkazuje na volitelný název souboru knihovny lokalizované typů (. Soubor TLB) pro ovládací prvek.  
  
 *pszHelpDir*  
 Název adresáře, kde můžete najít v souboru nápovědy knihovny typů. Pokud **NULL**, soubor nápovědy předpokládá se, že ve stejném adresáři jako knihovny typů, sám sebe.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl zaregistrován knihovny typů; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce aktualizuje registru s názvem typu knihovny a jeho umístění na serveru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="afxoleunregisterclass"></a>Afxoleunregisterclass –  
 Odebere položku Ovládací prvek nebo vlastnost třídy stránky registrační databázi systému Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID); 
```  
  
### <a name="parameters"></a>Parametry  
 *clsID*  
 ID jedinečný třídy stránky ovládací prvek nebo vlastnost.  
  
 `pszProgID`  
 Jedinečný Identifikátor programu stránky ovládací prvek nebo vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud ovládací prvek nebo vlastnost třídy stránky byl úspěšně odregistrován; jinak 0.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="afxoleunregistertypelib"></a>Afxoleunregistertypelib –  
 Volání této funkce pro odebrání položky knihovny typu z registrační databázi systému Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID); 
```  
  
### <a name="parameters"></a>Parametry  
 `tlID`  
 Jedinečné ID knihovny typů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně odregistrován; knihovny typů jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
