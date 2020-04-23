---
title: CCmdUI – třída
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
ms.openlocfilehash: 3e167d9e305481e05808f5e553222c10abbc88de
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752723"
---
# <a name="ccmdui-class"></a>CCmdUI – třída

Používá se pouze `ON_UPDATE_COMMAND_UI` v `CCmdTarget`rámci obslužné rutiny v odvozené třídě.

## <a name="syntax"></a>Syntaxe

```
class CCmdUI
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CCmdUI::ContinueRouting](#continuerouting)|Sděluje mechanismus směrování příkazů, aby pokračoval v směrování aktuální zprávy v řetězci obslužných rutin.|
|[CCmdUI::Povolit](#enable)|Povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz.|
|[CCmdUI::SetCheck](#setcheck)|Nastaví stav kontroly položky uživatelského rozhraní pro tento příkaz.|
|[CCmdUI::SetRadio](#setradio)|Stejně `SetCheck` jako členská funkce, ale funguje na rozhlasových skupinách.|
|[CCmdUI::SetText](#settext)|Nastaví text pro položku uživatelského rozhraní pro tento příkaz.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CCmdUI::m_nID](#m_nid)|ID objektu uživatelského rozhraní.|
|[CCmdUI::m_nIndex](#m_nindex)|Index objektu uživatelského rozhraní.|
|[CCmdUI::m_pMenu](#m_pmenu)|Odkazuje na nabídku `CCmdUI` reprezentovanou objektem.|
|[CCmdUI::m_pOther](#m_pother)|Odkazuje na objekt okna, který odeslal oznámení.|
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Odkazuje na obsaženou podnabídku `CCmdUI` reprezentovanou objektem.|

## <a name="remarks"></a>Poznámky

`CCmdUI`nemá základní třídu.

Když uživatel aplikace stáhne nabídku dolů, každá položka nabídky musí vědět, zda by měla být zobrazena jako povolená nebo zakázaná. Cíl příkazu nabídky poskytuje tyto informace implementací obslužné rutiny ON_UPDATE_COMMAND_UI. Pro každý z objektů uživatelského rozhraní příkazu v aplikaci použijte okno [Průvodce třídou](mfc-class-wizard.md) nebo **Vlastnosti** (v **zobrazení třídy)** k vytvoření prototypu položky mapy zpráv a funkce pro každou obslužnou rutinu.

Při stažené nabídky, rozhraní prohledá a volá každý ON_UPDATE_COMMAND_UI `CCmdUI` obslužné rutiny, každý obslužná rutina volá členské funkce, jako `Enable` je například a `Check`, a rozhraní pak odpovídajícím způsobem zobrazí každou položku nabídky.

Položku nabídky lze nahradit tlačítkem ovládacího panelu nebo jiným objektem uživatelského rozhraní příkazu bez změny kódu v obslužné rutině. `ON_UPDATE_COMMAND_UI`

Následující tabulka shrnuje `CCmdUI`efekt členských funkcí příkazu na různé položky uživatelského rozhraní příkazu.

|Položka uživatelského rozhraní|Povolení|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Položka nabídky|Povolí nebo zakáže|Kontroly nebo zrušení kontrol|Kontroluje pomocí tečky|Nastaví text položky.|
|Tlačítko Panel nástrojů|Povolí nebo zakáže|Vybere, zruší výběr nebo neurčité.|Stejné jako`SetCheck`|(Nelze použít)|
|Podokno stavového řádku|Zviditelnění nebo neviditelného textu|Nastaví vyskakovací nebo normální ohraničení.|Stejné jako`SetCheck`|Nastaví text podokna|
|Normální tlačítko v`CDialogBar`|Povolí nebo zakáže|Zaškrtávací políčko Kontroly nebo zrušení kontroly|Stejné jako`SetCheck`|Nastaví text tlačítka|
|Normální ovládání v`CDialogBar`|Povolí nebo zakáže|(Nelze použít)|(Nelze použít)|Nastaví text okna.|

Další informace o použití této třídy naleznete v tématu [Jak aktualizovat objekty uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CCmdUI`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="ccmduicontinuerouting"></a><a name="continuerouting"></a>CCmdUI::ContinueRouting

Volání této členské funkce sdělte mechanismu směrování příkazů, aby pokračoval v směrování aktuální zprávy v řetězci obslužných rutin.

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>Poznámky

Toto je pokročilá členská funkce, která by měla být použita ve spojení s obslužnou rutinou ON_COMMAND_EX, která vrací hodnotu FALSE. Další informace naleznete [v technické poznámce 6](../../mfc/tn006-message-maps.md).

## <a name="ccmduienable"></a><a name="enable"></a>CCmdUI::Povolit

Volání této členské funkce povolit nebo zakázat položku uživatelského rozhraní pro tento příkaz.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
TRUE povolit položku, FALSE zakázat.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

## <a name="ccmduim_nid"></a><a name="m_nid"></a>CCmdUI::m_nID

ID položky nabídky, tlačítka panelu nástrojů nebo jiného `CCmdUI` objektu uživatelského rozhraní reprezentovaného objektem.

```
UINT m_nID;
```

## <a name="ccmduim_nindex"></a><a name="m_nindex"></a>CCmdUI::m_nIndex

Index položky nabídky, tlačítka panelu nástrojů nebo jiného `CCmdUI` objektu uživatelského rozhraní reprezentovaného objektem.

```
UINT m_nIndex;
```

## <a name="ccmduim_pmenu"></a><a name="m_pmenu"></a>CCmdUI::m_pMenu

Ukazatel `CMenu` (typu) na nabídku `CCmdUI` reprezentovanou objektem.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Poznámky

NULL, pokud položka není nabídka.

## <a name="ccmduim_psubmenu"></a><a name="m_psubmenu"></a>CCmdUI::m_pSubMenu

Ukazatel `CMenu` (typu) na obsaženou podnabídku `CCmdUI` reprezentovanou objektem.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Poznámky

NULL, pokud položka není nabídka. Pokud je dílčí nabídka rozbalovací, *m_nID* obsahuje ID první položky v rozbalovací nabídce. Další informace naleznete [v technické poznámce 21](../../mfc/tn021-command-and-message-routing.md).

## <a name="ccmduim_pother"></a><a name="m_pother"></a>CCmdUI::m_pOther

Ukazatel (typu) `CWnd`na objekt okna, například nástroj nebo stavový řádek, který odeslal oznámení.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Poznámky

NULL, pokud je položka nabídka `CWnd` nebo non-objekt.

## <a name="ccmduisetcheck"></a><a name="setcheck"></a>CCmdUI::SetCheck

Volání této členské funkce nastavit položku uživatelského rozhraní pro tento příkaz do příslušného stavu kontroly.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Parametry

*nKontrola*<br/>
Určuje stav kontroly, který má být nastaven. Pokud 0, zrušit kontroly; pokud 1, kontroly; a pokud 2, nastaví neurčitý.

### <a name="remarks"></a>Poznámky

Tato členská funkce funguje pro položky nabídky a tlačítka panelu nástrojů. Neurčitý stav platí pouze pro tlačítka panelu nástrojů.

## <a name="ccmduisetradio"></a><a name="setradio"></a>CCmdUI::SetRadio

Volání této členské funkce nastavit položku uživatelského rozhraní pro tento příkaz do příslušného stavu kontroly.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
TRUE povolit položku; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce `SetCheck`funguje jako , s tím rozdílem, že pracuje na položky uživatelského rozhraní, které fungují jako součást rozhlasové skupiny. Zrušení zaškrtnutí ostatních položek ve skupině není automatické, pokud položky samy o sobě nezachovávají chování rádiové skupiny.

## <a name="ccmduisettext"></a><a name="settext"></a>CCmdUI::SetText

Volání této členské funkce nastavit text položky uživatelského rozhraní pro tento příkaz.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Ukazatel na textový řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Viz také

[MDI vzorku knihovny MFc](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
