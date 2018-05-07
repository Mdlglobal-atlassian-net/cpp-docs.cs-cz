---
title: COleObjectFactory – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd68493c9be5eb0bff63504cf49b38b9a2f216d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory – třída
Implementuje OLE třídy factory, který vytvoří objekty OLE například servery, objekty automatizace a dokumenty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Vytvoří `COleObjectFactory` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](#getclassid)|Vrátí OLE třídy ID objektů, které vytvoří tento objekt pro vytváření.|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Určuje, zda je platná licence ovládacího prvku.|  
|[COleObjectFactory::IsRegistered](#isregistered)|Určuje, jestli objekt pro vytváření zaregistrované s OLE systémové knihovny DLL.|  
|[COleObjectFactory::Register](#register)|Registruje tento objekt pro vytváření objektů OLE systémové knihovny DLL.|  
|[COleObjectFactory::RegisterAll](#registerall)|Registruje všechny objekty aplikace objektu Factory OLE systémové knihovny DLL.|  
|[COleObjectFactory::Revoke](#revoke)|Odvolá tento objekt factory registrace OLE systémové knihovny DLL.|  
|[COleObjectFactory::RevokeAll](#revokeall)|Odvolá registrace aplikace objektu Factory systémem OLE knihovny DLL.|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|Zruší registraci všechny objekty aplikace objektu Factory.|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Zaregistruje tento objekt pro vytváření objektů OLE systémový registr.|  
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Registruje všechny objekty aplikace objektu Factory OLE systémový registr.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Vyžaduje jedinečný klíč z knihovny DLL ovládacího prvku.|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Voláno rámcem vytvořit nový objekt tuto továrnu typu.|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Ověřuje, že klíč vložených v ovládacím prvku shoduje klíč vložených v kontejneru.|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Ověřuje, že je ovládací prvek licenci pro použití v době návrhu.|  
  
## <a name="remarks"></a>Poznámky  
 `COleObjectFactory` Třída obsahuje členské funkce pro provádění následující funkce:  
  
-   Správa registrace objektů.  
  
-   Aktualizace registrace systému OLE, jakož i běhu registrace, které informují OLE, objekty běží a je připravena k přijímat zprávy.  
  
-   Vynucování licencování omezením pomocí ovládacího prvku licencovanou vývojáři v době návrhu a licencované aplikace za běhu.  
  
-   Probíhá registrace řízení objektu Factory OLE systémový registr.  
  
 Další informace o vytvoření objektu, najdete v článcích [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md) a [datové objekty a zdroje dat: vytváření a likvidace](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Další informace o registraci najdete v článku [registrace](../../mfc/registration.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory  
 Vytvoří `COleObjectFactory` objekt, inicializuje jako registrace objekt pro vytváření a přidá ji do seznamu objektů Factory.  
  
```  
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    LPCTSTR lpszProgID);

 
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    int nFlags,  
    LPCTSTR lpszProgID);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Odkaz na ID třídy OLE představuje tento objekt pro vytváření.  
  
 `pRuntimeClass`  
 Ukazatel na run-time třída C++ objektů, které můžete vytvořit tento objekt pro vytváření.  
  
 `bMultiInstance`  
 Určuje, zda jednu instanci aplikace může podporovat více instancí. Pokud **TRUE**, pro každý požadavek pro vytvoření objektu je spuštěných víc instancí aplikace.  
  
 `nFlags`  
 Obsahuje jeden nebo více z následujících příznaků:  
  
- **afxRegDefault** ThreadingModel nastaví model vláken typu Apartment =.  
  
- **afxreginsertable –** umožňuje zobrazit v **vložit objekt** dialogové okno pro objekty OLE.  
  
- `afxRegApartmentThreading` Nastaví v registru na ThreadingModel model vláken typu Apartment =.  
  
- **afxregfreethreading –** nastaví model vláken v registru na ThreadingModel = volné.  
  
     Dvěma příznaky můžete kombinovat `afxRegApartmentThreading` a `afxRegFreeThreading` nastavit ThreadingModel = obě. V tématu [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) ve Windows SDK pro další informace o dělení na vlákna registrace modelu.  
  
 `lpszProgID`  
 Ukazatel na řetězec obsahující identifikátor ústní programu, například "Microsoft Excel."  
  
### <a name="remarks"></a>Poznámky  
 Použití objektu, ale je nutné zaregistrovat se.  
  
 Další informace najdete v tématu [klíč CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) ve Windows SDK.  
  
##  <a name="getclassid"></a>  COleObjectFactory::GetClassID  
 Vrátí odkaz na ID třídy OLE představuje tento objekt pro vytváření.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Představuje odkaz na ID třídy OLE tento objekt pro vytváření.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [klíč CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) ve Windows SDK.  
  
##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey  
 Požadavky jedinečný licenční klíč z ovládacího prvku DLL a uloží jej do `BSTR` na kterou odkazuje `pbstrKey`.  
  
```  
virtual BOOL GetLicenseKey(
    DWORD dwReserved,  
    BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>Parametry  
 `dwReserved`  
 Vyhrazeno pro budoucí použití.  
  
 `pbstrKey`  
 Ukazatel na `BSTR` , uloží licenční klíč.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud řetězec licenční klíč není **NULL**; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce vrátí hodnotu 0 a ukládá ustanovení v `BSTR`. Pokud použijete k vytvoření projektu knihovny MFC ActiveX ControlWizard, poskytuje ControlWizard přepsání, který načte ovládacího prvku licenční klíč.  
  
##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid  
 Určuje, zda je platná licence ovládacího prvku.  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud úspěšně; jinak hodnota false.  
  
##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered  
 Vrátí nenulovou hodnotu, pokud objekt factory je registrován s OLE systémové knihovny DLL.  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt factory je zaregistrován; jinak 0.  
  
##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject  
 Voláno rámcem vytvořit nový objekt.  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na vytvořený objekt. Paměť výjimku ho můžete vyvolat, pokud se nezdaří.  
  
### <a name="remarks"></a>Poznámky  
 Funkci k vytvoření objektu z něco, jiné než přepsat [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) předaný konstruktoru.  
  
##  <a name="register"></a>  COleObjectFactory::Register  
 Registruje tento objekt pro vytváření objektů OLE systémové knihovny DLL.  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt factory je úspěšně zaregistrován; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána obvykle [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.  
  
##  <a name="registerall"></a>  COleObjectFactory::RegisterAll  
 Registruje všechny objekty aplikace objektu Factory OLE systémové knihovny DLL.  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekty Factory se úspěšně zaregistroval; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána obvykle [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.  
  
##  <a name="revoke"></a>  COleObjectFactory::Revoke  
 Odvolá tento objekt factory registrace OLE systémové knihovny DLL.  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá framework automaticky předtím, než se aplikace ukončí. V případě potřeby ji volat z přepsání [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll  
 Odvolá všechny aplikace objektu Factory registrací s OLE systémové knihovny DLL.  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá framework automaticky předtím, než se aplikace ukončí. V případě potřeby ji volat z přepsání [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll  
 Zruší registraci všechny objekty aplikace objektu Factory.  
  
```  
static BOOL PASCAL UnregisterAll();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je úspěšné; jinak hodnota FALSE.  
  
##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry  
 Registruje všechny objekty aplikace objektu Factory OLE systémový registr.  
  
```  
void UpdateRegistry(LPCTSTR lpszProgID = NULL);  
virtual BOOL UpdateRegistry(BOOL bRegister);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszProgID`  
 Ukazatel na řetězec obsahující identifikátor čitelná pro člověka programu, například "Excel.Document.5."  
  
 `bRegister`  
 Určuje, zda objekt pro vytváření objektů třída ovládacích prvků k registraci.  
  
### <a name="remarks"></a>Poznámky  
 Postupujte podle stručný diskusí dvě formy pro tuto funkci:  
  
- **UpdateRegistry (** `lpszProgID` **)** zaregistruje tento objekt pro vytváření objektů OLE systémový registr. Tato funkce je volána obvykle [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.  
  
- **UpdateRegistry (** `bRegister` **)** je přepisovatelné Tato forma funkce. Pokud `bRegister` je **TRUE**, tato funkce zaregistruje třída ovládacích prvků s registrem systému. V opačném. zrušení registrace třídy.  
  
     Pokud použijete k vytvoření projektu knihovny MFC ActiveX ControlWizard, poskytuje ControlWizard přepsání tohoto čistý virtuální funkce.  
  
##  <a name="updateregistryall"></a>  COleObjectFactory::UpdateRegistryAll  
 Registruje všechny objekty aplikace objektu Factory OLE systémový registr.  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bRegister`  
 Určuje, zda objekt pro vytváření objektů třída ovládacích prvků k registraci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jsou úspěšně aktualizovány objekty Factory; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána obvykle [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.  
  
##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey  
 Ověřuje, že je kontejner licenci k používání ovládacího prvku OLE.  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrKey`  
 A `BSTR` ukládání kontejneru verze řetězec licence.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je licence běhu platný; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí verze volání [getlicensekey –](#getlicensekey) získat kopii ovládací prvek je řetězec licence a porovná je s řetězec v `bstrKey`. Pokud se dva řetězce shodují, funkce vrátí nenulovou hodnotu; v opačném případě vrátí hodnotu 0.  
  
 Této funkci můžete poskytovat přizpůsobené ověření licence, které můžete přepsat.  
  
 Funkce [verifyuserlicense –](#verifyuserlicense) ověřuje licence návrhu.  
  
##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense  
 Ověřuje licence návrhu pro ovládací prvek OLE.  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je licence návrhu platný; jinak 0.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer – třída](../../mfc/reference/coletemplateserver-class.md)
