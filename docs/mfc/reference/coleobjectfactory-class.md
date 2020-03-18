---
title: COleObjectFactory – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 22805550d13ecb400b151495363e5eda2dfb3b76
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421539"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory – třída

Implementuje objekt pro vytváření tříd OLE, který vytváří objekty OLE, jako jsou servery, automatizační objekty a dokumenty.

## <a name="syntax"></a>Syntaxe

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleObjectFactory:: COleObjectFactory](#coleobjectfactory)|Vytvoří objekt `COleObjectFactory`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleObjectFactory:: GetClassID](#getclassid)|Vrátí ID třídy OLE objektů, které vytvoří tento objekt pro vytváření.|
|[COleObjectFactory:: IsLicenseValid](#islicensevalid)|Určuje, zda je licence ovládacího prvku platná.|
|[COleObjectFactory::-registered](#isregistered)|Označuje, zda je objekt pro vytváření objektů zaregistrován pomocí knihoven DLL systému OLE.|
|[COleObjectFactory:: Register](#register)|Registruje objekt pro vytváření objektů pomocí knihoven DLL systému OLE.|
|[COleObjectFactory:: RegisterAll](#registerall)|Registruje všechny továrny objektů aplikace pomocí knihoven DLL systému OLE.|
|[COleObjectFactory:: REVOKE](#revoke)|Odvolá registraci této továrny objektů pomocí knihoven DLL systému OLE.|
|[COleObjectFactory:: RevokeAll](#revokeall)|Odvolá registrace továrn objektů aplikace pomocí knihoven DLL systému OLE.|
|[COleObjectFactory:: UnregisterAll](#unregisterall)|Zruší registraci všech objektů objektu Application Factory.|
|[COleObjectFactory:: UpdateRegistry](#updateregistry)|Registruje tento objekt pro vytváření objektů pomocí systémového registru OLE.|
|[COleObjectFactory:: UpdateRegistryAll](#updateregistryall)|Registruje všechny továrny objektů aplikace pomocí systémového registru OLE.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[COleObjectFactory:: GetLicenseKey](#getlicensekey)|Požaduje jedinečný klíč z knihovny DLL ovládacího prvku.|
|[COleObjectFactory::-CreateObject](#oncreateobject)|Volá se rozhraním, aby se vytvořil nový objekt pro tento typ objektu pro vytváření.|
|[COleObjectFactory:: VerifyLicenseKey](#verifylicensekey)|Ověřuje, že klíč vložený v ovládacím prvku odpovídá klíči vloženému do kontejneru.|
|[COleObjectFactory:: VerifyUserLicense](#verifyuserlicense)|Ověřuje, zda je ovládací prvek licencován pro použití v době návrhu.|

## <a name="remarks"></a>Poznámky

Třída `COleObjectFactory` má členské funkce pro provádění následujících funkcí:

- Správa registrace objektů.

- Aktualizace systémového registru OLE a také registrace za běhu, který informuje OLE o tom, že objekty běží a jsou připravené přijímat zprávy.

- Vynucování licencí tím, že omezuje použití ovládacího prvku na licencované vývojáře v době návrhu a na licencované aplikace v době běhu.

- Registrace továrn objektů řízení pomocí systémového registru OLE.

Další informace o vytváření objektů najdete v článcích [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md) a [datové objekty a zdroje dat: vytváření a zničení](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Další informace o registraci najdete v článku [registrace](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="coleobjectfactory"></a>COleObjectFactory:: COleObjectFactory

Vytvoří objekt `COleObjectFactory`, inicializuje ho jako neregistrovaný objekt pro vytváření objektů a přidá ho do seznamu továren.

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

*CLSID*<br/>
Odkaz na ID třídy OLE, kterou objekt pro vytváření objektů představuje.

*pRuntimeClass*<br/>
Ukazatel na běhovou třídu objektů, C++ které může tento objekt factory vytvořit.

*bMultiInstance*<br/>
Označuje, zda jedna instance aplikace může podporovat více instancí. Při hodnotě TRUE se pro každý požadavek na vytvoření objektu spustí více instancí aplikace.

*nFlags*<br/>
Obsahuje jeden nebo více následujících příznaků:

- `afxRegDefault` nastaví model vláken na ThreadingModel = Apartment.

- `afxRegInsertable` umožňuje ovládacímu prvku zobrazit v dialogovém okně **Vložit objekt** pro objekty OLE.

- `afxRegApartmentThreading` nastaví model vláken v registru na ThreadingModel = Apartment.

- `afxRegFreeThreading` nastaví model vláken v registru na ThreadingModel = Free.

   Můžete zkombinovat dva příznaky `afxRegApartmentThreading` a `afxRegFreeThreading` a nastavit ThreadingModel = obojí. Další informace o registraci modelu vláken naleznete v tématu [InprocServer32](/windows/win32/com/inprocserver32) v Windows SDK.

*lpszProgID*<br/>
Ukazatel na řetězec obsahující slovní identifikátor programu, jako je například Microsoft Excel.

### <a name="remarks"></a>Poznámky

Chcete-li však objekt použít, je nutné jej zaregistrovat.

Další informace najdete v tématu [klíč CLSID](/windows/win32/com/clsid-key-hklm) v Windows SDK.

##  <a name="getclassid"></a>COleObjectFactory:: GetClassID

Vrátí odkaz na ID třídy OLE, který Tato továrna představuje.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ID třídy OLE, kterou Tato továrna představuje.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [klíč CLSID](/windows/win32/com/clsid-key-hklm) v Windows SDK.

##  <a name="getlicensekey"></a>COleObjectFactory:: GetLicenseKey

Požádá o jedinečný licenční klíč z knihovny DLL ovládacího prvku a uloží jej do objektu BSTR, na který odkazuje *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Vyhrazeno pro budoucí použití.

*pbstrKey*<br/>
Ukazatel na objekt BSTR, který bude obsahovat licenční klíč.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud řetězec licenčního klíče není NULL; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce vrací hodnotu 0 a neukládá nic do BSTR. Použijete-li k vytvoření projektu ControlWizard ActiveX knihovny MFC, ControlWizard poskytuje přepsání, které načte licenční klíč ovládacího prvku.

##  <a name="islicensevalid"></a>COleObjectFactory:: IsLicenseValid

Určuje, zda je licence ovládacího prvku platná.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud successul; v opačném případě false.

##  <a name="isregistered"></a>COleObjectFactory::-registered

Vrací nenulovou hodnotu, pokud je objekt pro vytváření zaregistrován pomocí knihoven DLL systému OLE.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je továrna registrována; v opačném případě 0.

##  <a name="oncreateobject"></a>COleObjectFactory::-CreateObject

Volá se rozhraním, aby se vytvořil nový objekt.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vytvořený objekt. Může vyvolat výjimku paměti, pokud se nezdařila.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci, pokud chcete vytvořit objekt z jiné než [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) předané do konstruktoru.

##  <a name="register"></a>COleObjectFactory:: Register

Registruje objekt pro vytváření objektů pomocí knihoven DLL systému OLE.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je továrna úspěšně registrována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána funkcí [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

##  <a name="registerall"></a>COleObjectFactory:: RegisterAll

Registruje všechny továrny objektů aplikace pomocí knihoven DLL systému OLE.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou továrny úspěšně registrovány; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána funkcí [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

##  <a name="revoke"></a>COleObjectFactory:: REVOKE

Odvolá registraci této továrny objektů pomocí knihoven DLL systému OLE.

```
void Revoke();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci automaticky před ukončením aplikace. V případě potřeby ji zavolejte z přepsání [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="revokeall"></a>COleObjectFactory:: RevokeAll

Odvolá všechny registrace objektu factory aplikace pomocí knihoven DLL systému OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci automaticky před ukončením aplikace. V případě potřeby ji zavolejte z přepsání [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="unregisterall"></a>COleObjectFactory:: UnregisterAll

Zruší registraci všech objektů objektu Application Factory.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

##  <a name="updateregistry"></a>COleObjectFactory:: UpdateRegistry

Registruje všechny továrny objektů aplikace pomocí systémového registru OLE.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parametry

*lpszProgID*<br/>
Ukazatel na řetězec obsahující identifikátor uživatelsky čitelného programu, jako je například Excel. Document. 5.

*bRegister*<br/>
Určuje, zda má být registrován objekt Factory objektu třídy ovládacího prvku.

### <a name="remarks"></a>Poznámky

Následují krátké diskuze dvou forem této funkce:

- **UpdateRegistry (** `lpszProgID` **)** Registruje tento objekt pro vytváření objektů pomocí systémového registru OLE. Tato funkce je obvykle volána funkcí [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

- **UpdateRegistry (** `bRegister` **)** Tato forma funkce je přepsatelné. Pokud má *bRegister* hodnotu true, tato funkce registruje třídu ovládacího prvku se systémovým registrem. V opačném případě zruší registraci třídy.

   Použijete-li k vytvoření projektu ControlWizard ActiveX knihovny MFC, ControlWizard poskytuje přepsání této čistě virtuální funkce.

##  <a name="updateregistryall"></a>COleObjectFactory:: UpdateRegistryAll

Registruje všechny továrny objektů aplikace pomocí systémového registru OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*bRegister*<br/>
Určuje, zda má být registrován objekt Factory objektu třídy ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou továrny úspěšně aktualizovány; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána funkcí [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

##  <a name="verifylicensekey"></a>COleObjectFactory:: VerifyLicenseKey

Ověřuje, že je kontejneru licencovaný pro použití ovládacího prvku OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parametry

*bstrKey*<br/>
Objekt BSTR, který ukládá verzi licenčního řetězce kontejneru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je licence za běhu platná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí verze volá [GetLicenseKey](#getlicensekey) k získání kopie licenčního řetězce ovládacího prvku a porovná ho s řetězcem v *bstrKey*. Pokud se dva řetězce shodují, funkce vrátí nenulovou hodnotu; v opačném případě vrátí 0.

Tuto funkci můžete přepsat tak, aby poskytovala vlastní ověření licence.

Funkce [VerifyUserLicense](#verifyuserlicense) ověří licenci pro dobu návrhu.

##  <a name="verifyuserlicense"></a>COleObjectFactory:: VerifyUserLicense

Ověří licenci na dobu návrhu pro ovládací prvek OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je licence v době návrhu platná; v opačném případě 0.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer – třída](../../mfc/reference/coletemplateserver-class.md)
