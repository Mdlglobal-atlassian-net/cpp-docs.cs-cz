---
title: Csnapinpropertypageimpl – třída
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
ms.openlocfilehash: ea79a5624937b27fe69be2c15bac3a0c40592252
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575744"
---
# <a name="csnapinpropertypageimpl-class"></a>Csnapinpropertypageimpl – třída

Tato třída poskytuje metody pro implementaci objektu page vlastnost modul snap-in.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Změní stav **OK** a **zrušit** tlačítka.|
|[CSnapInPropertyPageImpl::Create](#create)|Inicializuje nově vytvořený `CSnapInPropertyPageImpl` objektu.|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Volá se rozhraním, když uživatel klikne **použít** tlačítka při používání seznamu vlastností wizard-type.|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Volá se rozhraním, když uživatel klikne **pomáhají** tlačítka při používání seznamu vlastností wizard-type.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Volá se rozhraním, když aktuální stránka už není aktivní.|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Volá se rozhraním, když uživatel klikne **zrušit** tlačítko a před místo zrušení.|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Volá se rozhraním, když uživatel klikne **resetování** tlačítka při používání seznamu vlastností wizard-type.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Volá se rozhraním, když aktuální stránka stane aktivní.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Volá se rozhraním, když uživatel klikne **zpět** tlačítka při používání seznamu vlastností wizard-type.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Volá se rozhraním, když uživatel klikne **Dokončit** tlačítka při používání seznamu vlastností wizard-type.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Volá se rozhraním, když uživatel klikne **Další** tlačítka při používání seznamu vlastností wizard-type.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Předává aktuální zprávu pro všechny stránky vlastností.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Volání aktivace nebo deaktivace **použít** tlačítko.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows `PROPSHEETPAGE` struktura používá `CSnapInPropertyPageImpl` objektu.|

## <a name="remarks"></a>Poznámky

`CSnapInPropertyPageImpl` poskytuje základní implementaci pro objekt stránky vlastností modul snap-in. Základní funkce stránky vlastností modul snap-in jsou implementovány pomocí několika různých rozhraní a namapujte typy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsnap.h

##  <a name="canceltoclose"></a>  CSnapInPropertyPageImpl::CancelToClose

Voláním této funkce po provedení neopravitelné změny dat na stránce modální seznam vlastností.

```
void CancelToClose();
```

### <a name="remarks"></a>Poznámky

Tato funkce se změní **OK** tlačítko **Zavřít** a zakažte **zrušit** tlačítko. Tato změna upozornění, která uživatele, že změna je trvalé a změny se nedá zrušit.

`CancelToClose` Členská funkce neprovede v nemodálního seznamu vlastností, protože nemá nemodálního seznamu vlastností **zrušit** tlačítko ve výchozím nastavení.

##  <a name="csnapinpropertypageimpl"></a>  CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

Vytvoří `CSnapInPropertyPageImpl` objektu.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
[in] Nadpis na stránce vlastností.

### <a name="remarks"></a>Poznámky

Chcete-li inicializovat podkladová struktura, zavolejte [CSnapInPropertyPageImpl::Create](#create).

##  <a name="create"></a>  CSnapInPropertyPageImpl::Create

Volání této funkce lze inicializovat podkladová struktura stránky vlastností.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač `PROPSHEETPAGE` struktury obsahující atributy nově vytvořený seznam vlastností.

### <a name="remarks"></a>Poznámky

Měli byste nejprve zavolat [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) před voláním této funkce.

##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp

`m_psp` je struktura, jejíž členové uložení vlastnosti `PROPSHEETPAGE`.

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Poznámky

Tuto strukturu použijte pro inicializaci vzhled stránky vlastností po jejím vytváření.

Další informace o této struktuře, včetně seznamu členů, naleznete v tématu [PROPSHEETPAGE](https://msdn.microsoft.com/library/aa815151) v sadě Windows SDK.

##  <a name="onapply"></a>  CSnapInPropertyPageImpl::OnApply

Tato členská funkce je volána, když uživatel klikne **OK** nebo **použít** tlačítko.

```
BOOL OnApply();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou změny přijaty; jinak 0.

### <a name="remarks"></a>Poznámky

Před `OnApply` může být volána rozhraním, musíte zavoláte `SetModified` a nastavte její parametr na hodnotu TRUE. Tím se aktivují **použít** tlačítko ihned poté, co uživatel provede změny na stránce vlastností.

Přepsání této členské funkce lze určit, jakou akci program provede, když uživatel klikne **použít** tlačítko. Při přepsání, funkce by měla vrátit TRUE, pokud chcete přijmout změny a hodnotu FALSE a znemožnit změny tak vliv.

Výchozí implementace `OnApply` vrátí hodnotu TRUE.

##  <a name="onhelp"></a>  CSnapInPropertyPageImpl::OnHelp

Tato členská funkce je volána, když uživatel klikne **pomáhají** tlačítko pro stránku vlastností.

```
void OnHelp();
```

### <a name="remarks"></a>Poznámky

Přepište tato členská funkce pro zobrazení nápovědy pro stránku vlastností.

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

Tato členská funkce je volána, když na stránce už není aktivní stránkou.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud data byla úspěšně aktualizována; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce k provádění úloh ověření speciální datové přepište.

##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel

Tato členská funkce je volána, když uživatel klikne **zrušit** tlačítko a před zrušení akce proběhla.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Návratová hodnota

Povolit operace zrušení; nenulovou hodnotu jinak 0.

### <a name="remarks"></a>Poznámky

Přepsání této členské funkce lze zadat akce program provede, když uživatel klikne **zrušit** tlačítko.

Výchozí implementace `OnQueryCancel` vrátí hodnotu TRUE.

##  <a name="onreset"></a>  CSnapInPropertyPageImpl::OnReset

Tato členská funkce je volána, když uživatel klikne **zrušit** tlačítko.

```
void OnReset();
```

### <a name="remarks"></a>Poznámky

Při volání této funkce se změní na všechny stránky vlastností, které byly provedené uživatelem dříve kliknutím **použít** tlačítka se zahodí, a seznam vlastností uchovává fokus.

Přepsání této členské funkce lze určit, jakou akci provede program, když uživatel klikne **zrušit** tlačítko.

##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive

Tato členská funkce se volá při stránky je vybrán uživatelem a stane aktivní stránkou.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud na stránce se úspěšně nastavila aktivní; jinak 0.

### <a name="remarks"></a>Poznámky

Přepište tato členská funkce k provádění úloh, když je aktivován na stránce. Přepsání metody tato členská funkce by měly volat výchozí verze, před provedením libovolné jiné zpracování.

Výchozí implementace vrací hodnotu TRUE.

##  <a name="onwizardback"></a>  CSnapInPropertyPageImpl::OnWizardBack

Tato členská funkce je volána, když uživatel klikne **zpět** tlačítko v průvodci.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Návratová hodnota

- 0 na automatický přechod na předchozí stránku.

- na stránce zabránit ve změně hodnotu -1.

Přejít na stránku, než na kterém další vrátíte identifikátor dialogových oken, který se má zobrazit.

### <a name="remarks"></a>Poznámky

Přepsání této členské funkce lze zadat některé akce, kdy musí uživatel provést **zpět** po kliknutí na tlačítko.

##  <a name="onwizardfinish"></a>  CSnapInPropertyPageImpl::OnWizardFinish

Tato členská funkce je volána, když uživatel klikne **Dokončit** tlačítko v průvodci.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud seznam vlastností je zničen při dokončení Průvodce; jinak nula.

### <a name="remarks"></a>Poznámky

Přepsání této členské funkce lze zadat některé akce, kdy musí uživatel provést **Dokončit** po kliknutí na tlačítko.

##  <a name="onwizardnext"></a>  CSnapInPropertyPageImpl::OnWizardNext

Tato členská funkce je volána, když uživatel klikne **Další** tlačítko v průvodci.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Návratová hodnota

- 0 na automatický přechod na další stránku.

- na stránce zabránit ve změně hodnotu -1.

Přejít na stránku, než na kterém další vrátíte identifikátor dialogových oken, který se má zobrazit.

### <a name="remarks"></a>Poznámky

Přepsání této členské funkce lze zadat některé akce, kdy musí uživatel provést **Další** po kliknutí na tlačítko.

##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings

Voláním této členské funkce pro předávání zpráv na každou stránku v seznamu vlastností.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
[in] Určuje další informace, závislé na zprávu.

*lParam*<br/>
[in] Určuje další informace, závislé na zprávu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zpráva by neměly předávat na další stránku vlastností. jinak nula.

### <a name="remarks"></a>Poznámky

Pokud na stránce vrátí nenulovou hodnotu, seznam vlastností neodešle zprávy na následujících stránkách.

##  <a name="setmodified"></a>  CSnapInPropertyPageImpl::SetModified

Voláním této členské funkce k povolení nebo zakázání **použít** tlačítko závislosti na tom, zda bude použito nastavení na stránce vlastností pro příslušný objekt externí.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parametry

*bChanged*<br/>
[in] Hodnota TRUE označuje, že nastavení stránky vlastností byl změněn od posledního se uplatňují; FALSE označuje, že nastavení stránky vlastností se použily, nebo třeba ji ignorovat.

### <a name="remarks"></a>Poznámky

Seznam vlastností udržuje sledování, které stránky jsou "nečisté", to znamená, u kterých jste volali stránky vlastností `SetModified( TRUE )`. **Použít** tlačítko bude vždy povolen při volání `SetModified( TRUE )` pro jednu ze stránek. **Použít** tlačítka se deaktivuje při volání `SetModified( FALSE )` pro jednu ze stránek, ale pouze pokud žádná z ostatních stránek není "dirty."

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
