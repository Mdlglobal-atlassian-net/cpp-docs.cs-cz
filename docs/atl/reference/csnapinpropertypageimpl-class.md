---
title: CSnapInPropertyPageImpl Class
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
ms.openlocfilehash: abf4cf5804f6ef7335192feb298f1a4a06f841e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496396"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl Class

Tato třída poskytuje metody pro implementaci objektu stránky vlastností modulu snap-in.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Změní stav tlačítek **OK** a **Storno** .|
|[CSnapInPropertyPageImpl::Create](#create)|Inicializuje nově vytvořený `CSnapInPropertyPageImpl` objekt.|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Volá se rozhraním, když uživatel klikne na tlačítko **použít nyní** při použití seznamu vlastností Průvodce-typ.|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Volá se rozhraním, když uživatel klikne na tlačítko **pomoci** při použití seznamu vlastností Průvodce-typ.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Volá se rozhraním, když aktuální stránka už není aktivní.|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Volá se rozhraním, když uživatel klikne na tlačítko **Storno** a před tím, než bylo zrušení provedeno.|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Volá se rozhraním, když uživatel klikne na tlačítko **obnovit** při použití seznamu vlastností Průvodce-typ.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Volá se rozhraním, když se aktivuje aktuální stránka.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Volá se rozhraním, když uživatel klikne na tlačítko **zpět** při použití seznamu vlastností Průvodce-typ.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Volá se rozhraním, když uživatel klikne na tlačítko **Dokončit** při použití seznamu vlastností Průvodce-typ.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Volá se rozhraním, když uživatel klikne na tlačítko **Další** při použití seznamu vlastností Průvodce-typ.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Přepošle aktuální zprávu na všechny stránky seznamu vlastností.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Zavolejte na aktivovat nebo deaktivovat tlačítko **použít nyní** .|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Struktura systému `PROPSHEETPAGE` Windows, kterou `CSnapInPropertyPageImpl` objekt používá.|

## <a name="remarks"></a>Poznámky

`CSnapInPropertyPageImpl`poskytuje základní implementaci objektu stránky vlastností modulu snap-in. Základní funkce stránky vlastností modulu snap-in jsou implementovány pomocí několika různých rozhraní a typů map.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsnap. h

##  <a name="canceltoclose"></a>  CSnapInPropertyPageImpl::CancelToClose

Volání této funkce poté, co byla provedena neopravitelná změna na data na stránce modálního seznamu vlastností.

```
void CancelToClose();
```

### <a name="remarks"></a>Poznámky

Tato funkce změní tlačítko **OK** na **Zavřít** a zakáže tlačítko **Storno** . Tato změna upozorní uživatele, že změna je trvalá a změny nelze zrušit.

Členská funkce neprovede v nemodálním seznamu vlastností nic, protože nemodální seznam vlastností nemá ve výchozím nastavení tlačítko **Storno.** `CancelToClose`

##  <a name="csnapinpropertypageimpl"></a>  CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

`CSnapInPropertyPageImpl` Vytvoří objekt.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
pro Název stránky vlastností

### <a name="remarks"></a>Poznámky

Chcete-li inicializovat podkladovou strukturu, zavolejte [CSnapInPropertyPageImpl:: Create](#create).

##  <a name="create"></a>  CSnapInPropertyPageImpl::Create

Voláním této funkce inicializujete podkladovou strukturu stránky vlastností.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač `PROPSHEETPAGE` struktury obsahující atributy nově vytvořeného seznamu vlastností.

### <a name="remarks"></a>Poznámky

Před voláním této funkce byste nejdřív měli zavolat [CSnapInPropertyPageImpl:: CSnapInPropertyPageImpl](#csnapinpropertypageimpl) .

##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp

`m_psp`je struktura, jejíž členové ukládají charakteristiky `PROPSHEETPAGE`.

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Poznámky

Tuto strukturu použijte k inicializaci vzhledu stránky vlastností poté, co je vytvořena.

Další informace o této struktuře, včetně výpisu jejích členů, najdete v tématu [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) v Windows SDK.

##  <a name="onapply"></a>  CSnapInPropertyPageImpl::OnApply

Tato členská funkce se volá, když uživatel klikne na tlačítko **OK** nebo **použít nyní** .

```
BOOL OnApply();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou změny přijaty; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Před `OnApply` voláním rozhraní může být nutné volat `SetModified` a nastavit jeho parametr na hodnotu true. Tím se aktivuje tlačítko **použít nyní** , jakmile uživatel provede změnu na stránce vlastností.

Přepište tuto členskou funkci, pokud chcete určit akci, kterou program provede, když uživatel klikne na tlačítko **použít nyní** . Při přepsání by měla funkce vracet hodnotu TRUE, aby přijímala změny a nedocházelo k tomu, aby se změny projevily.

Výchozí implementace `OnApply` funkce vrátí hodnotu true.

##  <a name="onhelp"></a>CSnapInPropertyPageImpl:: help

Tato členská funkce se volá, když uživatel klikne na tlačítko pro **nápovědu** pro stránku vlastností.

```
void OnHelp();
```

### <a name="remarks"></a>Poznámky

Tuto členskou funkci přepište, pokud chcete zobrazit nápovědu pro stránku vlastností.

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

Tato členská funkce se volá, když stránka už není aktivní stránkou.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla data úspěšně aktualizována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci pro provádění speciálních úloh ověření dat.

##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel

Tato členská funkce se volá, když uživatel klikne na tlačítko **Storno** a před tím, než dojde k akci zrušit.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové pro povolení operace zrušení; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci přepište, pokud chcete určit akci, kterou program provede, když uživatel klikne na tlačítko **Storno** .

Výchozí implementace `OnQueryCancel` funkce vrátí hodnotu true.

##  <a name="onreset"></a>  CSnapInPropertyPageImpl::OnReset

Tato členská funkce se volá, když uživatel klikne na tlačítko **Storno** .

```
void OnReset();
```

### <a name="remarks"></a>Poznámky

Když je tato funkce volána, změny všech stránek vlastností, které byly provedeny uživatelem dříve, klikněte na tlačítko **použít nyní** , jsou zahozeny a seznam vlastností zůstane aktivní.

Tuto členskou funkci přepište, pokud chcete určit, jakou akci program provede, když uživatel klikne na tlačítko **Storno** .

##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive

Tato členská funkce se volá, když uživatel vybere stránku a bude se jednat o aktivní stránku.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla stránka úspěšně nastavena jako aktivní; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci, aby se prováděly úlohy při aktivaci stránky. Vaše přepsání této členské funkce by mělo volat výchozí verzi před provedením jakéhokoli jiného zpracování.

Výchozí implementace vrátí hodnotu TRUE.

##  <a name="onwizardback"></a>  CSnapInPropertyPageImpl::OnWizardBack

Tato členská funkce se volá, když uživatel klikne na tlačítko **zpět** v průvodci.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Návratová hodnota

- 0 pro automatické přechodu na předchozí stránku.

- -1, pokud chcete zabránit změně stránky.

Chcete-li přejít na jinou stránku, než na další, vraťte identifikátor dialogového okna, které se má zobrazit.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci, pokud chcete určit určitou akci, kterou musí uživatel provést po kliknutí na tlačítko **zpět** .

##  <a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish

Tato členská funkce se volá, když uživatel klikne na tlačítko **Dokončit** v průvodci.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je seznam vlastností zničen po dokončení Průvodce; jinak nula.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci, pokud chcete určit určitou akci, kterou musí uživatel provést při kliknutí na tlačítko pro **dokončení** .

##  <a name="onwizardnext"></a>  CSnapInPropertyPageImpl::OnWizardNext

Tato členská funkce se volá, když uživatel klikne na tlačítko **Další** v průvodci.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Návratová hodnota

- 0 pro automatické přechodu na další stránku.

- -1, pokud chcete zabránit změně stránky.

Chcete-li přejít na jinou stránku, než na další, vraťte identifikátor dialogového okna, které se má zobrazit.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci, pokud chcete určit určitou akci, kterou musí uživatel provést při kliknutí na tlačítko přechodu na **Další krok** .

##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings

Tuto členskou funkci volejte pro přeposlání zprávy na každou stránku v seznamu vlastností.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
pro Určuje další informace závislé na zprávě.

*lParam*<br/>
pro Určuje další informace závislé na zprávě.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud by zpráva neměla být předána na další stránku vlastností; jinak nula.

### <a name="remarks"></a>Poznámky

Pokud stránka vrátí nenulovou hodnotu, seznam vlastností zprávu nepošle na další stránky.

##  <a name="setmodified"></a>  CSnapInPropertyPageImpl::SetModified

Voláním této členské funkce povolíte nebo zakážete tlačítko **použít nyní** na základě toho, zda by mělo být nastavení na stránce vlastností použito na příslušný externí objekt.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parametry

*bChanged*<br/>
pro TRUE pro indikaci, že nastavení stránky vlastností bylo od posledního použití změněno; FALSE pro indikaci, že nastavení stránky vlastností bylo použito nebo by mělo být ignorováno.

### <a name="remarks"></a>Poznámky

Seznam vlastností uchovává přehled o tom, které stránky jsou "dirty", což jsou stránky vlastností, pro které jste `SetModified( TRUE )`volali. Tlačítko **použít nyní** bude vždy povoleno, pokud zavoláte `SetModified( TRUE )` jednu ze stránek. Tlačítko **použít nyní** bude zakázáno při volání `SetModified( FALSE )` na jednu ze stránek, ale pouze v případě, že žádná z ostatních stránek není "dirty".

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
