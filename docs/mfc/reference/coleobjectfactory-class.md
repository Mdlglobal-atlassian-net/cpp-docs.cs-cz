---
title: COleObjectFactory – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 295749648dd54349c3fa735008ef8c04d51c8e04
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441899"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory – třída

Implementuje OLE třídy factory, která vytváří objekty OLE, jako jsou servery, automatizační objekty a dokumenty.

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
|[COleObjectFactory::GetClassID](#getclassid)|ID objektů, které vytvoří tento objekt pro vytváření třídy vrátí OLE.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Určuje, zda je platná licence ovládacího prvku.|
|[COleObjectFactory::IsRegistered](#isregistered)|Určuje, zda je objekt factory zaregistrované v OLE systémové knihovny DLL.|
|[COleObjectFactory::Register](#register)|Zaregistruje tento objekt pro vytváření objektů OLE systémové knihovny DLL.|
|[COleObjectFactory::RegisterAll](#registerall)|Zaregistruje všechny objekty pro vytváření objektů aplikaci OLE systémové knihovny DLL.|
|[COleObjectFactory::Revoke](#revoke)|Odvolá registrace tento objekt factory OLE systémové knihovny DLL.|
|[COleObjectFactory::RevokeAll](#revokeall)|Odvolá registrace továrny objekt aplikace s OLE systémové knihovny DLL.|
|[COleObjectFactory::UnregisterAll](#unregisterall)|Zruší registraci všech objektů pro vytváření objektu aplikace.|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Zaregistruje tento objekt pro vytváření objektů OLE systémového registru.|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Zaregistruje všechny objekty pro vytváření objektů aplikaci OLE systémového registru.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Vyžaduje jedinečný klíč z ovládacího prvku knihovny DLL.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Volá se rozhraním, chcete-li vytvořit nový objekt factory pro typ.|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Ověřuje, že vložené v ovládacím prvku klíč odpovídá klíči vložené do kontejneru.|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Ověřuje, že ovládací prvek je licencován pro použití v době návrhu.|

## <a name="remarks"></a>Poznámky

`COleObjectFactory` Třída má členské funkce pro provádění následující funkce:

- Správa registrace objektů.

- Aktualizuje se registr systému OLE, jakož i registraci za běhu, která informuje OLE, objekty jsou spuštěné a jste připravení začít přijímat zprávy.

- Vynucení licencování tím, že omezíte řízení licencovaný vývojáři v době návrhu a licencované aplikace v době běhu.

- Registrace továrny objekt ovládacího prvku OLE systémového registru.

Další informace o vytváření objektů najdete v článcích [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md) a [datové objekty a zdroje dat: vytváření a ničení](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Další informace o registraci, najdete v článku [registrace](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory

Vytvoří `COleObjectFactory` objektu, inicializuje jako zrušit objekt pro vytváření a přidá ji do seznamu objektů pro vytváření.

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

*identifikátor CLSID*<br/>
Odkaz na ID třídy OLE, představuje tento objekt pro vytváření objektů.

*pRuntimeClass*<br/>
Ukazatel na třídu za běhu, které můžete vytvořit tento objekt pro vytváření objektů jazyka C++.

*bMultiInstance*<br/>
Určuje, zda jednu instanci aplikace může podporovat víc instancí. Při hodnotě TRUE se více instancí aplikace jsou spouštěny pro každý požadavek na vytvoření objektu.

*nFlags*<br/>
Obsahuje jeden nebo více z následujících příznaků:

- `afxRegDefault` Nastaví model vláken ThreadingModel = objektu Apartment.

- `afxRegInsertable` Umožňuje ovládacímu prvku se zobrazí v **vložit objekt** dialogové okno pro objekty OLE.

- `afxRegApartmentThreading` Nastaví model vláken v registru ThreadingModel = objektu Apartment.

- `afxRegFreeThreading` Nastaví model vláken v registru ThreadingModel = Free.

     Můžete kombinovat dvěma příznaky `afxRegApartmentThreading` a `afxRegFreeThreading` nastavit ThreadingModel = obojí. Zobrazit [InprocServer32](/windows/desktop/com/inprocserver32) v sadě Windows SDK pro další informace o dělení na vlákna registrace modelu.

*lpszProgID*<br/>
Ukazatel na řetězec obsahující identifikátor slovní programu, jako je například "Microsoft Excelu."

### <a name="remarks"></a>Poznámky

Tento objekt použít, ale zaregistrujte ji.

Další informace najdete v tématu [klíč CLSID](/windows/desktop/com/clsid-key-hklm) v sadě Windows SDK.

##  <a name="getclassid"></a>  COleObjectFactory::GetClassID

Vrátí odkaz na ID třídy OLE, představuje tento objekt pro vytváření.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Návratová hodnota

Představuje odkaz na ID třídy OLE tento objekt pro vytváření.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [klíč CLSID](/windows/desktop/com/clsid-key-hklm) v sadě Windows SDK.

##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey

Požaduje jedinečný licenční klíč z ovládacího prvku knihovny DLL a ukládá ho do BSTR, na které odkazuje *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Vyhrazeno pro budoucí použití.

*pbstrKey*<br/>
Ukazatel na BSTR, ve kterém bude uložený klíč licence.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud řetězec licenční klíč není NULL. jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce vrátí hodnotu 0 a uloží nic BSTR. Pokud používáte ActiveX ControlWizard knihovny MFC k vytvoření projektu, poskytuje ControlWizard přepsání, která načte ovládacího prvku licenční klíč.

##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid

Určuje, zda je platná licence ovládacího prvku.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud úspěšně; naopak hodnota false.

##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered

Vrací nenulovou hodnotu, pokud objekt factory zaregistruje OLE systémové knihovny DLL.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je registrovaný objekt factory; jinak 0.

##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject

Volá se rozhraním, chcete-li vytvořit nový objekt.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vytvořený objekt. Pokud selže může vrátit výjimku paměti.

### <a name="remarks"></a>Poznámky

Přepsání této funkce můžete vytvořit objekt z něco jiného než [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) předaný konstruktoru.

##  <a name="register"></a>  COleObjectFactory::Register

Zaregistruje tento objekt pro vytváření objektů OLE systémové knihovny DLL.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt factory je úspěšně zaregistrovaný; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

##  <a name="registerall"></a>  COleObjectFactory::RegisterAll

Zaregistruje všechny objekty pro vytváření objektů aplikaci OLE systémové knihovny DLL.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud továren jsou úspěšně registrována. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

##  <a name="revoke"></a>  COleObjectFactory::Revoke

Odvolá registrace tento objekt factory OLE systémové knihovny DLL.

```
void Revoke();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci automaticky předtím, než se aplikace ukončí. V případě potřeby ji volat z přepsání [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll

Odvolá všechny registrace továrny objekt aplikace s OLE systémové knihovny DLL.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci automaticky předtím, než se aplikace ukončí. V případě potřeby ji volat z přepsání [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll

Zruší registraci všech objektů pro vytváření objektu aplikace.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; v opačném případě FALSE.

##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry

Zaregistruje všechny objekty pro vytváření objektů aplikaci OLE systémového registru.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parametry

*lpszProgID*<br/>
Ukazatel na řetězec obsahující identifikátor čitelné programu, jako je například "Excel.Document.5."

*bRegister*<br/>
Určuje, zda je objekt factory třídy ovládacího prvku k registraci.

### <a name="remarks"></a>Poznámky

Postupujte podle stručný diskuse o dvě různými formami pro tuto funkci:

- **UpdateRegistry (** `lpszProgID` **)** zaregistruje tento objekt pro vytváření objektů s registrem systému OLE. Tato funkce je obvykle volána [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

- **UpdateRegistry (** `bRegister` **)** tento formulář funkce je přepsatelný. Pokud *bRegister* má hodnotu TRUE, tato funkce registrů třídy ovládacího prvku s registrem systému. V opačném případě ji zruší registraci třídy.

     Pokud používáte ActiveX ControlWizard knihovny MFC k vytvoření projektu, poskytuje ControlWizard přepsání této čistě virtuální funkce.

##  <a name="updateregistryall"></a>  COleObjectFactory::UpdateRegistryAll

Zaregistruje všechny objekty pro vytváření objektů aplikaci OLE systémového registru.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*bRegister*<br/>
Určuje, zda je objekt factory třídy ovládacího prvku k registraci.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou úspěšně aktualizovány továren; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey

Ověřuje, že je kontejner licenci k používání ovládacího prvku OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parametry

*bstrKey*<br/>
Uložení kontejneru verzi licence řetězce BSTR.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je platná licence za běhu jinak 0.

### <a name="remarks"></a>Poznámky

Volá výchozí verze [getlicensekey –](#getlicensekey) získat kopii tohoto ovládacího prvku v řetězci licence a porovná ho s řetězcem v *bstrKey*. Pokud se shodují se dva řetězce, funkce vrátí nenulovou hodnotu; v opačném případě vrátí hodnotu 0.

Můžete přepsat tuto funkci k poskytování přizpůsobených ověření licence.

Funkce [verifyuserlicense –](#verifyuserlicense) ověří vývojářskou licenci.

##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense

Ověří vývojářskou licenci pro ovládací prvek OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je platná; vývojářskou licenci jinak 0.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer – třída](../../mfc/reference/coletemplateserver-class.md)
