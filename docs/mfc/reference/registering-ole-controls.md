---
title: Registrace ovládacích prvků OLE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 468eb677a0073e25c9ef33182aea0d321cded352
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335615"
---
# <a name="registering-ole-controls"></a>Registrace ovládacích prvků OLE
Ovládací prvky OLE, jako u jiných objektů serveru OLE je přístupný další aplikace používající OLE. Tím se dosahuje registrace knihovny typů a tříd ovládacího prvku.  
  
 Tyto funkce umožňují přidávat a odebírat ovládacího prvku třídy stránky vlastností a knihovnu typů v registrační databázi Windows:  
  
### <a name="registering-ole-controls"></a>Registrace ovládacích prvků OLE  
  
|||  
|-|-|  
|[Afxoleregistercontrolclass –](#afxoleregistercontrolclass)|Přidá třídu ovládacího prvku do registrační databázi.|  
|[Afxoleregisterpropertypageclass –](#afxoleregisterpropertypageclass)|Stránka vlastností ovládacího prvku přidá do registrační databázi.|  
|[Afxoleregistertypelib –](#afxoleregistertypelib)|Přidá knihovnu typů ovládacího prvku do registrační databázi.|  
|[Afxoleunregisterclass –](#afxoleunregisterclass)|Odebere z registrační databáze třídy ovládacího prvku nebo třídy stránky vlastností.|  
|[Afxoleunregistertypelib –](#afxoleunregistertypelib)|Odebere knihovny typů ovládacího prvku z registrační databázi.|  
  
 `AfxOleRegisterTypeLib` je obvykle volána v implementaci ovládacího prvku DLL `DllRegisterServer`. Obdobně `AfxOleUnregisterTypeLib` je volán `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, a `AfxOleUnregisterClass` jsou obvykle volány `UpdateRegistry` členskou funkci třídy ovládacího prvku objekt pro vytváření nebo vlastnosti stránky.  
  
##  <a name="afxoleregistercontrolclass"></a>  Afxoleregistercontrolclass –  
 Zaregistruje třídu ovládacího prvku se registrační databázi Windows.  
  
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
 *hInstance*  
 Popisovač instance modulu přidružené k třídě ovládacího prvku.  
  
 *identifikátor CLSID*  
 Třída jedinečné ID ovládacího prvku.  
  
 *pszProgID*  
 Jedinečný Identifikátor programu ovládacího prvku.  
  
 *idTypeName*  
 ID prostředku řetězce, který obsahuje název čitelný pro uživatele typu ovládacího prvku.  
  
 *idBitmap*  
 ID prostředku rastrového obrázku používá k reprezentování ovládacího prvku OLE v panelu nástrojů nebo z palety.  
  
 *nRegFlags*  
 Obsahuje jeden nebo více z následujících příznaků:  
  
- `afxRegInsertable` Umožňuje ovládacímu prvku se zobrazí v dialogovém okně Vložit objekt pro objekty OLE.  
  
- `afxRegApartmentThreading` Nastaví model vláken v registru ThreadingModel = objektu Apartment.  
  
- `afxRegFreeThreading` Nastaví model vláken v registru ThreadingModel = Free.  
  
     Můžete kombinovat dvěma příznaky `afxRegApartmentThreading` a `afxRegFreeThreading` nastavit ThreadingModel = obojí. Zobrazit [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) v sadě Windows SDK pro další informace o dělení na vlákna registrace modelu.  
  
> [!NOTE]
>  V MFC – verze před MFC 4.2 **int** *nRegFlags* parametr byl parametr typu BOOL *bInsertable*, který povolené nebo zakázané ovládací prvek, který má být vložen z Insert Dialogové okno objektu.  
  
 *dwMiscStatus*  
 Obsahuje jeden nebo více z následujících příznaků stav (pro popis příznaků výčtu viz OLEMISC v sadě Windows SDK):  
  
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
 Jedinečné ID třídy ovládacího prvku.  
  
 *wvermajor –*  
 Číslo hlavní verze třídy ovládacího prvku.  
  
 *wverminor –*  
 Číslo podverze třídy ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud byl zaregistrován třídě ovládacího prvku; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje používat kontejnery, které jsou OLE-control ovládacího prvku. `AfxOleRegisterControlClass` aktualizace registru s názvem ovládacího prvku a umístění v systému a také nastaví model vláken, který podporuje ovládací prvek v registru. Další informace najdete v tématu [Technická poznámka 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment Model práce s vlákny v ovládacích prvků technologie OLE," a [o procesech a vláknech](http://msdn.microsoft.com/library/windows/desktop/ms681917) v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]  
  
 Výše uvedený příklad ukazuje, jak `AfxOleRegisterControlClass` je volána s příznakem pro Vložitelný a příznak pro objektu apartment modelu sloučeny pomocí operátoru OR dohromady a vytvoří šestého parametru:  
  
 [!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]  
  
 Ovládací prvek se zobrazí v dialogovém okně Vložit objekt povolené kontejnery a bude s ohledem na modelu objektu apartment. Ovládací prvky s ohledem na model Apartment musí statické třídy, která data se chrání prostřednictvím zámky, zkontrolujte, aby při ovládacího prvku v objektu apartment jeden přistupuje statická data, před jeho dokončením, a jiná instance stejné třídy spustí pomocí, to není zakázáno plánovačem stejná statická data. Všechny přístupy ke statickým datům umístí kód kritický oddíl.  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxctl.h  
  
##  <a name="afxoleregisterpropertypageclass"></a>  Afxoleregisterpropertypageclass –  
 Zaregistruje Windows registrační databáze třídy stránky vlastností.  
  
```  
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,  
   REFCLSID  clsid,  
   UINT idTypeName,  
   int nRegFlags); 
```  
  
### <a name="parameters"></a>Parametry  
 *hInstance*  
 Popisovač instance modulu přidružené třídy stránky vlastností.  
  
 *identifikátor CLSID*  
 ID jedinečné třídy stránky vlastností.  
  
 *idTypeName*  
 ID prostředku řetězce, který obsahuje uživatelem čitelný název stránky vlastností.  
  
 *nRegFlags*  
 Příznak může obsahovat:  
  
- `afxRegApartmentThreading` Nastaví model vláken v registru ThreadingModel = objektu Apartment.  
  
> [!NOTE]
>  V MFC verze starší než MFC 4.2 **int** *nRegFlags* parametr nebyl k dispozici. Všimněte si také, že `afxRegInsertable` příznak není platná možnost pro stránky vlastností a způsobí vyhodnocení v knihovně MFC, pokud je nastavena  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud byl zaregistrován třídě ovládacího prvku; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje používat kontejnery, které jsou OLE-control na stránce vlastností. `AfxOleRegisterPropertyPageClass` aktualizace registru s názvem stránky vlastností a jeho umístění v systému a také nastaví model vláken, který podporuje ovládací prvek v registru. Další informace najdete v tématu [Technická poznámka 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment Model práce s vlákny v ovládacích prvků technologie OLE," a [o procesech a vláknech](http://msdn.microsoft.com/library/windows/desktop/ms681917) v sadě Windows SDK.  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxctl.h  
  
##  <a name="afxoleregistertypelib"></a>  Afxoleregistertypelib –  
 Zaregistruje knihovnu typů s registrační databáze Windows a umožňuje používat další kontejnery, které jsou OLE-control knihovnu typů.  
  
```   
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,  
    REFGUID tlid,  
    LPCTSTR pszFileName = NULL,  
    LPCTSTR pszHelpDir  = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 *hInstance*  
 Popisovač instance aplikace, které jsou přidružené ke knihovně typů.  
  
 *tlid*  
 Jedinečné ID knihovny typů.  
  
 *pszFileName*  
 Odkazuje na volitelný název souboru knihovny typů lokalizované (. Na soubor TLB) pro ovládací prvek.  
  
 *pszHelpDir*  
 Název adresáře, kde můžete najít v souboru nápovědy pro knihovnu typů. Pokud má hodnotu NULL, soubor nápovědy je považován za ve stejném adresáři jako samotné knihovny typů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud knihovna typů byla registrována; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce aktualizuje registr název knihovny typů a jeho umístění v systému.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdisp.h  
  
##  <a name="afxoleunregisterclass"></a>  Afxoleunregisterclass –  
 Odebere položku Ovládací prvek nebo vlastnost třídy stránky z registrační databázi Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID); 
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor clsID*  
 ID jedinečné třídy stránky, ovládací prvek nebo vlastnost.  
  
 *pszProgID*  
 Jedinečný Identifikátor programu na stránce ovládací prvek nebo vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud ovládací prvek nebo vlastnost třídy stránky byl úspěšně odregistrován; jinak 0.  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxctl.h  
  
##  <a name="afxoleunregistertypelib"></a>  Afxoleunregistertypelib –  
 Voláním této funkce odeberte záznam knihovny typů z registrační databázi Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID); 
```  
  
### <a name="parameters"></a>Parametry  
 *tlID*  
 Jedinečné ID knihovny typů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud byl úspěšně odregistrován; knihovny typů jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]  

### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdisp.h  

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
