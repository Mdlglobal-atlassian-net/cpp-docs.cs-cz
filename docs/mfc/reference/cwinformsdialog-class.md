---
title: Třída CWinFormsDialog
ms.date: 03/27/2019
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
ms.openlocfilehash: 3772033df59e065cedca61012cd479c812cf5b66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367431"
---
# <a name="cwinformsdialog-class"></a>Třída CWinFormsDialog

Obálka pro třídu dialogového okna knihovny MFC, která je hostitelem uživatelského ovládacího prvku Windows Forms.

## <a name="syntax"></a>Syntaxe

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>Parametry

*Ovládací prvek TManagedControl*<br/>
Uživatelský ovládací prvek rozhraní .NET Framework, který se zobrazí v aplikaci knihovny MFC.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CWinFormsDialog::Dialog CWinFormsDialog](#cwinformsdialog)|Vytvoří `CWinFormsDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CWinFormsDialog::Ovládací prvek GetControl](#getcontrol)|Načte odkaz na uživatelský ovládací prvek Windows Forms.|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Načte popisovač okna do uživatelského ovládacího prvku Windows Forms.|
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Inicializuje dialogové okno Knihovny MFC vytvořením a hostováním uživatelského ovládacího prvku windows forms.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)||
|----------|-|
|[CWinFormsDialog::operátor -&gt;](#operator_-_gt)|Nahradí [cWinFormsDialog::GetControl](#getcontrol) ve výrazech.|
|[CWinFormsDialog::operátor TManagedControl^](#operator-tmanagedcontrol-hat)|Přetypuje typ jako odkaz na uživatelský ovládací prvek windows forms.|

## <a name="remarks"></a>Poznámky

`CWinFormsDialog`je obálka pro třídu dialogového okna knihovny MFC ( [CDialog),](../../mfc/reference/cdialog-class.md)která je hostitelem uživatelského ovládacího prvku Windows Forms. To umožňuje zobrazení ovládacích prvků rozhraní .NET Framework v modálním nebo nemodálním dialogovém okně knihovny MFC.

Další informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) a [hostování uživatelského ovládacího prvku formuláře systému Windows jako dialogového okna knihovny MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a>CWinFormsDialog::Dialog CWinFormsDialog

Vytvoří `CWinFormsDialog` objekt.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Parametry

*nIDŠablona*<br/>
Obsahuje ID prostředku šablony dialogového okna. Pomocí editoru dialogů vytvořte šablonu dialogu a uložte ji do souboru skriptu prostředků aplikace. Další informace o šablonách dialogů naleznete v [tématu CDialog Class](../../mfc/reference/cdialog-class.md).

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a>CWinFormsDialog::Ovládací prvek GetControl

Načte odkaz na uživatelský ovládací prvek Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na ovládací prvek Windows Forms v dialogovém okně knihovny MFC.

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsDialog::GetControlHandle

Načte popisovač okna do uživatelského ovládacího prvku Windows Forms.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač okna uživatelskému ovládacímu prvku Windows Forms.

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a>CWinFormsDialog::OnInitDialog

Inicializuje dialogové okno Knihovny MFC vytvořením a hostováním uživatelského ovládacího prvku windows forms.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která určuje, zda aplikace nastavila vstupní fokus na jeden z ovládacích prvků v dialogovém okně. Pokud `OnInitDialog` vrátí nenulovou hodnotu, systém Windows nastaví vstupní fokus na první ovládací prvek v dialogovém okně. Tato metoda může vrátit 0 pouze v případě, že aplikace explicitně nastavila vstupní fokus na jeden z ovládacích prvků v dialogovém okně.

### <a name="remarks"></a>Poznámky

Při vytvoření dialogového okna Knihovna MFC (pomocí [metody Create](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect)nebo [DoModal](../../mfc/reference/cdialog-class.md#domodal) zděděné z [cdialog](../../mfc/reference/cdialog-class.md)) je odeslána WM_INITDIALOG zpráva a tato metoda je volána. Vytvoří instanci ovládacího prvku Windows Forms v dialogovém okně a upraví velikost dialogového okna tak, aby vyhovovala velikosti uživatelského ovládacího prvku. Poté hostuje nový ovládací prvek v dialogovém okně knihovny MFC.

Přepište tuto členovou funkci, pokud potřebujete provést speciální zpracování při inicializování dialogového okna. Další informace o použití této metody naleznete v [tématu CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a>CWinFormsDialog::operátor -&gt;

Nahradí [cWinFormsDialog::GetControl](#getcontrol) ve výrazech.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor poskytuje pohodlnou `GetControl` syntaxi, která nahrazuje ve výrazech.

Informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a>CWinFormsDialog::operátor TManagedControl^

Přetypuje typ jako odkaz na uživatelský ovládací prvek windows forms.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor přetypuje typ jako odkaz na ovládací prvek Windows Forms. Používá se k `CWinFormsDialog<TManagedControl>` předání dialogového okna funkcím, které přijímají ukazatel na objekt uživatelského ovládacího prvku formuláře Windows Forms.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Třída CWinFormsView](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
