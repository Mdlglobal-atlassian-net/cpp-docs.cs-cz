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
ms.openlocfilehash: 165ba7c1918c3ccc5d5d7e0bc067fba86678a3e7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753801"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory – třída

Implementuje objekty třídy OLE, které vytváří objekty OLE, jako jsou servery, objekty automatizace a dokumenty.

## <a name="syntax"></a>Syntaxe

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Vytvoří `COleObjectFactory` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleObjectFactory::GetClassID](#getclassid)|Vrátí ID třídy OLE objektů, které vytvoří tato továrna.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Určuje, zda je licence ovládacího prvku platná.|
|[COleObjectFactory::IsRegistered](#isregistered)|Označuje, zda je objektová továrna registrována u knihoven DLL systému OLE.|
|[COleObjectFactory::Registrovat](#register)|Zaregistruje tuto objektovou továrnu pomocí knihoven DLL systému OLE.|
|[COleObjectFactory::RegisterAll](#registerall)|Registruje všechny továrny na objekty aplikace pomocí knihoven DLL systému OLE.|
|[COleObjectFactory::Odvolat](#revoke)|Odvolává registraci této objektové továrny pomocí knihoven DLL systému OLE.|
|[COleObjectFactory::Revokeall](#revokeall)|Odvolává registrace objektových továren aplikace pomocí knihoven DLL systému OLE.|
|[COleObjectFactory::Zrušit registraciVšech](#unregisterall)|Zruší registrace všech továren objektů aplikace.|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Zaregistruje tuto objektovou továrnu pomocí systémového registru OLE.|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Zaregistruje všechny továrny objektu aplikace pomocí systémového registru OLE.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Požaduje jedinečný klíč z dll ovládacího prvku.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Volat rámci vytvořit nový objekt tohoto typu továrny.|
|[COleObjectFactory::Ověřitlicenční klíč](#verifylicensekey)|Ověří, zda klíč vložený do ovládacího prvku odpovídá klíč vložený do kontejneru.|
|[COleObjectFactory::Ověřit licenci uživatele](#verifyuserlicense)|Ověří, zda je ovládací prvek licencován pro použití v době návrhu.|

## <a name="remarks"></a>Poznámky

Třída `COleObjectFactory` má členské funkce pro provádění následujících funkcí:

- Správa registrace objektů.

- Aktualizace registru systému OLE, stejně jako registrace za běhu, která informuje OLE, že objekty jsou spuštěny a připraveny přijímat zprávy.

- Vynucení licencování omezením použití ovládacího prvku na licencované vývojáře v době návrhu a na licencované aplikace za běhu.

- Registrace továren objektů ovládacího prvku pomocí systémového registru OLE.

Další informace o vytváření objektů naleznete v článcích [Datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md) a [Datové objekty a zdroje dat: Vytváření a ničení](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Další informace o registraci naleznete v článku [Registrace](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="coleobjectfactorycoleobjectfactory"></a><a name="coleobjectfactory"></a>COleObjectFactory::COleObjectFactory

Vytvoří `COleObjectFactory` objekt, inicializuje jej jako neregistrovanou objektovou továrnu a přidá jej do seznamu továren.

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

*Identifikátor clsid*<br/>
Odkaz na ID třídy OLE, které tato objektová továrna představuje.

*třída pRuntimeClass*<br/>
Ukazatel na run-time třídy c++ objekty, které lze vytvořit.

*bMultiInstance*<br/>
Označuje, zda jedna instance aplikace může podporovat více instancí. Pokud TRUE, více instancí aplikace jsou spuštěny pro každý požadavek na vytvoření objektu.

*nPříznaky*<br/>
Obsahuje jeden nebo více z následujících příznaků:

- `afxRegDefault`Nastaví model zřetězení na ThreadingModel=Apartment.

- `afxRegInsertable`Umožňuje, aby se ovládací prvek zobrazil v dialogovém okně **Vložit objekt** pro objekty OLE.

- `afxRegApartmentThreading`Nastaví model podprocesu v registru na ThreadingModel=Apartment.

- `afxRegFreeThreading`Nastaví model podprocesu v registru na ThreadingModel=Free.

   Můžete kombinovat dva `afxRegApartmentThreading` příznaky `afxRegFreeThreading` a nastavit ThreadingModel=Both. Další informace o registraci modelu vlákna naleznete v části [InprocServer32](/windows/win32/com/inprocserver32) v sadě Windows SDK.

*lpszProgID*<br/>
Ukazatel na řetězec obsahující verbální identifikátor programu, například "Microsoft Excel".

### <a name="remarks"></a>Poznámky

Chcete-li však objekt použít, musíte jej zaregistrovat.

Další informace naleznete v tématu [KLÍČ CLSID](/windows/win32/com/clsid-key-hklm) v sadě Windows SDK.

## <a name="coleobjectfactorygetclassid"></a><a name="getclassid"></a>COleObjectFactory::GetClassID

Vrátí odkaz na ID třídy OLE, které tato továrna představuje.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ID třídy OLE, které tato továrna představuje.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [KLÍČ CLSID](/windows/win32/com/clsid-key-hklm) v sadě Windows SDK.

## <a name="coleobjectfactorygetlicensekey"></a><a name="getlicensekey"></a>COleObjectFactory::GetLicenseKey

Požaduje jedinečný licenční klíč z dll ovládacího prvku a ukládá jej v BSTR na odkaz *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwVyhrazeno*<br/>
Vyhrazeno pro budoucí použití.

*pbstrKey*<br/>
Ukazatel na BSTR, který bude ukládat licenční klíč.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud řetězec licenčního klíče není NULL; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce vrátí 0 a neukládá nic v BSTR. Pokud k vytvoření projektu použijete Průvodce řízením ActiveX knihovny MFC, průvodce ovládacím prvkem poskytne přepsání, které načte licenční klíč ovládacího prvku.

## <a name="coleobjectfactoryislicensevalid"></a><a name="islicensevalid"></a>COleObjectFactory::IsLicenseValid

Určuje, zda je licence ovládacího prvku platná.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Návratová hodnota

TRUE-li successul; jinak nepravdivé.

## <a name="coleobjectfactoryisregistered"></a><a name="isregistered"></a>COleObjectFactory::IsRegistered

Vrátí nenulovou hodnotu, pokud je továrna registrována u knihoven DLL systému OLE.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je továrna registrována; jinak 0.

## <a name="coleobjectfactoryoncreateobject"></a><a name="oncreateobject"></a>COleObjectFactory::OnCreateObject

Volat rámci k vytvoření nového objektu.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vytvořený objekt. Může vyvolat výjimku paměti, pokud se nezdaří.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci vytvořit objekt z něčeho jiného než [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) předánkonstruktoru.

## <a name="coleobjectfactoryregister"></a><a name="register"></a>COleObjectFactory::Registrovat

Zaregistruje tuto objektovou továrnu pomocí knihoven DLL systému OLE.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je továrna úspěšně zaregistrována; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

## <a name="coleobjectfactoryregisterall"></a><a name="registerall"></a>COleObjectFactory::RegisterAll

Registruje všechny továrny na objekty aplikace pomocí knihoven DLL systému OLE.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou továrny úspěšně zaregistrovány; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

## <a name="coleobjectfactoryrevoke"></a><a name="revoke"></a>COleObjectFactory::Odvolat

Odvolává registraci této objektové továrny pomocí knihoven DLL systému OLE.

```cpp
void Revoke();
```

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto funkci automaticky před ukončením aplikace. V případě potřeby jej zavolejte z přepsání [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

## <a name="coleobjectfactoryrevokeall"></a><a name="revokeall"></a>COleObjectFactory::Revokeall

Odvolá všechny registrace objektů aplikace pomocí knihovny DL systému OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto funkci automaticky před ukončením aplikace. V případě potřeby jej zavolejte z přepsání [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

## <a name="coleobjectfactoryunregisterall"></a><a name="unregisterall"></a>COleObjectFactory::Zrušit registraciVšech

Zruší registrace všech továren objektů aplikace.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

## <a name="coleobjectfactoryupdateregistry"></a><a name="updateregistry"></a>COleObjectFactory::UpdateRegistry

Zaregistruje všechny továrny objektu aplikace pomocí systémového registru OLE.

```cpp
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parametry

*lpszProgID*<br/>
Ukazatel na řetězec obsahující identifikátor programu čitelný pro člověka, například "Excel.Document.5".

*bRegistrovat*<br/>
Určuje, zda má být registrována objektová továrna třídy ovládacího prvku.

### <a name="remarks"></a>Poznámky

Následuje stručná diskuse o obou formách této funkce:

- **UpdateRegistry(** `lpszProgID` **)** Zaregistruje tuto objektovou továrnu pomocí systémového registru OLE. Tato funkce je obvykle volána [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

- **UpdateRegistry(** `bRegister` **)** Tato forma funkce je overridable. Pokud *bRegister* je PRAVDA, tato funkce zaregistruje třídu ovládacího prvku se systémovým registrem. V opačném případě zruší registraci třídy.

   Pokud k vytvoření projektu použijete Průvodce řízením activexu knihovny MFC, průvodce ovládacím prvkem poskytne přepsání této čisté virtuální funkce.

## <a name="coleobjectfactoryupdateregistryall"></a><a name="updateregistryall"></a>COleObjectFactory::UpdateRegistryAll

Zaregistruje všechny továrny objektu aplikace pomocí systémového registru OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*bRegistrovat*<br/>
Určuje, zda má být registrována objektová továrna třídy ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou továrny úspěšně aktualizovány; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) při spuštění aplikace.

## <a name="coleobjectfactoryverifylicensekey"></a><a name="verifylicensekey"></a>COleObjectFactory::Ověřitlicenční klíč

Ověří, zda je kontejner licencován k použití ovládacího prvku OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parametry

*bstrKey*<br/>
BSTR ukládání kontejneru verzi licenčního řetězce.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je licence za běhu platná; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí verze volá [GetLicenseKey](#getlicensekey) získat kopii licenční řetězec ovládacího prvku a porovná jej s řetězcem v *bstrKey*. Pokud se dva řetězce shodují, funkce vrátí nenulovou hodnotu; jinak vrátí 0.

Tuto funkci můžete přepsat a zajistit vlastní ověření licence.

Funkce [VerifyUserLicense](#verifyuserlicense) ověří licenci návrhu.

## <a name="coleobjectfactoryverifyuserlicense"></a><a name="verifyuserlicense"></a>COleObjectFactory::Ověřit licenci uživatele

Ověří licenci návrhu pro ovládací prvek OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je licence návrhu platná; jinak 0.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
