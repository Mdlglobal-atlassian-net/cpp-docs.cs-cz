---
title: CCmdUI – – třída
ms.date: 09/06/2019
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
ms.openlocfilehash: 42aec2937cd81ebbb50482321b8deae001723d3a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907828"
---
# <a name="ccmdui-class"></a>CCmdUI – – třída

Se používá pouze v rámci `ON_UPDATE_COMMAND_UI` obslužné rutiny `CCmdTarget`v odvozené třídě.

## <a name="syntax"></a>Syntaxe

```
class CCmdUI
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CCmdUI::ContinueRouting](#continuerouting)|Oznamuje mechanismu směrování příkazů, aby pokračoval v směrování aktuální zprávy o řetězu obslužných rutin.|
|[CCmdUI –:: Enable](#enable)|Povoluje nebo zakazuje položku uživatelského rozhraní pro tento příkaz.|
|[CCmdUI –:: SetCheck](#setcheck)|Nastaví stav kontroly položky uživatelského rozhraní pro tento příkaz.|
|[CCmdUI::SetRadio](#setradio)|Podobně jako `SetCheck` členské funkce, ale funguje ve skupinách přepínačů.|
|[CCmdUI::SetText](#settext)|Nastaví text pro položku uživatelského rozhraní pro tento příkaz.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CCmdUI::m_nID](#m_nid)|ID objektu uživatelského rozhraní.|
|[CCmdUI::m_nIndex](#m_nindex)|Index objektu uživatelského rozhraní.|
|[CCmdUI::m_pMenu](#m_pmenu)|Odkazuje na nabídku reprezentovanou `CCmdUI` objektem.|
|[CCmdUI::m_pOther](#m_pother)|Odkazuje na objekt Window, který odeslal oznámení.|
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Odkazuje na obsaženou podnabídku reprezentovanou `CCmdUI` objektem.|

## <a name="remarks"></a>Poznámky

`CCmdUI`nemá základní třídu.

Když uživatel vaší aplikace vyžádá nabídku dolů, musí každá položka nabídky obsahovat informace o tom, jestli má být zobrazená jako povolená nebo zakázaná. Cíl příkazu nabídky poskytuje tyto informace implementací obslužné rutiny ON_UPDATE_COMMAND_UI. Pro každý příkaz pro objekty uživatelského rozhraní v aplikaci použijte [Průvodce třídou](mfc-class-wizard.md) nebo okno **vlastností** (v **zobrazení tříd**) k vytvoření položky mapování zpráv a prototypu funkce pro každou obslužnou rutinu.

Když je nabídka vyvolána, rozhraní vyhledá a zavolá každou obslužnou rutinu ON_UPDATE_COMMAND_UI, každá `CCmdUI` obslužná rutina volá `Enable` členské `Check`funkce, jako jsou a a rozhraní a následně zobrazí každou položku nabídky.

Položka nabídky může být nahrazena tlačítkem ovládacího panelu nebo jiným objektem uživatelského rozhraní příkazu bez změny kódu v `ON_UPDATE_COMMAND_UI` obslužné rutině.

Následující tabulka shrnuje členské funkce efektu `CCmdUI`v různých příkazech uživatelského rozhraní.

|Položka uživatelského rozhraní|Povolit|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Položka nabídky|Povoluje nebo zakazuje|Zkontroluje nebo vrátí.|Kontroluje použití tečky.|Nastaví text položky|
|Tlačítko panelu nástrojů|Povoluje nebo zakazuje|Vybere, nevybere nebo neurčité|Stejné jako`SetCheck`|(Nelze použít)|
|Podokno stavového řádku|Změní text na viditelný nebo neviditelný.|Nastaví automaticky otevírané okno nebo normální ohraničení.|Stejné jako`SetCheck`|Nastaví text podokna.|
|Tlačítko normální v`CDialogBar`|Povoluje nebo zakazuje|Zaškrtávací políčko nebo zrušení kontroly|Stejné jako`SetCheck`|Nastaví text tlačítka.|
|Normální řízení v`CDialogBar`|Povoluje nebo zakazuje|(Nelze použít)|(Nelze použít)|Nastaví text okna.|

Další informace o použití této třídy naleznete v tématu [jak aktualizovat objekty uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CCmdUI`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="continuerouting"></a>CCmdUI –:: ContinueRouting

Zavolejte tuto členskou funkci pro oznámení mechanismu směrování příkazů, aby pokračovalo v směrování aktuální zprávy o řetězu obslužných rutin.

```
void ContinueRouting();
```

### <a name="remarks"></a>Poznámky

Toto je pokročilá členská funkce, která by se měla používat ve spojení s obslužnou rutinou ON_COMMAND_EX, která vrací hodnotu FALSE. Další informace najdete v části [technická Poznámka 6](../../mfc/tn006-message-maps.md).

##  <a name="enable"></a>CCmdUI –:: Enable

Voláním této členské funkce povolíte nebo zakážete položku uživatelského rozhraní pro tento příkaz.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*Přání*<br/>
TRUE pro povolení položky, FALSE pro její zakázání

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

##  <a name="m_nid"></a>CCmdUI –:: m_nID

ID položky nabídky, tlačítka panelu nástrojů nebo jiného objektu uživatelského rozhraní reprezentovaného `CCmdUI` objektem.

```
UINT m_nID;
```

##  <a name="m_nindex"></a>CCmdUI –:: m_nIndex

Index položky nabídky, tlačítka panelu nástrojů nebo jiného objektu uživatelského rozhraní reprezentovaného `CCmdUI` objektem.

```
UINT m_nIndex;
```

##  <a name="m_pmenu"></a>CCmdUI –:: m_pMenu

Ukazatel ( `CMenu` typu) do nabídky reprezentované `CCmdUI` objektem.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Poznámky

Hodnota NULL, pokud položka není nabídka.

##  <a name="m_psubmenu"></a>CCmdUI –:: m_pSubMenu

Ukazatel ( `CMenu` typu) na obsaženou podnabídku reprezentovanou `CCmdUI` objektem.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Poznámky

Hodnota NULL, pokud položka není nabídka. Pokud je podnabídkou automaticky otevírané okno, *m_nID* obsahuje ID první položky v místní nabídce. Další informace najdete v části [technická Poznámka 21](../../mfc/tn021-command-and-message-routing.md).

##  <a name="m_pother"></a>CCmdUI –:: m_pOther

Ukazatel (typu `CWnd`) k objektu Window, jako je například nástroj nebo stavový řádek, který odeslal oznámení.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Poznámky

Hodnota null, pokud je položka nabídka nebo `CWnd` objekt, který není objektem.

##  <a name="setcheck"></a>CCmdUI –:: SetCheck

Zavolejte tuto členskou funkci pro nastavení položky uživatelského rozhraní pro tento příkaz na příslušný stav kontroly.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Parametry

*Npokuste*<br/>
Určuje stav kontroly, který se má nastavit. Pokud 0, zrušit kontrolu; Pokud 1, zkontroluje; a pokud 2, nastaví neurčitelné.

### <a name="remarks"></a>Poznámky

Tato členská funkce funguje pro položky nabídky a tlačítka panelu nástrojů. Neurčitý stav se vztahuje pouze na tlačítka panelu nástrojů.

##  <a name="setradio"></a>CCmdUI –:: SetRadio

Zavolejte tuto členskou funkci pro nastavení položky uživatelského rozhraní pro tento příkaz na příslušný stav kontroly.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*Přání*<br/>
TRUE pro povolení položky; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce funguje `SetCheck`jako, s tím rozdílem, že funguje na položkách uživatelského rozhraní, které fungují jako součást skupiny přepínačů. Zrušení kontroly ostatních položek ve skupině není automatické, pokud tyto položky neudržují chování skupiny rádi.

##  <a name="settext"></a>CCmdUI –:: SetText

Chcete-li nastavit text položky uživatelského rozhraní pro tento příkaz, zavolejte tuto členskou funkci.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Ukazatel na textový řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázka MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
