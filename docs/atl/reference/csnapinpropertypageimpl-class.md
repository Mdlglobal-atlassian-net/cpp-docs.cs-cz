---
title: Třída CSnapInPropertyPageimpl
ms.date: 11/04/2016
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
ms.openlocfilehash: 3f09e8500eadd36eec53db95f10261834d672101
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747576"
---
# <a name="csnapinpropertypageimpl-class"></a>Třída CSnapInPropertyPageimpl

Tato třída poskytuje metody pro implementaci objektu stránky vlastnosti modulu snap-in.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSnapinPropertyPageimpl::csnapinpropertyPageimpl](#csnapinpropertypageimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSnapinPropertyPageimpl::Zrušitzavření](#canceltoclose)|Změní stav tlačítek **OK** a **Storno.**|
|[CSnapinPropertyPageimpl::Vytvořit](#create)|Inicializuje nově `CSnapInPropertyPageImpl` vytvořený objekt.|
|[CSnapinPropertyPageimpl::OnApply](#onapply)|Volat rámci, když uživatel klepne na tlačítko **Použít nyní** při použití seznamu vlastností typu průvodce.|
|[CSnapinPropertyPageimpl::OnHelp](#onhelp)|Volat rámci, když uživatel klepne na tlačítko **Nápověda** při použití seznamu vlastností typu průvodce.|
|[CSnapinPropertyPageimpl::OnKillActive](#onkillactive)|Volat rámci, když aktuální stránka již není aktivní.|
|[CSnapinPropertyPageimpl::OnQueryCancel](#onquerycancel)|Volat rámci po kliknutí uživatele na tlačítko **Storno** a před zrušení proběhlo.|
|[CSnapinPropertyPageimpl::OnReset](#onreset)|Volat rámci, když uživatel klepne na tlačítko **Obnovit** při použití seznamu vlastností typu průvodce.|
|[CSnapinPropertyPageimpl::OnSetActive](#onsetactive)|Volat rámci při aktuální stránka se stane aktivní.|
|[CSnapinPropertyPageimpl::OnWizardBack](#onwizardback)|Volat rámci, když uživatel klepne na tlačítko **Zpět** při použití seznamu vlastností typu průvodce.|
|[CSnapinPropertyPageimpl::OnWizardFinish](#onwizardfinish)|Volat rámci, když uživatel klepne na tlačítko **Dokončit** při použití seznamu vlastností typu průvodce.|
|[CSnapinPropertyPageimpl::OnWizardNext](#onwizardnext)|Volat rámci, když uživatel klepne na tlačítko **Další** při použití seznamu vlastností typu průvodce.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Předá aktuální zprávu na všechny stránky seznamu vlastností.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Volání pro aktivaci nebo deaktivaci tlačítka **Použít nyní.**|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Struktura `PROPSHEETPAGE` systému Windows `CSnapInPropertyPageImpl` používá objekt.|

## <a name="remarks"></a>Poznámky

`CSnapInPropertyPageImpl`poskytuje základní implementaci pro objekt stránky vlastností modulu snap-in. Základní funkce stránky vlastností modulu snap-in jsou implementovány pomocí několika různých rozhraní a typů map.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsnap.h

## <a name="csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a>CSnapinPropertyPageimpl::Zrušitzavření

Volání této funkce po neopravitelné změny byla provedena data na stránce seznamu modální vlastností.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>Poznámky

Tato funkce změní tlačítko **OK** na **Zavřít** a zakáže tlačítko **Storno.** Tato změna upozorní uživatele, že změna je trvalá a změny nelze zrušit.

Členská `CancelToClose` funkce neprovede nic v seznamu nemodivě vlastností, protože nemodivá seznam vlastností nemá tlačítko **Storno** ve výchozím nastavení.

## <a name="csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a>CSnapinPropertyPageimpl::csnapinpropertyPageimpl

Vytvoří `CSnapInPropertyPageImpl` objekt.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Parametry

*lpszNázev*<br/>
[v] Název stránky vlastností.

### <a name="remarks"></a>Poznámky

Chcete-li inicializovat základní strukturu, zavolejte [CSnapInPropertyPageImpl::Create](#create).

## <a name="csnapinpropertypageimplcreate"></a><a name="create"></a>CSnapinPropertyPageimpl::Vytvořit

Volání této funkce inicializovat základní strukturu stránky vlastností.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač `PROPSHEETPAGE` struktury obsahující atributy nově vytvořeného seznamu vlastností.

### <a name="remarks"></a>Poznámky

Před voláním této funkce byste měli nejprve zavolat [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl.](#csnapinpropertypageimpl)

## <a name="csnapinpropertypageimplm_psp"></a><a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp

`m_psp`je struktura, jejíž členové `PROPSHEETPAGE`ukládají vlastnosti .

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Poznámky

Pomocí této struktury inicializovat vzhled stránky vlastností po jeho vytvoření.

Další informace o této struktuře, včetně výpisu jejích členů, naleznete v tématu [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) v sadě Windows SDK.

## <a name="csnapinpropertypageimplonapply"></a><a name="onapply"></a>CSnapinPropertyPageimpl::OnApply

Tato členská funkce je volána, když uživatel klepne na **tlačítko OK** nebo **Použít nyní.**

```
BOOL OnApply();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou změny přijaty; jinak 0.

### <a name="remarks"></a>Poznámky

Předtím, než `OnApply` může být volána `SetModified` v rámci, musíte mít volal a nastavit jeho parametr na TRUE. Tím aktivujete tlačítko **Použít nyní,** jakmile uživatel provede změnu na stránce vlastností.

Přepsáním této členské funkce určete, jakou akci váš program provede, když uživatel klepne na tlačítko **Použít nyní.** Při přepsání by funkce měla vrátit hodnotu TRUE, aby přijala změny, a nepravda, aby se změny neprojevily.

Výchozí implementace `OnApply` vrátí hodnotu TRUE.

## <a name="csnapinpropertypageimplonhelp"></a><a name="onhelp"></a>CSnapinPropertyPageimpl::OnHelp

Tato členská funkce je volána, když uživatel klepne na tlačítko **Nápověda** pro stránku vlastností.

```cpp
void OnHelp();
```

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci a zobrazte nápovědu pro stránku vlastností.

## <a name="csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a>CSnapinPropertyPageimpl::OnKillActive

Tato členská funkce je volána, když stránka již není aktivní stránkou.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla data úspěšně aktualizována; jinak 0.

### <a name="remarks"></a>Poznámky

Přepište tuto člennou funkci a provádějte speciální úlohy ověření dat.

## <a name="csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a>CSnapinPropertyPageimpl::OnQueryCancel

Tato členská funkce je volána, když uživatel klepne na tlačítko **Storno** a před akcí zrušení proběhla.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová povolit operaci zrušení; jinak 0.

### <a name="remarks"></a>Poznámky

Přepsáním této členské funkce určete akci, kterou program provede, když uživatel klepne na tlačítko **Storno.**

Výchozí implementace `OnQueryCancel` vrátí hodnotu TRUE.

## <a name="csnapinpropertypageimplonreset"></a><a name="onreset"></a>CSnapinPropertyPageimpl::OnReset

Tato členská funkce je volána, když uživatel klepne na tlačítko **Storno.**

```cpp
void OnReset();
```

### <a name="remarks"></a>Poznámky

Při volání této funkce jsou změny všech stránek vlastností, které byly provedeny uživatelem, který dříve klepl na tlačítko **Použít nyní,** zahozeny a seznam vlastností si zachová fokus.

Přepsáním této členské funkce určete, jakou akci program provede, když uživatel klepne na tlačítko **Storno.**

## <a name="csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a>CSnapinPropertyPageimpl::OnSetActive

Tato členská funkce je volána, když je stránka vybrána uživatelem a stane se aktivní stránkou.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla stránka úspěšně nastavena aktivní; jinak 0.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci a k provádění úkolů při aktivaci stránky. Přepsání této členské funkce by mělo před provedením jakéhokoli jiného zpracování volat výchozí verzi.

Výchozí implementace vrátí hodnotu PRAVDA.

## <a name="csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a>CSnapinPropertyPageimpl::OnWizardBack

Tato členská funkce je volána, když uživatel klepne na tlačítko **Zpět** v průvodci.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Návratová hodnota

- 0 pro automatický postup na předchozí stránku.

- -1, aby se zabránilo změně stránky.

Chcete-li přejít na jinou stránku než na další, vraťte identifikátor zobrazeného dialogového okna.

### <a name="remarks"></a>Poznámky

Přepsat tuto členovou funkci určit některé akce, které uživatel musí provést při klepnutí na tlačítko **Zpět.**

## <a name="csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a>CSnapinPropertyPageimpl::OnWizardFinish

Tato členská funkce je volána, když uživatel klepne na tlačítko **Dokončit** v průvodci.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je seznam vlastností zničen po dokončení průvodce; jinak nula.

### <a name="remarks"></a>Poznámky

Přepište tuto členovou funkci a určete nějakou akci, kterou musí uživatel provést po klepnutí na tlačítko **Dokončit.**

## <a name="csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a>CSnapinPropertyPageimpl::OnWizardNext

Tato členská funkce je volána, když uživatel klepne na tlačítko **Další** v průvodci.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Návratová hodnota

- 0 pro automatický postup na další stránku.

- -1, aby se zabránilo změně stránky.

Chcete-li přejít na jinou stránku než na další, vraťte identifikátor zobrazeného dialogového okna.

### <a name="remarks"></a>Poznámky

Přepište tuto členovou funkci a určete nějakou akci, kterou musí uživatel provést při klepnutí na tlačítko **Další.**

## <a name="csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings

Volání této členské funkce předat zprávu na každou stránku v seznamu vlastností.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
[v] Určuje další informace závislé na zprávě.

*Lparam*<br/>
[v] Určuje další informace závislé na zprávě.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud by zpráva neměla být předána na další stránku vlastností; jinak nula.

### <a name="remarks"></a>Poznámky

Pokud stránka vrátí nenulovou hodnotu, seznam vlastností neodešle zprávu na další stránky.

## <a name="csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified

Volání této členské funkce povolit nebo zakázat **použít nyní** tlačítko, na základě toho, zda nastavení na stránce vlastností by měla být použita na příslušný externí objekt.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parametry

*bZměněno*<br/>
[v] TRUE označuje, že nastavení stránky vlastností byly změněny od posledního použití; FALSE označuje, že nastavení stránky vlastností byly použity nebo by měly být ignorovány.

### <a name="remarks"></a>Poznámky

Seznam vlastností sleduje, které stránky jsou "špinavé", to znamená `SetModified( TRUE )`stránky vlastností, pro které jste volali . Tlačítko **Použít nyní** bude vždy povoleno, pokud zavoláte `SetModified( TRUE )` na jednu ze stránek. Tlačítko **Použít nyní** bude při `SetModified( FALSE )` volání jedné ze stránek zakázáno, ale pouze v případě, že žádná z ostatních stránek není "špinavá".

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
